---
title: "HOWTO: Install Sun Studio 12 Update 1 for Ubuntu 9.04 Jaunty Jackalope"
date: 2009-09-03
forum: Outdated Tutorials &amp; Tips
---

### Post by Saxywolf on 2009-09-03
_Install Sun Studio 12 Update 1 for Ubuntu 9.04 Jaunty Jackalope; Written September 2, 2009_
(not sure if it'll stay on the Sun forum so I put it here)
First, I'm a newb. So this is really just to guide others through the journey. For the most part, I actually had to follow the included instructions rather then the "help" provided elsewhere (like this... hehe) as I usually have to. Sadly thats not what I did the first couple times. Nor do I usually follow the Lego instructions. Please correct me if you spot something wrong (specifically the PATH, since the command to check access to the developers tools didn't exactly work). If any of the versions are different (and even if they aren't) I suggest you read the readme since they actually seem applicable (even if not quite newb friendly... Dear Google, whats csh/sh/ksh/bash?).

**_Download:_**
[http://developers.sun.com/sunstudio/downloads/](http://developers.sun.com/sunstudio/downloads/)
Join, then go for the Free Download
[http://developers.sun.com/sunstudio/downloads/thankyou.jsp](http://developers.sun.com/sunstudio/downloads/thankyou.jsp)
Choose Option 2 and you should get:
SunStudio12u1-Linux-x86-tarfile.tar.bz2

**_Unpack:_**
Put the folder 'SunStudio12u1-Linux-x86-tar' anywhere
I just dragged it to my desktop

**_Install:_**
Set yourself as admin in a terminal:
```
sudo -s
```
Move to the /opt folder:
```
cd /opt/
```
Run the install:
```
[YOUR_path_to_installer]/SunStudio12u1-Linux-x86-tar/SunStudio12u1-Linux-x86-tar.sh --accept-license
```

**_Set Up Access to the Developer Tools and Man Pages:_**
e.g. Supposedly this: [http://docs.sun.com/app/docs/doc/820-7601/gemls?a=view](http://docs.sun.com/app/docs/doc/820-7601/gemls?a=view)
see this for more info: [https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)
Check that SunStudio12 installed to /opt/sunstudio12.1/
Edit the environment variable file
```
sudo gedit /etc/environment
```
Most likely PATH should already be there, so just add this with the other paths in quotes
```
:/opt/sunstudio12.1/bin
```
I had to add the MANPATH variable so I added a whole bunch of folders as follows:
```
MANPATH="/usr/share/man:/usr/local/man:/opt/sunstudio12/sunstudio12.1/man"
```

**_Test Access to Developer Tools:_**
This is where my install experience too a different path (get it?)
The Sun page says this command should work:
```
/usr/bin/version
```
I still get the "bash: /usr/bin/version: No such file or directory"
But, simply running the command 'version' works the same as the command '/opt/sunstudio12/sunstudio12.1/bin/version*'

**_Run Sun Studio 12 (wait, this is Netbeans?):_**
run this command in any terminal (I have no idea what the & does):
```
sunstudio &
```
More appropriately, create a launcher (aka shortcut) on your desktop

---

### Post by Canislupus on 2009-09-26
> **Saxywolf said:**
> _Install Sun Studio 12 Update 1 for Ubuntu 9.04 Jaunty Jackalope; Written September 2, 2009_
This is where my install experience too a different path (get it?)


*GROAN*
LOL! Thanks for sharing your experience with us, Saxy.  I'm following this as we speak.

I can't believe there's not more replies to this post.  Doesn't anyone use this excellent (and free) IDE? It seems like the best IDE out there, imho, of course.

oh... and I found a couple of typos...
```
MANPATH="/usr/share/man:/usr/local/man:/opt/sunstudio12/sunstudio12.1/man"
```
should be
```

MANPATH="/usr/share/man:/usr/local/man:/opt/sunstudio12.1/man"

```
as there is no /sunstudio12/ directory. :-)

And as for ```
sunstudio &
```
that just tells the terminal not to wait for the executed command to finish (you get your bash prompt back, but the program continues to run, without tying up your terminal window).

{Btw.... dear Ubuntu community.... please give us an up-to date Eclipse version in the repos...}

---

### Post by honey toast on 2009-10-12
:P You won't believe how useful this post of your was to me. This post was do or die for me. I tried to install those compilers last week without any success. I was so pist off with Suns for their choppy instructions. They were so hard to follow, but then I found this post of yours, and I was able to install them. Now I need to figure out how to write a program in C with Netbeans. thanks

---

### Post by solomonhomicz on 2009-11-16
Will this work on a 64 bit system?

---

