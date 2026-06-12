---
title: "Absolute Beginner - Software Help"
date: 2013-08-27
forum: New to Ubuntu
---

### Post by Abhilash_Anandan on 2013-08-27
Hey! 

This is my first post in the forums. Nice to see you guys, hoping to meet a lot of wonderful people.

I just got Ubuntu installed a few minutes ago and I'm here. I like being on the go, ie. I mainly live on the internet. What are the softwares that you guys use to keep stuff synced? Cloud accounts? IM?

And, any must have Linux softwares?

---

### Post by Niall_Dawson on 2013-08-27
Personally, I'd use a server with LAMP (apache, php and mysql) to access and back my files up remotely (still kind of new myself but the basics are easy, trust me ;) ) if you do decide to do that I'd install shorewall, which is a firewall service which is supercool and easy to use. The best way to manage your mySQL Database is with phpmyadmin. Theres many tutorials up here on how to use these :) 

PS: if youre using Ubuntu Server its convient to use the desktop GUI.

---

### Post by Jonathan Precise on 2013-08-27
If you have the latest ubuntu version installed (Ubuntu 13.04), then go to System settings, and click on online accounts. Then click on the account service you want to use, and then you should be directed to their login page. Please see their [legal notice]("http://www.canonical.com/legal") and [privacy policy]("http://www.ubuntu.com/privacy-policy").

I recommend avant-window-navigator and some applets to go with it. It can be installed by going to a terminal and typing:

```
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo add-apt-repository ppa:dockbar-main/ppa
sudo apt-get update
sudo apt-get install awn-applet-dockbarx avant-window-navigator awn-settings awn-applets-all
```

If there is any error, don't worry, as avant-window-navigator and most of its applets should be installed (it worked for me!).

---

### Post by Abhilash_Anandan on 2013-08-27
> **Niall_Dawson said:**
> Personally, I'd use a server with LAMP (apache, php and mysql) to access and back my files up remotely (still kind of new myself but the basics are easy, trust me ;) ) if you do decide to do that I'd install shorewall, which is a firewall service which is supercool and easy to use. The best way to manage your mySQL Database is with phpmyadmin. Theres many tutorials up here on how to use these :) 

PS: if youre using Ubuntu Server its convient to use the desktop GUI.

Thank you Neil_Dawson. I guess I wasn't clear enough. I don't have a server or anything. I just browse. :p

> **Jonathan Precise said:**
> If you have the latest ubuntu version installed (Ubuntu 13.04), then go to System settings, and click on online accounts. Then click on the account service you want to use, and then you should be directed to their login page. Please see their [legal notice]("http://www.canonical.com/legal") and [privacy policy]("http://www.ubuntu.com/privacy-policy").

I recommend avant-window-navigator and some applets to go with it. It can be installed by going to a terminal and typing:

```
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo add-apt-repository ppa:dockbar-main/ppa
sudo apt-get update
sudo apt-get install awn-applet-dockbarx avant-window-navigator awn-settings awn-applets-all
```

If there is any error, don't worry, as avant-window-navigator and most of its applets should be installed (it worked for me!).

Thank you Jonathan Precise. I did the Online Accounts thing. Yes, I have ubuntu 13.04. 

I pasted the commands and it said something about PPA? What is PPA? I did the first three commands without any problems. The 4th one gave me an error.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 awn-applets-all : Depends: awn-applet-bandwidth-monitor but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
 

```

I don't see any changes? What is avant-window-navigator & applets?

What is a wbui install & why go full? And why not to have fast startup in Windows 8? I did not like Windows 8.

---

### Post by nerdtron on 2013-08-27
> **Abhilash_Anandan said:**
> 

I just got Ubuntu installed a few minutes ago and I'm here. I like being on the go, ie. I mainly live on the internet. What are the softwares that you guys use to keep stuff synced? Cloud accounts? IM?

And, any must have Linux softwares?

You mainly live in the internet and want your stuffs to be in synced? Use firefox or Chrome and use their Sync feature to sync your tabs, preferences and even passwords. For syncing files, there is Dropbox. And that is pretty much it.
Install Pidgin or Empathy or Skype to chat with your friends on Facebook and other IM accounts.

---

### Post by Crusty Old Fart on 2013-08-28
"rsync" is highly recommended and most likely was installed as part of your new Ubuntu OS.
See the man page.
From a terminal window, enter the following command:
```

man rsync

```

Oh yeah, almost forgot...Welcome to the playpen.

---

### Post by mastablasta on 2013-08-28
> **nerdtron said:**
>  For syncing files, there is Dropbox. And that is pretty much it.



that's not preety much it. 

by default ubuntu comes with Ubuntu One which offers 5GB free space and more if you buy it. it can sync between various devices.

then one can also use Spideroak which provides encrypted data sharing. is quite a bit slower than dropbox and ubutnu one and it offers only 2 or 3 GB free space, but then again it's encrypted. and you have the key.

i am sure there are others out there. you can even create your own cloud. 

as for software to use - install what you need/want. what do you plan to do (develop, game, video editing, sound editing, picture editing, wirting...)? just surf the internet?

---

### Post by newb85 on 2013-08-28
+1 for UbuntuOne.  I prefer it because it can sync any folders on my system I choose.  (I haven't tried Dropbox, but I've been told by multiple friends who use it that it doesn't have this capability.)

---

### Post by Jonathan Precise on 2013-08-29
> **Abhilash_Anandan said:**
> Thank you Jonathan Precise. I did the Online Accounts thing. Yes, I have ubuntu 13.04. 

I pasted the commands and it said something about PPA? What is PPA? I did the first three commands without any problems. The 4th one gave me an error.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 awn-applets-all : Depends: awn-applet-bandwidth-monitor but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
 

```

I don't see any changes? What is avant-window-navigator & applets?

What is a wbui install & why go full? And why not to have fast startup in Windows 8? I did not like Windows 8.

Regarding the PPA question:

A PPA is a Personal package archive. In other words, it contains software not included with a standard ubuntu install.:)

For the avant-window-navigator problem, try:

```
sudo apt-get install awn-applet-dockbarx avant-window-navigator awn-settings awn-applet-yama awn-applet-digital clock
```

Put in simpler terms, avant-window-navigator (awn for short) is just a task-bar (like the bottom bar you see in windows, but it looks different). Plugins for awn just provide things like a clock, Application Icons, and menus. Customize to your liking!!!;)


-----------------------------------------------------------------------Regarding my signature-----------------------------------------------------------------------

A wubi install (Ubuntu installer for windows) can get damaged easily, something that's not likely to happen in a full installation. The reason why (boring explanation, feel free to skip the rest of this paragraph) is that the windows file-system (NTFS) can get corrupted and fragmented easily. This does not happen in a standard ubuntu, as it has an ext4 (or ext3, or ext2) file-system.

As for fast start-up, disable it, as it uses hibernation. This can be bad because (once again, a boring explanation, feel free to skip it) if you use ubuntu to mount a file-system (without the hiberfile) you use for work in windows, and you change anything in it, your data can be LOST!!!!!!! Disable fast start-up to avoid this.

---

