---
title: "Question about xorgxrdp-hwe-18.04 and xserver-xorg-core"
date: 2023-11-28
forum: New to Ubuntu
---

### Post by suntofu on 2023-11-28
[COLOR=#0C0D0E][FONT=-apple-system]Recently, I had to install xrdp on ubuntu 18.04.5 for a school project to allow for RDP from my windows laptop. After facing the blue screen issue where it just hangs there before giving an error, I searched the internet and I found out about these commands here which is what I used[/FONT][/COLOR]


```
s[FONT=var(--ff-mono)]udo apt install xserver-xorg-core
[/FONT]sudo apt-get -y install xserver-xorg-input-all
[FONT=var(--ff-mono)]sudo apt install xorgxrdp[/FONT]
```

[COLOR=#0C0D0E][FONT=-apple-system]However, I then came upon a post that says this is a dirty fix to solve blue screen issue issue and that it is recommended to use this line instead.

[/FONT][/COLOR]```
[COLOR=#0C0D0E][FONT=ui-monospace]sudo apt-get install xorgxrdp-hwe-18.04[/FONT][/COLOR]
```

[COLOR=#0C0D0E][FONT=-apple-system]Do I have to install xorgxrdp-hwe-18.04 too or can I just stick with my current setup?[/FONT][/COLOR][COLOR=#0C0D0E][FONT=-apple-system]
[/FONT][/COLOR]

---

### Post by MAFoElffen on 2023-11-28
This is a post I posted for installing Minimal X "On-Demand" back in 2012... [https://ubuntuforums.org/showthread.php?t=2137470&p=12614657#post12614657](https://ubuntuforums.org/showthread.php?t=2137470&p=12614657#post12614657)

This is the updated script I have for the Ama-Gi Project LiveUSB:
```

#!/bin/bash


  ## Mike Ferreira: <MAFoElffen@ubuntu.com>, 2021.08.11
   
  ## Setup/Install Minimum X on Debian based Server (Ubuntu)
  # -- Server monitoring software needs a minimal X config for remote 
  # -- graphical admin consoles to use X enabled monitoring tools to  
  # -- display.
  # --
  # -- I like this config so far...
  # -- 
  # -- This install adds a minimal X config that allows an "instance" load of X that 
  # -- server admin tools from a remote graphical X console needs to get working 
  # -- over X enabled ssh.
  # --
  # -- This X instance does not load by default (local on server) and unloads X on exit.


## Installs a Minimal X Server Core
echo "# Installing the XServer core"
echo "#"
echo " "
# Install minimal
sudo aptitude install --without-recommends xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-video-vesa xserver-xorg-video-fbdev xinit


## Installs basic drivers. Uncomment for proper driver if you have one of these
# These are just basic xorg video drivers to drive low-end server GPU's
 # ATI, on most my server boards, Radeon Rage XL.
 #  sudo aptitude install xserver-xorg-video-ati


 ## Intel    
  sudo aptitude install xserver-xorg-video-intel


 ## Sis    
 # sudo aptitude install xserver-xorg-video-sis


 ## Nvidia    
 # sudo aptitude install xserver-xorg-video-nv


# Installs a minimal window environment with a few utils to manage it 
 # After, this can be started locally using "startX" or
 # remotely using "ssh -X username@servername", then load program... 
 # Program will load in an X window on the remote console.
 # 
 # Same is through if I have scripts calling xmessage to display 
 # graphical console error messages...
sudo aptitude install openbox obconf obmenu openbox-themes


# Installs a few graphical apps. To tie into the WE  
sudo aptitude install leafpad synaptic python-software-properties
sudo aptitude install pcmanfm chromium-browser xvidtune gnome-nettool
# sudo aptitude install gmrun wicd


# Add an .Xuthority file to user home
 # If you use ssh with "-X" to enable X over shh, 
 # it needs to see the .Xauthority file of the user.
rm ~/.Xauthority
touch ~/.Xauthority
chmod ~/.Xauthority


# Replaces the menu.xml with with all the edits to add the above app's to the OpenBox menu.
cat << _EOT_ > ~/.config/openbox/menu.xml
<?xml version="1.0" encoding="utf-8"?>
<openbox_menu xmlns="http://openbox.org/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://openbox.org/                 file:///usr/share/openbox/menu.xsd">
    <!-- This file created by MAFoElffen 2013.03.25 -->
        <menu id="root-menu" label="Openbox 3">
        <item label="Byobu">
            <action name="Execute">
                <execute>xterm byobu-launcher</execute>
            </action>
        </item>
        <item label="Terminal Emulator">
            <action name="Execute">
                <execute>x-terminal-emulator</execute>
            </action>
        </item>
        <item label="Web Browser">
            <action name="Execute">
                <execute>x-www-browser</execute>
            </action>
        </item>
        <!-- This requires the presence of the 'menu' package to work -->
        <menu id="applications-menu" label="Applications">
            <item label="Leafpad">
                <action name="Execute">
                    <execute>leafpad</execute>
                </action>
            </item>
            <item label="Leafpad as Root">
                <action name="Execute">
                    <execute>gksudo leafpad</execute>
                </action>
            </item>
            <item label="File Manager">
                <action name="Execute">
                    <execute>pcmanfm</execute>
                </action>
            </item>
        </menu>
        <separator/>
        <menu id="/Debian"/>
        <separator/>
        <menu id="client-list-menu"/>
        <separator/>
        <menu id="system-menu-" label="System Utils">
            <item label="X Video Tune">
                <action name="Execute">
                    <execute>xvidtune</execute>
                </action>
            </item>
            <item label="Synaptic">
                <action name="Execute">
                    <execute>gksudo synaptic</execute>
                </action>
            </item>
            <item label="Network Tools">
                <action name="Execute">
                    <execute>gnome-nettools</execute>
                </action>
            </item>
        </menu>
        <item label="ObMenu">
            <action name="Execute">
                <execute>obmenu</execute>
            </action>
        </item>
        <item label="ObConf">
            <action name="Execute">
                <execute>obconf</execute>
            </action>
        </item>
        <item label="Reconfigure">
            <action name="Reconfigure"/>
        </item>
        <item label="Restart">
            <action name="Restart"/>
        </item>
        <separator/>
        <item label="Exit">
            <action name="Exit"/>
        </item>
    </menu>
</openbox_menu>

```
You can see you don't need much.  On my test-case for supporting XRDP users, I have 'xorgxrdp' installed. I do not have the later package installed, and it works fine. I would say that is probably an improvement, but not needed as minimal. I would add xinit, and the minimal input drivers for a keyboard and mouse. Refer to my script above for those packages. 

You didn't say what minimal desktop you were going to use with xrdp... If you are looking for minimal, I would use either openbox or lxqt-core.

One RDP protocol tip... RDP's limitation is that only one instance of the user you are lgging in with can be logged in at one time. Meaning, if you are logged in as you, you cannot log in again via xrdp. To get around that, I usually created a user (named xrdp_user) that was used just for XRDP sessions. Next, you are going to need to either create/edit the /etc/xrdp/startwm.sh to be able to start that desktop session or install a lightweight Desktop Manager (DM). If you decide to install a DM, I would go with LightDM.

---

### Post by ActionParsnip on 2023-11-28
What are you wanting to do on the remote system? There may be a sleeker solution to what you want to achieve

---

### Post by MAFoElffen on 2023-11-28
> **suntofu said:**
> [COLOR=#0C0D0E][FONT=-apple-system]Recently, I had to install xrdp on ubuntu 18.04.5 for a school project to allow for RDP from my windows laptop. [/FONT][/COLOR]
I would say this. (His homework.)

Which even though on now an old, unsupported OS... (Ubuntu 18.04 End Of Support was at the end of May 2023) I can see that as Academic Instruction, where they use the same instruction plans for years past their due date.

Easier and more elegant would be just install the full package of ubuntu-desktop, which includes full XServer and a Desktop, then install xrdp, and be done with it. But what is the challenge of getting that to work, right? There is more to learn when you understand which pieces "you need" (at a minimum) to make it work.

When I went back to college, all the Desktops we used were Windows Servers, and all our classwork & projects were on Hyper-V VM's, were we could remote VPN into our Class network, into our machines, via RDP. This included Windows and Linux VM Machines. If you didn't log out of your computer before you left, you couldn't work on your homework. (Because of that single user RDP limitation) Same if your session got hung. There was no-one there at night or over the weekend to reset it for you. If it was a weekend, you lost days of work. This made for some wild class projects, were we used every physical machine on a desktop (28), plus an additional 28 rack mounted Servers, switches and routers for our class projects. Our final project was for a State's worth of infrastructure, with one side of the class being the Western part of the State, and the other the Eastern part of the State. You can imagine what we came up with after 2 years of Server Admin (both Windows & Linux) and CCNA networking courses (Cisco Academy) for a Final Project. My part of that (since I had years more of 'professional experience') was building a Virtual Server Farm, and a bank of Virtual Remote Management Consoles to manage everything in the Domain and Sub-Domains. I had fun with it. We could get as creative as we wanted. Because of my previous professional experience, I was hired as a Student Tudor for the whole time I was there. They asked me to apply as one of their professors before I graduated.

---

