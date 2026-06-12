---
title: "Open Office 3 Install"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by Pevichaey5 on 2008-10-16
hey guys

been a while since i was running ubuntu, but i have a problem with installing OOo 3

i have extracted the files from the tar.gz then tried to run setup from the directory and got this

```

toby@toby-laptop:~/Desktop/OOO300_m9_native_packed-1_en-US.9358$ sudo ./setup
Checksumming...
Extracting ...
./setup: 478: rpm2cpio: not found
cpio: premature end of archive
find: usr: No such file or directory
basename: missing operand
Try `basename --help' for more information.
/dev/pts/0
Error: Failed to extract the Java Runtime Environment (JRE) files. (exit code 7)
toby@toby-laptop:~/Desktop/OOO300_m9_native_packed-1_en-US.9358$ 

```

i have installed the java packager but it hasn't made a difference

cheers

---

### Post by gjoellee on 2008-10-16
Learn how to install OOo3 here: [http://www.kshoster.net/node/56](http://www.kshoster.net/node/56)

---

### Post by TCSnyder on 2008-10-16
go to the synaptic package manager and make sure you have all the java packages installed

---

### Post by Pevichaey5 on 2008-10-16
cheers for the fast reply, but i downloaded the rpm (oops) but that web link you showed me helps alot

i downloading the correct one now

cheers once again

---

### Post by ksjyothi on 2009-02-11
if u have downloaded the OOO300_m15_native_packed-1_en-US.9379 

extract it  on desktop 

you need rpm to install .sh installers this will solve the problem. do reply when it works

Type sudo apt-get install rpm 

then click the setup  in the folder   and  follow the instructions in the  installation window

---

