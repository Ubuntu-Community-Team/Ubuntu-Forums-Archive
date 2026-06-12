---
title: "fldigi does not stay up and running"
date: 2016-05-19
forum: New to Ubuntu
---

### Post by jack178 on 2016-05-19
have installed fldigi but it will come up on screen for a few seconds and goes back off can anyone help?

---

### Post by jack178 on 2016-05-19
solved fldigi now i need to get cqrlog to run help please

---

### Post by jeremy31 on 2016-05-19
How did you solve your issue with fldigi?  I don't remember any issue with fldigi but getting it to work with my Signalink USB took a bit of searching.  I haven't tried cqrlog

---

### Post by jack178 on 2016-05-20
sorry but i jumped the gun  did not slove the fldigi problem  still does not work as i said it comes up on screen for a few seconds and then goes off cqrlog does the same thing  any help would be appreciated

---

### Post by jeremy31 on 2016-05-21
Post the results for ```
uname -a; dpkg -l | grep fldigi; groups
```

---

### Post by jack178 on 2016-05-21
uname -a; dpkg -l | grep fldigi; groups
Linux orphan1966-Inspiron-3252 4.4.0-23-generic #41-Ubuntu SMP Mon May 16 23:04:25 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
ii  fldigi                                        3.23.01-1                                           amd64        digital modem program for hamradio operators
ii  fldigi-dbg                                    3.23.01-1                                           amd64        debugging symbols for fldigi
ii  libflxmlrpc-dev                               0.1.4-1ubuntu1                                      amd64        fldigi suite XmlRpc library - Development files
ii  libflxmlrpc1v5                                0.1.4-1ubuntu1                                      amd64        fldigi suite XmlRpc library
orphan1966 adm dialout cdrom sudo dip plugdev lpadmin sambashare

---

### Post by jeremy31 on 2016-05-26
Sorry it took a while to get back to this

Have you tried starting fldigi from terminal ```
fldigi
```
My 16.04 install brings it up fine.  I installed from the repos and not kamal's PPA but I doubt there is much difference

---

