# Description
ReadCSVFile.py module does the following:
```
- Ingest the reports generated (*.tar.gz files) by the Red Hat Cost Management Metrics Operator
- Untar the files
- Identify the report with the metric 'node_capacity_cpu_cores'
- Retrieve the information 'interval_start', 'interval_end', 'node'
- Aggregate the details per hour to provide the max vCPU count usage for a specific OpenShift cluster
```
# Pre-requisites

- OpenShift cluster version 4.9 or higher
- Red Hat Cost Management Metrics operator v1.1.9 deployed via OpenShift Web Console or OpenShift CLI
- Reports generated for a period of time, for a month, by the operator are downloaded and stored in a directory accessible by the Python module

Please install the following Python packages on the machine which will be used to run this Python module: \
```
Python (Version: 3.9.7) \
Pandas (Version: 1.5.2) \
Natsorted (Version: ) \
CSV (Version: )
```

# Install the Red Hat Cost Management Metrics Operator


# Things to note:
- The Operator v1.1.9 generates a report once every 6 hours
- The Operator generates 4 files
- Generated file names have the following pattern:\
```
*_openshift_usage_report.0.csv\
*_openshift_usage_report.1.csv\
*_openshift_usage_report.2.csv\
*_openshift_usage_report.3.csv\
```

- _report_0.csv has namespace related information
- _report_1.csv has node related information
- _report_2.csv has pod related information including node capacity
- _report_3.csv has persistent volume related information

# Command to run the Python module
Please use the following command to execute the Python module
```
$ python ReadCSVFile.py <directory where the downloaded reports are stored>
```
E.g.:
```
$ python ReadCSVFile.py /users/operator-reports/upload/
```

# Open Issues

The following issues are open with the Red Hat BU:
```
https://issues.redhat.com/projects/COST/issues/COST-3309
```

The following issues need to be addressed with the Python module:
```
- Start and End date range as an input parameter to the Python module
```
