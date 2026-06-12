---
title: "Adobe Air"
date: 2012-07-14
forum: New to Ubuntu
---

### Post by harfin on 2012-07-14
I have tried to follow a couple of threads dealing with Adobe Air in the general section of this forum, but it got far too technical for me!

I am using Precise Pangolin, and find it great for everything now **except** Adobe Air.  I run Evolution as my email client and Chrome as my browser.

I use a greeting card programme (Jackie Lawson) and for the last 3 years have also used their advent calender (which uses Adobe Air) at Christmas time. That organisation have now introduced a facility (also using Adobe Air) to enable users to send greeting cards direct from the desktop via a 'widget'.

When I tried to download the widget, the process stalled and on investigation it seems that the widget is attempting to install the latest version of Adobe Air.

The Adobe website says that Adobe is no longer supporting Adobe Air for Linux, but that a version is being developed within the Linux community.

Can anyone offer any advice or help please, as I really don't want to lose my greeting card and advent calender facility.

---

### Post by m3topaz on 2012-07-14
I use Air on Precise, 64-bit.

IF you are using 32-bit, it should be pretty straightforward to install:

1) Get the installer:
$ wget [http://airdownload.adobe.com/air/lin/download/2.6/AdobeAIRInstaller.bin](http://airdownload.adobe.com/air/lin/download/2.6/AdobeAIRInstaller.bin)

2) Make executable:
$ chmod ugo+x AdobeAIRInstaller.bin

3) Run the installer:
$ sudo ./AdobeAIRInstaller.bin

IF you have 64-bit, you probably need to run this before executing the above:
$ sudo apt-get install ia32-libs-gtk

IF you are on 64-bit and you get problems with an error about Gnome keyring, run these and try once again:
$ sudo ln -s /usr/lib/x86_64-linux-gnu/libgnome-keyring.so.0 /usr/lib/libgnome-keyring.so.0
$ sudo ln -s /usr/lib/x86_64-linux-gnu/libgnome-keyring.so.0.2.0 /usr/lib/libgnome-keyring.so.0.2.0

I use Air for one application only, Balsamiq. These notes are from the last time I switched computer, last month.

Good luck!

---

### Post by harfin on 2012-07-15
> **m3topaz said:**
> I use Air on Precise, 64-bit.
IF you are using 32-bit, it should be pretty straightforward to install:
1) Get the installer:
$ wget [http://airdownload.adobe.com/air/lin/download/2.6/AdobeAIRInstaller.bin](http://airdownload.adobe.com/air/lin/download/2.6/AdobeAIRInstaller.bin)
2) Make executable:
$ chmod ugo+x AdobeAIRInstaller.bin
Good luck!

Thanks for that, m3topaz!
Did as you suggested and re point (1) 'Get the Installer'; I have checked and can see the file in my Downloads folder
Then I ran the command as per your point (2), i.e. 'Make executable', and I got the following:
[B]myusername@ubuntu:~$ chmod ugo+x AdobeAIRInstaller.bin
chmod: cannot access `AdobeAIRInstaller.bin': No such file or directory[/B]

Any suggestions?
Harfin

---

### Post by d4m1r on 2012-07-15
Try:

```
sudo chmod ugo+x AdobeAIRInstaller.bin
```

---

### Post by rickm1945 on 2012-07-15
> **d4m1r said:**
> Try:

```
sudo chmod ugo+x AdobeAIRInstaller.bin
```
I got the installer and and got the error message about Keyring, so I ran the other two commands,

```

```$ sudo ln -s /usr/lib/x86_64-linux-gnu/libgnome-keyring.so.0 /usr/lib/libgnome-keyring.so.0
$ sudo ln -s /usr/lib/x86_64-linux-gnu/libgnome-keyring.so.0.2.0 /usr/lib/libgnome-keyring.so.0.2.0
rebooted and still got the same error message again about the Keyring, and KDE.  
I am running Unbutu 12.04 64 bit.

---

### Post by harfin on 2012-07-15
Tried as suggested, i.e.:

[B]username@ubuntu:~$ sudo chmod ugo+x AdobeAIRInstaller.bin
[sudo] password for username: (*mypassword*)
chmod: cannot access `AdobeAIRInstaller.bin': No such file or directory[/B]

I am running 32bit by the way.

The downloaded file is in my downloads folder; should I move it to somewhere else?

Alan

---

### Post by m3topaz on 2012-07-16
Ooops - sorry about the lack of 'sudo' in step 2...

It looks like you aren't in your 'Downloads' folder. From the terminal, go there with:
$ cd ~/Downloads

See that the installer is there:
$ ls
This should have a file listing which includes the installer by name.
Then go back to step 2 (with sudo!) and continue.

---

### Post by harfin on 2012-07-16
> **m3topaz said:**
> Ooops - sorry about the lack of 'sudo' in step 2...
It looks like you aren't in your 'Downloads' folder. From the terminal, go there with:
$ cd ~/Downloads
See that the installer is there:
$ ls
This should have a file listing which includes the installer by name.
Then go back to step 2 (with sudo!) and continue.

Well I progressed a lot further! Thanks for that
However (isn't there always one!), when the Adobe Air installer is installing, it comes back with an error message, namely:
**Adobe AIR could not be installed. Install either Gnome Keyring or KDE KWallet before installing Adobe AIR.**

I saw that an earlier entry on this thread referred to this error, but in that case the user had the 64bit system, and I have the 32bit system.

Do I run the commands that you recommended for the 64 bit system, even if I don't have the 64bit version?

Harfin
:confused:

---

### Post by crash76 on 2012-07-22
I am on Ubuntu 12.04 x64, I used this instructions and had no problems at all:
[http://jeffhendricks.net/?p=68](http://jeffhendricks.net/?p=68)

---

### Post by harfin on 2012-07-23
> **crash76 said:**
> I am on Ubuntu 12.04 x64, I used this instructions and had no problems at all:
[http://jeffhendricks.net/?p=68](http://jeffhendricks.net/?p=68)

The issue is not whether the instructions work for the 64 bit set up or not.

I have the 32 bit set up.

My question is should **_I_** should use the 64bit extra instructions, _**even if I don't have the 64 bit set up**_.

The extra instructions given were:

[INDENT]IF you are on 64-bit and you get problems with an error about Gnome keyring, run these and try once again:
$ sudo ln -s /usr/lib/x86_64-linux-gnu/libgnome-keyring.so.0 /usr/lib/libgnome-keyring.so.0
$ sudo ln -s /usr/lib/x86_64-linux-gnu/libgnome-keyring.so.0.2.0 /usr/lib/libgnome-keyring.so.0.2.0[/INDENT]

---

### Post by munnster on 2012-08-04
Harfin, I found these install instructions on .liberiangeek.net. For 32-bit use these commands before attempting to install:

sudo ln -s /usr/lib/i386-linux-gnu/libgnome-keyring.so.0 /usr/lib/libgnome-keyring.so.0

sudo ln -s /usr/lib/i386-linux-gnu/libgnome-keyring.so.0.2.0 /usr/lib/libgnome-keyring.so.0.2.0

It worked for me. I hope this helps you as well. :)

---

### Post by harfin on 2012-08-06
> **munnster said:**
> Harfin, I found these install instructions on .liberiangeek.net. For 32-bit use these commands before attempting to install:

sudo ln -s /usr/lib/i386-linux-gnu/libgnome-keyring.so.0 /usr/lib/libgnome-keyring.so.0

sudo ln -s /usr/lib/i386-linux-gnu/libgnome-keyring.so.0.2.0 /usr/lib/libgnome-keyring.so.0.2.0

It worked for me. I hope this helps you as well. :)

Hi and very many thanks for that.
Alas when the second entry line is entered I get: 
[INDENT][/INDENT] ln: invalid option - - '/'

Any thoughts?

---

### Post by vaul on 2012-11-08
Harfin, it may help to check that you do not have any unneeded spaces in the command.

---

### Post by harfin on 2012-11-13
> **vaul said:**
> Harfin, it may help to check that you do not have any unneeded spaces in the command.

The original line from Munnster is the first line below, the second line is a copy of my entry (they look identical to me):
sudo ln -s /usr/lib/i386-linux-gnu/libgnome-keyring.so.0 /usr/lib/libgnome-keyring.so.0
sudo ln -s /usr/lib/i386-linux-gnu/libgnome-keyring.so.0 /usr/lib/libgnome-keyring.so.0

When my line was entered, I was then asked for my (sign-on) password and after entering that the reply was:
sudo: ln-s/usr/lib/i386-linux-gnu/libgnome-keyring.so.0/usr/lib/libgnome-keyring.so.0: command not found
?

---

### Post by harfin on 2012-11-13
Finally!

I eventually got Adobe AIR installed!

Thanks for everyone's help!
Kind regards
Alan

---

### Post by nickjones101 on 2013-01-03
Thank you very much for the symlink info, this has enabled me to complete Air installation too (Lubuntu 12.04 32bit).

Cheers!

---

