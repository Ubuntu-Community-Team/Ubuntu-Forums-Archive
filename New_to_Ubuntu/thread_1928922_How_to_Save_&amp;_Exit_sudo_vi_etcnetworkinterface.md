---
title: "How to Save &amp; Exit sudo vi /etc/network/interfaces"
date: 2012-02-21
forum: New to Ubuntu
---

### Post by RyujiOtogi on 2012-02-21
'Ello. I'm a helpless Linux noob in desperate need of some common sense here. :confused:

I'm running Ubuntu Server 11.10 x64 bit using VirtualBox on my Mac OS X Lion. I'm trying to change my DHCP to a Static IP address, so I typed sudo vi /etc/network/interfaces as an internet How-To instructed me. I've got two questions:

1) The How-To says to change "iface eth0 inet **dhcp**" to "iface eth0 inet** static**", which is easy enough. Then it says I've got to enter my address, netmask, network,  broadcast, and gateway values. I can see what the address, netmask, and network values are in OS X Lion: System Preferences-->Internet & Wireless-->Network-->Advanced-->TCP/IP.  

But I don't know what to enter for broadcast and gateway, if those are necessary. If I must, how I do find out those addresses? I suppose you may need have OS X to help me out here. 

2) Ok, so this is what's really frustrating me. The How-To's I've been reading simply say to save and exit the network configuration settings in "sudo vi /etc/network/interfaces" discussed above, while moving on to the next step. Since Google hasn't helped (at all) in discovering ***HOW TO*** save or even exit 'sudo vi', I presume only the stupidest n00b on the face of the planet would have to ask. Well, that's me. I've hit the enter button after making the changes, hit ESC, tried sudo exit commands, and basically went crazy all over my keyboard in a vain and pitiful attempt just to exit the freakin' 'sudo vi' configurations. I've had to power off my virtual machine to reboot, and try again with just as much [un]success. 

I've come here because no amount of Googling has helped me. So please Ubuntu community, if you could help get this n00b's face out of his butt you would make someone really happy. :P

---

### Post by prshah on 2012-02-21
> **RyujiOtogi said:**
> 
But I don't know what to enter for broadcast and gateway, if those are necessary. If I must, how I do find out those addresses? I suppose you may need have OS X to help me out here. 

***HOW TO*** save or even exit 'sudo vi',

To answer in reverse order:

In vi(m), use ":" to bring up the command line. You can then use the single letter command w(rite) and q(quit) and enter. You can use them singly or combined, ie, "wq" to write and quit. Additional useful command include "!" (for abandon) eg, "q!" will quit abandoning changes. Please do not include the double quotes ("") shown when issuing your commands.

Gateway is required to connect to the Internet. You can ignore broadcast safely.

Gateway will typically (for most home users) be the same as the router address (ususally, 192.168.1.1). This is also sometimes called the "Default route".

Hope this helps.

---

### Post by bab1 on 2012-02-21
> **RyujiOtogi said:**
> [FONT=Century Gothic]'Ello. I'm a helpless Linux noob in desperate need of some common sense here. :confused:

I'm running Ubuntu Server 11.10 x64 bit using VirtualBox on my Mac OS X Lion. I'm trying to change my DHCP to a Static IP address, so I typed sudo vi /etc/network/interfaces as an internet How-To instructed me. I've got two questions:

1) The How-To says to change "iface eth0 inet **dhcp**" to "[/FONT][FONT=Century Gothic]iface eth0 inet** static**", which is easy enough. Then it says I've got to enter my address, netmask, network,  broadcast, and gateway values. I can see what the address, netmask, and network values are in OS X Lion: System Preferences-->Internet & Wireless-->Network-->Advanced-->TCP/IP.  

But I don't know what to enter for broadcast and gateway, if those are necessary. If I must, how I do find out those addresses? I suppose you may need have OS X to help me out here. 

2) Ok, so this is what's really frustrating me. The How-To's I've been reading simply say to save and exit the network configuration settings in "sudo vi /etc/network/interfaces" discussed above, while moving on to the next step. Since Google hasn't helped (at all) in discovering ***HOW TO*** save or even exit 'sudo vi', I presume only the stupidest n00b on the face of the planet would have to ask. Well, that's me. I've hit the enter button after making the changes, hit ESC, tried sudo exit commands, and basically went crazy all over my keyboard in a vain and pitiful attempt just to exit the freakin' 'sudo vi' configurations. I've had to power off my virtual machine to reboot, and try again with just as much [un]success. 

I've come here because no amount of Googling has helped me. So please Ubuntu community, if you could help get this n00b's face out of his butt you would make someone really happy. :P
[/FONT]

To make it a little simpler, just substitute *nano* for *vi*  The commands are listed at the bottom of the screen.  The command would be ```
sudo nano /etc/network/interfaces
```

---

### Post by Elfy on 2012-02-21
> **bab1 said:**
> To make it a little simpler, just substitute *nano* for *vi*  The commands are listed at the bottom of the screen.  The command would be ```
sudo nano /etc/network/interfaces
```

Then

Ctrl+O to save

Ctrl+X to exit

Banner at the bottom of the terminal shows commands.

If you know you want to save it then Ctrl+X will prompt for a save before exit if it has not been saved.

If you run 

sudo nano -B /file/path

it will also create a backup for you.

---

### Post by RyujiOtogi on 2012-02-21
Ah, thank you! Being able to use the command line again was a huge help. :)

---

### Post by thirnick on 2012-02-21
a program call netstat might be useful

netstat -r        /routing table

netstat -i        /interface table

---

