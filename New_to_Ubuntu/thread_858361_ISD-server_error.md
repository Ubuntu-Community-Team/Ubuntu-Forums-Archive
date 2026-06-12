---
title: "ISD-server error"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by gregbzh on 2008-07-13
Could someone please tell me what this is?  It has started appearing on every startup.
[IMG]http://bp0.blogger.com/_8qMEp8JsO7Q/SHpBTj6WwSI/AAAAAAAAAYs/UEweP9gGPvo/s400/ISD-server+error.png[/IMG]

Cheers.

---

### Post by nowshining on 2008-07-13
the ISD service can't be started as it says port 5800 is being used by something else.

something is using port 5800 - u need to find out what it is..

---

### Post by jsalelle on 2008-09-25
ISD is the client service that the Italc program uses. 
Italc is a program very useful in classroom environment: the teacher can see in his computer what the pupils are doing, control the pupils computers, etc... The daemon running at all the pupils computers and so at the teacher computer for the Italc program to work is called ICA client. That is, Italc has two parts,the ICA client and ICA master, and uses the ISD service to communicate.
When you have Italc installed, it runs on start up.
The problem, as you may see [here]("http://ubuntuforums.org/showthread.php?t=786355") in better english ;-) is that when you use the "remember session" feature of Gnome, ICA is started twice, or more times!!!
The solution is to go to sessions manager and delete the extra starts.

---

