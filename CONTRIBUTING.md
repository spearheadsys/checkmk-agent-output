# CONTRIBUTING to Checkmk agent output

:+1::tada: First of all, thank you for taking the time to contribute! :tada::+1:

The following is a set of guidelines for contributing to Checkmk agent output.

These are mostly guidelines, not rules. Use your best judgment, and feel free to propose changes to this document in a pull request.


## Welcome
As Checkmk users we would like to "monitor all the things". As Checkmk partners working with Tribe29 to resell and provide value added services we often have to provide demos and PoC's for systems we do not have access to. 


This repo and our efforts in collecting this output resolves for us and hopefully others the following challenges:
- confirming that Checkmk can monitor particular systems and showcasing these using stored agent output
- development of checks whether by extending existing ones or to begin a development effort from scratch


## Scenarios
Checkmk is growing steadily with new checks added weekly and the community doing custom work. However we sometimes find ourselves in one of the following situations:

1. A potential Checkmk user would like to "see" what their systems look like while being monitored with Checkmk. 
2. An existing check could be extended to iunclude new features.
3. An existing check could be refactored for performance, new metrics ,etc.
4. As a Checkmk partener (reseller, support, services) you may be tasked to demo Checkmk for specific systems that you do not have access to and could not

## Contributing

We invite anyone that is interested in providing us with agent output to do so taking care to anonymize the data and strip it of any confidential data. 

## Getting started 

There are three types of agent output we are looking for:

1. [SNMP based agent output](#snmp-based-agent-output)
2. [Checkmk agent based output](#checkmk-agent-based-output)
3. [Checkmk active checks output](#checkmk-active-checks-output)

Below are methods for obtaining the agent output, storing it and adding it to this repository.

### SNMP based agent output
To generate [SNMP based output](https://docs.checkmk.com/latest/en/snmp.html#simulation) you must first add your system to Checkmk. You can then use one of the following procedures based on which you prefer:

* The command line: 

`OMD[mysite]:~$ cmk --snmpwalk switch23`

The output will be saved in the var/check_mk/snmpwalks directory. This file needs to be anonymized and stripped of confidential data (see below).

Please read the [official documentation](https://docs.checkmk.com/latest/en/snmp.html#_creating_a_walk_from_the_command_line) regarding the generation of this output specifically if your SNMP device does not provide all OID via a snmapwalk. Specifically you may be required to use the `--extraoid <OID>` option to cmk `--snmapwalk`


* The Web UI:
You can [generate an SNMP from the Web UI](https://docs.checkmk.com/latest/en/snmp.html#snmpwalks). Use the context menu of the Checkmk service (the hamburger menu) and click on Download SNMP walk.


### Checkmk agent based output

tbd.

### Checkmk active checks output

tbd.

## Anonymizing and stripping confidential data
Please read this carefully as it is important that you do not upload confidential/sensitive data to this repository. This service is public and anyone can access this information.

Anonymization will depend on the system/application you are generating the output for. For example, snmp based output generally has the sysDescr OID which may contain sensitive information. If you have naming conventions for networks/vlans from which sensitive information can be deduced you may want to remove those as well.

Another potential place to look for sensitive information is the process table, if applicable to your system. You may possibly want to look for processes that contain usernames/passwords/etc in the actual command line.

Keeping the output sane is importnat so that these outputs can then be succesfully used within Checkmk. We recommend that you do not remove entire lines from the output but rather obfuscate or anonimize.

Another potential piece of sensitive information that may be found in standard snmp output is the IP address as part of an OID. Public IP addresses can usually be traced to a company, server, etc. so please remove such addresses from your output. Non-routable/internal IP addresses are usually fine.


As we gather more experience we will update our documentation and recommendations accordingly.




