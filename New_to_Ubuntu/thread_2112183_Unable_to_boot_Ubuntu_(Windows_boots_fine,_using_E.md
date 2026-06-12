---
title: "Unable to boot Ubuntu (Windows boots fine, using EasyBCD)"
date: 2013-02-04
forum: New to Ubuntu
---

### Post by Onigami on 2013-02-04
**EDIT by varunendra:**
* Not able to boot Ubuntu
* Used EasyBCD after initial failure ([post #11]("http://ubuntuforums.org/showthread.php?p=12492308"))
* Boot-Repair did not help either. ([post #17]("http://ubuntuforums.org/showthread.php?p=12497349"))
----------------------------------------------
**Original post:**

I have Ubuntu 12.10 installed and I'm using a wireless adapter, an Edimax 7811Un. The problem I'm having is grub isn't working, when I select Ubuntu in the boot menu, I'm met with grub> on my screen.

I've read that my wireless adapter has had bugs with Ubuntu and installing it, however I downloaded the current drivers and attempted to install them to find this in the Terminal: Authentication requested [root] for make clean

I looked up how to correct this problem on this site: [http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/](http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/)

However, using the method mentioned here in attempting to correct my adapter, it doesn't work. I can only get into Ubuntu through the USB stick, booting it in 'Try Ubuntu'

I believe if I can get Ubuntu to connect to the wifi I can fix the grub> issue I'm having. How do I correct the bug with my wifi adapter while having my current problem?

Any help is appreciated, thank you!

---

### Post by carl4926 on 2013-02-04
Get to your ubuntu install

Open a terminal and do this

```
sudo update-grub
```
```
sudo grub-install /dev/sda
```

Reboot without your USBflash drive

---

### Post by carl4926 on 2013-02-04
Once it's booting up normally we need to see the result of this to help with your wireless
```
lspci -nnk | grep -iA2 net
```
Unless your using a USB wireless dongle?

---

### Post by Onigami on 2013-02-04
> **carl4926 said:**
> Once it's booting up normally we need to see the result of this to help with your wireless
```
lspci -nnk | grep -iA2 net
```
Unless your using a USB wireless dongle?

It's a wireless dongle, just a USB chip I plug in.

---

### Post by carl4926 on 2013-02-04
```
lsusb -v
```will list details on usb devices

---

### Post by Onigami on 2013-02-04
I tried the sudo update-grub and recieved this message: /usr/sbin/grub-probe: error: failed to get canonical path of /cow.

---

### Post by carl4926 on 2013-02-04
> **Onigami said:**
> I tried the sudo update-grub and recieved this message: /usr/sbin/grub-probe: error: failed to get canonical path of /cow.

Umm...
Doesn't sound so good
Not sure what that means

---

### Post by carl4926 on 2013-02-04
> **Onigami said:**
> I tried the sudo update-grub and recieved this message: /usr/sbin/grub-probe: error: failed to get canonical path of /cow.

So you were booting to an installed system with the aid of the USB,  not booting to a Live session on the USB?

---

### Post by Onigami on 2013-02-04
> **carl4926 said:**
> So you were booting to an installed system with the aid of the USB,  not booting to a Live session on the USB?

I can't boot a live session, when I use the USB stick it simply gives me the options to use Memtest, test for errors, install Ubuntu or try without installing.

EDIT: Ubuntu 12.10 64 is installed, would I have slightly better luck if I used 12.04 64 or switching to 32 bit? I only use 64 because of my RAM.

---

### Post by carl4926 on 2013-02-04
I'm sorry
But to me it's not entirely clear if you can boot your installed system or not? At first I thought you could. But now I think not.

If you can't boot the live cd?
> I can't boot a live session, when I use the USB stick it simply gives me the options to use Memtest, test for errors, install Ubuntu or try without installing.Is that what you mean?

Because earlier you said
>  I can only get into Ubuntu through the USB stick, booting it in 'Try Ubuntu'

I think you need to get so you either just re-install over the top or boot to a live session and repair grub
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by Onigami on 2013-02-04
Let me explain all the steps I took, it might help you understand my situation. I first partitioned off 65GB off my main HD of 500GB for Ubuntu, I split the partition up into 3 groups. 500MB for the /boot for Ubuntu (as mentioned on the guide), 4GB for the swap and 60GB for Ubuntu. After installation I rebooted and it went straight to windows. I used EasyBCD to put Ubuntu into my loader and find myself on the black "grub>" command screen with nothing to do.

If I stick the USB stick in, I can load Ubuntu using the "Try Ubuntu" and "Install Ubuntu" options, I'm not sure if it is loading from the OS on the partitioned drive or not, the drive that is for Ubuntu is just a regular disk drive with all the files on it. When I click 'Try Ubuntu without Installing' every session is a new one. No matter what files I extract into Documents or the Desktop, no files are saved when I reboot. As was my problem with the wifi dongle not working.

To me, it doesn't sound like it is loading Ubuntu from the drive, instead just booting a 'trial' session from the USB. I don't know if it's because I have a UEFI system or not, but I think that is having something to do with this.

I guess the main problems I'm having is Ubuntu will install but won't boot. I can't update grub because I can't connect to the internet. I can't connect to the internet because there's a bug with the dongle I need to fix, I can't fix it because I have no access to the actual system to update it properly.

Wish it was I can instead of I can't, you know? Lol.

---

### Post by carl4926 on 2013-02-04
You don't need a /boot partition

Just:
swap
ext4 for /
(some might decide to make a /home as well, to keep personal files in place between installs)
In that case you would make / about 20GB and assign as much as you can to /home (also ext4)

> If I stick the USB stick in, I can load Ubuntu using the "Try Ubuntu" and "Install Ubuntu" options, I'm not sure if it is This is just Ubuntu on the USB NOT what you installed!


> I used EasyBCDOh dear. Don't use that - all I read is trouble.

> I have a UEFI Ah....
I don't have it and can't properly advise. But you do need to read any Sticky posts there might be about that.

---

### Post by Onigami on 2013-02-05
If I can figure out how to update the wireless through the actual Ubuntu OS I could run the Boot Repair, but the issue is just that, I am having issues getting the wifi dongle to update.

Does anyone know of a method in which I can manually install or direct the package to install the driver to the actual partition which has the OS?

I appreciate all the help, carl, you helped me narrow down exactly what is going on, or so I think. Lol.

---

### Post by varunendra on 2013-02-05
Onigami,
Internet access is absolutely not necssary to be able solve boot issues, although it may help in some cases.

Your current problem is not being able to boot and you are getting some good advise from carl.

I suggest you get your booting issue solved first, then start a new thread in "Networking & Wireless" section of the forums for the wifi problem (if arises in the installed system).

As you are already getting help regarding booting issue, would you like me to edit the title of your thread so you can get more relevant help?

Mixing problems in a single thread can make it too confusing for someone willing to help. So I strongly recommend to start a new thread for wireless, and get the title of this one changed to reflect "Boot Issue".

---

### Post by Onigami on 2013-02-07
> **varunendra said:**
> Onigami,
Internet access is absolutely not necssary to be able solve boot issues, although it may help in some cases.

Your current problem is not being able to boot and you are getting some good advise from carl.

I suggest you get your booting issue solved first, then start a new thread in "Networking & Wireless" section of the forums for the wifi problem (if arises in the installed system).

As you are already getting help regarding booting issue, would you like me to edit the title of your thread so you can get more relevant help?

Mixing problems in a single thread can make it too confusing for someone willing to help. So I strongly recommend to start a new thread for wireless, and get the title of this one changed to reflect "Boot Issue".

How do I change the title of this thread? As I am having issues getting my internet working on Ubuntu, how can I solve my boot issue offline? I have downloaded Ubuntu Secure Remix and installed it onto a USB stick, only when I try to install it on Ubuntu I get the following error:

ubuntu@ubuntu:~$ sudo apt-get install -y boot-repair && boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package boot-repair
ubuntu@ubuntu:~$

---

### Post by varunendra on 2013-02-07
> **Onigami said:**
> How do I change the title of this thread?
You can not, but if you wish, I can do it for you since I am a mod :)

I have not used Ubuntu Secure Remix, but what I read about it tells me that it has boot-repair already installed (it is not meant to 'install' it, but to directly 'Use' it - good idea!)

So if this Ubuntu Secure Remix live usb you have created gives you a desktop like [this]("https://help.ubuntu.com/community/UbuntuSecureRemix#Desktop"), then you can click the Boot-Repair launcher button to directly launch it. You don't need to install it, as it already is there.

And since this thread has come too far dealing with boot issue, I still suggest to get its title changed.

Would you like me to do it for you?

---

### Post by Onigami on 2013-02-07
> **varunendra said:**
> You can not, but if you wish, I can do it for you since I am a mod :)

I have not used Ubuntu Secure Remix, but what I read about it tells me that it has boot-repair already installed (it is not meant to 'install' it, but to directly 'Use' it - good idea!)

So if this Ubuntu Secure Remix live usb you have created gives you a desktop like [this]("https://help.ubuntu.com/community/UbuntuSecureRemix#Desktop"), then you can click the Boot-Repair launcher button to directly launch it. You don't need to install it, as it already is there.

And since this thread has come too far dealing with boot issue, I still suggest to get its title changed.

Would you like me to do it for you?

I would appreciate that a lot!

Unfortunately, I did have a desktop like that and attempted to simply run the program as all the guides show, it didn't work. I was once again met with it automatically booting to Windows by default. There was a point during the boot repair which it asked me to 'connect to the internet and click continue' which I had to click continue without connecting. I'm not sure if that's significant or not.

It did give me a text file which I didn't think to save, would those results help in solving my problem? Also, not that it may mean much but while I was sitting in front of that black grub> screen, I decided to tinker with the commands and stumbled across the root being in something like hd0,1 when there are hd0, 0-3 and Ubuntu is on hd0,2 could that have something to do with it?

---

### Post by varunendra on 2013-02-07
Thread Title changed!

YES, that text file that boot-repair created would help us a lot. Please post its contents in your next post.
*(while posting the file's contents, wrap it in 'Code' tags. Follow the "Code Tags example link in my signature to see how to do it)*

---

