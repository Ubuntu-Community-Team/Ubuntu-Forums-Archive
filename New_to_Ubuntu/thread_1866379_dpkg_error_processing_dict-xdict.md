---
title: "dpkg: error processing dict-xdict"
date: 2011-10-21
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2011-10-21
i installed dict-kdict through the Kpackage Manager. After installing  I am not able to install or update any software and I got the following error message in the Terminal. How to solve this issue ?

```
kevin@kevin-desktop:~$ sudo aptitude
[sudo] password for kevin: 
(Reading database ... 189866 files and directories currently installed.)
Removing dict-xdict ...
invoke-rc.d: unknown initscript, /etc/init.d/dictd not found.
dpkg: error processing dict-xdict (--remove):
 subprocess installed post-removal script returned error exit status 100
Errors were encountered while processing:
 dict-xdict
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Press return to continue.

kevin@kevin-desktop:~$ 

```

---

### Post by gsmanners on 2011-10-21
Interesting. I would suggest either installing dictd (so you can actually use dict-xdict) or removing dict-xdict.

(And maybe they should update the package if their init script is going to depend on dictd. That would seem to make dictd a dependency, hmm?)

---

### Post by 1991sudarshan on 2011-10-21
> **gsmanners said:**
> Interesting. I would suggest either installing dictd (so you can actually use dict-xdict) or removing dict-xdict.

(And maybe they should update the package if their init script is going to depend on dictd. That would seem to make dictd a dependency, hmm?)


I installed the dictd and I get the same error again 


```
kevin@kevin-desktop:~$ sudo apt-get install dictd 
[sudo] password for kevin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dict librecode0 recode
Suggested packages:
  dict-wn dict-jargon dict-foldoc
The following packages will be REMOVED:
  dict-xdict
The following NEW packages will be installed:
  dict dictd librecode0 recode
0 upgraded, 4 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 1,037kB of archives.
After this operation, 2,753kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid/main librecode0 3.6-17 [702kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ lucid/main recode 3.6-17 [122kB]                                                                                                
Get:3 http://us.archive.ubuntu.com/ubuntu/ lucid/main dict 1.11.2+dfsg-2 [73.5kB]                                                                                          
Get:4 http://us.archive.ubuntu.com/ubuntu/ lucid/main dictd 1.11.2+dfsg-2 [139kB]                                                                                          
Fetched 1,037kB in 30s (34.5kB/s)                                                                                                                                          
Preconfiguring packages ...
(Reading database ... 189866 files and directories currently installed.)
Removing dict-xdict ...
invoke-rc.d: unknown initscript, /etc/init.d/dictd not found.
dpkg: error processing dict-xdict (--remove):
 subprocess installed post-removal script returned error exit status 100
Errors were encountered while processing:
 dict-xdict
E: Sub-process /usr/bin/dpkg returned an error code (1)                                                                                                                     
kevin@kevin-desktop:~$
```

---

### Post by matt_symes on 2011-10-21
Hi

Open a terminal and type
[FONT=monospace]
[/FONT]```
echo "exit 0;" | sudo tee /etc/init.d/dictd
```

```
sudo dpkg -r dict-xdict
```

Kind regards

---

### Post by 1991sudarshan on 2011-10-21
> **matt_symes said:**
> Hi

Open a terminal and type
[FONT=monospace]
[/FONT]```
echo "exit 0;" | sudo tee /etc/init.d/dictd
``````
sudo dpkg -r dict-xdict
```Kind regards

it works. Thank you so much. Could please tell me what was the problem caused by the dict-xdict. I really did not understand which it was causing such a issue


```
kevin@kevin-desktop:~$ echo "exit 0;" | sudo tee /etc/init.d/dictd
[sudo] password for kevin:                                                                                                                                                  
exit 0;                                                                                                                                                                     
kevin@kevin-desktop:~$ sudo dpkg -r dict-xdict                                                                                                                              
(Reading database ... 189866 files and directories currently installed.)                                                                                                    
Removing dict-xdict ...                                                                                                                                                     
kevin@kevin-desktop:~$
```

---

### Post by matt_symes on 2011-10-21
Hi
[FONT=monospace]
[/FONT]> invoke-rc.d: unknown initscript, /etc/init.d/dictd not found.

So you created the file that returned a status of success (exit 0) and allowed the rest of the uninstall to continue.

I think you can get dpkg to do it itself but i'm too lazy to read through the man page tonight.

Please mark this thread as solved.

Kind regards

---

