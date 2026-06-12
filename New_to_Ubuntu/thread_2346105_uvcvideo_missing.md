---
title: "uvcvideo missing ?"
date: 2016-12-11
forum: New to Ubuntu
---

### Post by Vaclav Vasek on 2016-12-11
I am trying to connect Canon EOS camera to retrieve pictures. 
I cannot get Shotwell to finish the job - it looses USB connection. 

I am looking for a replacment for SHotwell and aparenlty I need uvcvideo driver. 
Here is the repose I get : 

jim@jim-desktop:~$ sudo modprobe uvcvideo
[sudo] password for jim: 
jim@jim-desktop:~$ sudo modprobe uvcvideo
jim@jim-desktop:~$ 

Am I doing it wrong ?

---

### Post by deadflowr on 2016-12-11
Now that you've run modprobe, check that the module loaded with 
```
lsmod
```
> Am I doing it wrong ?
No, it only reports problems, like try loading a non-existent mod; something like 
```
sudo modprobe itchy-and-sratchy
```
the output will look something like this
> modprobe: FATAL: Module itchy-and-scratchy not found in directory /lib/modules/4.8.0-30-generic
Of course all said and done a module being loaded means nothing if no device can actually properly utilize it.

---

