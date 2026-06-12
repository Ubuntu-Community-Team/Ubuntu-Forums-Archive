---
title: "Shell script to check if it is running?"
date: 2010-09-28
forum: Programming Talk
---

### Post by huangyingw on 2010-09-28
hello, 
   I have just googled out some script, but, it seems not correctly works to reach my goal.
   I am intending to write a script, called "apt-mirror.sh" in crontab to automatically download Ubuntu mirror files.
   As bellow:
```
root@Mldonkey:~/myproject/git/linux/bashrc# cat apt-mirror.sh
#! /bin/bash
echo $$ > /tmp/program.lock

RSYNCSOURCE=rsync://mirrors.sohu.com/ubuntu/
#RSYNCSOURCE=rsync://debian.nctu.edu.tw/ubuntu/
#RSYNCSOURCE=rsync://ubuntu.dormforce.net/ubuntu/
#RSYNCSOURCE=rsync://mirror.anl.gov/ubuntu/

BASEDIR=/media/volgrp/UbuntuMirror/

if [ -f /tmp/program.lock ] ; then
  # the lock file already exists, so what to do?
  if [ "$(ps -p `cat /tmp/program.lock` | wc -l)" -gt 1 ]; then
	    # process is still running
	    echo "$0: quit at start: lingering process `cat /tmp/program.lock`"
	    exit 0
  else
		  # process not running, but lock file not deleted?
		  echo " $0: orphan lock file warning. Lock file deleted."
		  rm /tmp/program.lock
      rsync -ahHv --log-file=/root/rlog --delete-after \
        --exclude "dapper*" --exclude "hardy*" --exclude "intrepid*" --exclude "jaunty*" --exclude "maverick*"\
      ${RSYNCSOURCE} ${BASEDIR}
  fi
fi

rm /tmp/program.lock

```
But the result is not my expectation, see bellow evidence:
```
root@Mldonkey:~/myproject/git/linux/bashrc# ./apt-mirror.sh
./apt-mirror.sh: quit at start: lingering process 8779
root@Mldonkey:~/myproject/git/linux/bashrc# ps ax|grep rsync
 8787 pts/3    S+     0:00 grep rsync
root@Mldonkey:~/myproject/git/linux/bashrc# 
```

---

### Post by spjackson on 2010-09-28
At the start of the script you write the current process id to file, overwriting anything that may have been there before. Consequently your test for the file is always true, and the test for the running pid is always true. (ps outputs the header line plus the details of the pid specified, which is 2 lines.)
```

echo $$ > /tmp/program.lock

```belongs at the top of your else branch, I think.

---

### Post by huangyingw on 2010-09-29
> **spjackson said:**
> At the start of the script you write the current process id to file, overwriting anything that may have been there before. Consequently your test for the file is always true, and the test for the running pid is always true. (ps outputs the header line plus the details of the pid specified, which is 2 lines.)
```

echo $$ > /tmp/program.lock

```belongs at the top of your else branch, I think.
Great thanks. According to your guidance, I have updated to the following, and it works now:
```
#! /bin/bash

RSYNCSOURCE=rsync://mirrors.sohu.com/ubuntu/
#RSYNCSOURCE=rsync://debian.nctu.edu.tw/ubuntu/
#RSYNCSOURCE=rsync://ubuntu.dormforce.net/ubuntu/
#RSYNCSOURCE=rsync://mirror.anl.gov/ubuntu/

BASEDIR=/media/volgrp/UbuntuMirror/

if [ "$(ps -p `cat /tmp/program.lock` | wc -l)" -gt 1 ]; then
          # process is still running
          echo "$0: quit at start: lingering process `cat /tmp/program.lock`"
          exit 0
else
      	  echo " $0: orphan lock file warning. Lock file deleted."
      	  echo $$ > /tmp/program.lock
    rsync -ahHv --log-file=/root/rlog --delete-after \
      --exclude "dapper*" --exclude "hardy*" --exclude "intrepid*" --exclude "jaunty*" --exclude "maverick*"\
    ${RSYNCSOURCE} ${BASEDIR}
fi

```

---

### Post by pbrane on 2010-09-29
One other way to check that the script is running or not:
```

# check to see if script is already running
PDIR=${0%`basename $0`}
LCK_FILE=`basename $0`.lck

if [ -f "${LCK_FILE}" ]; then
  MYPID=`head -n 1 "${LCK_FILE}"`
		
  TEST_RUNNING=`ps -p ${MYPID} | grep ${MYPID}`
		
  if [ -z "${TEST_RUNNING}" ]; then
    # The process is not running
    # Echo current PID into lock file
    echo $$ > "${LCK_FILE}"
  else
    # the process IS running
    # handle it
    exit 0
  fi
else
  echo $$ > "${LCK_FILE}"
fi

```

---

### Post by huangyingw on 2010-10-04
> **pbrane said:**
> One other way to check that the script is running or not:
```

# check to see if script is already running
PDIR=${0%`basename $0`}
LCK_FILE=`basename $0`.lck

if [ -f "${LCK_FILE}" ]; then
  MYPID=`head -n 1 "${LCK_FILE}"`
		
  TEST_RUNNING=`ps -p ${MYPID} | grep ${MYPID}`
		
  if [ -z "${TEST_RUNNING}" ]; then
    # The process is not running
    # Echo current PID into lock file
    echo $$ > "${LCK_FILE}"
  else
    # the process IS running
    # handle it
    exit 0
  fi
else
  echo $$ > "${LCK_FILE}"
fi

```
Thanks. Your solution seems better than mine. I will take yours as my mirror downloader:)

---

