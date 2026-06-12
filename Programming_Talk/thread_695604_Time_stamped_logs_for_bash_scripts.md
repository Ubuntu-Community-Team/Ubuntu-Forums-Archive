---
title: "Time stamped logs for bash scripts"
date: 2008-02-13
forum: Programming Talk
---

### Post by mjhaas on 2008-02-13
I've been working on a way to log various administrative scripts in the way that I want and after much head scratching I've hit on a way to do it using named pipes. As I didn't google any similar solutions I thought I'd post my code here in case anyone else wants it.

```
#!/bin/bash
#
# Functions to log scripts to to a file. Inputs, standard output and standard
# error are all logged with a time stamp prefix. File descriptors 4 and 5 are
# used to save standard output and standard error.
#
# Usage
#
# . logging.sh
#
# start_logging logfile "%F %T : "
#
# Script goes here
# ..
#
# stop_logging
#

function start_logging {

#   Parameters
#
#   ${1} : Log File
#   ${2} : Prefix in strftime format
	
	echo Starting Logging >&2

	TEMPDIR=$(mktemp -d)
	
	local PIPE=${TEMPDIR}/pipe
	mkfifo -m 600 ${PIPE}

	perl -e "
	use POSIX qw(strftime);
	while (<STDIN>) {
	    print(strftime('${2}', localtime(time)), \$_);
	}" < ${PIPE} > ${1} &

	exec 4>&1 5>&2 1>${PIPE} 2>&1

	set -v
	
	echo Logging Started >&2
}

function stop_logging {
	
	echo Stopping Logging >&2

	set +v

	exec 1>&4 2>&5 4>&- 5>&-

	rm -rf ${TEMPDIR}
	
	echo Logging Stopped >&2
}
```

Now to get the stop_logging function to mail the log to an admin ..

---

