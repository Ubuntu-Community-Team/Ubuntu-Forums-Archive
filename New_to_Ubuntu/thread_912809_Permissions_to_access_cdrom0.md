---
title: "Permissions to access cdrom0"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by jrsc109 on 2008-09-07
Hello - Newbie here

I want to install drivers for Devolo homeplug unit; however, when the CD is in the drive and I try to access it I get the following message:
"The folder contents could not be displayed.  You do not have the permissions necessary to view the contents of cdrom0"

I think I have given myself all the permissions needed, but must be missing something fundamental.

As I say, I am a complete newbie and any help will be appreciated.

Many thanks

---

### Post by Sin@Sin-Sacrifice on 2008-09-07
You try 'sudo mount /media/cdrom0' without the quotes in a terminal yet? Whenever I put a data disk in my drive I have to mount it that way. I think it's because ubuntu sees them as another drive. Not sure exactly... but it works. I like that though... that ascertains that I am the only one that can access drives and whathaveyous on the system. Much more secure than the blunders of microsoft. Try it out...

---

### Post by doug1212 on 2008-09-07
Hi,
Re: Devolo driver,
If you are referring to the USB drivers, I believe that they may be broken with the latest kernels. Use the Ethernet connections and they are plug and play, although there is a Linux command line utility to encrypt the connection that builds and install OK.

Hope this helps,
Doug.

---

### Post by jrsc109 on 2008-09-08
Thanks both.  Great advice each, and I have now discovered that my router is not resolving URLs, which hasn't helped in fixing the problem.
Will try again why my new router arrives.  Thanks again

---

### Post by woosie on 2008-09-20
Another complete newbie here.
I'm getting the same "You do not have the permissions necessary to view the contents of cdrom0" when I try to use the cd to install the dlanconfig program to set up the security on my homeplug adapters.
I tried the 'sudo mount /mount/media/cdrom0' as suggested
And got:
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: /dev/scd0 already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/scd0 is already mounted on /media/cdrom0
In reply...
I tried downloading the software from: 
[http://www.devolo.com/co_EN_cs/produkte/dlan/mldlanhsstarterkit-dn.html](http://www.devolo.com/co_EN_cs/produkte/dlan/mldlanhsstarterkit-dn.html)
But being a newbie had no idea what to do with it.
Any ideas on what I can try next?

---

### Post by doug1212 on 2008-09-21
> **woosie said:**
> Another complete newbie here.
I'm getting the same "You do not have the permissions necessary to view the contents of cdrom0" when I try to use the cd to install the dlanconfig program to set up the security on my homeplug adapters.
I tried the 'sudo mount /mount/media/cdrom0' as suggested
And got:
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: /dev/scd0 already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/scd0 is already mounted on /media/cdrom0
In reply...
I tried downloading the software from: 
[http://www.devolo.com/co_EN_cs/produkte/dlan/mldlanhsstarterkit-dn.html](http://www.devolo.com/co_EN_cs/produkte/dlan/mldlanhsstarterkit-dn.html)
But being a newbie had no idea what to do with it.
Any ideas on what I can try next?

Hi,
Devolo offers source code for password admin utility and usb driver, don,t bother with the usb it doesn't work.

Download the source archive and extract to folder on desktop.

To build the utility you will require compiling tools.

```
sudo apt-get install linux-headers-$(uname -r)
```

```
sudo apt-get install build-essential
```

```
sudo apt-get install libpcap0.8-dev
```

Open folder in terminal, then:

```
./configure
```

```
make cfgtool
```

```
sudo make install-cfgtool
```

Write down the security ID as you won't be able to see it when plugged in :)

To run the command line utility (requires root privileges) assuming eth0 is your lan card:

```
sudo /usr/local/sbin/dlanconfig eth0
```

Doug

---

### Post by woosie on 2008-09-21
Thanks for that - it worked perfectly!

---

