---
title: "Do SSD need customisation?"
date: 2012-05-16
forum: New to Ubuntu
---

### Post by quirino77 on 2012-05-16
Hi!

I'm using Ubuntu 12.04 64 bits. And a SSD.
Do 12.04 need some customization when using SSD?
Some time ago, SSDs needed this to get performance (i'm not talking about a few MB/s) and to preserve lifetime.
My motherboard have AHCI and it's already enabled.

The only think i did it not to use swap and i mount the temp to RAM. Since i use 8 GB RAM, i could afford this "luxury".

---

### Post by oldfred on 2012-05-16
You have done most of it. You want to change some settings to reduce writes and enable trim with the discard command in your fstab.

How to Tweak Your SSD in Ubuntu for Better Performance
[http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/](http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/)
See comment: There’s no reason to use BOTH noatime and nodiratime, using noatime implies nodiratime.
[http://techgage.com/print/enabling_and_testing_ssd_trim_support_under_linux](http://techgage.com/print/enabling_and_testing_ssd_trim_support_under_linux)

With SSD or Flash drives, Use ext2 or ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

I did not change settings when I first installed, so I did this. This comments suggest an alternative way to using discard.
Alternate to discard, call fstrim via cron
[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)
fred@fred-Precise:~$ sudo fstrim -v /
/: 23267893248 bytes were trimmed

fred@fred-Precise:~$ cat /sys/block/sda/queue/scheduler
noop deadline [cfq]

---

### Post by quirino77 on 2012-05-17
Thank's oldfred.

All the links are about 1 year old. The one from howtogeek i had read, but i got in doubt.

Even with the latest Ubuntu (12.04), are this tweaks still necessary?

---

### Post by oldfred on 2012-05-17
You still need discard for trim and noatime to reduce writes. You can also use ext4 but turn journal off. I think that was about all I actually did.

---

### Post by SlugSlug on 2012-05-17
I just enabled discard,

new ssd's have massive lifetimes so dont worry about the noatime

as for alignment - dnt bother. I've installed a few SSD's in older customers PC's as an affordable upgrade,  tested all with and without alignment and gained only a few MB/s

---

### Post by idoitprone on 2012-05-17
> **SlugSlug said:**
> I just enabled discard,

new ssd's have massive lifetimes so dont worry about the noatime

as for alignment - dnt bother. I've installed a few SSD's in older customers PC's as an affordable upgrade,  tested all with and without alignment and gained only a few MB/s

Not really. If your talking about SLC then maybe.  Most ssd uses sandforce controller to reduce writes. If you have heavy compressed files or mp3 then there wont be any benefit

---

### Post by SlugSlug on 2012-05-18
> **idoitprone said:**
> Not really. If your talking about SLC then maybe.  Most ssd uses sandforce controller to reduce writes. If you have heavy compressed files or mp3 then there wont be any benefit


\Not sure I follow

---

### Post by idoitprone on 2012-05-18
> **SlugSlug said:**
> \Not sure I follow

[http://en.wikipedia.org/wiki/Single-level_cell#Single-level_cell](http://en.wikipedia.org/wiki/Single-level_cell#Single-level_cell)

[http://en.wikipedia.org/wiki/SandForce#Technology](http://en.wikipedia.org/wiki/SandForce#Technology)

---

### Post by 23senick on 2012-05-19
Sounds like your machine is up to date. Some of the following may then not apply, as newer SSDs are probably better, but posting it here in case it may help you or others.  

My Ubuntu experience with a netbook with Solid State Drive (SSD) was frustrating.  For example when browsing the screen would freeze for a few seconds, and with annoying regularity.  Its easy to find advice about why this is and how to improve things.  The key problem is (allegedly) while SSDs read faster than hard drives (eg when opening a programme) they write much slower (eg when saving a file). Certainly true of older ones.  And most default settings in programmes are not SSD friendly - by default the computer does lots of writing to the drive. 
 
I found while there’s loads of advice for this issue, for a Linux newbie it always had some key bit of info missing .  So this isn’t original - it’s just what I found helpful with hopefully full instructions.  It’s not for tekkies - but may help those who are new/learning. And of course any improvements welcome!

I made these tweaks to my Acer Aspire One (A110L - 8GB)  running Xubuntu 12.04 LTS.  I re-formatted the SSD using file system is ext4. If you’re running different systems you may need to tweak instructions or even further advice!  Now I've made the changes, it really flies, despite being an old cheap netwook.  

Please note these are system file changes so back up important files first, and preferably have a disk version of your operating system ready just in case.  

1. Stop unnecessary saving to the Hard Drive

One thing before you begin - when you format the SSD in ext4, you should get an option about whether you want to format it with or without journaling.  Without is probably best if speed is your priority, but mine is formatted with journaling, which is supposed to protect you from data loss.  This also affects one of the recommended tweaks.
&#65279;
Why use the Ext4 file system?  This is because it supports TRIM which helps SSD drives.  There’s an action below which (I think) only relates to ext4 file systems.

If you have an SSD, type:

sudo nano /etc/fstab

This allows you to edit the fstab file - a system file which controls lots of your computers actions, so be careful.  

You can tweak your system as follows IF YOU FORMATTED WITH JOURNALLING:

There’s a line in the fstab file as below:

&#65279;UUID=[NUMS-AND-LETTERS] /               ext4    errors=remount-ro 0       1

Insert the text in red below

&#65279;UUID=[NUMS-AND-LETTERS] /              ext4    noatime,discard,data=ordered,errors=remount-ro 0       1

A further change to fstab is below.  At the end of the text, add the following (Cut and paste worked for me):

tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
none /var/tmp aufs noatime,br:/tmp=rw:/var/tmp=ro 0 0
none /var/log aufs noatime,br:/tmp=rw:/var/log=ro 0 0
none /var/cache aufs noatime,br:/tmp=rw:/var/cache=ro 0 0

Press ctrl+x to exit. it asks if you want to save changes Y/N - answer yes to save changes

The result?  TRIM is enabled.  And the computer will no longer record that you accessed files (which actually meant new info on the files ie re-write to the hard drive) which caused pauses when your netbook needs to create a temp file - I think this happens when you print or open email attachments.  Instead a temporary file is created in the RAM - so writes to memory are much quicker. It also has the advantage (again, allegedly) of prolonging the life of your drive, because SSDs are likely to wear out more quickly if data is re-written to them frequently.  

Any downsides? Well your netbook won’t be keeping logs of all your activity. It loses them when you shut down.  I guess most of us wouldn’t notice this.  If you want to keep your log files, omit the 3rd line.

see this link for details and other options:

[https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist) 

2.Tweak your operating system so it schedules tasks to suit SSDs

There is always lots going on in your computer - so tweak the system so the way it does them suits SSDs.  The default task scheduler in Linux is an “elevator" which suits hard drives not SSDs. To change this open a terminal and type in cat /sys/block/sda/queue/scheduler

It will show something like 
&#65279;
noop anticipatory deadline [cfq]

Move the brackets using the cursor arrow keys until either noop or deadline is bracketed.  This change needs to be done each time you log in as the system reverts to CFQ.  

There are ways to make this permanent.  If the sole storage device in the system is an SSD, consider setting the I/O scheduler for the entire system via the elevator kernel parameter: 

For example, with GRUB2, add the following in /etc/default/grub: 

sudo nano /etc/default/grub

GRUB_CMDLINE_LINUX="elevator=noop"

Again, select ctrl+x to exit, and “y” to save changes.You must run update-grub afterwards - so then in terminal type

sudo update-grub


3. Speed up Firefox

Many of my problems were with browsing.  Again, because Firefox writes to the hard disk.  If Firefox is your browser you can change this - in the address bar type about-config. You then get a warning - if you are happy to proceed click on I will be careful, I promise.

Click the right mouse key somewhere on the list that has appeared, select “new” then “integer" tell Firefox you want a new integer - name it toolkit.storage.synchronous and set its value to 0.

Firefox by default caches data to the hard drive. This is no good for a slow-writing SSD but it can be fixed by telling Firefox to cache data in a temporary file in RAM (/tmp) which you set up under the first step. 

To do this, type about:config in the browser window. Click ‘I’ll be careful, I promise!’ and then create  a new string by (as above) right-clicking and selecting new and then string and naming it browser.cache.disk.parent_directory - when Firefox asks for a value  type  ‘/tmp’

Result? Firefox saves to the temp file in RAM (quicker)

Another alternative to this in about:config - you can achieve similar result by typing browser.cache.disk.enable and double clicking on the line to set it to false, which will stop Firefox caching to disk completely.  

Other Firefox fixes:

Another issue is Firefox’s default maintenance of a large history file of where you browse. In older versions you could reduce the size by reduce in options the number of days it stores (edit-preferences-privacy) eg to 10 . 

New versions only allow you to disable history through edit/preferences/privacy.  

REFERENCES

Here are links with useful suggestions

[http://tombuntu.com/index.php/2008/09/04/four-tweaks-for-using-linux-with-solid-state-drives/](http://tombuntu.com/index.php/2008/09/04/four-tweaks-for-using-linux-with-solid-state-drives/) 

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives) 

[http://itezer.com/blog/ubuntu-linux/125-four-tweaks-for-using-ubuntu-with-ssd.html](http://itezer.com/blog/ubuntu-linux/125-four-tweaks-for-using-ubuntu-with-ssd.html)

---

### Post by quirino77 on 2012-05-20
My fstab is:

UUID=xxx /               ext4    noatime,discard,nodiratime,errors=remount-ro 0       1
tmpfs                       /tmp                          tmpfs defaults,noatime,mode=1777                  0 0

I will try the others mounts you told.


I have journal on on my / partition. Can i turn it off being the / ? If i could, is it with the command: sudo tune2fs -O ^has_journal /dev/sda3

I used to make the Firefox tweak to use the temp. But not anymore since i also use Chrome and Chromium and i don't know how to do the same on them.

By the way, i don't few my machine slow or with freezes. I feel it quite fast. I'm satisfied, just want to preserve the SSD.

---

### Post by 23senick on 2012-05-21
I would suggest you take care and do some research before making changes, unless you have the skills to undo it if it goes wrong.  If you don't experience freezes then why change things?  

The freezes I experienced were not long - a few seconds - but it did frustrate me.  If you don't experiences freezes perhaps you have a newer SSD.  And if so maybe these changes aren't good for you?

I know some people say SSDs can be worn out by frequent re-writes - but as I say in my first post, this is apparently a matter of dispute.

---

### Post by quirino77 on 2012-05-25
After thinking a while i realized that you are right. It do not worth the worry and time. Since i have few free time and a baby to spend the few free time with, it worth not to spend time with this.

I would like to learn, but it is not the priority right now.

Thank's to everyone.

---

### Post by Paqman on 2012-05-25
> **quirino77 said:**
> After thinking a while i realized that you are right. It do not worth the worry and time. Since i have few free time and a baby to spend the few free time with, it worth not to spend time with this.

I would like to learn, but it is not the priority right now.

Thank's to everyone.

Good decision. They grow up quick!

---

### Post by adad on 2012-08-04
This article worked for me to tweak my SSD under Ubuntu 12.04.

[http://brizoma.com/2012/08/04/running-ubuntu-and-other-linux-flavors-on-an-ssd/](http://brizoma.com/2012/08/04/running-ubuntu-and-other-linux-flavors-on-an-ssd/)

I have a single partition on my SSD and just pick the old installation from the HDD for the swap file. I have plenty of RAM, so there is no problem using the slower HDD file.

Just remember to select no swap file during Ubuntu's install.

---

### Post by troymius on 2012-10-07
I still struggle here.

My friend Erik says he put an SSD in his Linux laptop, did zero adjustments to system settings and it worked great and probably still works but he is not sure as he gave the laptop to somebody after two or three years. 

My friend Matt, on the other hand, says that adjustments HAVE to be made for an SSD to work in Linux.

(1) So who is right? Was Erik just lucky? If I do not make any adjustments, will the drive die way too soon? 

(2) Do you think that in near future there will be kernel and distro that would make the right settings automatically?

---

