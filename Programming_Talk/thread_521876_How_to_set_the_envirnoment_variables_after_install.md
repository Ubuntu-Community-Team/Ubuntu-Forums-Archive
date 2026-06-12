---
title: "How to set the envirnoment variables after installing Oracle10g Database Express"
date: 2007-08-09
forum: Programming Talk
---

### Post by watermark1983 on 2007-08-09
I was installing Oracle Database10g
and i type the command : sudo gedit /etc/bash/bashrc
and add :
ORACLE_HOME=/usr/lib/oracle/xe/app/oracle/product/ 10.2.0/server
ORACLE_OWNER=oraclexe
ORACLE_SID=XE
export ORACLE_HOME
export ORACLE_SID
export PATH=$ORACLE_HOME/bin:$PATH


but the erro message shows up : canot found the file.and canot save it.


where i could find the .bashrc
and i searched some information.some tells to add the envirnoment variables in bash_profile.
and i dont understand the relationship between the bash_profile and bashrc...


waiting for help online...............:)
__________________

---

### Post by bjarneh on 2007-08-09
for the global environment variable you want to change the

/etc/bash.bashrc

not /etc/bash/bashrc


for your personal settings you can edit

~/.bashrc


/etc/profile only gets read on startup, while the bashrc gets read every time you start bash, i think?

the problem seem to be a typo /etc/bash/bashrc --> /etc/bash.bashrc

---

### Post by watermark1983 on 2007-08-09
oh,i see,
Let me check it...thank you very much.......

sorry,i am a newbin here

---

### Post by watermark1983 on 2007-08-09
> **bjarneh said:**
> for the global environment variable you want to change the

/etc/bash.bashrc

not /etc/bash/bashrc


for your personal settings you can edit

~/.bashrc


/etc/profile only gets read on startup, while the bashrc gets read every time you start bash, i think?

the problem seem to be a typo /etc/bash/bashrc --> /etc/bash.bashrc


  I get some file that :
 $ sudo su oracle
and the terminal will turn out like this:
Oraclexxxx@xxx:$ 
and you could add the enivrnoment under Oracle user ,and 
add the envirnoment variables to the file : bash_profile
so then i type sudo gedit ./bash_profile
but it goes wrong.
so  i am wondering it is the same command of "sudo gedit ./bash" when i convert to the user of Oracle.

   xxx@xxx:$ sudo su oracle
Oracle xxxx@xxx :$ sudo gedit  ./bash_profile
 
i think it is not right.and will you plz tel me the right command if i convert to the user of Oracle like what i have said above:confused:

---

