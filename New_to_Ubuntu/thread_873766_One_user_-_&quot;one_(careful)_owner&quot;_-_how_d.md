---
title: "One user - &quot;one (careful) owner&quot; - how do I..."
date: 2008-07-29
forum: New to Ubuntu
---

### Post by JustGus on 2008-07-29
I've noticed one of the single biggest time-wasting and frustrating issues I'm having with Ubuntu is that I keep finding I can't access or copy and insert folders into folders.  This requires me to re-read how to make changes to permissions in the Terminal, often without it working, requiring me to re-google and try again.  
The madness of this is that I'm the only person who will ever use this Linux computer, so the root vs. user signon requirements are essentially safeguarding me from...me - and are making things inanely difficult in the process.
I've read all the admonishments about having a single user/admin, but as these are obviously irrelevant in many cases (like mine) is there any way I can set up a single sign on and dispense with root vs. user?
Any advice very gratefully received.
Gus

---

### Post by hyper_ch on 2008-07-29
Have a read through this:  [http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

But according from your post, especially the "can't access or copy and insert folders into folders" part, shows me, that you don't have much of an understanding yet and that you'll be worse off by login in as root.

There is no reason to often access folders outside your home and there's good reason a normal user should not have access to it.

---

### Post by Nepherte on 2008-07-29
It is certainly possible. However, you might want to think this over *again*. If you insist, you should be able to find the answer somewhere on the internet, not here because it is against the forum policy (cfr. [http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)). I hope the link I gave you might persuade you not to do it.

---

### Post by northern lights on 2008-07-29
> **JustGus said:**
> user signon requirements are essentially safeguarding me from...me
Nailed it. But don't consider it a limitation. It might be a nuisance if you're used to logging on as admin in Windows all the time. But that's also why Windows is so easy to break.


> **JustGus said:**
> is there any way I can set up a single sign on and dispense with root vs. user?I would clear advise against that, as I promise you'll screw your machine in less than a day. The time you spend typing in your password does by no means compare to the time you will spend recovering your system.

If you must, google.

Here's some reading:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")
[Forum policy on login-as-root tutorials]("http://ubuntuforums.org/showthread.php?t=765414")

---

### Post by oldsoundguy on 2008-07-29
First off "root" vs user permissions save you from having installs happen like they happen in Windows .. where you click on a .jpg and a spy bot or worm gets installed into your system.  Permissions are the most important thing that help keep your system virus and malware free.

second, really no need to move folders into folders.  The majority of time when you are moving a folder, it is to make that folder and contents available to the system in one way or another so that something you ARE installing with permissions will WORK when the system goes searching for the information. (and with a bit of investigation and practice .. you can actually DRAG AND DROP in Ubuntu .. takes research and practice, but it can be done!)

third, copying code from some site you "Googled" and inserting it into your system as root is not the best of ideas.  Official and approved sites of Linux providers usually screen and REMOVE malicious code.  Unofficial sites do NOT do so.  Using unofficial sites with "nice little program fixes" is asking for trouble .. just like clicking on that nice little .exe file in Windows that the site says you just "got to have" to view/hear/whatever the content on their site.

Once you get a Linux build tweaked and all of the programs you want to use installed from THE REPOSITORIES or APPROVED sites, the system becomes virtually transparent.  There is little or no need to move things around as you can access all of your created data and process or change or add to or remove all of same from YOUR desktop.  System files are best left alone (xorg and some others are the major exceptions, but you will discover those that DO require access soon enough simply because when you are installing something, it will TELL you that you need access!)

---

### Post by billgoldberg on 2008-07-29
Logging in as root isn't advice.

You nailed it by saying the computer protects you from yourself.

A normal user only need access to /home (or /media) where you can do everything you want.

If you are messing with files who aren't in there and you are having trouble copying them, you should most certainly not run as root.

For future reference (even though I don't really like giving this advice) , you can use

```
gksudo nautilus --no-desktop
```

That way you want have any problems opening those files. 

Don't use this for normal usage.

---

### Post by eldragon on 2008-07-29
one last advice.

if you are just one user. and are in need of moving folders you normally do not have permissions to, you are definately doing something wrong.

just remember all your stuff should be at your home dir.

example, if your username is john, then you should always try to work within /home/john
those files SHOULD be owned by john, and thus, you should be able to meddle with them.


one shortcomming is wireless. i guess 8.10 should make wireless and wired networking easier to setup. maybe add a network-admin group which has read/write access to pertinent system places. for now you will have to deal with preceeding commands with sudo (not that problematic if you ask me). 


i hope i cleared some stuff up :D and please, do not do that, its a security threat. imagine what could happen if someone found a vulnerability in firefox that gives the attacker access to the user's session. if that user is root. he could do whatever he wants to your system. not good.

---

### Post by dnairb on 2008-07-29
One question that needs to be asked is what are you trying to move/copy, and why?... um OK that's 2 questions....

---

### Post by oldos2er on 2008-07-29
Instead of changing permissions, it's much easier to use "sudo cp /something /somewhere". What exactly are you doing that you need to work outside your home directory so often?

---

### Post by SunnyRabbiera on 2008-07-29
The thing is things are set up the way they are for a reason, by having the root account disabled and the core files protected it prevents the system from being corrupted.
Why do you think Windows has so many viruses and issues, because it allows root access by default and not caring if something enters the system.
That tells you the two different mindsets of linux and windows, the windows take is "any idiot can use it and mess it up and who gives a crap if they do"
and the linux take is "any idiot can use it, but make sure that nothing happens to the core system by mistake"
Maybe in the future of ubuntu there will be ways of entering administrator mode without the terminal but for now the system works...

---

### Post by t0p on 2008-07-29
> **JustGus said:**
> I've noticed one of the single biggest time-wasting and frustrating issues I'm having with Ubuntu is that I keep finding I can't access or copy and insert folders into folders.  This requires me to re-read how to make changes to permissions in the Terminal, often without it working, requiring me to re-google and try again.  
The madness of this is that I'm the only person who will ever use this Linux computer, so the root vs. user signon requirements are essentially safeguarding me from...me - and are making things inanely difficult in the process.
I've read all the admonishments about having a single user/admin, but as these are obviously irrelevant in many cases (like mine) is there any way I can set up a single sign on and dispense with root vs. user?
Any advice very gratefully received.
Gus

You want to do stuff to folders, permissions-wise?  Type **gksudo** in a Terminal.  In the lil Run box that appears, type **nautilus**.  Now you can do whatever you want to your files and directories, via the GUI.

Happy now?

---

### Post by decoherence on 2008-07-29
Some folks have already asked, but I just want to emphasize the question.

What are you doing that requires access outside of your home folder? Rather than breaking the permissions system (which has been in place for decades and is THE reason why UNIX-like systems are less prone to viruses than their Windows counterparts) a better question would be "how do I do X? [www.xyz.com](www.xyz.com) says I can do it this way, but I have to copy *this* file over to *that* directory and I get permission denied errors. Is there a better way?"

Unless you are doing some under-the-hood customization (in which case, you probably aren't gonna complain about permissions since they can save your butt) or something is broken, you should never need to directly access files outside of your home.

I would tend to think that if there are circumstances where the typical Ubuntu user HAS to make changes outside of home, it should be reported as a user experience related bug.

---

### Post by t0p on 2008-07-29
> **decoherence said:**
> 
I would tend to think that if there are circumstances where the typical Ubuntu user HAS to make changes outside of home, it should be reported as a user experience related bug.

Maybe you never feel the need to edit files outside your home directory, but don't assume your behaviour is normal.

For instance, if you use **wvdial** (a normal action for people who use ppp), you will need to edit the file /etc/wvdial.conf.

That's just one example.  There are many more.

---

### Post by bodhi.zazen on 2008-07-29
> **JustGus said:**
> I've noticed one of the single biggest time-wasting and frustrating issues I'm having with Ubuntu is that I keep finding I can't access or copy and insert folders into folders.  This requires me to re-read how to make changes to permissions in the Terminal, often without it working, requiring me to re-google and try again.  
The madness of this is that I'm the only person who will ever use this Linux computer, so the root vs. user signon requirements are essentially safeguarding me from...me - and are making things inanely difficult in the process.
I've read all the admonishments about having a single user/admin, but as these are obviously irrelevant in many cases (like mine) is there any way I can set up a single sign on and dispense with root vs. user?
Any advice very gratefully received.
Gus

Every major OS works this way, windows has the idea of an administrator and power users.

The general idea is to "protect" the system files form accidental change, either from the end user or malware.

You should not be changing the permissions of system files, rather learn to use sudo 

```
sudo -i
```

```
gksu nautilus
```

---

### Post by oldos2er on 2008-07-29
> **t0p said:**
> Maybe you never feel the need to edit files outside your home directory, but don't assume your behaviour is normal.

For instance, if you use **wvdial** (a normal action for people who use ppp), you will need to edit the file /etc/wvdial.conf.

That's just one example.  There are many more.

 I don't think anyone's suggested one never needs to work outside /home. But for the example you gave, you edit the file once, and it's done; the OP said "I can't access or copy and insert folders into folders," which appears to be a different situation.

 Again (to the OP), instead of changing permissions, use "sudo cp ..." or "gksudo nautilus".

---

### Post by JustGus on 2008-07-29
Thanks for the many replies.  
In answer to "why", I wanted to do this because I need to install a plugin into [SqueezeCenter]("http://www.slimdevices.com/pi_features.html") and the only way I could do this was to extract it on the desktop and then try to drop the folder into the appropriate plugin folder.  The problem (I think) is that one folder is showing permissions as attributed to "root", while the other folder shows permissions attributed to "server" (the user)

I'm trying to use the device as a simple media server, but the transition to the new OS has been painful!  Will read the various links provided.  Thanks for the advice and support.  In the spirit of open dialogue, while many seem to think 'protecting me from me' is a good thing, it seems the result is just a more confusing approach (and more confusion is likely to lead to more errors).

---

### Post by bodhi.zazen on 2008-07-29
> **JustGus said:**
> Thanks for the many replies.  
In answer to "why", I wanted to do this because I need to install a plugin into [SqueezeCenter]("http://www.slimdevices.com/pi_features.html") and the only way I could do this was to extract it on the desktop and then try to drop the folder into the appropriate plugin folder.  The problem (I think) is that one folder is showing permissions as attributed to "root", while the other folder shows permissions attributed to "server" (the user)

I'm trying to use the device as a simple media server, but the transition to the new OS has been painful!  Will read the various links provided.  Thanks for the advice and support.  In the spirit of open dialogue, while many seem to think 'protecting me from me' is a good thing, it seems the result is just a more confusing approach (and more confusion is likely to lead to more errors).

Learning a new OS is a challenge, no argument there. I would suggest to you that operating systems no longer work the way you envision them. This is not paternalistic, just a fact of modern computing. Every modern OS, yes including windows, protects system files from non-administrative users, or as you say it 'protecting me from me'. The difference is with the tools to access system files. Windows uses the idea of an administrative user. Linux calls the administrative user "root". Ubuntu accesses root with sudo and gksu (for graphical applications).

I also take issue with the idea that there is only "one user" on any system connected to the internet. If you are connected to the internet you are exposed to many users and every modern operating system, including windows, takes appropriate precautions. Now you may be the only user with physical access, that much is true.

What you are suggesting is dismantling the basic protections built into your new OS, and to experienced users seems unwise. I suggest you learn your new OS before judging the kind people who have taken the time to advise you in this thread.

I am closing this thread to prevent it from becoming yet another discussion re: loggin in to Ubuntu as root. The issue has been discussed many times and, as is explained in the link [hyper_ch]("http://ubuntuforums.org/member.php?u=122588") gave to you, logging in as root is not supported on these forums.

---

