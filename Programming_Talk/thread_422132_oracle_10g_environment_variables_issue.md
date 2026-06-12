---
title: "oracle 10g environment variables issue"
date: 2007-04-24
forum: Programming Talk
---

### Post by michaelw436 on 2007-04-24
Hey guys, I am new to Ubuntu, and am an aspiring Oracle DBA. I am working on installing Oracle on Feisty Fawn according the instructions that I found out at dizwell.com.  Everything is going well, except for setting the oracle environment variables in the oracle users .bashrc file. I added the export statements to that .bashrc file, but they don't seem to be working... any help? below is the tail of the .bashrc file, and then me trying to echo them out as the oracle user, and they don't seem to be working. Please help! Thanks!

**ubuntu1@ubuntu1-pc:~$ tail /home/oracle/.bashrc**
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

export ORACLE_BASE=/oracle
export ORACLE_HOME=/oracle/10g
export ORACLE_SID=orcl10
export PATH=$PATH:$ORACLE_HOME/bin

**ubuntu1@ubuntu1-pc:~$ su - oracle**
Password: 
**$ echo $ORACLE_BASE**

**$ echo $ORACLE_HOME**

$ exit

---

