---
title: "Alternative Path Doesn't Exist Error"
date: 2013-03-01
forum: New to Ubuntu
---

### Post by ChemMeister on 2013-03-01
When i try to install build-esential using ```
sudo apt-get install build-essential
``` I get the error
```
update-alternatives: error: alternative path /usr/bin/gcc doesn't exist
```

Any ideas on how to fix this?

---

### Post by matt_symes on 2013-03-01
Hi

Please post the output, from a terminal, for these commands

```
ls -l /usr/bin/gcc
```

```
dpkg -l gcc
```

```
dpkg --audit
```

```
update-alternatives --get-selections | grep gcc
```

```
update-alternatives --display cc
```

```
dpkg-divert --list "*gcc*"
```

and finally.

```
sudo apt-get -f install
```

Kind regards

---

### Post by ChemMeister on 2013-03-01
> **matt_symes said:**
> Hi

Please post the output, from a terminal, for these commands

```
ls -l /usr/bin/gcc
```

```
dpkg -l gcc
```

```
dpkg --audit
```

```
update-alternatives --get-selections | grep gcc
```

```
update-alternatives --display cc
```

```
dpkg-divert --list "*gcc*"
```

and finally.

```
sudo apt-get -f install
```

Kind regards

```
doudou@Pumpkin-Ubuntu:~$ ls -l /usr/bin/gcc
lrwxrwxrwx 1 root root 7 Mar 13  2012 /usr/bin/gcc -> gcc-4.6

```

```
doudou@Pumpkin-Ubuntu:~$ sudo dpkg -l gcc
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
iF  gcc            4:4.6.3-1ubunt GNU C compiler


```

```
sudo dpkg --audit
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 g++                  GNU C++ compiler
 build-essential      Informational list of build-essential packages

The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 gcc                  GNU C compiler
```

```
doudou@Pumpkin-Ubuntu:~$ update-alternatives --get-selections | grep gcc
doudou@Pumpkin-Ubuntu:~$
```

```
doudou@Pumpkin-Ubuntu:~$ update-alternatives --display cc
update-alternatives: error: no alternatives for cc.

```

```
doudou@Pumpkin-Ubuntu:~$ sudo dpkg-divert --list "*gcc*"
doudou@Pumpkin-Ubuntu:~$ 

```

```
doudou@Pumpkin-Ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up gcc (4:4.6.3-1ubuntu5) ...
update-alternatives: error: alternative path /usr/bin/gcc doesn't exist.
dpkg: error processing gcc (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of g++:
 g++ depends on gcc (>= 4:4.6.3-1ubuntu5); however:
  Package gcc is not configured yet.
dpkg: error processing g++ (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of build-essential:
 build-essential depends on gcc (>= 4:4.4.3); however:
  Package gcc is not configured yet.
 build-essential depends on g++ (>= 4:4.4.3); however:
  Package g++ is not configured yet.
dpkg: error processing build-essential (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 gcc
 g++
 build-essential
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

thanks!

---

### Post by matt_symes on 2013-03-01
Hi

Try this from the terminal

```
sudo dpkg -P gcc
```

```
sudo apt-get clean
```

```
sudo apt-get -f install
```

Post back any errors.

Kind regards

---

