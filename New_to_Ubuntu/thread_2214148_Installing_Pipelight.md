---
title: "Installing Pipelight"
date: 2014-03-30
forum: New to Ubuntu
---

### Post by Kevin_Verax on 2014-03-30
Hi, I am brand new to using Linux operating systems. I am currently running Ubuntu Version: 12.04 "Precise" ( 64-bit ) on my HP Pavillion 14 Chromebook.

I have recently been trying to install Pipelight as an alternative to Silverlight. I have been trying to use these steps:

[http://linuxg.net/how-to-install-pipelight-0-2-0-on-ubuntu-13-10-13-04-12-10-12-04-linux-mint-16-15-14-13-pear-os-8-7-and-elementary-os-0-2/](http://linuxg.net/how-to-install-pipelight-0-2-0-on-ubuntu-13-10-13-04-12-10-12-04-linux-mint-16-15-14-13-pear-os-8-7-and-elementary-os-0-2/)


I get to the point where it says to do this:

[COLOR=#555555][FONT=consolas]$ sudo apt-get update


[/FONT][/COLOR]And, after it goes through the process of whatever it is doing, I get this:

[COLOR=#696969]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. [/COLOR]

I run the command it lists above, only to get this:

[COLOR=#696969]Setting up pipelight (0.2.3~daily-201401050217~ubuntu13.04.1) ...[/COLOR]
[COLOR=#696969]
[/COLOR]
[COLOR=#696969]The following modules require a license confirmation before they can be enabled:[/COLOR]
[COLOR=#696969]
[/COLOR]
[COLOR=#696969]
[*] Microsoft Silverlight 5.1[/COLOR]
[COLOR=#696969]    By continuing the installation you agree that you've read and accepted the[/COLOR]
[COLOR=#696969]    MICROSOFT SOFTWARE LICENSE TERMS:[/COLOR]
[COLOR=#696969]    [http://go.microsoft.com/fwlink/?LinkId=229303](http://go.microsoft.com/fwlink/?LinkId=229303)[/COLOR]
[COLOR=#696969]
[/COLOR]
[COLOR=#696969]    Microsoft Silverlight Privacy Statement:[/COLOR]
[COLOR=#696969]    [http://go.microsoft.com/fwlink/?LinkId=229306](http://go.microsoft.com/fwlink/?LinkId=229306)[/COLOR]
[COLOR=#696969]
[/COLOR]
[COLOR=#696969]    To find out more click here:[/COLOR]
    [http://www.microsoft.com/silverlig](http://www.microsoft.com/silverlig)ht/
[COLOR=#696969]
[/COLOR]
[COLOR=#696969]
[*] mpg2splt.ax[/COLOR]
[COLOR=#696969]    This library is part of the Microsoft DirectX End-User Runtime.[/COLOR]
[COLOR=#696969]    By continuing the installation you agree that you've read and accepted the[/COLOR]
[COLOR=#696969]    Microsoft Software License Terms.[/COLOR]
[COLOR=#696969]    You can find them in /usr/share/pipelight/licenses/license-mpg2splt.txt[/COLOR]
[COLOR=#696969]
[/COLOR]
[COLOR=#696969]    To find out more click here:[/COLOR]
[COLOR=#696969]    [http://www.microsoft.com/en-us/download/details.aspx?id=35](http://www.microsoft.com/en-us/download/details.aspx?id=35)[/COLOR]
[COLOR=#696969]
[/COLOR]
[COLOR=#696969]
[/COLOR]I have tried installing a few other things, and I run into the same problem. Any help would be greatly appreciated.

---

### Post by monkeybrain20122 on 2014-03-30
Those are eula, when they appear just type y (for 'yes')

---

### Post by Kevin_Verax on 2014-03-30
> **monkeybrain20122 said:**
> Those are eula, when they appear just type y (for 'yes')

It will not let me type any commands.

---

### Post by monkeybrain20122 on 2014-03-30
That tutorial you linked to is outdated.

First go to your home folder, press ctrl+h to see hidden files, if you see a folder called .wine-pipelight, delete it (if not then don't need to do anything)

Now remove those two repositories and whatever you have installed. Open a terminal, type
```
sudo add-apt-repository --remove ppa:mqchael/pipelight
sudo add-apt-repository --remove ppa:ehoover/compholio
sudo apt-get remove --purge pipelight

```
Then  
```

sudo add-apt-repository ppa:pipelight/stable 
sudo apt-get update 
sudo apt-get install --install-recommends pipelight-multi 
sudo pipelight-plugin --update
```

Then close all your browsers (Firefox, Chrome etc) and run in the terminal
```
pipelight-plugin --enable silverlight
```
The guide uses sudo, but you don't have to, and I would rather not
then some licensing agreement will show up, just type y.

Restart your browser and you should see wine installer at work.

[http://fds-team.de/cms/pipelight-installation.html](http://fds-team.de/cms/pipelight-installation.html)

---

### Post by Kevin_Verax on 2014-03-30
When I get to the command:

[COLOR=#696969]sudo apt-get update

[/COLOR]This is what I get:

[COLOR=#696969][/COLOR][COLOR=#696969]E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)[/COLOR][COLOR=#696969]E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/COLOR]

---

### Post by monkeybrain20122 on 2014-03-30
Do you have another instance of the software manager running? (like Software Centre, synaptic, update-manager) If yes then close it, if you can't see anything it may be because it is checking updates in the background, just wait a few minutes til it is done.

---

### Post by Kevin_Verax on 2014-03-30
I currently have Ubuntu Software Center and Update Manager installed. Neither are installing anything or even seem to be checking for updates. 

I still get the same response when I use:

[COLOR=#696969]sudo apt-get update[/COLOR]

---

### Post by monkeybrain20122 on 2014-03-30
ok
```
sudo rm /var/lib/apt/lists/lock
sudo rm /var/cache/apt/archives/lock
```

---

### Post by Kevin_Verax on 2014-03-30
Okay, I will try again in about 15 minutes. I will post the results.

---

### Post by monkeybrain20122 on 2014-03-30
> **Kevin_Verax said:**
> Okay, I will try again in about 15 minutes. I will post the results.

Sorry, see my edit. Shouldn't have taken that long.

---

### Post by Kevin_Verax on 2014-03-30
> **monkeybrain20122 said:**
> ok
```
sudo rm /var/lib/apt/lists/lock
sudo rm /var/cache/apt/archives/lock
```

I did those two commands then tried the:
[COLOR=#696969]
[/COLOR][COLOR=#696969]sudo apt-get update[/COLOR]

Same results.

---

### Post by monkeybrain20122 on 2014-03-30
Try reboot?

---

### Post by Kevin_Verax on 2014-03-31
```
(elementary)kevin@localhost:~$ sudo apt-get update 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?



```

This is what I am still getting. I realize I have failed to mention that I am running this operating alongside ChromeOS via Crouton, if it makes any difference.

---

### Post by monkeybrain20122 on 2014-03-31
> **Kevin_Verax said:**
> 
This is what I am still getting. I realize I have failed to mention that I am running this operating alongside ChromeOS via Crouton, if it makes any difference.

Yeah it may. I have no idea what Crouton is, I suggest you to start another thread to get this sorted first.

---

