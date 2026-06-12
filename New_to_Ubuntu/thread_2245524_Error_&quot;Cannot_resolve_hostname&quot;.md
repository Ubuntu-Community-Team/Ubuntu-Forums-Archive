---
title: "Error &quot;Cannot resolve hostname&quot;"
date: 2014-09-24
forum: New to Ubuntu
---

### Post by Aberlour on 2014-09-24
I am new to Ubuntu and know next to nothing about it. My computer experience began with CP/M and MS-DOS and stopped with Win XP Pro..

I have salvaged a Toshiba Satellite A40 which I am hoping to use to run Ubuntu. At present I do not have a HDD (one is on order) so I am booting from CD (Shackbox Premium). 

Everything on the laptop works fine except connecting to the web, which is like looking into a deep dark well - there is light at the top but it quickly gets dark.

I can get a PCMCIA wifi card and wired connection to access my router (which is used for a WinXP laptop). However, when I run Epiphany browser I receive a well known error: "Oops . . . .  (cannot resolve hostname xxxxxxx)" etc.

I have done the following:

Open xterm and then type:[INDENT]su root
password - 123456789, etc
cd /etc 
echo 'name server 8.8.8.8' > resolv.conf
[/INDENT]

But I still get the Error "Cannot resolve hostname" 

My problem now is that further instructions on forums are much more technical that I can grasp, often using terms that I am  not familiar with. I am assuning that (part of) the problem is that I don't have a HDD installed and the changes above are not being written to disk?? If not, where can I find more information that will take me step-wise through solutions in 'plain-speak' please?

Thanks
Alan ~ Aberlour

---

### Post by yancek on 2014-09-24
If you are using  Ubuntu on a DVD and the problem is that changes are not saved, that is expected behavior as the filesystem on the DVD is read-only.  No changes will be saved on reboot.  Or, is the problem that you are not able to access the internet at all?

---

### Post by kira-yamato-2008 on 2014-09-24
If you're having issues with internet access the generic pre-loaded drives for Ubuntu might not recognize your wifi adapter/internal NIC card, assuming you have a wifi NIC. In that case the simplest solution is to get a USB wifi adapter. I personally recommend that you check NewEgg for the Rosewill RNX-N150UBE or RNX-N180UBE. They both tend to be inexpensive, if you want the 300Mbit Wireless N capability go with the N180UBE, which also has a massive antenna with it, which is great if your AP is far away, or beyond several walls.

Edit: If you're not on a Wireless N network the adaptors both are also B/G compatible.

---

### Post by Aberlour on 2014-09-24
Thanks for the replies. The laptop / Ubuntu recognises the the wireless N router, connects to it. When using the PCMCIA wifi card I can see the various 'available' neighbourhood wifi networks. It is not a router or network issue - same router and PCMCIA card work fine on a Windows laptop.

But after connecting the Toshiba (Ubuntu) to the router (enabling network, etc) I just get the "Cannot resolve hostname" error.  So, I cannot access the internet, either through the wireless or wired connection - same error comes up both ways.

Clearly the change to the config file cannot be saved to the CD, but I would have thought that changes to it in memory would apply to the session, but would be lost on re-boot just like the language settings, etc, are lost.

I'll fit a HDD soon and see if it helps, but I think that is not where the problem really lies.

AA

---

### Post by kira-yamato-2008 on 2014-09-24
Hmm have you tried clicking the actual wifi icon at the top right corner? I know this might sound dumb, but there is a GUI wifi connection tool, I assume you used it, but you can never be too sure.

It might be that some how your NIC card is incompatible with the router... This I'd assume would be an exceedingly rare issue, but  sometimes things like this slip through the cracks.

---

### Post by Aberlour on 2014-09-24
Kira, thanks. - I have done all that. The problem is that Ubuntu cannot resolve the DNS. There are many posts on other forums about this, but all suggest the resolv.config solution that I mentioned first. All of the wifi card, wired connection and router setups are working fine. The problem - in the simplest terms - AFAIK, seems to be Ubuntu on my laptop doesn't understand what to do with a URL.

---

### Post by yancek on 2014-09-24
Looking at my resolv.conf file, there is an ip entry for the Gateway and another for the internet provider DNS nameserver.  Have you checked that file to see what you have?  The command you posted will overwrite whatever was previously there.  You need to change it to ADD an entry to the end of the file by using two >>:

> echo 'name server 8.8.8.8' >> resolv.conf

---

### Post by yancek on 2014-09-24
Looking at my resolv.conf file, there is an ip entry for the Gateway and another for the internet provider DNS nameserver.  Have you checked that file to see what you have?  The command you posted will overwrite whatever was previously there.  You need to change it to ADD an entry to the end of the file by using two >>:

> echo 'name server 8.8.8.8' >> resolv.conf

You can get the gateway ip with:  route -n

---

### Post by Aberlour on 2014-09-24
Thanks Yancek. I will have a closer look tomorrow. I should then have a HDD in it which will also make the boot-up faster.

---

### Post by yancek on 2014-09-24
The info I posted above was from another Linux system, non-Ubuntu.  I booted Ubuntu 14.04 and notice that /etc/resolv.conf is just a link to /run/resolvconf/resolv.conf file which has nothing in it but the localhost ip which is not what I expected.  Not sure what the solution is.

---

### Post by sandyd on 2014-09-25
> **yancek said:**
> The info I posted above was from another Linux system, non-Ubuntu.  I booted Ubuntu 14.04 and notice that /etc/resolv.conf is just a link to /run/resolvconf/resolv.conf file which has nothing in it but the localhost ip which is not what I expected.  Not sure what the solution is.

That is because of the new dnsmasq+NetworkManager integration.

I was about to post a screenshot about setting a static ip (along with a DNS server) in the networkmanager gui and seeing if that works, [s]but it seems my network manager systray icon has vanished[/s]

The window should look something like below (at least in 14.04 anyways), just set a unused static ip, gateway, and the dns server.

[ATTACH=CONFIG]256668[/ATTACH]

---

### Post by Aberlour on 2014-09-25
I am in the course of installing a large HDD and lots of RAM and then downloading the latest version of Ubuntu to DVD (via another laptop). I'll then try loading it on the Toshiba. A message originally on the Toshiba's desktop refers to a problem with the original bootable DVD not having the correct configuration(s). This should be fixed with the new d/l.

Hmpff - now the laptop will not power on. This may be terminal . . .

Final update - ALL NOW FIXED. Thanks folks. 2Gb RAM, HDD and latest Ubuntu installed. Problem was that the original installation CD omitted a crucial file, and the suggested fix did not work. 

AA

---

