---
title: "[SOLVED] Networking with Windows"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by Inxi on 2008-11-23
Please note, I have never ever used a Linux before... 

I am having trouble allowing my parents to see my computer. I have just installed Ubuntu 8.10 without any extra programs, dual-boot with a Windows XP that only has SP2 and a sound driver. My parents made a network group on Windows long ago, I can see it, but they cannot see me, and I don't know how to enter it (become member of the group). I seem to be outside of it and my parents can't find my computer from theirs.

I also can't find my Firewall anywhere. Nor can I find my network configurations. I read some guides and they say go to System>Administration>Firewall, it's not there. I can't add it in the menu, either.

I have a wireless connection with my dad's computer.

I basically need my parents to be able to use my printer that's connected to my computer. Ubuntu automatically recognized it, and it prints fine from my Linux desktop (the WinXP part needs the driver and I don't want to bother).

Thanks. Sorry if this was asked before, I saw some threads about this, but they all involved Samba and I don't know what that is.

---

### Post by Poserman on 2008-11-23
check if samba is installed (go to system and find synaptic and search for samba in that). if it is, you should be able to share a folder (right mouse click and search for share). i'm not on ubuntu right now, but if you share a folder they should be able to find you. share a folder (doesn't have to contain files), and then open the terminal (click on the ubuntu logo and under the top folder is terminal) and type ifconfig. go to the windows pc and type this at windows\run:
\\(ipadress)

for example, if your ip adress (you use the ifconfig command for that) is 192.168.1.2 then you type this in windows:
\\192.168.1.2

that should display the folder of your pc.

---

### Post by doas777 on 2008-11-23
ok, first things first. Ubuntu has a firewall called iptables, but it is wholly invissible to the GUI user. to rememdy this, I install a gui front end called firestarter, and set it to run everytime i log in. 

if you want to do it that way, open a terminal (Application -> Accessories -> Terminal) and run:```
sudo apt-get install firestarter
```

if you want the firestarter gui to load in your tray at login, then go to System -> Preferences -> Session. click "Add" on the right.
```

Name: Firestarter
Command: gksu firestarter
Description: a firewall. kewl!

```

 since it uses 'gksu' it will ask for your password while loading. this is needed because for firestarter to change your firewall settings in iptables, you need to be running as root.

as for samba, it is the file/printer sharing protocol that linux uses to talk to windows. it's an OSS implementation of the windows SMB/CIFS protocol suites.

Samba is not installed by default to increase ubuntu's security, so the folder and printer sharing gui apps do nothing until samba is installed and configured. 

check out this guide on samba install. it should help a lot.
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

good luck,
franklin

---

### Post by Inxi on 2008-11-23
Well, I'm having a stranger problem now.

My OS somehow installed Samba on its own when I tried to share a folder. I now have a shared folder. My dad was able to find my computer on his computer by typing in my IP address. He can visit my folder, he can see my printer. But, when he goes to the printer, the printer asks for a driver and says that the "server" does not have the driver installed. He tries to install the driver on his computer, but it doesn't work, obviously. Would installing the XP driver on the XP partition remedy this? o.O

---

### Post by Kellemora on 2008-11-23
Hi Inxi

The Printer Driver MUST be installed on the Computer sending the printing document.

So, if he has a Windows Machine, he should be able to install the driver for your printer from the disk that came with it.
If the printer is USB he can print right to the printer from his machine.
It's much faster and easier that way than sending the file to through the Windows Share, which then ties up both drivers and slows things down.

For example:  I have two options to reach my printer on another machine.  One is to Select the Windows Shared Printer via Cups through to the Samba Share.  The other option is to Select the same printer directly through the USB port to the printer.  This bypasses the driver on the other machine completely, so no printing windows pop-up on that machine.  If I print through the Samba Windows Share, a screen does pop-up saying printing a received downlevel document.

TTUL
Gary

---

### Post by Inxi on 2008-11-23
My dad solved the problem (he manually showed Windows the driver's location or something), so that's good for now. Thanks very much for your help, especially Poserman!

---

### Post by doas777 on 2008-11-23
keep in mind, all you need is the driver, you don;t need all the hp software installed. you would probably need to physically connect the printer to do the full software install.

---

### Post by hyper_ch on 2008-11-23
(1) are you sure you even need a firewall? In most cases you won't...

(2) as for the rest, you need to setup samba for that, try the ubuntu wiki: [https://wiki.ubuntu.com](https://wiki.ubuntu.com)

@ doas77
Firestarter hasn't been updated for a long time and it's not Ubuntu recommendation anymore - however first you should consider whether you really need to alter the default iptables settings at all.

---

### Post by Inxi on 2008-11-23
I asked about the firewall not because I wanted one, but because some page told me to go to a Firewall config when I couldn't even find one.

And I got Samba already. Not sure how, but I do.

---

### Post by hyper_ch on 2008-11-23
Inxi: there are many pages out there that tell many things... however this should not hinder you to use your brain.

If you are, as I assume, behind a router (probably built into your modem) then there is very little use of altering the default behaviour of iptables (= by default it does not filter anything).

---

### Post by doas777 on 2008-11-23
> **hyper_ch said:**
> (1) are you sure you even need a firewall? In most cases you won't...

(2) as for the rest, you need to setup samba for that, try the ubuntu wiki: [https://wiki.ubuntu.com](https://wiki.ubuntu.com)

@ doas77
Firestarter hasn't been updated for a long time and it's not Ubuntu recommendation anymore - however first you should consider whether you really need to alter the default iptables settings at all.

in my case, yes I do need some firewall control, but what is the current recomended gui software that works in tandem with moblock/mobloquer?

thanks,
franklin

---

### Post by Inxi on 2008-11-23
> **hyper_ch said:**
> Inxi: there are many pages out there that tell many things... however this should not hinder you to use your brain.It was on this forum. And I don't see what my brain has to do with any of this.

> **hyper_ch said:**
> If you are, as I assume, behind a router (probably built into your modem) then there is very little use of altering the default behaviour of iptables (= by default it does not filter anything).My router is not in-built into anything. I don't know what IP tables even are. I don't usually deal with networking beyond setting a WEP key and such. I view a firewall as something that blocks information coming from the internet (aka Windows Firewall). I assumed Ubuntu may very well have one.

---

