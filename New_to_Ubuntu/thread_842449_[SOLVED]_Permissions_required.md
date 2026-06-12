---
title: "[SOLVED] Permissions required"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by Norman Thom on 2008-06-27
I need to give myself permissions to mount secondary drives,
copy backgrounds to background folder. . . 

in other words it's my computer and I would like to use it as I wish.

Can anybody help me . . . please.

Thanking you in advance,

Norm

---

### Post by suicidejack on 2008-06-27
Not sure how familiar you are with the command line but check out the command *chown* -> it changes who owns/has access to the file. use *chown -R pathname* to change the permissions on every file/directory from the top directory down

---

### Post by Norman Thom on 2008-06-27
Thank you Suicidejack:

I'm not very familiar with using the command line.
What puzzles me is the use of 'pathname'
Could you show me an example and I may be able to catch on.
Are there particular pathnames to the functions of this OS?
And how do I define the specific pathway?

Thanks again

Norm

---

### Post by manishtech on 2008-06-27
> **Norman Thom said:**
> I need to give myself permissions to mount secondary drives,
copy backgrounds to background folder. . . 

in other words it's my computer and I would like to use it as I wish.

Can anybody help me . . . please.

Thanking you in advance,

Norm
Which secondary drives? Removable drives like flash drives and external hard disks?

Or you mean mounting partitions on your primary hard disk?

---

### Post by Norman Thom on 2008-06-27
Thanks for responding Manishtech:

It's a second internal drive.

I can see it in the OS but cannot mount it.

Norm

---

### Post by kk0sse54 on 2008-06-27
If you prefer the GUI way you can press alt+f2 then type in ```
gksudo nautilus
``` in order to open up nautilus as root. Then just mount the hard drive from there and change it's ownership to your user name making sure that you havr read and write access.
The terminal way would be to mount your hard drive as root then as said before use chown to change permission. To find out more about chown try typing man chown

---

### Post by suicidejack on 2008-06-27
well for example, lets say you want to change the permissions on your background folder so that you can copy your backgrounds.  let's say your backgrounds are in your home directory in another folder called backgrounds.  when you start your terminal you should see something along the lines of:
```
your-name@computer-name:~$ 
```
the little ~ thing means that you are currently in your home folder. to change the permissions so that you can copy all the files in the background directory all you would have to do is type in ```
sudo chown -R user-name background
``` (you need to be root user which is the administrator - the command sudo puts you temporarily as the root user - to change the permissions)

sorry for the bad explanation - i just realized how bad i am at explaining this! here are some sites that will hopefully explain this better than i can.  if you happen to know the path to the directory where the backgrounds are that you want to copy and the directory that you want to copy them to i can give more specific code.  
short and sweet intro to linux pathnames: [http://www.certiguide.com/apfr/cg_apfr_LinuxPathNamesandFileNames.htm](http://www.certiguide.com/apfr/cg_apfr_LinuxPathNamesandFileNames.htm)
info on linux pathnames: [http://tldp.org/LDP/gs/node5.html](http://tldp.org/LDP/gs/node5.html) <--don't need to read the whole thing but will help you understand the pathname setup as well as some basic commands for moving around in the shell if you are interested
info on chown command: [http://en.wikipedia.org/wiki/Chown](http://en.wikipedia.org/wiki/Chown)

as to the secondary drives - could you give the error that you are getting when you mount them?  you should be able to mount secondary drives no problem.

---

### Post by Norman Thom on 2008-06-27
Thanks C!oud :

Your hint re nautilus allowed me to copy my files to my background folder.
Still having problems with the hard drive.  
Getting the error msg:NTSF signiture is missing
failed to mount<device> invalid argument . . .

Norm

---

### Post by manishtech on 2008-06-27
> **suicidejack said:**
> well for example, lets say you want to change the permissions on your background folder so that you can copy your backgrounds.  let's say your backgrounds are in your home directory in another folder called backgrounds.  when you start your terminal you should see something along the lines of:
```
your-name@computer-name:~$ 
```
the little ~ thing means that you are currently in your home folder. to change the permissions so that you can copy all the files in the background directory all you would have to do is type in ```
sudo chown -R user-name background
``` (you need to be root user which is the administrator - the command sudo puts you temporarily as the root user - to change the permissions)

sorry for the bad explanation - i just realized how bad i am at explaining this! here are some sites that will hopefully explain this better than i can.  if you happen to know the path to the directory where the backgrounds are that you want to copy and the directory that you want to copy them to i can give more specific code.  
short and sweet intro to linux pathnames: [http://www.certiguide.com/apfr/cg_apfr_LinuxPathNamesandFileNames.htm](http://www.certiguide.com/apfr/cg_apfr_LinuxPathNamesandFileNames.htm)
info on linux pathnames: [http://tldp.org/LDP/gs/node5.html](http://tldp.org/LDP/gs/node5.html) <--don't need to read the whole thing but will help you understand the pathname setup as well as some basic commands for moving around in the shell if you are interested
info on chown command: [http://en.wikipedia.org/wiki/Chown](http://en.wikipedia.org/wiki/Chown)

as to the secondary drives - could you give the error that you are getting when you mount them?  you should be able to mount secondary drives no problem.
is it necessary to do chown?

---

### Post by oldos2er on 2008-06-27
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by suicidejack on 2008-06-27
> is it necessary to do chown?
manishtech, not sure what you mean by that...

i guess the nautilus thing works but i've never heard of doing it like that.

---

