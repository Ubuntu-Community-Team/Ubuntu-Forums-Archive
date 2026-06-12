---
title: "Codecs for playing music"
date: 2013-06-06
forum: New to Ubuntu
---

### Post by SMK40000 on 2013-06-06
So im very new to ubuntu. Is there anything i need to know before i get started? I already have it installed and noticed that I don't have Java or any Codecs for playing music. Appreciate it in advance.:D

---

### Post by hansdown on 2013-06-06
Welcome to the forum, SMK40000.

Which version are you running?

---

### Post by Buntu Bunny on 2013-06-06
Hello SMK40000! Welcome to Ubuntu and the Ubuntu Forums. You don't mention which Ubuntu you're using, but here are a few sites to take a look at to get started.

[http://www.omgubuntu.co.uk/2013/04/10-things-to-do-after-installing-ubuntu-13-04]("http://www.omgubuntu.co.uk/2013/04/10-things-to-do-after-installing-ubuntu-13-04")

[http://www.thegeeksolutions.in/2012/10/things-to-do-after-installing-ubuntu.html]("http://www.thegeeksolutions.in/2012/10/things-to-do-after-installing-ubuntu.html")

[https://wiki.ubuntu.com/AlwaysEnableUniverseMultiverse]("https://wiki.ubuntu.com/AlwaysEnableUniverseMultiverse")

---

### Post by VMC on 2013-06-07
> **SMK40000 said:**
> So im very new to ubuntu. Is there anything i need to know before i get started? I already have it installed and noticed that I don't have Java or any Codecs for playing music. Appreciate it in advance.:D

Here's another link for [multimedia-video-music]("http://ubuntuforums.org/showthread.php?t=766683"). Personally, I just use [VLC]("http://www.videolan.org/vlc/download-ubuntu.html") and be done with video, music issues, unless of course its hardware related.

---

### Post by mastablasta on 2013-06-07
you need ot open software center, then search and install ubutnu restricted extras. it has all you need. : [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by houseworkshy on 2013-06-07
This is not about codec but I think it should be one of the first things to understand.  

Perhaps the only tecy bits a newcomer needs to know on day one.  I'll use one of them to help explain the other.    

Though you have a firewall in the default installation it is not enabled by default.
  
To set up the standard defaults open a terminal and enter "sudo ufw default deny"  The 'sudo" is because it is an admin action and you'll have to enter your password to prove you are admin.  The ufw is the Ubuntu firewall, the rest is what you do with it.    

It is worth knowing that the "sudo" has a timer for how long the admin window lasts, it's default is 15 minets.  The timer is based on when the command is entered not how long the action takes to complete.  So if you were doing an admin task which took longer than a quarter of an hour,  even though the terminal you first entered the command into would insist on your using sudo again if you tried to do another admin task,  that first command would finish it's job with full privalages. If you enter several admin command within the time window only the first will require "sudo".  You can close this window early,  which is wise if you are doing things online, to do so enter "sudo -k"  

You've set up the firewall in a general purpose manner, now to start it.  So "ufw enable" if sudo has timed out "sudo ufw enable"  

A lot of the advice you will see on forums etc will take the form of commands entered in the terminal and a disproportionate amount of them will be admin actions using sudo, mainly because so many post with problems which need the powers of root to fix.  On your own machine you shouldn't need it nearly so much after you've set things up as you like and all runs well.  Be aware of it's power to break as well as mend.  

You can check terminal advice you are given against the built in manual pages, simply type "man" in front of any command to see it's page.  Eg "man sudo"  

Turning on the firewall before going online is important and on a default install it has to be done throungh the terminal.  It's the only part, IHMO,  which a begginer really needs to do with the command line straight away.  Almost everything else you are likely to do at first while feeling around the OS can be done without ducking under the graphic user interphase.  There are graphic interphases for the firewall too, which can be installed, but to get them ... one usually goes online.

Have fun

---

### Post by mastablasta on 2013-06-07
> **houseworkshy said:**
>  

Turning on the firewall before going online is important and on a default install it has to be done throungh the terminal. It's the only part, IHMO, which a begginer really needs to do with the command line straight away. Almost everything else you are likely to do at first while feeling around the OS can be done without ducking under the graphic user interphase. There are graphic interphases for the firewall too, which can be installed, but to get them ... one usually goes online.


there is a good reason why it is disabled.

furthermore it should not supposed to be dangerous to connect to online repositories and install gufw (the graphic interface). I am not sure, but it might even be on the DVD repository. if you believe repositories have been compomised then the firewall won't help you much anyway.

aditionally modern routers and modems usually have a firewall built in.

---

### Post by 3rdalbum on 2013-06-07
Some of the advice given was good, but the firewall advice was off-the-mark. Ubuntu ignores all incoming connections from the internet, so a firewall will do nothing useful that your system will not already be doing..

If this was Windows XP you would be correct, but this is Ubuntu and it is more sensibly designed than Windows XP.

---

### Post by newb85 on 2013-06-07
> **3rdalbum said:**
> Ubuntu ignores all incoming connections from the internet, so a firewall will do nothing useful that your system will not already be doing..

This is true, unless you set your machine up as a server, in which case you do need to set up a firewall.

On a different note, as a new user, it's important for you to understand the different approach to installing applications.  The Software Center functions a lot like an App Store.  Going to the web and downloading packages can be done, but it's not the most optimal.  The SC is really easy.  More involved package management can be done through Synaptic Package Manager (not installed yet) or using apt-get in the terminal.

---

### Post by houseworkshy on 2013-06-17
Those are fair comments.   The reason I gave that firewall advice was because I hadn't made any assumptions about knowlage level or hardware.  A router is not the only way of connecting to the net and I didn't presume one was present, though less common now dial up isn't gone yet.  Also one can install a desktop which isn't a servor and then convert it into one depending on what one installs.  This could be done by a novice accidentially, even some games have this effect.  Synaptic package manager is explicit about which files are part of any package, the software mangager isn't.  If any 10.04 users were supprised by updates continuing after the support period it was because they'd converted to being a servor, which has an extra two years of updates, without knowing it.  So that is why I gave what may have been redundant advice, just in case it wasn't.  It could be useful and if not wouldn't be harmful.

---

### Post by abhich on 2013-06-17
go to the software center and install the ubutnu restricted extras ... 

it did the trick for me

---

