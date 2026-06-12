---
title: "Virtual Box (I need basic help with this)"
date: 2012-10-28
forum: New to Ubuntu
---

### Post by Airycat on 2012-10-28
I need to use some programs that simply won't work with Ubuntu. Specifically at the moment, my Dragon speech recognition.

It won't work in Wine. I've tried several times to install it with that and it always ends up with a "failed" message.

so...

I've installed Virtualbox and am trying to install Dragon in it. (I chose the Windows 7 OS because that's what I used it with before I installed Ubuntu.) It created a box on the left side, but when I click to power on I get the following message:

[[img]http://farm9.staticflickr.com/8331/8133052329_3e1cc1e18d.jpg[/img]](http://www.flickr.com/photos/airycat/8133052329/)
[Screenshot from 2012-10-28 16:51:19](http://www.flickr.com/photos/airycat/8133052329/) by [Airycat](http://www.flickr.com/people/airycat/), on Flickr

:arrow: It says to press the host key... which it says is **right ctrl**, I know what ctrl is, but what does it mean by *right* ctrl? The ctrl on the right? the ctrl with the right arrow? Neither of these seemed to do anything.

Then I pressed continue and got this message:

[[img]http://farm9.staticflickr.com/8331/8133052807_e11ce5c67f.jpg[/img]](http://www.flickr.com/photos/airycat/8133052807/)
[Screenshot from 2012-10-28 16:49:27](http://www.flickr.com/photos/airycat/8133052807/) by [Airycat](http://www.flickr.com/people/airycat/), on Flickr

:arrow: What do I do to enable this?

Once these are cleared up, should my program finally be able to run? If not, what else do I need to do to get it to work?

TIA
~Faith

---

### Post by BertN45 on 2012-10-28
The first pop-up is just an information message that you can ignore or suppress. The second pop-up say that your PC does not support virtualisation, so you have to run without it. You have to go to settings -> system -> acceleration and disable the mentioned setting (VT-x/AMD-V).

The alternative is that you enter the bios and check whether the VT-x (Intel) or AMD-V (AMD) setting in the BIOS is activated. I would only do that if you are familiar with changing the BIOS and I would first try to get VirtualBox running without it.

---

### Post by pandacookie on 2012-10-28
I don't think you have Dragon installed correctly. It looks to me as if you installed Dragon as an operating system. You need to install Dragon directly onto your Windows virtual PC.

---

### Post by Airycat on 2012-10-28
Switched to 7-32 and got past that point. It didn't automatically go to the CD-ROM drive but I selected it and now I'm getting this message!

[[img]http://farm9.staticflickr.com/8474/8133217879_e2296377e4.jpg[/img]](http://www.flickr.com/photos/airycat/8133217879/)
[Screenshot from 2012-10-28 17:54:53](http://www.flickr.com/photos/airycat/8133217879/) by [Airycat](http://www.flickr.com/people/airycat/), on Flickr

Is pandacookie correct? Do I need to install my Windows 7 and install Dragon on that?

Maybe so. It has two required exe files. If I install Windows in the virtual box, can I simply open that and install Dragon with the auto-installer (install.exe)? If yes... How would I install windows in virtualbox?

---

### Post by Vaphell on 2012-10-28
all virtualbox does is providing you with a fake computer. That fake computer still needs an operating system to function.
You need a windows installer, dvd or .iso file. You boot the prepared fake computer, it detects bootable disc, now standard OS installation happens: 'install windows', next, next, next, ok, next, done. Once you go through the installation of the system you reboot the virtual machine, log in to it as if it was a real system and then you install your software, just like you did in your win7.

---

### Post by Airycat on 2012-10-28
Won't install 64 bit OS which is what I have, but I discovered I still have my XP disk, so I'm installing that and it seems to be working!

OMG!!! A little computer on my computer!  It's working!!!

---

### Post by Airycat on 2012-10-28
Cute little computer is useless because it can't update my old xp disk and it won't install my current Windows 7 disk.

---

### Post by Vaphell on 2012-10-28
what do you mean by update?

---

### Post by BertN45 on 2012-10-29
I assume it will not install Windows 7, because your Ubuntu system is 32 bits and Windows 7 that you have is 64 bits. You can put 32 bits in 64 bits, but you can't put 64 bits into 32 bits. If your hardware is 64 bits, I would re-install Ubuntu and download and install the 64 bit version. If you do that re-install the VT-x/AMD-V option will very probably work again, because that only works with a 64-bit Operating System. That option will speed up your cute little computer.

It is wise to tell us what hardware you have, at least type of processor and memory. You can find it on the first tab of the System Monitor. You can also see there how many bits (32 or 64) Ubuntu has.

---

### Post by mastablasta on 2012-10-29
> **Vaphell said:**
> what do you mean by update?
 
exactly. you don't relaly need to update it. and if you do need to update it you can download MS Windows SP (service pack) CD and update through that. that's about all updating you need.

---

### Post by squakie on 2012-10-29
+1 for installing Windows 7 in the VM, 64-bit *if* (1) your system is a 64-bit system (2) your version of Windows 7 is 64-bit. 

After you get an OS installed and load in Dragon, I would imagine you have a USB microphone (like the little headset they used to include with Dragon).  If so, you need to enable the USB device in the settings for the VM.

It's also possible the version of VirtualBox you have does not have USB support.  I just download the version from Oracle's site as well as the add-on there.

---

### Post by Airycat on 2012-11-01
> **squakie said:**
> +1 for installing Windows 7 in the VM, 64-bit *if* (1) your system is a 64-bit system (2) your version of Windows 7 is 64-bit. 

After you get an OS installed and load in Dragon, I would imagine you have a USB microphone (like the little headset they used to include with Dragon).  If so, you need to enable the USB device in the settings for the VM.

It's also possible the version of VirtualBox you have does not have USB support.  I just download the version from Oracle's site as well as the add-on there.

I have the 64 bit Ubuntu 12.10. I added VirtualBox from the Software Center. I added Windows 7 using the recommended nsettings. When I click on it I get the following message 

[[IMG]http://farm9.staticflickr.com/8044/8146173086_1700480603.jpg[/IMG]]("http://www.flickr.com/photos/airycat/8146173086/")
[Screenshot from 2012-11-01 15:13:14]("http://www.flickr.com/photos/airycat/8146173086/") by [Airycat]("http://www.flickr.com/people/airycat/"), on Flickr

I don't know how to do what it is saying.

---

### Post by Vaphell on 2012-11-01
it says:
- install dkms if you havent already
```
sudo apt-get install dkms
```
- run
```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by s1baker on 2012-11-01
It means you need to recompile virtualbox to be in agreement with your kernel. This message is very common whenever the Linux kernel is updated (seems like every 2 or 3 weeks now ) through the normal software updates that come in regularly. After the kernel is updated, Virtualbox always has to be recompiled. Completely normal.

Close out the Virtualbox window and Windows 7 ( or whatever you may be running under virtualbox ), then open a terminal.

put this in the terminal
```

/etc/init.d/vboxdrv setup

``` 

It will ask you for your password.
It will run and might say something like "can't find dmk..something or other" and it will continue.
Takes a few minutes.

Then run virtualbox again.

---

### Post by Airycat on 2012-11-01
> **s1baker said:**
> It will ask you for your password.

It says "No such file or directory"

Putting in previously mentioned code requests my password, but it is not accepting it. I ***know*** what my password is. When I go to the boot/setup section (BIOS Security Features, I think) it said there is not password and I can't do anything, but I have to put in my password when I turn on Ubuntu. I have no problem with that except that since I upgraded, I have to turn off the numbers lock even though it has numbers in it.

[[img]http://farm9.staticflickr.com/8473/8146619575_59a97f8112.jpg[/img]](http://www.flickr.com/photos/airycat/8146619575/)
[Screenshot from 2012-11-01 19:47:51](http://www.flickr.com/photos/airycat/8146619575/) by [Airycat](http://www.flickr.com/people/airycat/), on Flickr

My frustration level with this is currently about 250%.

This message was under the other one for the Virtualbox.

[[img]http://farm9.staticflickr.com/8185/8146654438_97b6a9aaea.jpg[/img]](http://www.flickr.com/photos/airycat/8146654438/)
[Screenshot from 2012-11-01 19:41:58](http://www.flickr.com/photos/airycat/8146654438/) by [Airycat](http://www.flickr.com/people/airycat/), on Flickr

---

### Post by pkadeel on 2012-11-02
First of all about your most recent post;
You have to enter your ubuntu password in the terminal instead of the password used for entering computer's BIOS setup utility.

If you remember your password correctly which i guess you do, and still the terminal is not accepting it then check a couple of things before getting frustrated.
Is CAPS lock on while you are entering the password?
If there are numbers in the password, are you entering these correctly. may be the numlock is off while you are entering the numbers.

Now after you resolve your password issue, for the virtualbox problem i suggest to undo everything and start with fresh virtualbox install.
first remove old installation of virtualbox. I assume you installed it from ubuntu software center so uninstall it from there.

After that open a terminal and install install dkms if you have not already installed it.
sudo apt-get install dkms

After that install virtualbox-4.2
sudo apt-get install virtualbox-4.2

Add yourself to vboxusers group. replace <your_login_id> with your actual login id.
sudo adduser <your_login_id> vboxusers

Logout ubuntu and then login again

Then go to virtualbox website  and download virtualbox extension pack v4.2.x

Finally start virtualbox and from menu select File > Preferences. Find settings for Extensions in the list and there install your downloaded extension pack.


Also on the General tab set a feasible location for where you will create your new virtual machine. For windows 7 you will be needing atleast 30 GB so make sure the partition you select has that much space. I personally recommend a dedicated partition  for that purpose if you intend to use the virtual machine for long time.

Now you are all set for creating a new virtual machine.

Ah! by the way allocate 1GB or more RAM for win7

---

### Post by s1baker on 2012-11-02
sorry, my bad.
I meant:
```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by Airycat on 2012-11-06
> **pkadeel said:**
> 

After that open a terminal and install install dkms if you have not already installed it.
sudo apt-get install dkms

After that install virtualbox-4.2
sudo apt-get install virtualbox-4.2


I get stuck here. What next?
[[img]http://farm8.staticflickr.com/7269/8162684270_cf6bbe9364.jpg[/img]](http://www.flickr.com/photos/airycat/8162684270/)
[Screenshot from 2012-11-06 16:29:18](http://www.flickr.com/photos/airycat/8162684270/) by [Airycat](http://www.flickr.com/people/airycat/), on Flickr

---

### Post by Vaphell on 2012-11-07
do you use open source version available in default repos or the one from oracle with proprietary extensions? Remove the one you have and install again.


```
apt-cache search virtualbox
```
should return a list of packages that are in repos. Do you see anything Oracle?

In case you don't have any and use ose version, consider installing oracle one by following the procedure described here:
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads), under Debian based distributions

---

### Post by pkadeel on 2012-11-07
> **Airycat said:**
> I get stuck here. What next?
Ok i guess the repository for virtualbox is not present in your sources list.
Open terminal and do as follows;
```

gksu gedit /etc/apt/sources.list

```
depending on you ubuntu version (i.e. precise, oneiric etc) append following line to the file openned replacing the ubuntu version with proper one. for further detail refer to
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)
```

deb http://download.virtualbox.org/virtualbox/debian precise contrib

```
save and close the file. now back in terminal
```

wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install virtualbox-4.2

```
I hope you shall be able to install it now without any problem.

---

