---
title: "Installing DHCP Server Without Internet Connection"
date: 2015-02-18
forum: New to Ubuntu
---

### Post by samer4 on 2015-02-18
** I am trying to Install the DHCP Server on Ubuntu Server 14.04 **

So I have a project at school and I have never used ubuntu before.

I installed Ubuntu Server but for some reason it didn't install the DHCP Server so now I have do it manually.

But I am not supposed to use internet connection.

How can I install the DHCP Server without internet if possible?!

---

### Post by Doug S on 2015-02-18
Hi and welcome to Ubuntu forums> **samer4 said:**
> I installed Ubuntu Server but for some reason it didn't install the DHCP ServerCorrect, the DHCP server is a post installation addition. > **samer4 said:**
> so now I have do it manually.Yes, that's right.> **samer4 said:**
> But I am not supposed to use internet connection. How can I install the DHCP Server without internet if possible?!That doesn't make any sense.

If you are allowed to use another computer to get the package, I guess you could do that and then copy the .deb files over via a memory stick or something. However, if you have never used Ubuntu before, it doesn't make sense to do it that way, unless that is the point of the assignment.

---

### Post by samer4 on 2015-02-18
The lab is not connected to the internet for security reasons.

I went to Ubuntu website but I cannot figure out which .deb files to download and how to run them.

---

### Post by Doug S on 2015-02-19
See [this page]("http://packages.ubuntu.com/trusty/isc-dhcp-server") and start by checking if you have the "depends on" packages, because if not you will need them also.

For example, I wonder if I have the "adduser" package that it depends on?```
doug@s15:~/sguide-trunk/serverguide/serverguide/C$ [COLOR=#ff0000]dpkg -l | grep adduser[/COLOR]
[COLOR=#ff0000]ii [/COLOR] [COLOR=#ff0000]adduser[/COLOR]                              3.113+nmu3ubuntu3                     all          add and remove users and groups
```Agh, I do.

O.K. lower down of the page I referenced above, there is a section called "Download isc-dhcp-server" click on the correct link for your installation, i386 or amd64 and get the .deb to somewhere then (amd64 example):```
sudo dpkg -i isc-dhcp-server_4.2.4-7ubuntu12_amd64.deb
```And if you are not already doing so, use the [Ubuntu serverguide]("https://help.ubuntu.com/lts/serverguide/dhcp.html") as your main reference for setup.

---

### Post by samer4 on 2015-02-19
Okay and how do I know if I have those packages or not?

I will definitely wait for our update!

---

### Post by Doug S on 2015-02-19
> **samer4 said:**
> Okay and how do I know if I have those packages or not?Here is an example of what I get for a package that I do not have:```
doug@s15:~/sguide-trunk/serverguide/serverguide/C$ [COLOR=#ff0000]dpkg -l | grep ubuntu-gnome-desktop[/COLOR]
doug@s15:~/sguide-trunk/serverguide/serverguide/C$
```i.e. nothing was listed.

---

### Post by samer4 on 2015-02-19
> **Doug S said:**
> See [this page]("http://packages.ubuntu.com/trusty/isc-dhcp-server") and start by checking if you have the "depends on" packages, because if not you will need them also.

For example, I wonder if I have the "adduser" package that it depends on?```
doug@s15:~/sguide-trunk/serverguide/serverguide/C$ [COLOR=#ff0000]dpkg -l | grep adduser[/COLOR]
[COLOR=#ff0000]ii [/COLOR] [COLOR=#ff0000]adduser[/COLOR]                              3.113+nmu3ubuntu3                     all          add and remove users and groups
```Agh, I do.

O.K. lower down of the page I referenced above, there is a section called "Download isc-dhcp-server" click on the correct link for your installation, i386 or amd64 and get the .deb to somewhere then (amd64 example):```
sudo dpkg -i isc-dhcp-server_4.2.4-7ubuntu12_amd64.deb
```And if you are not already doing so, use the [Ubuntu serverguide]("https://help.ubuntu.com/lts/serverguide/dhcp.html") as your main reference for setup.


The Ubuntu server guide doesn't cover how to Install the DHCP Server manually without internet connection using a flash drive though.

---

### Post by Doug S on 2015-02-19
> **samer4 said:**
> The Ubuntu server guide doesn't cover how to Install the DHCP Server manually without internet connection using a flash drive though.No, I meant to use the serverguide for the setup of it once you had it installed.

Are you saying you don't know how to mount a flashdrive so that you can copy over the .deb file?
Edit: If so try [this]("https://help.ubuntu.com/community/Mount/USB#Manually_Mounting")

---

### Post by samer4 on 2015-02-19
So the way I install the DHCP Server is to download the .deb file then put it on a flash drive then use this command "sudo mount -t vfat /dev/sdb1 /media/external" to mount the flash disk

then use this command to install the DHCP "sudo dpkg -i isc-dhcp-server_4.2.4-7ubuntu12_amd64.deb" ?

---

### Post by Doug S on 2015-02-19
> **samer4 said:**
> So the way I install the DHCP Server is to download the .deb file then put it on a flash drive then use this command "sudo mount -t vfat /dev/sdb1 /media/external" to mount the flash disk

then use this command to install the DHCP "sudo dpkg -i isc-dhcp-server_4.2.4-7ubuntu12_amd64.deb" ?Well yes, but I would copy the file to the local drive first, just to save time if I needed it again in future. I would then install it from the copied to spot. The example install command I gave was assuming you were currrently in the same directory as the .deb file, otherwise precede the file name with the path stuff

---

### Post by samer4 on 2015-02-19
> **Doug S said:**
> Well yes, but I would copy the file to the local drive first, just to save time if I needed it again in future. I would then install it from the copied to spot. The example install command I gave was assuming you were currrently in the same directory as the .deb file, otherwise precede the file name with the path stuff

This might sound stupid but remember I am new to ubuntu! How can I copy them to the local drive first if I am using Ubuntu Server and its just command lines?

---

### Post by Doug S on 2015-02-20
> **samer4 said:**
> This might sound stupid but remember I am new to ubuntu! How can I copy them to the local drive first if I am using Ubuntu Server and its just command lines?```
man cp
```type 'q' to exit once you have read the page.

---

### Post by SeijiSensei on 2015-02-20
I just installed isc-dhcp-server on a brand-new Ubuntu Server 14.04 VM.  It had no other dependencies, so you don't need to worry about any other files but the DHCP server .deb.

---

### Post by samer4 on 2015-02-23
Okay I will try that and report back, thank you for your help!

---

