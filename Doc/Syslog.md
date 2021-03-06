# Syslog

This input option allows you to listen to Syslog Events either through a UDP port or by attaching Real-Time KQL to a local log file.

**You can watch a demonstration of using Real-Time KQL for Syslog [here](https://youtu.be/kw6bSGolnpU).**

**Jump To:**

* [UDP Port Monitoring](#UDPPort)
  * [Listening to a specific port](#PortListening)
* [Log File Monitoring](#LogFile)
  * [Reading a local log file](#FileReading)
* [Syslog Options Overview](#SyslogOptionsOverview)



## <a id="UDPPort"></a>UDP Port Monitoring

### <a id="PortListening"></a>Listening to a specific port

You can attach Real-Time KQL to a UDP port of your choice to capture all incoming syslog messages.

**Example usage**:

`sudo ./RealTimeKql syslog --udpport=514 --outputconsole`

**Example breakdown**:

* `--udpport=514` : listen to UDP port 514
* `--outputconsole` : print events to console



## <a id="LogFile"></a>Log File Monitoring

### <a id="FileReading"></a>Reading a local log file

You can also use Real-Time KQL to process local log files generated by syslog services such as rsyslogd.

**Example Usage:**

`sudo ./RealTimeKql syslog --logfile=/var/log/auth.log --outputconsole `

**Example Usage Breakdown:**

* `--logfile=/var/log/auth.log` : attach Real-Time KQL to the `/var/log/auth.log` file
* `--outputconsole` : write the results to console



## <a id="SyslogOptionsOverview"></a>Syslog Options Overview

You can also run `sudo ./RealTimeKql syslog --help ` from the terminal to get this same overview of your options:

```
Usage: RealTimeKql Syslog [options]

Options:
  -?|-h|--help                                 Show help information
  -n|--networkAdapter <value>                  Network Adapter Name. Optional, when not specified, listner listens on all adapters. Used along with UDP Port.
  -p|--udpport <value>                         Listen to a UDP port for syslog messages. eg, --udpport=514.
  -l|--logfile <value>                         Retrieve syslog messages from local log specified. eg, --logfile=/var/log/syslog.
  -q|--query <value>                           Optional: KQL filter query file that describes what processing to apply to the events on the stream. It uses a subset of Kusto Query Language, https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/
  -oc|--outputconsole                          Log the output to console.
  -oj|--outputjson <value>                     Write output to JSON file. eg, --outputjson=FilterOutput.json
  -bscs|--blobstorageconnectionstring <value>  Azure Blob Storage Connection string. Optional when want to upload as JSON to blob storage.
  -bsc|--blobstoragecontainer <value>          Azure Blob Storage container name. Optional when want to upload as JSON to blob storage.
  -ad|--adxauthority <value>                   Azure Data Explorer (ADX) authority. Optional when not specified microsoft.com is used. eg, --adxauthority=microsoft.com
  -aclid|--adxclientid <value>                 Azure Data Explorer (ADX) ClientId. Optional ClientId that has permissions to access Azure Data Explorer.
  -akey|--adxkey <value>                       Azure Data Explorer (ADX) Access Key. Used along with ClientApp Id
  -ac|--adxcluster <value>                     Azure Data Explorer (ADX) cluster address. eg, --adxcluster=CDOC.kusto.windows.net
  -ad|--adxdatabase <value>                    Azure Data Explorer (ADX) database name. eg, --adxdatabase=TestDb
  -at|--adxtable <value>                       Azure Data Explorer (ADX) table name. eg, --adxtable=OutputTable
  -ar|--adxreset                               The existing data in the destination table is dropped before new data is logged.
  -ad|--adxdirect                              Default upload to ADX is using queued ingest. Use this option to do a direct ingest to ADX.
```