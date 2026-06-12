---
title: "[SOLVED] downloading flashplayer 9?"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by Camilia on 2008-08-17
I have been trying download flashplayer. I tried using the flashplayer in add and remove and synapse. Using synapse is difficult for I can't view the end of the page. I want to download it so I can here the news at comcast.net

---

### Post by aysiu on 2008-08-17
You should be able to install it by just visiting a website that requires Flash.

More details (with screenshots) here:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

If you want a quick tutorial on Add/Remove and Synaptic, read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by residualbit on 2008-08-17
or search for the "ubuntu restricted extras" package in add/remove. It will add flash and Mozilla support among many other useful plugins.

---

### Post by Camilia on 2008-08-17
Have already done that. I visit comcast.net and when I try to view the news get link to download adobe flashplayer. I click it and get a list of 3 versions. They are tar.gz, .rpm, YUM. I have noticed tar.gz being used at this forum, thus I downloaded that 1.

[QUOTE=nkirk1;5605530]or search for the "ubuntu restricted extras" package in add/remove. It will add flash and Mozilla support among many other useful plugins.[/QUOT

I have tried the add/remove section. Clickedflashblock extension for firefox and nothing happened.

---

### Post by residualbit on 2008-08-17
they should all be the same package (just different compression mediums) I usually go for RPMs becase i have the RPM manager installed already(just search RPM in synaptic) and Red Hat used to be quite popular (until Ubuntu came along) so there are still a ton of rpm packages out there.

---

### Post by Camilia on 2008-08-17
> **nkirk1 said:**
> or search for the "ubuntu restricted extras" package in add/remove. It will add flash and Mozilla support among many other useful plugins.

Did a search for the restricted extras. Didn't find it.

---

### Post by aysiu on 2008-08-17
> **Camilia said:**
> Have already done that. I visit comcast.net and when I try to view the news get link to download adobe flashplayer. I click it and get a list of 3 versions. They are tar.gz, .rpm, YUM. I have noticed tar.gz being used at this forum, thus I downloaded that 1.
No, please read [the link I posted.](http://www.psychocats.net/ubuntu/flash)

You should click the *Install missing plugins* prompt. Don't go to the Adobe website to downlaod Flash.

---

### Post by aysiu on 2008-08-17
> **Camilia said:**
> Did a search for the restricted extras. Didn't find it.
That's because you have to show all available applications.

Read [this link](http://psychocats.net/ubuntu/nonfree) for more details.

And please really do read the links I'm posting. It'll be much easier than doing this back of forth of "It didn't work." "Then try this."

The links I'm giving you have screenshots and step-by-step instructions.

---

### Post by residualbit on 2008-08-17
ok. first go to software sources under the system->admin menu. make sure under the "ubuntu software" tab you have the restricted software enabled and under the third party tab, enable the first one (not the source code) close the window and it will ask you to reload the package info. after that you should be able to find it in add/remove. also, make sure you you have add/remove showing "all available applications" (you will find this to the left of the search box at the top, by default it only shows supported apps)

---

### Post by Camilia on 2008-08-17
> **nkirk1 said:**
> they should all be the same package (just different compression mediums) I usually go for RPMs becase i have the RPM manager installed already(just search RPM in synaptic) and Red Hat used to be quite popular (until Ubuntu came along) so there are still a ton of rpm packages out there.

Did search in synaptic package manager  for RPM and got multi media music box.

> **aysiu said:**
> That's because you have to show all available applications.

Read [this link](http://psychocats.net/ubuntu/nonfree) for more details.

And please really do read the links I'm posting. It'll be much easier than doing this back of forth of "It didn't work." "Then try this."

The links I'm giving you have screenshots and step-by-step instructions.

I think I follow the example at the link.

---

### Post by residualbit on 2008-08-17
> **aysiu said:**
> That's because you have to show all available applications.

Read [this link](http://psychocats.net/ubuntu/nonfree) for more details.

And please really do read the links I'm posting. It'll be much easier than doing this back of forth of "It didn't work." "Then try this."

The links I'm giving you have screenshots and step-by-step instructions.

he's staff, listen to him. that is your best bet!

---

### Post by Camilia on 2008-08-17
> **nkirk1 said:**
> ok. first go to software sources under the system->admin menu. make sure under the "ubuntu software" tab you have the restricted software enabled and under the third party tab, enable the first one (not the source code) close the window and it will ask you to reload the package info. after that you should be able to find it in add/remove. also, make sure you you have add/remove showing "all available applications" (you will find this to the left of the search box at the top, by default it only shows supported apps)

I am confused. You mean system - administration?

I am going to just go to the link aysiu gave me and follow the example.

> **aysiu said:**
> You should be able to install it by just visiting a website that requires Flash.

More details (with screenshots) here:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

If you want a quick tutorial on Add/Remove and Synaptic, read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Just getting more and more confused. Went to this link [http://www.psychocats.net/ubuntu/flash#instal](http://www.psychocats.net/ubuntu/flash#instal) Says go to youtube and click the Install Missing Plugins button. I don't see that.

Also using Synaptic is difficult for can't view the buttons at the bottom of the page.

---

### Post by sharks on 2008-08-17
try for flashplugin-nonfree in synaptic
for terminal:
sudo apt-get install flashplugin-nonfree

---

### Post by dentaku65 on 2008-08-17
Close Firefox

Download the file sources.txt on your desktop.

Open a terminal window and type:
```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.ORIGINAL
```
```
sudo mv ~/Desktop/sources.txt /etc/apt/sources.list
```
```
sudo apt-get update && sudo apt-get dist-upgrade
```
(accept the packages proposed if any)

Install flash
```
sudo apt-get remove gnash && sudo apt-get install flashplugin-nonfree
```

Restart Firefox and enjoy Flash vido sites

---

### Post by Camilia on 2008-08-17
> **aysiu said:**
> That's because you have to show all available applications.

Read [this link](http://psychocats.net/ubuntu/nonfree) for more details.

And please really do read the links I'm posting. It'll be much easier than doing this back of forth of "It didn't work." "Then try this."

The links I'm giving you have screenshots and step-by-step instructions.

I read it and tried. No success. Confused!! Says go to youtube and click the Install Missing Plugins button. I don't see that. Try to view film and get the link which has 3 versions. 

For 4th time I download it. Open with archives. Don't know what else to do.

> **dentaku65 said:**
> Close Firefox

Download the file sources.txt on your desktop.

Open a terminal window and type:
```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.ORIGINAL
```
```
sudo mv ~/Desktop/sources.txt /etc/apt/sources.list
```
```
sudo apt-get update && sudo apt-get dist-upgrade
```
(accept the packages proposed if any)

Install flash
```
sudo apt-get remove gnash && sudo apt-get install flashplugin-nonfree
```

Restart Firefox and enjoy Flash vido sites

What does this mean: Download the file sources.txt on your desktop. 
I flash player installer on desktop. Is that what you mean? All these abbreviations are confusing me.

Found flashplugin-nonfree in Synaptic package manager. Can't view the bottom of the page. I click the x and get message still marked changes that haven't been made. Quitting will cause loss. 

If I were in windows I would adjust the resolution. What can I do to view the whole page so I can click the right buttons.

Decided to dowload ubuntu-restricted extras. Now all I get is a black page

I can't it to work either. Have downloded the ubuntu-restricted-extras flashplugin-nonfree and downloaded the flashplayer 9 tar version. Got a flashplayer installer on desktop. I don't know what to do with it.

> **aysiu said:**
> Unlike most other guides that will plop you to the terminal immediately, this will guide you step by step with screenshots and not assume anything:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

Link says you Click the Install Missing Plugins button at youtube. It didn't see the Missing Plugins button. Only got the link to download flashplayer with the 3 versions.

> **pparks1 said:**
> I tried to provide a short concise set of steps which don't require any knowledge of apt and other utilities.

This is the guide that I put together for another forum. [http://itcertforum.com/forum/showthread.php?t=205](http://itcertforum.com/forum/showthread.php?t=205).   Most members there have had absolutely no experience whatsoever with Linux and many downloaded it after chatting with me.  Many used this guide and successfully were able to get their systems up and operational.   And it's almost exclusively a command line setup guide.   

Just because it's at the command line, doesn't necessarily mean it's complicated.  Maybe by posting my guide link, it will provide him with the information that he needs.

I followed these instructions
Installing the Flash Player...for things like YouTube videos
[http://www.adobe.com/shockwave/downl...ShockwaveFlash](http://www.adobe.com/shockwave/downl...ShockwaveFlash)
Choose Download .tar.gz for Linux. Choose Save file when asked
Open a terminal
Pasted 
gunzip *.gz
tar -xvf *.tar
cd install_flash_player_9_linux/
sudo ./flashplayer-installer 

Got this message
Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

> **Cope57 said:**
> ```
sudo aptitude update && sudo aptitude install swfdec-mozilla swfdec-gnome swfdec-mozilla
```
**Y**/n to any additional dependencies.

But then again, it should work since they are in the Ubuntu [[COLOR="Red"]universe[/COLOR]] repositories.

I do not have Adobe flash installed, and I am able to view flash movies / animations on YouTube, and other places using swfdec.

I pasted the sudo in the terminal and still can't view anything in comcast or youtube.

> **Loaded.len said:**
> "sudo apt-get install ubuntu-restricted extras" worked for me (on several machines) or if you prefer GUI over CLI...

Click Applications
Click Add/Remove
Select All Available Applications in the "Show:" dropdown
Search for "restricted"
Select ubuntu-restricted extras and Apply.

Come to think of it, I DID have some problems on one particular machine... a Blue and White G3 PPC. Never did get it figured out on that bad boy, the PPC architecture just doesn't jive with anything flash related running on Linux.

I tried it and now I get a black page at comcast.net

Now I have flashplayer installer with a lock and package instal_flash player on my desk top. Clicked flashplayer-installer. It installed.
Click install_flash package and get prompted for a location.

---

### Post by Eastisle on 2008-08-17
> **Camilia said:**
> Now I have flashplayer installer with a lock and package instal_flash player on my desk top. Clicked flashplayer-installer. It installed.
Click install_flash package and get prompted for a location.

Hi Camilia, 

If you already did this in the terminal: ```
sudo apt-get install ubuntu-restricted-extras 
```


Open up firefox, in the address bar type:   ```
about:plugins
```

You should see "Shockwave Flash" and something like libflashplayer.so

Anyway, let us know what you see.

---

### Post by Camilia on 2008-08-17
> **Eastisle said:**
> Hi Camilia, 

If you already did this in the terminal: ```
sudo apt-get install ubuntu-restricted-extras 
```


Open up firefox, in the address bar type:   ```
about:plugins
```

You should see "Shockwave Flash" and something like libflashplayer.so

Anyway, let us know what you see.

It says enabled. 

I am beginning to think of going back to windows but fearful for got trojans in it after surfing for pictures for avatar. For I have spent hours trying to get the system set up to view films. I miss hearing the news I want. I was finding good news that is only on film.

---

### Post by dentaku65 on 2008-08-17
> **Camilia said:**
> What does this mean: Download the file sources.txt on your desktop. 
I flash player installer on desktop. Is that what you mean? All these abbreviations are confusing me.

Well... did you see the attach named sources.txt on my post?
I was saying to download that file on your desktop, that's it.

---

### Post by TJCIB on 2008-08-17
Well, as a problem solver, let's start with the simplest problem.

For your terminal (copy and paste):
Make sure you have the Medibuntu repository activated:
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
Then
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

I would remove all of your flash stuff that you've installed and start over.  
```

sudo apt-get purge gnash gnash-common icedtea-gcjwebplugin libflash-mozplugin libflashsupport mozilla-plugin-gnash openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib swfdec-mozilla
```

Then to install *many* of the basic codecs/flash/java you will need:
```
sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar
```

That should get you started.  I know its weird to have 120981 people telling you 61398156 things to do.  This has always worked for me.  I have installed about 20-25 systems in a school computer lab where students really want youtube and flash games...hehe

---

### Post by pparks1 on 2008-08-17
> **Camilia said:**
> I followed these instructions
Installing the Flash Player...for things like YouTube videos
[http://www.adobe.com/shockwave/downl...ShockwaveFlash](http://www.adobe.com/shockwave/downl...ShockwaveFlash)
Choose Download .tar.gz for Linux. Choose Save file when asked
Open a terminal
Pasted 
gunzip *.gz
tar -xvf *.tar
cd install_flash_player_9_linux/
sudo ./flashplayer-installer 

Got this message
Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

Ok, the problem that you have is that when you downloaded the file, you likely saved it to the desktop.   

When you launced the terminal, it likely put you here /home/username (substitute with your user name)

You need to get into the location that contains the flash player file...So this would have done it (if the file was on your desktop
cd ~/Desktop

Then continue with
gunzip *.gz
tar -xvf *.tar
cd install_flash_player_9_linux/
sudo ./flashplayer-installer 


Note:  you will be asked where Firefox is installed to.   Before you start, look at /usr/lib and see what the firefox directory is called (eg.  /usr/lib/Firefox-3.0)

---

### Post by Camilia on 2008-08-18
> **dentaku65 said:**
> Well... did you see the attach named sources.txt on my post?
I was saying to download that file on your desktop, that's it.

What attachement  are you referring to you? Which post?

---

### Post by zakirs on 2008-08-18
camilla good work u stayed this long in a post :D ... btw is your  flash workign now ?? ..  i also had problem installing with synaptic
so i installed using tar file ...

---

### Post by Camilia on 2008-08-18
Well I decided to start over. For in outlook express when I had problems I removed the address and started over. Did so by putting cd for windows in the computer. Then in windows put the ubuntu cd.

Typed in the terminal sudo apt-get install flashplugin-nonfree and it works now. Somehow I had confused the computer.

Thank you everyone for your suggestions. This gives me reasons to keep on trying to use ubuntu and to refer it to others. 

I shall read more of what is in psychocats.net

> **zakirs said:**
> camilla good work u stayed this long in a post :D ... btw is your  flash workign now ?? ..  i also had problem installing with synaptic
so i installed using tar file ...

Yes!! I finally got it working. Decided to use the approach I use when I have proplems with email address not working. Started completely over. Reinstalled windows to get the sound in there working, which removed ubuntu. Then reinstalled ubuntu. Was hoping to have windows and ubuntu but it didn't happen. Anyways then in the terminal pasted sudo apt-get install flashplugin-nonfree.

I just couldn't give up since so many tried to help me. Some how I had gotten the computer confused. For found flashplayer was enabled but still unable to view films.

---

### Post by dentaku65 on 2008-08-18
> **Camilia said:**
> What attachement  are you referring to you? Which post?

Was my previous post 
[http://ubuntuforums.org/showpost.php?p=5605618&postcount=18]("http://ubuntuforums.org/showpost.php?p=5605618&postcount=18")
see at the end.

---

