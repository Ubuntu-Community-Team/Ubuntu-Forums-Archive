---
title: "Package Installer Error"
date: 2012-05-05
forum: New to Ubuntu
---

### Post by 3dmatrix on 2012-05-05
I am trying to introduce a friend of mine to Linux. She wants to try out on a very old comp with just abt 750 mb ram. I installed Ubuntu 12.04 but the sysrem was getting too slow and finally crashed. Then i tried Lubuntu on it and it worked very well. But i am having a lot of problem installing softwares / upgrading the system.

I am behind a proxy and i do not know if there is any way to set universal proxy setting. I have done the proxy setting in synaptic and added a few softwares but some how it gets stuck at times with some other softwares.

I wanted to add adobe flash pluging and it was waiting for ages. So i killed the process and rebooted. After that synaptic did not work. The error was.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I used the sudo dpkg --configure -a command and found it was stuck at adobe flash plugin stage for ages. This had occured earier many times for other packages also and i used several commands like,

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
dpkg --configure -a
sudo apt-get install
sudo apt-get update 
sudo apt-get upgrade

etc at random ! and it used to somehow go through or i used to delete the lock file in the apt or dpkg folder and some how it used to work. 

But this time it was not giving in so i finally, after trying for two days, got irritated and deleted the entire apt and dpkg folders and since then neither synaptic nor any package manager or any of the above commands are working.

I have been till now blindly trying out my way but now i need to get the comp ready and return it fast so i need proper help. Can any one kindly help me out with this. I need to upgrade the system and add some packages and make it run normally. I am not just interesed in starting synaptic etc but i am interested in making the entire software installing and upgrading process normal so that my friend does not faces any problem while using it. As she is very new to Linux she might simply not use Linux if she faces so much problem.

Please advise.
.

---

### Post by strask on 2012-05-05
> **3dmatrix said:**
> But this time it was not giving in so i finally, after trying for two days, got irritated and deleted the entire apt and dpkg folders and since then neither synaptic nor any package manager or any of the above commands are working.

I'm not sure there is any graceful way to recover from doing that. You might have to re-install ubuntu.

---

### Post by 3dmatrix on 2012-05-05
> **strask said:**
> I'm not sure there is any graceful way to recover from doing that. You might have to re-install ubuntu.

Thats perfectly fine. I definitely Do Not wish to hand over that computer to a person new to Linux in such a PATCHY condition :) but i wish to know well before instaling lubuntu, how to go about solving this kind of problem. I do not wish to keep installing it again and again :)

---

### Post by cortman on 2012-05-05
If it's behind a proxy, you need to add an apt.conf file in /etc/apt with the proxy info. Follow this nomenclature:

```
Acquire::http::Proxy "http://yourproxyaddress:proxyport";
```

See the apt.conf manpage for more info, or this [wiki page.]("https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy")

---

### Post by 3dmatrix on 2012-05-07
> **cortman said:**
> If it's behind a proxy, you need to add an apt.conf file in /etc/apt with the proxy info. Follow this nomenclature:

```
Acquire::http::Proxy "http://yourproxyaddress:proxyport";
```

See the apt.conf manpage for more info, or this [wiki page.]("https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy")

Thanx ! Does that work for all kinds of software installation or upgrades ? Like using Synaptic, apt, software center/installer, upgrade manager ? I wish to know this because i had provided the proxy info in synaptic and it did work well for some packages, till it had to download adobe flash plugin / mas font etc and then again it stopped without any responce.

.

---

### Post by 3dmatrix on 2012-05-07
I added the proxy info in apt.conf file.
But the problem remains.

When in Synaptic i opted for installing Adobe flash plugin i received the following response :

debconf: unable to initialize frontend: Gnome
debconf: (Unable to load Gtk -- is libgtk2-perl installed?)
debconf: falling back to frontend: Dialog
Preconfiguring packages ...
Selecting previously unselected package libspeexdsp1.
(Reading database ... 100578 files and directories currently installed.)
Unpacking libspeexdsp1 (from .../libspeexdsp1_1.2~rc1-3ubuntu2_i386.deb) ...
Selecting previously unselected package libnspr4-0d.
Unpacking libnspr4-0d (from .../libnspr4-0d_4.8.9-1ubuntu2_i386.deb) ...
Selecting previously unselected package flashplugin-installer.
Unpacking flashplugin-installer (from .../flashplugin-installer_11.2.202.235ubuntu0.12.04.1_i386.deb) ...
Selecting previously unselected package libasound2-plugins.
Unpacking libasound2-plugins (from .../libasound2-plugins_1.0.25-1ubuntu1_i386.deb) ...
Processing triggers for update-notifier-common ...
flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.235.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.235.orig.tar.gz)

At this stage it kept waiting endlessly and finally i restarted the comp.
After that when i started Synaptic again it gave the following error :

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I started upgrade manager and and that said due to some errors the upgrade will be partial and i agreed to it.
But it also kept endlessly waiting at the downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.235.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.235.orig.tar.gz) stage !

I do not understand why it has not been programed to tell what problem it is encountering.

I also tried Lubuntu package manager for installing some package and after selecting the package i clicked on "more info" and again it kept waiting without any response.

Its been many days since i am trying to install Lubuntu on this comp but it seems i might have to return my friend's comp and ask her to keep using windows.

---

### Post by cortman on 2012-05-07
> **3dmatrix said:**
> Thanx ! Does that work for all kinds of software installation or upgrades ? Like using Synaptic, apt, software center/installer, upgrade manager ? I wish to know this because i had provided the proxy info in synaptic and it did work well for some packages, till it had to download adobe flash plugin / mas font etc and then again it stopped without any responce.

.

Yes, this works for all package-related actions in Lubuntu.

> **3dmatrix said:**
> I added the proxy info in apt.conf file.
But the problem remains.

When in Synaptic i opted for installing Adobe flash plugin i received the following response :

debconf: unable to initialize frontend: Gnome
debconf: (Unable to load Gtk -- is libgtk2-perl installed?)
debconf: falling back to frontend: Dialog
Preconfiguring packages ...
Selecting previously unselected package libspeexdsp1.
(Reading database ... 100578 files and directories currently installed.)
Unpacking libspeexdsp1 (from .../libspeexdsp1_1.2~rc1-3ubuntu2_i386.deb) ...
Selecting previously unselected package libnspr4-0d.
Unpacking libnspr4-0d (from .../libnspr4-0d_4.8.9-1ubuntu2_i386.deb) ...
Selecting previously unselected package flashplugin-installer.
Unpacking flashplugin-installer (from .../flashplugin-installer_11.2.202.235ubuntu0.12.04.1_i386.deb) ...
Selecting previously unselected package libasound2-plugins.
Unpacking libasound2-plugins (from .../libasound2-plugins_1.0.25-1ubuntu1_i386.deb) ...
Processing triggers for update-notifier-common ...
flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.235.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.235.orig.tar.gz)

At this stage it kept waiting endlessly and finally i restarted the comp.
After that when i started Synaptic again it gave the following error :

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I started upgrade manager and and that said due to some errors the upgrade will be partial and i agreed to it.
But it also kept endlessly waiting at the downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.235.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.235.orig.tar.gz) stage !

I do not understand why it has not been programed to tell what problem it is encountering.

I also tried Lubuntu package manager for installing some package and after selecting the package i clicked on "more info" and again it kept waiting without any response.

Its been many days since i am trying to install Lubuntu on this comp but it seems i might have to return my friend's comp and ask her to keep using windows.

Is the proxy filtering http or ftp content?

---

### Post by 3dmatrix on 2012-05-07
> **cortman said:**
> Yes, this works for all package-related actions in Lubuntu.



Is the proxy filtering http or ftp content?

Its difficult to tell that. But some how these same things work fine on my Ubuntu laptop.
Also i am in China at this moment and any kind of restriction might be possible :)

So what should be my next step ? I am not able to use Synaptic, Apt, Upgrade Manager and Software installer.

---

### Post by cortman on 2012-05-07
Can you successfully ping

```
archive.canonical.com
```

You might be best off reinstalling Lubuntu, as was suggested, and adding the proxy info to apt-conf, then running

```
sudo apt-get update
```

---

### Post by 3dmatrix on 2012-05-07
> **cortman said:**
> Can you successfully ping

```
http://archive.canonical.com/pool/partner/a/adobe-flashplugin/
```

Or just

```
archive.canonical.com
```

You might be best off reinstalling Lubuntu, as was suggested, and adding the proxy info to apt-conf, then running

```
sudo apt-get update
```

I have installed Lubuntu for the 3rd time, added apt.conf proxy details and every time it is getting stuck with this same kind of problem. So i need to find a solution for this or i will keep reinstalling it for weeks. Its not just Adobe flash it might again get stuck while installing any other package. The problem is Lubuntu is behaving like a deaf and dumb person. It just does not communicates as to what prob is being faced. I need a proper solution. I cannot hand over my friend this kind of unrealiable system. She is a first time Linux user and that may bring a bad name for Linux.

---

### Post by cortman on 2012-05-07
> **3dmatrix said:**
> I have installed Lubuntu for the 3rd time, added apt.conf proxy details and every time it is getting stuck with this same kind of problem. So i need to find a solution for this or i will keep reinstalling it for weeks. Its not just Adobe flash it might again get stuck while installing any other package. The problem is Lubuntu is behaving like a deaf and dumb person. It just does not communicates as to what prob is being faced. I need a proper solution. I cannot hand over my friend this kind of unrealiable system. She is a first time Linux user and that may bring a bad name for Linux.

I understand your frustration. Can you try pinging the addresses I gave?

---

### Post by 3dmatrix on 2012-05-07
> **cortman said:**
> I understand your frustration. Can you try pinging the addresses I gave?

Both from the Lubuntu and Ubuntu comp it gives the following result :

ping [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/)
ping: unknown host [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/)

But i can access that link from my browser.

---

### Post by cortman on 2012-05-07
> **3dmatrix said:**
> Both from the Lubuntu and Ubuntu comp it gives the following result :

ping [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/)
ping: unknown host [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/)

But i can access that link from my browser.

Sorry- gave you a bad address. Just run the command

```
ping archive.canonical.com
```

Does that go through?

---

### Post by 3dmatrix on 2012-05-07
> **cortman said:**
> Sorry- gave you a bad address. Just run the command

```
ping archive.canonical.com
```

Does that go through?

Got this error on the Lubuntu comp :

ping archive.canonical.com -c 4
PING archive.canonical.com (91.189.92.150) 56(84) bytes of data.

--- archive.canonical.com ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3024ms

If i do not use the -c 4 option it waits endlessly !

---

### Post by phendrome on 2012-05-07
I'm sorry for my lack of knowledge here.

But regarding the issue on Adobe Flash I'd recommend [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/?src=ss") - an add-on for Mozilla Firefox (also works on every other appropriate channel like Aurora or Nightly) .

**What it is:**
[QUOTE=Flash-Aid]Remove conflicting flash plugins from Ubuntu/Debian Linux systems,  install the appropriate version according to system architecture and  apply some tweaks to improve performance and fix common issues.[/QUOTE]

---

### Post by cortman on 2012-05-07
> **3dmatrix said:**
> Got this error on the Lubuntu comp :

ping archive.canonical.com -c 4
PING archive.canonical.com (91.189.92.150) 56(84) bytes of data.

--- archive.canonical.com ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3024ms

If i do not use the -c 4 option it waits endlessly !

The proxy simply isn't configured correctly. Please copy/paste what you entered into apt.conf here.
Does it require a username/password?
If so, add the information (don't post it here, of course).

> Its difficult to tell that. But some how these same things work fine on my Ubuntu laptop.
Also i am in China at this moment and any kind of restriction might be possible 

So what should be my next step ? I am not able to use Synaptic, Apt, Upgrade Manager and Software installer.

Be completely sure you know everything you need to know about the proxy.
What is the proxy setup you're using on your Ubunut laptop, if that works?

---

### Post by 3dmatrix on 2012-05-07
> **cortman said:**
> The proxy simply isn't configured correctly. Please copy/paste what you entered into apt.conf here.
Does it require a username/password?
If so, add the information (don't post it here, of course).



Be completely sure you know everything you need to know about the proxy.
What is the proxy setup you're using on your Ubunut laptop, if that works?

The proxy info includes the username and pass in the format :

[http://username:password@proxyserver.net:port/](http://username:password@proxyserver.net:port/)

.

---

### Post by cortman on 2012-05-07
Have you used this method?
Delete apt.conf first.

> BASH rc method

This method adds a two lines to your .bashrc file in your $HOME directory. This method is useful if you would like apt-get and other applications for instance wget, to use a http-proxy.


gedit ~/.bashrc
Add these lines to the bottom of your ~/.bashrc file (substitute your details for yourproxyaddress and proxyport)


http_proxy=http://yourproxyaddress:proxyport
export http_proxy
Save the file. Close your terminal window and then open another terminal window or source the ~/.bashrc file:

source ~/.bashrc
Test your proxy with sudo apt-get update and whatever networking tool you desire. You can use firestarter or conky to see active connections.

If you make a mistake and go back to edit the file again, you can close the terminal and reopen it or you can source ~/.bashrc as shown above.

source ~/.bashrc
How to login a proxy user

If you need to login to the Proxy server this can be achieved in most cases by using the following layout in specifying the proxy address in http-proxy. (substitute your details for username, password, yourproxyaddress and proxyport)


http_proxy=http://username:password@yourproxyaddress:proxyport

---

### Post by 3dmatrix on 2012-05-07
well i did the bashrc b4 writing here but i neither did the source nor did i delete the apt-conf file.
So i will try that and tell u soon.

---

### Post by 3dmatrix on 2012-05-07
I have renamed the apt.conf file instead of deleting it.

and have that proxy info in 3 places :

/etc/bash.bashrc:

./.bashrc

and at 

./home/user/.bashrc

done source . . . . . still neither ping nor update manager is working.

---

### Post by cortman on 2012-05-07
At this point I can only conclude that there is something missing in the information you have about the proxy itself, or it was entered wrongly.
You should consider installing Xubuntu- very nearly as lightweight as Lubuntu, and it has a network proxy utility built in. :)

---

### Post by 3dmatrix on 2012-05-08
> **cortman said:**
> At this point I can only conclude that there is something missing in the information you have about the proxy itself, or it was entered wrongly.
You should consider installing Xubuntu- very nearly as lightweight as Lubuntu, and it has a network proxy utility built in. :)

The proxy info cannot be wrong as i have to regularly enter those details in every other package in different laptops. And i have a print out of all that supplied by the admin and if it was wrong i would not have been able to access internet through firefox and synaptic. In fact i installed firefox on Lubuntu through Synaptic under this same proxy server network  :)  on that same comp.

(1) Well i am happy with Lubuntu's low resource hunger. It barely uses 150-200 mb ram out of 750 mb available, so i have enuf ram to use for Liber office etc. In that case dont you think it would be more advisable if i can install xubuntu's network proxy utility in Lubuntu. So kindly tell me what i need to do for that.

(2) First i need to stop apt / upgrade manager / dpkg from trying to install adobe flash. Every time they try to complete that unsucessfull installation. How can i stop that for the time being and rather install other packages that can be done without problem.

(3) My friend is getting impatient so i might have to take her laptop to her place tomorrow to show her the status. There i might get an opportunity to use her wifi network to check if packages like Adobe flash could be installed, as her network is not behind any proxy.

Kindly advise.

---

### Post by cortman on 2012-05-08
Not sure what the package for the xfce network applet is, but I'm sure it's available.
One thing that did come to mind, have you tried setting your repository sources to different mirrors? You can do that in Synaptic. Set it to a mirror near you.

---

### Post by 3dmatrix on 2012-05-08
> **cortman said:**
> Not sure what the package for the xfce network applet is, but I'm sure it's available.
One thing that did come to mind, have you tried setting your repository sources to different mirrors? You can do that in Synaptic. Set it to a mirror near you.

First i need to stop apt / upgrade manager / dpkg from trying to install adobe flash. Every time they try to complete that unsucessfull installation. How can i stop that for the time being and rather install other packages that can be done without problem.

---

### Post by cortman on 2012-05-08
If you're using apt-get install, it shouldn't be trying to install anything else besides what you tell it to.

---

### Post by 3dmatrix on 2012-05-08
> **cortman said:**
> If you're using apt-get install, it shouldn't be trying to install anything else besides what you tell it to.

I am NOT trying to install anything now. FIRST i am trying to STOP the previous incomplete installation of Adobe flash. Because every time i start synaptic / upgrade manager / apt or any thing similar it tries to complete that previous incom[plete installation and as it is not able to install it (for what ever reason) it simply sits there for ages doing nothing. That way it neither installs Adobe flash nor allows me to install anything else. Please read my previous mails i have mentioned many times abt this problem since last few days. I am still in the same stage where i was few days back. This was exactly the same reason why i got fed up last time and deleted the entire folder of apt and dkpg and here i was asked to reinstall Lubuntu but i repetedly asked to help me find the solution of the problem as by reinstalling it is not helping. I have reinstalled Lubuntu for the 3rd time and it every time gets stuck at the same place. Now i need to know how to STOP the installation. May be Lubuntu is too INCOMPLETE OS for me to work with.

---

### Post by cortman on 2012-05-08
Perhaps I have not understood what you're trying to do.
My impression has been that you are trying to install software, and are unable to because of a proxy.
Now you seem to be proposing that you are trying to NOT install software, and that somehow it automatically begins installing packages at the slightest mouse movement,
I'm sorry, but apparently we are not communicating here. It may be time for someone with more knowledge or understanding to step in.
Or perhaps you're right, and Lubuntu isn't for you.

---

### Post by 3dmatrix on 2012-05-09
Every bit of information is clearly mentioned there. Many be many times. So i do not wish to mention it again and again. And if there were other people who could solve it then they would have appeared on the scene by now. Problem occurs when people see things but not read it. I am planning to return that laptop to my friend and ask her to keep using windows. I am a dedicated Linux user for more than 5 years. If i struggle for many days with simple things without proper help then imagin how scary it is for people who are new to Linux. And people in the Linux world consider that these people would come running to embrace Linux !

---

### Post by 3dmatrix on 2012-05-25
Thanx every one for your suggestion.
I was some how able to tackle through all the problems that i faced while doing the installation but eventually my friend is very happy with what she got. She cannot believe that her comp is able to do all the work and still run so fast and has relatively safer OS. Some of the problems like that of Screen brightness and Adobe flash could be resolved till the last moment. I am attaching links of some of the threads that were raised while doing this work. Hope it helps others.

[http://ubuntuforums.org/showthread.php?t=1946411](http://ubuntuforums.org/showthread.php?t=1946411)
[http://ubuntuforums.org/showthread.php?t=1971380](http://ubuntuforums.org/showthread.php?t=1971380)
[http://ubuntuforums.org/showthread.php?t=1979323](http://ubuntuforums.org/showthread.php?t=1979323)
[http://ubuntuforums.org/showthread.php?t=1977974](http://ubuntuforums.org/showthread.php?t=1977974)
[http://ubuntuforums.org/showthread.php?t=1974136](http://ubuntuforums.org/showthread.php?t=1974136)

---

