---
title: "wifi login password problem"
date: 2012-10-07
forum: New to Ubuntu
---

### Post by oldubdummy on 2012-10-07
I have a Dell netbook Inspiron 910 (purchased 3/2009) which came with and runs Ubuntu (v. 8.04). Although I know nothing about Ubuntu it has worked fine for me until recently when I've encountered a wifi connection problem. The system seems to automatically generate a 16 character password for any wifi site I try to log into. I don't seem to be able to override this and consequently can't login into wifi sites (even those which aren't password protected). Also, for some reason it will let me log into my own wifi network at home. Can anyone help? Thanks

---

### Post by will1982 on 2012-10-07
Can you upgrade the OS?

---

### Post by DuckHook on 2012-10-07
Difficult to remember back that far:D. 8.04 ceased being supported in 2010, so you have been exposed to vulnerabilities for going on 2 years. If you wish to keep using 8.04, I would frankly suggest not using WIFI anyway, since none of the exploits have been remedied, but perhaps I'm just being paranoid. Sorry can't be of more help.

---

### Post by jingaling on 2012-10-07
As the guys have already said, I'd also strongly recommend upgrading as 8.04 reached EOL in 2010 and is no longer maintained.

If you don't like Unity (although I'd urge you to spend a couple of week with it before you make up your mind) you could always install something like XFCE or Cinnamon.

Please let us know how you get on :)

Jing

---

### Post by oldubdummy on 2012-10-10
Thanks to the 3 people who have replied. I'm so new I don't even know how to use forums. Just stumbled on a way (I think). I tried to upgrade to the latest version but was told by the system I ran out of space to load it. I would like to upgrade. How do I clear space to even upgrade?

---

### Post by DuckHook on 2012-10-10
> I'm so new I don't even know how to use forums.In that case, welcome. The forums are easy to use, once you get the hang of them. You seem to have caught on right smartly.

> I would like to upgrade. How do I clear space to even upgrade?We need more details to help you on this one.

1. How large is your HD?
2. Do you have Windows or other OSes on separate partitions?
3. Do you want to save any data that is currently on your computer?
4. If so, do you have any USB keys/drives that can be used to back up this data? What capacity?
5. Do you like the idea of installing a fresh install of the latest version instead of upgrading?

Also, please provide some basic system information like CPU type, amount of main memory, and video card. If you feel up to it, you can simply run the following commands in a terminal, then cut and paste the output to this thread:

First run:

```
lscpu
```Then:

```
free
```Then:

```
lspci
```Then:

```
df
```If you are not comfortable enough with the command line to run these commands, the user manuals that came with your computer can provide this info.

---

### Post by jingaling on 2012-10-10
All of DuckHook's comments and questions are completely valid and we definitely need this information to help. However, I would add that you really should run a backup of your machine before you make any changes to it (I.E. attempt an upgrade/re-install).

The best way of doing this is using Clonezilla, I wrote a guide a while ago (see link below) it's a little rough around the edges as I only wrote it very quickly to help someone in another forum but it should point you in the right direction of backing up and if required, restoring your machine.

[http://goo.gl/XRMqR](http://goo.gl/XRMqR)

---

### Post by squakie on 2012-10-10
Once we have the  information back that DuckHook requested we can give you clearer instructions.  You will want to save any important data, etc. so you could do that anytime.  Jingaling mentioned 1 way.  Since you will probably be doing an install as opposed to upgrading, make sure you have those files backed up so that you can retrieve them easily - perhaps just copying the files to CD or DVD will accomplish this.

Beyond that, after we make sure the specs of your PC support the newest Ubuntu, I would suspect you would be best off with a complete install of version 12.  Trying to upgrade from a release as old as you have will basically be impossible.

EDIT:  I just looked up your PC and found it is a Dell "mini" - a netbook.  The information I found said it would have either an 8gb or 16gb solid state disk.  It's no wonder you can't update, as I suspect you have the 8gb model.  You may want to look at a version of linux that takes less hard disk space as well, as 8gb is pretty tight on space.  Ubuntu 12.04 desktop requires a MINIMUM of 5gb of space.  Add a swap file and any applications and your saved data and you good be looking at a full disk (in your case, SSD).

---

### Post by audiomick on 2012-10-10
> **squakie said:**
>  Trying to upgrade from a release as old as you have will basically be impossible.

I don't know that it is impossible. I believe the older versions are available out of archives somewhere. 8.04 was an LTS, so you would have to upgrade to 10.04 and then to 12.04. I wouldn't bother, though. I personally would be happier copying all the files I want to keep off to somewhere else and then doing a fresh install.

Also, if squakie is right about the size of your drive, you will likely run out of space on the way. I think even the 16GB drive would be a bit too tight for comfort. On top of that, that machine may not be too happy with the Unity desktop. Something like Lubuntu may be a better option.

---

### Post by grahammechanical on 2012-10-10
So, what are you going to do? Upgrade? Change operating systems? Or try to fix the WiFi access problem?

If you want help to fix the problem then you need to give more detail on the problems. As it is four years since I last used 8.04 I cannot give directions using the menu system. You will have to use terminal commands. Are you familiar with the terminal? Even a little bit?

It could be that the settings have changed, somehow. You will need this information to reconnect to your home WiFi:

Router password; encryption mode (usually WPA-PSK) and wireless key (usually 10 characters).

You can usually find this information in the instruction guide that came with the router or on a label stuck on the bottom of the router.

Basically what you need to do is find the utility that sets up network connections (It will be in a menu somewhere - perhaps System>Administration). And set up a new connection using that information. Then delete the old connection. And reboot.

You should be able to select your WiFi from a list of wireless access points in range. try changing the password to that of the wireless key of the router.

If you do find the utility to set up network connections, then tell us what information it requires of you and we will try to direct you where to find it.

Remember, the password is not the password that you use to connect to your computer. It can be called the encryption key, WPA-PSK key, Wireless key. It is the password or phase phrase that gives you access to the router.

The utility will ask for

Wireless tab

SSID - that is the name of your WiFi connection that identifies the router.
Mode - Infrastructure should work
BSSID - ignore - leave blank
Device MAC address - should be automatically detected. It identifies the wireless card in your machine.
Cloned MAC address - leave blank
MTU - Automatic

IPv4 Settings tab

Method - Automatic (DHCP)

do not worry about the rest on this tab

IPv6 Settings tab

Method - Automatic (DCHP)

do not worry about the rest on this tab


Security tab

Security - WPA & WPA2 Personal

Password - this is the wireless key or encryption key or WPA-PSK key. It is the password that grants access to the router.


Regards.

---

### Post by oldubdummy on 2012-10-11
I'm able to connect again. Not sure what I did exactly but I just poked around in the network settings and maybe I unlocked or reset something critical. So for the time being I'm going to use it as is. My main use for this computer is for traveling and I'm just leaving on a trip tomorrow. Thanks to everyone who responded and I may try installing a new version of Ubuntu when I return. I guess from the comments that the best choice is lubuntu. I think it's pretty amazing that you guys have given me this great advice. Thanks again!

---

