---
title: "Why does my shell script require &quot;crcr&quot; ???"
date: 2007-09-06
forum: Programming Talk
---

### Post by mozkill on 2007-09-06
On my server, I am trying to start a java process with a shell script.  My initialization script sends the following command:

> #!/bin/bash
. /etc/rc.status
rc_reset  
case "$1" in
    start)
        echo -n "Starting Java Server "
        cd /home/JavaServer
        **./startserver.sh < crcr > console.log 2>&1 &**
        disown -a
        rc_status -v
        ;;
.....
esac


MY question is "WHY do I need the '<crcr'  redirect for it to work?  The script wont work without that item and I can't figure out why.  I really want to understand what this means.  Why would you want to feed back to a script a file called "crcr" that has 2 carrage returns in it and why won't the java process start without this??

so confused, thanks for any help you can give....

---

### Post by dwhitney67 on 2007-09-06
What are the contents of the startserver.sh script file?  Maybe if you peruse that file, you will find your answer.

---

### Post by mozkill on 2007-09-19
There is nothing obvious.  Here is a sample of what is in the file (obfuscated of course).  The startup works fine on a windows machine with the same classes and same JDK version, without the need for the "crcr" thing...

> #       Start the Server
#
cd $SERVER_HOME 
$JAVA_HOME/bin/java \
$JAVAOPTS  \
-classpath "$CLASSPATH" \
com.company.server.Site $1 $2 $3


---

