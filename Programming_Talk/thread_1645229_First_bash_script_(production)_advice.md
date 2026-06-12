---
title: "First bash script (production) advice"
date: 2010-12-14
forum: Programming Talk
---

### Post by Grenage on 2010-12-14
Greetings.

I've dabbled with Bash scripts on rare occasions, normally just to make another's work fit my needs; now I have a real-world use for a script, and I've cobbled one together.  That said, it's my first script that I'll be making use of, I know that what I have come up with will be... poor.  If anyone can shed some light on what's bad practice, or what they'd do differently, that would be great.

It's a 'plugin' for nagios, designed to parse the previous hour's log files for errors from a particular host.  It seems to do the job, but even a wrecked car will get you from A to B:

```
if [[ $1 == '--help' ]]
then
	echo "Usage: $0 [REGEX] [CURRENT_LOG] [PREVIOUS_LOG] [SYMLINK_CURRENT] [SYMLINK_PREVIOUS] [OK] [WARNING] CRITICAL]"
	echo -e "Parse logs, count errors, and return error code to Nagios; also refresh symbolic links\n"
	echo "REGEX                 Match criteria (used in awk)"
	echo 'CURRENT_LOG           Absolute path to current syslog; use "NULL" if not required.'
	echo "PREVIOUS_LOG          Absolute path to previous syslog"
	echo 'SYMLINK_CURRENT       Symlink name for current log; use "NULL" if not required'
	echo "SYMLINK_PREVIOUS      Symlink name for previous log; use NULL if not required"
	echo "OK                    Threshold value required for OK status to be returned"
	echo "WARNING               Threshold value required for WARNING status to be returned"
	echo -e "CRITICAL              Threshold value required for CRITICAL status to be returned\n"
	echo "Simple example: $0 switch NULL /var/log/log2 NULL old,log 0 5 19"
	echo 'Real example: '$0' [a-z]*switch[0-9] $(date +/var/log/syslog_server/%Y/%m/%d/%H/syslog.log)  $(date -d "-1 hour" +/var/log/syslog_server/%Y/%m/%d/%H/syslog.log) current.log previous.log 0 5 19'
	exit 0
elif (( $# != 8 ))
then
	echo "Usage: $0 [REGEX] [CURRENT_LOG] [PREVIOUS_LOG] [SYMLINK_CURRENT] [SYMLINK_PREVIOUS] [OK] [WARNING] [CRITICAL]"
	echo "Try '$0 --help' for more information"
	exit 0
fi

for i in $6 $7 $8
do
	if [[ $i != [0-9]* ]]
	then
		echo "Threshold parameters must be positive integers"
		exit 0
	fi
done

# If previous log exists, count log errors for regex matches in column one (hostname):
if [[ -e $3 ]]
then
	ERRORCOUNT=$(awk '
		BEGIN { count = 0}
		$1 ~ /'$1'/ {count++}
		END {print count}
	' $3)
else
	echo "There appears to be no previous log file."
	exit 1
fi

# Nagios return codes:
OK=(0 "OK - $ERRORCOUNT warning(s) discovered.");
WARNING=(1 "WARNING - $ERRORCOUNT warnings discovered.");
CRITICAL=(2 "CRITICAL - $ERRORCOUNT warnings disovered.");
UNKNOWN=(3 'UNKNOWN - investigation required.');

# Nagios share path:
SHAREPATH='/usr/local/nagios/share/'

# Delete old symbolic links and create anew, pointing to recent logs (if they exist):
if [[ $SHAREPATH$4 != "NULL" ]]
then
	if [[ -e $2 ]]
	then
		if [[ -e $SHAREPATH$4 ]]
		then
			rm $SHAREPATH$4
		fi
		ln -s $2 $SHAREPATH$4
		LINK0='<a href="http://'$(hostname)'/'$4'">Current log,</a>'
	else
		LINK0=''
	fi
else
	LINK0=''
fi
if [[ $SHAREPATH$5 != "NULL" ]]
then
	if [[ -e $SHAREPATH$5 ]]
	then
		rm $SHAREPATH$5
	fi
	ln -s $3 $SHAREPATH$5
	LINK1='<a href="http://'$(hostname)'/'$5'">previous log.</a>'
	fi
else
	LINK1=''
fi

# Perform actions based on error count:
if (( $ERRORCOUNT >= $8 ))
then
    echo "${CRITICAL[1]} $LINK0 $LINK1"
    exit ${CRITICAL[0]}
elif (( $ERRORCOUNT >= $7 ))
then
	echo "${WARNING[1]} $LINK0 $LINK1"
	exit ${WARNING[0]}
elif (( $ERRORCOUNT >= $6 ))
then
	echo "${OK[1]} $LINK0 $LINK1"
	exit ${OK[0]}
else
	echo "${UNKNOWN[1]}"
	exit ${UNKNOWN[0]}
fi
```

---

### Post by Arndt on 2010-12-14
> **Grenage said:**
> Greetings.

I've dabbled with Bash scripts on rare occasions, normally just to make another's work fit my needs; now I have a real-world use for a script, and I've cobbled one together.  That said, it's my first script that I'll be making use of, I know that what I have come up with will be... poor.  If anyone can shed some light on what's bad practice, or what they'd do differently, that would be great.

It's a 'plugin' for nagios, designed to parse the previous hour's log files for errors from a particular host.  It seems to do the job, but even a wrecked car will get you from A to B:

```
if [[ $1 == '--help' ]]
then
	echo "Usage: $0 [REGEX] [CURRENT_LOG] [PREVIOUS_LOG] [SYMLINK_CURRENT] [SYMLINK_PREVIOUS] [OK] [WARNING] CRITICAL]"
	echo -e "Parse logs, count errors, and return error code to Nagios; also refresh symbolic links\n"
	echo "REGEX                 Match criteria (used in awk)"
	echo 'CURRENT_LOG           Absolute path to current syslog; use "NULL" if not required.'
	echo "PREVIOUS_LOG          Absolute path to previous syslog"
	echo 'SYMLINK_CURRENT       Symlink name for current log; use "NULL" if not required'
	echo "SYMLINK_PREVIOUS      Symlink name for previous log; use NULL if not required"
	echo "OK                    Threshold value required for OK status to be returned"
	echo "WARNING               Threshold value required for WARNING status to be returned"
	echo -e "CRITICAL              Threshold value required for CRITICAL status to be returned\n"
	echo "Simple example: $0 switch NULL /var/log/log2 NULL old,log 0 5 19"
	echo 'Real example: '$0' [a-z]*switch[0-9] $(date +/var/log/syslog_server/%Y/%m/%d/%H/syslog.log)  $(date -d "-1 hour" +/var/log/syslog_server/%Y/%m/%d/%H/syslog.log) current.log previous.log 0 5 19'
	exit 0
elif (( $# != 8 ))
then
	echo "Usage: $0 [REGEX] [CURRENT_LOG] [PREVIOUS_LOG] [SYMLINK_CURRENT] [SYMLINK_PREVIOUS] [OK] [WARNING] [CRITICAL]"
	echo "Try '$0 --help' for more information"
	exit 0
fi

for i in $6 $7 $8
do
	if [[ $i != [0-9]* ]]
	then
		echo "Threshold parameters must be positive integers"
		exit 0
	fi
done

# If previous log exists, count log errors for regex matches in column one (hostname):
if [[ -e $3 ]]
then
	ERRORCOUNT=$(awk '
		BEGIN { count = 0}
		$1 ~ /'$1'/ {count++}
		END {print count}
	' $3)
else
	echo "There appears to be no previous log file."
	exit 1
fi

# Nagios return codes:
OK=(0 "OK - $ERRORCOUNT warning(s) discovered.");
WARNING=(1 "WARNING - $ERRORCOUNT warnings discovered.");
CRITICAL=(2 "CRITICAL - $ERRORCOUNT warnings disovered.");
UNKNOWN=(3 'UNKNOWN - investigation required.');

# Nagios share path:
SHAREPATH='/usr/local/nagios/share/'

# Delete old symbolic links and create anew, pointing to recent logs (if they exist):
if [[ $SHAREPATH$4 != "NULL" ]]
then
	if [[ -e $2 ]]
	then
		if [[ -e $SHAREPATH$4 ]]
		then
			rm $SHAREPATH$4
		fi
		ln -s $2 $SHAREPATH$4
		LINK0='<a href="http://'$(hostname)'/'$4'">Current log,</a>'
	else
		LINK0=''
	fi
else
	LINK0=''
fi
if [[ $SHAREPATH$5 != "NULL" ]]
then
	if [[ -e $SHAREPATH$5 ]]
	then
		rm $SHAREPATH$5
	fi
	ln -s $3 $SHAREPATH$5
	LINK1='<a href="http://'$(hostname)'/'$5'">previous log.</a>'
	fi
else
	LINK1=''
fi

# Perform actions based on error count:
if (( $ERRORCOUNT >= $8 ))
then
    echo "${CRITICAL[1]} $LINK0 $LINK1"
    exit ${CRITICAL[0]}
elif (( $ERRORCOUNT >= $7 ))
then
	echo "${WARNING[1]} $LINK0 $LINK1"
	exit ${WARNING[0]}
elif (( $ERRORCOUNT >= $6 ))
then
	echo "${OK[1]} $LINK0 $LINK1"
	exit ${OK[0]}
else
	echo "${UNKNOWN[1]}"
	exit ${UNKNOWN[0]}
fi
```

1) I would misunderstand your usage line, because [ ] bracketing usually means that the thing in question is optional.

2) Don't exit with status 0 when there is an error. You want scripts which happen to use this script to be able to catch errors early. It's also a good idea to include the name of the script in the error message.

---

### Post by Grenage on 2010-12-14
> **Arndt said:**
> 1) I would misunderstand your usage line, because [ ] bracketing usually means that the thing in question is optional.

2) Don't exit with status 0 when there is an error. You want scripts which happen to use this script to be able to catch errors early. It's also a good idea to include the name of the script in the error message.

Good catches, thank you; I'll make the appropriate changes.  I don't know why I exited with a 0, when a 3 would have been appropriate (for this plugin).

---

