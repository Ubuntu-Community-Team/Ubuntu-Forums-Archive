---
title: "Cannot get browser connection...help!"
date: 2012-12-01
forum: New to Ubuntu
---

### Post by getagrip on 2012-12-01
I was running an older version of Ubuntu for a few years now. I'm using this on a small EEE-PC I use to surf and write e-mails.

Today I upgraded to Ubuntu 12.04 and cannot get connection. I was on the phone with AT&T tech who helped me "PING" a few sites and verified that my system was working and that the computer is connected. 

However he cannot help me beyond that ...so I'm sitting here with a browser telling me "SERVER NOT FOUND" ...while the computer tells me I'm connected.......what gives??

---

### Post by getagrip on 2012-12-01
....anybody?:(

---

### Post by steeldriver on 2012-12-01
Can you ping the server by name, or only by numeric IP address? if the latter, then it is likely a DNS issue

What kind of internet connection do you have (cable? DSL?) and what is your network hardware (routers / modems etc.)?

---

### Post by getagrip on 2012-12-01
I have AT&T U-Verse broadband. There is a modem in my house connected to their residential cables running through my neighborhood. 
I'm connecting wireless to that modem. BTW with the AT&T tech we ping using numeric IP,it did not work typing in the URL.

---

### Post by steeldriver on 2012-12-01
OK can you try

```
service resolvconf status
``````
cat /etc/resolv.conf
``````
cat /etc/resolvconf/resolv.conf.d/original
``````
dig google.com
```The newer ubuntus use the resolvconf service for DNS lookup and I suspect something has gone awry when it imported your previous static DNS settings

---

### Post by getagrip on 2012-12-01
> **steeldriver said:**
> OK can you try

```
service resolvconf status
``````
cat /etc/resolv.conf
``````
cat /etc/resolvconf/resolv.conf.d/original
``````
dig google.com
```The newer ubuntus use the resolvconf service for DNS lookup and I suspect something has gone awry when it imported your previous static DNS settings

not sure what I'm doing but I typed in each line (in my terminal) like you have above.
The last item "google.com" gave me:
SERVER:127.0.0.1#53(127.0.0.1)
WHEN: Sat Dec 1 22:13:56 2012
MSG SIZE rcvd: 28

I think this is saying that I am connected to my modem, but I still can get the browser to respond.

---

### Post by Sef on 2012-12-01
> Today I upgraded to Ubuntu 12.04 and cannot get connection.

1) What did you upgrade from?

2) How did you upgrade: fresh install or progressive upgrade?

---

### Post by getagrip on 2012-12-01
> **Sef said:**
> 1) What did you upgrade from?

2) How did you upgrade: fresh install or progressive upgrade?

good question.  For a few years I was running a version 11.-blah-blah, doing the regular updates to my software (browser etc.) 

But today I decided to upgrade from the periodic update notification I get. I just hit the upgrade button, for 12.04 LTS....and here I am. So it was a progressive upgrade , not a fresh install.

---

### Post by Sef on 2012-12-01
> For a few years I was running a version 11.-blah-blah, doing the regular updates to my software (browser etc.) 

Which version of 11.xx: 11.04 or 11.10?

---

### Post by NikTh on 2012-12-01
Hi , 
open a terminal and give here the results of the commands below. Execute them one at time. 

```
lspci -nnk | grep -iA2 net 
ping -c 2 8.8.8.8
ping -c 2 google.com
dmesg | grep -ie apparmor -ie net -ie ufw
nmcli nm status
```_Please click on **"New Reply"** and put the results inside [CODE] tags to be easier to read._ [See here how]("http://i.stack.imgur.com/zADbK.png")

Thanks

---

### Post by getagrip on 2012-12-01
> **NikTh said:**
> Hi , 
open a terminal and give here the results of the commands below. Execute them one at time. 

```
lspci -nnk | grep -iA2 net 
ping -c 2 8.8.8.8
ping -c 2 google.com
dmesg | grep -ie apparmor -ie net -ie ufw
nmcli nm status
```_Please click on **"New Reply"** and put the results inside [CODE] tags to be easier to read._ [See here how]("http://i.stack.imgur.com/zADbK.png")

Thanks

I have a easier solution. I have no personal file to lose on this machine, I think it may be easier to completely re-install 12.04 on my system.

I don't have a CD drive on this machine, only a USB. I see that downloading the "ISO" file on my flash drive and setting my bios to boot first from the USB does not work. I remember there was a way to boot from the flash drive and then it gave you the option to install on your system, is this still available? Because I don't want to go through that intermediate step of screwing around with the iso file?

---

### Post by NikTh on 2012-12-01
> **getagrip said:**
> I have a easier solution. I have no personal file to lose on this machine, I think it may be easier to completely re-install 12.04 on my system. 
Well , for me the re-installation is not a solution , but yes is easier and faster :) 

> **getagrip said:**
> I don't have a CD drive on this machine, only a USB. I see that downloading the "ISO" file on my flash drive and setting my bios to boot first from the USB does not work. I remember there was a way to boot from the flash drive and then it gave you the option to install on your system, is this still available? Because I don't want to go through that intermediate step of screwing around with the iso file?

You have to use a program like => [Unetbootin]("http://unetbootin.sourceforge.net/") to make the usb bootable. Scroll down the page to see a short installation tutorial (with pictures) . Is easy to use.

Thanks

---

