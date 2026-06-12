---
title: "HOWTO: Install Avast Antivirus."
date: 2006-08-04
forum: Outdated Tutorials &amp; Tips
---

### Post by yopnono on 2006-08-04
Download the .DEB from 
[http://www.avast.com/eng/download-avast-for-linux-edition.html](http://www.avast.com/eng/download-avast-for-linux-edition.html)

Install it using GDebi or use the terminal.
```
sudo dpkg -i file_name.deb
```

If you don't get any icon/menu entry in the Application-Accessories menu.
Then run this in the terminal
```
cd /usr/lib/avast4workstation/share/avast/desktop
sudo ./install-desktop-entries.sh install
```

If you like to use GTK 2.x then work your way to the avast directory.
```
cd /usr/lib/avast4workstation
```
Then just remove the 
```
sudo rm -rf lib-x11/
```
and
```
sudo rm -rf lib-gtk2/
```
Thats it.

EDIT: Screenshot GTK 1.2
EDIT 2: Added screenshot using GTK 2. See attachment (last img.) And added som info on how to make it use GTK 2.x, Thanks from forum members in this thread.

---

### Post by abandoned_hussam on 2006-08-04
what does it look like? could you post a screenshot?

---

### Post by yopnono on 2006-08-04
> **hussam said:**
> what does it look like? could you post a screenshot?
Done..

---

### Post by tjansson on 2006-08-04
Why would you need a virus scanner? All software is from a trusted source (apt) and ubuntu doesn't led you run sofware as root without password.

---

### Post by skymt on 2006-08-04
> **tjansson said:**
> Why would you need a virus scanner? All software is from a trusted source (apt) and ubuntu doesn't led you run sofware as root without password.

If you want to send a file you downloaded from the web to a Windows user, it's a good idea to make sure it's virus-free.

---

### Post by ephraste on 2006-08-26
Thanks works great !
i was lost with the menu entry

---

### Post by Matrixy on 2006-08-26
Hi,
how can i install it on amd64 ubuntu?

---

### Post by yopnono on 2006-08-26
Hi I have truly no idea, sorry. But check the avast forum.
[http://forum.avast.com/](http://forum.avast.com/)

---

### Post by Matrixy on 2006-08-26
ok thx

---

### Post by munkiepus on 2006-10-13
I managed to install the 32 bit version of avast on 64 bit Kubuntu with the following command and it works fine. You do need the 32bit libs though.

sudo dpkg -i --force-architecture avast4workstation_1.0.6-2_i386.deb



Steps:
I had already installed the 32bit libs (i think when i was installing wine)

not 100% :confused: sure but if i remember correctly it was from the following post 
[http://ubuntuforums.org/showthread.php?t=185557](http://ubuntuforums.org/showthread.php?t=185557)


the code i think you need you need is (copied from the other post):

Download the 32 bit libs
[COLOR="DarkSlateBlue"][http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Flibx%2Flibxxf86dga%2Flibxxf86dga1_1.0.0-0ubuntu3_i386.deb&md5sum=f1f2a20a6db2bf5eb44db45cdb3a1337&arch=i386&type=main]("http://http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Flibx%2Flibxxf86dga%2Flibxxf86dga1_1.0.0-0ubuntu3_i386.deb&md5sum=f1f2a20a6db2bf5eb44db45cdb3a1337&arch=i386&type=main")
Save the files to your desktop.

First we will install the needed libraries.
Code:

cd ~/Desktop dpkg -x libxxf86dga1_1.0.0-0ubuntu3_i386.deb libs sudo cp ~/Desktop/libs/usr/lib/* /usr/lib32
[/COLOR]


You now ahve the needed 32 bit libs and can force avast to install using them

sudo dpkg -i --force-architecture avast4workstation_1.0.6-2_i386.deb


Hope this helps, It worked for Me. 8) 




Now a question,
Does anyone know if there is an on access scanner for avast on linux?

---

### Post by KingArthur10 on 2006-10-13
Thankee for the heads up.  Didn't even know Avast! had a deb build.

---

### Post by paogeorge13 on 2006-10-26
All ok. I downloaded the file but:
paogeorge13@paogeorge-desktop:~$ sudo dpkg -i avast4workstation_1.0.6-2_i386.deb
dpkg: error processing avast4workstation_1.0.6-2_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 avast4workstation_1.0.6-2_i386.deb
paogeorge13@paogeorge-desktop:~$

Why?
I tried the second option but nothing again! Could you help me?
Thanks in advance! :)

---

### Post by paogeorge13 on 2006-10-26
ok. I solved the problem. Cya my friends!

---

### Post by omac on 2006-10-27
Yopnono,

Thank you, thank you, thank you.  Everything worked like a charm.  :-D

---

### Post by qalimas on 2006-10-27
I wasn't aware they had a .deb file, thanks :D  Will come in handy at work, where I get to scan for viruses a lot xD

---

### Post by dlpfmVfH on 2006-10-27
if you look in /usrlib/avast4workstation
you find /etc /lib-gtk2.0 and lib-x11

if you copy your own libraries to here, and recreate the symlinks
to the new libraries you get avast with a gtk2.0 interface matching
you're ubuntu theme...

---

### Post by yopnono on 2006-10-28
I think if you like to use gtk 2.0, you can delete the folders from the avast dir.

---

### Post by bpalyshka on 2006-11-02
awesome thank you very helpful

---

### Post by fly3rman on 2006-11-03
sudo rm -rf lib-x11/
and sudo rm -rf lib-gtk2/
helped, avast is now ubuntu looking

---

### Post by yopnono on 2006-11-03
added som info..

---

### Post by spesheled1 on 2006-11-04
Thanks for this info.  I needed a simple antivirus to check e-mail I was sending to Windows users.

---

### Post by snl on 2006-11-19
If I would like to add avast to /etc/cron.weekly so that it is updated and run every week, what script do I need?

Thank you.

---

### Post by yopnono on 2006-11-19
If you run * avast --help * in the terminal you will get all options you can use from the command line. also * avast-update * will update it from the cmd.

But I guess it will run as root if you use the cron.

---

### Post by sefs on 2008-08-18
How can I scan a single file via the gui, i only see basically scan folder options....and how about email... how do I scan email.

---

### Post by Visible Spirit on 2008-08-27
**@ yopnono**

Thanks for this post and the code to fix Avast menu icon and GUI.

Regards,
Visible Spirit

---

### Post by urvang on 2008-10-22
Thank you all for the nice instructions.
But, I have a problem.
I am behind my college proxy server. But I did not find a way to specify these proxy settings in Avast GUI. So when trying to update definitions, I get connect() timeout error.
Any idea how to resolve this?
Thanks.

---

### Post by Visible Spirit on 2008-10-30
@ Urvang

I don't know the answer to your question but I see no one has responded yet. I hope you resolved your issue, and if not I suggest checking out the Avast forums to see if someone there may have an answer for you. Avast isn't a directly supported software by Ubuntu development. That said, there are many people here that can help, so keep an eye on this thread and some one may see your post and have an answer if you haven't already found one.

[http://forum.avast.com/index.php?board=5.0](http://forum.avast.com/index.php?board=5.0) = This is the Linux/Unix board for Avast 4.

If you have resolved your issue, please post for all to see. I'm sure others will need this info in the future. ;)

HTH....


Regards,
Visible Spirit

---

### Post by james123suman on 2008-11-17
Could you please guide me how to install antivirus and if possible step by step pics of installing anti-virus.....[antivirus]("http://free.avg.com/")

---

