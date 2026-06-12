---
title: "Bluetooth disable 14.04"
date: 2015-08-09
forum: New to Ubuntu
---

### Post by jack117 on 2015-08-09
When my computer boots from Win7 to Ubuntu Bluetooth automatically turns on how to disable it completely otherwise I have to manually always turn it off from menu bar

and what does these commands in terminal means 0 upgrade 0 install 12 to remove when I press 0 and enter it shows are you root? 

I only understand this (Y/n) I click capital Y it installs everything, the above commands I don't get it?

---

### Post by CantankRus on 2015-08-09
To stop the bluetooth daemon from starting, create an override file.
ie run in terminal....
```
echo 'manual' | sudo tee /etc/init/bluetooth.override
```

You can still manually start the bluetooth service if needed with....
```
sudo service bluetooth start
```
and stop....
```
sudo service bluetooth stop
```

To have the bluetooth service autostart again, just remove the override file...
```
sudo rm /etc/init/bluetooth.override
```

> **jack117 said:**
> 
..... what does these commands in terminal means 0 upgrade 0 install 12 to remove when I press 0 and enter it shows are you root? 

I only understand this (Y/n) I click capital Y it installs everything, the above commands I don't get it?

That is telling you there is zero to upgrade, zero to install and 12 to remove..... not keys to press.

When you see (Y/n), because the "Y" is capitalised you can just press the Enter key to answer yes or type in "Y". Typing "Yes" or "yes" should also work.

If you are not sure, copy and paste what you are seeing in terminal and post here.

---

### Post by jack117 on 2015-08-09
[QUOTE=CantankRus;13335591]To stop the bluetooth daemon from starting, create an override file.
ie run in terminal....
```
echo 'manual' | sudo tee /etc/init/bluetooth.override
```

That code did override Bluetooth. I don't see Bluetooth in menu bar even though, show Bluetooth in menu bar is checked, however the Bluetooth indicator light is still on. I manually have to slide it to turn off the indicator, this is much worse than switching it off from menu bar.

To enable hibernation in 14.04 I had the following code 'sudo gedit /var/lib/polkit-1/localauthority/50-local.d/hibernate.pkla' 
when the .txt opens I pasted this
[Re-enable Hibernate]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes

yet hibernation was not enabled.

To change scroll overlay to scrollbar this code worked 'gsettings set com.canonical.desktop.interface scrollbar-mode normal' 
However, after restart it gets reset to overlay scroll

---

### Post by CantankRus on 2015-08-09
> Bluetooth indicator light is still on. I manually have to slide it to turn off the indicator
I don't use bluetooth. Are you talking about a light on the actual bluetooth device?

Don't use a laptop so no need for hibernation but from what I've seen hibernation is more trouble than it's worth.

The "**gsettings set com.canonical.desktop.interface scrollbar-mode normal**" command works here and maintains through a reboot.
Don't know why it doesn't work there, but looking at your original post and your lack of understanding of the terminal
but your willingness to run terminal commands I can see how you may have messed something up.

You could try adding the gsettings command to startup applications or just remove the **overlay-scrollbar** package.
Use the synaptic package manager when removing applications so you can check what else might be removed in the process.
```
sudo apt-get install synaptic
```

When removing the **overlay-scrollbar** package it will show you that it is also removing 2 other packages.
You should always check this as you may be left with a broken system.
In this case it's ok to continue and remove the other 2 packages.

---

### Post by jack117 on 2015-08-09
> **CantankRus said:**
> I don't use bluetooth. Are you talking about a light on the actual bluetooth device?

Yes my laptop has a Bluetooth led indicator and small slide button to turn on/off its inbuilt 

> **CantankRus said:**
> Don't use a laptop so no need for hibernation but from what I've seen hibernation is more trouble than it's worth.

I use hibernation in Win7 and use auto power on or task scheduler to wake up my computer, willing to do the same in Ubuntu. 

> **CantankRus said:**
> When removing the **overlay-scrollbar** package it will show you that it is also removing 2 other packages.You should always check this as you may be left with a broken system.
In this case it's ok to continue and remove the other 2 packages.

yes I installed it and searched for overlay, when I scrolled down found overlay-scrollbar with ubuntu logo when I marked them it showed exactly like the pic you attached. If I want to reinstall it later what is the code?
I usually use Ubuntu software centre to uninstall things.

---

### Post by CantankRus on 2015-08-09
```
sudo apt-get install overlay-scrollbar
```
will pull in the other 2 packages removed previously.

Same will happen using synaptic when marking **overlay-scrollbar** for installation.
It will notify you that it will also need to install the other 2 packages.

It's up to you what you use but unless your buying applications, synaptic is safer to use in my opinion.
....and if you use the terminal pay attention to what it's telling you.

---

### Post by jack117 on 2015-08-09
Bluetooth code worked! now I don't see indicator on anymore, all I did was remove the override file and again create it :KS

One last thing before marking this thread as solved ):P

I changed my logon screen image, first time it worked flawless, later I change it with another pic from then I see blank ubuntu red screen (for 2 sec) before my logon pic appear and my internet connection won't connect automatically, why is this happening can I resolve it.

I tried to reset default logon screen then internet connects automatically, but I still see blank screen before log on image appears. I haven't had this problem before why now?

---

### Post by CantankRus on 2015-08-10
Seems you may not have reversed exactly what you did to change the image.
Without knowing exactly what you did or what guide you followed it's hard for me to remedy.

---

### Post by jack117 on 2015-08-10
Bluettoth indicator gets turned on again after restart it doesn't matter, but when I boot in to Win7 from ubuntu and if I forget to turn off bluettoth it automatically get along from the boot. That's my main concern. 

> **CantankRus said:**
> Seems you may not have reversed exactly what you did to change the image.
Without knowing exactly what you did or what guide you followed it's hard for me to remedy.

I followed below link to change my log on:
[URL="http://ubuntuhandbook.org/index.php/2014/04/ubuntu-14-04-change-login-screen-background-remove-the-white-dots/"]http://ubuntuhandbook.org/index.php/2014/04/ubuntu-14-04-change-login-screen-background-remove-the-white-dots/
[/URL]
very first time when I tried to change, it didn't work, then I noticed the default image was in .png so I manually renamed my image format jpg to png it worked flawless like a default logon.

after few months, I again wanted to change it. I had jpg renamed to png it showed maroon blank ubuntu screen, then I converted the image with Shotwell it worked but that maroon screen shows up for 2 sec then my image that's so annoying.

---

### Post by CantankRus on 2015-08-10
I don't see this but I have changed a few things.
I have set the onscreen keybord to show at the greeter.
When doing this the area of the screen behind the keyboard showed as a pink/purple
instead of the image I had set.

To fix I went to **/usr/share/backgrounds** and renamed **warty-final-ubuntu.png** to **warty-final-ubuntu.png.bak**
and copied my greeter backgound pic to **/usr/share/backgrounds**, renaming it **warty-final-ubuntu.png**
The pic I use is a png the same reolution as my screen.
Maybe you see a flash of warty-final-ubuntu.png before your image loads.

I also change the background of the ubuntu plymouth animation from purple to black.

---

### Post by jack117 on 2015-08-10
> **CantankRus said:**
> To fix I went to **/usr/share/backgrounds** and renamed **warty-final-ubuntu.png** to **warty-final-ubuntu.png.bak**
and copied my greeter backgound pic to **/usr/share/backgrounds**, renaming it **warty-final-ubuntu.png**

No but even after reset t default I still get that maroon/purple screen for 2 sec 

I tried to do the same rename warty-final-ubuntu.png in /usr/share/backgrounds but rename is disabled, when I go to that folder and I am not allowed to paste any image even, should I do it with terminal? I don't know the commands.

I right clicked the warty-final>>properties it shows, I am not the owner? but I am the owner.

---

### Post by CantankRus on 2015-08-10
> **jack117 said:**
> No but even after reset t default I still get that maroon/purple screen for 2 sec 

I tried to do the same rename warty-final-ubuntu.png in /usr/share/backgrounds but rename is disabled, when I go to that folder and I am not allowed to paste any image even, should I do it with terminal? I don't know the commands.

I right clicked the warty-final>>properties it shows, I am not the owner? but I am the owner.
Ahhh sorry you said you had been doing a few things so I thought you had an understanding of root and permissions.
You don't have permissions to edit in /usr/share/backgrounds.

To do so you need to open nautilus with gksudo which allows you to run  graphical applications as root.
May need to install gksu.
gksu isn't installed by default any more but you may have already installed it as a dependency for other apps you have installed.

Open nautilus in /usr/share/backgrounds as root....
```
gksudo nautilus /usr/share/backgrounds
```

Careful working as root. Make a note of what you do so you can revert if need be.
You can also work in terminal using sudo but if you don't have a good grasp of terminal 
it is easier and far safer to do it graphically.

You own the contents of your home folder ...most everywhere else you need root privileges to edit.
Which is why you're asked for your admin password when installing applications or
making system wide changes.

---

### Post by jack117 on 2015-08-10
> **CantankRus said:**
> To do so you need to open nautilus with gksudo which allows you to run  graphical applications as root. May need to install gksu.  Open nautilus in /usr/share/backgrounds as root.... ```
gksudo nautilus /usr/share/backgrounds
```

The program 'gksudo' is currently not installed. You can install it by typing:
sudo apt-get install gksu

I did, after some progress it showed 

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
I entered apt-get update and this appears 

E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by CantankRus on 2015-08-10
> **jack117 said:**
> The program 'gksudo' is currently not installed. You can install it by typing:
sudo apt-get install gksu

I did, after some progress it showed 

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
I entered apt-get update and this appears 

E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
You can only run one apt process at a time.
ie if you have synaptic open you cant run a terminal **sudo apt-get**

You need to preface terminal commands requiring root permissions with sudo.
It doesn't tell you in terminal because not all linux distros use sudo.

sudo for terminal commands requiring root permissions.
gksudo for graphical applications requiring root permissions ...ie the command opens an application window.

---

### Post by jack117 on 2015-08-10
> **CantankRus said:**
> You can only run one apt process at a time.
ie if you have synaptic open you cant run a terminal **sudo apt-get**

You need to preface terminal commands requiring root permissions with sudo.
It doesn't tell you in terminal because not all linux distros use sudo.

sudo for terminal commands requiring root permissions.
gksudo for graphical applications requiring root permissions ...ie the command opens an application window.

I don't have synaptic open?

preface terminal commands? were do I get them, now how can I install gksudo I understand you got vexed with questions asked repeatedly can you direct me to a link at least like for example I showed you to change log on screen its easy peasy I just follow it as it is.

---

### Post by CantankRus on 2015-08-10
**gksudo** is installed as part of the **gksu** package.

Some links
[http://www.linfo.org/command_index.html](http://www.linfo.org/command_index.html) 
[http://www.tecmint.com/60-commands-of-linux-a-guide-from-newbies-to-system-administrator/](http://www.tecmint.com/60-commands-of-linux-a-guide-from-newbies-to-system-administrator/)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Also explore the community links at top of the forums

---

### Post by jack117 on 2015-08-10
the last link I came across thru as well

There are youtube videos that explain these commands I learned them before now I completely forgot all. Why is operating an Linux OS so painful not as simple as Windows.

---

### Post by CantankRus on 2015-08-10
> **jack117 said:**
> the last link I came across thru as well

There are youtube videos that explain these commands I learned them before now I completely forgot all. Why is operating an Linux OS so painful not as simple as Windows.
I completely disagree. You don't need to know terminal commands to use Ubuntu.
Terminal commands are an added bonus and in some situations are the best way of doing things. 
You may find most on this forum started on Windows. I spent many long hours installing drivers, configuring anti-virus crap, turning off unneeded 
services so as not to interfere with my gaming etc etc etc.
You forget how much time you put in to learning windows.

I started dual booting about 7 years ago and the rarely used XP install is still there for an old FPS game.
I can now write shell scripts to perform something as simple as toggle the showing of the clock to gathering 
info from various websites and displaying this on the desktop.
Customizing things can be difficult to the new user because with the constantly changing nature of Linux
it can be hard to find the correct info. 
You don't need to pressure yourself to learn... just take your time, use the forums and let it seep in.

Back up your personal files and be prepared to reinstall when you break things.
Half an hour and your back up and running.

Then again if you prefer not to learn a new OS you can just opt into
Windows 10 and it's accompanying Eula.

---

