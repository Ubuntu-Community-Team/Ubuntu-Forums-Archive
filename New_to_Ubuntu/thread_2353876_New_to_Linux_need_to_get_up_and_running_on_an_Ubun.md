---
title: "New to Linux need to get up and running on an Ubuntu machine"
date: 2017-02-25
forum: New to Ubuntu
---

### Post by sohappy on 2017-02-25
Hi, I need an Ubuntu machine for an AI course I'm planning on taking (must be required to run ROS [Robot Operating System]).
While I am trying to become and AI/data geek, I wasn't (no offence) planning on becoming a Linux geek as well.
What's the best way to get up an running quickly?  
Should I : 
Set up dual install on my Windows laptop?
Buy a second machine and install on that?
Buy a machine with Ubuntu already installed? 

Or any other suggestions welcome.

James
Sydney AU

---

### Post by &amp;KyT$0P# on 2017-02-25
Would it work to run [Xubuntu]("https://xubuntu.org/getxubuntu/") in a [virtual machine]("https://www.virtualbox.org/") on your Windows laptop?

I say Xubuntu because it is a more lightweight flavor of Ubuntu.  Thus you'll have more resources available for your robot software, as compared to what you'd have under Ubuntu.

If virtualisation will not work, this is likely your best bet -
> **sohappy said:**
> Buy a machine with Ubuntu already installed? 

Of the options you listed, this one would probably require the least effort to get working.  And you don't have to risk your Windows laptop at all.

---

### Post by TheFu on 2017-02-25
"Any other suggestions welcome." .... 

Ok - wipe those commercial OSes and force yourself to learn Unix.  You don't know what you are missing and your AI will be much better for it.  No offense.

Ok, seriously, I'd start with using a virtual machine. Don't use normal Ubuntu with that - use Xubuntu or Lubuntu or Ubuntu-Mate instead. These work better inside a VM than the normal Ubuntu due to 3D GPU accel issues. Besides that, the GUI is just another program. It isn't the OS. There are probably 50 different GUIs for Linux systems and about 10 are popular, widely used, world-wide.

If you do not learn the OS at a sufficient level, including all the non-GUI methods, tiny issues will cause you hours, days, weeks of frustration over something that is a 30 second problem.  Learning Unix is like learning a foreign language if you haven't been exposed previously.  Other commercial OSes seem similar and from a point-n-click standpoint, I suppose they are.  But that's only 10% of the power from any computer.  To unleash the rest, learn the shell and scripting and the underlying OS (which is VERY different from Windows).  The good news is that without the GUI, Linux is Unix and things I did 30 yrs ago still apply. Heck, I have scripts 30 yrs old that still work perfectly.  

BTW, if you are going into big data, Linux will be your primary OS. Learning it thoroughly is well worth your time.

How?  [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) is my considered answer to that question. In a few hrs, you'll not be too dangerous.  Do at least the first 5 things. If you just wanted to surf and write documents, you wouldn't need the "Command Line", but doing AI means you need a deeper understanding.  No offense.

---

### Post by RobGoss on 2017-02-26
I think having a second machine would be a good idea it will give you the best hands on knowledge and will not allow you to mess up your main machine if somethings goes wrong something to think about

Using a virtual machine maybe good for some people but in my option I prefer the realization of how things will perform on a real **desktop** or **laptop,** in most cases you can probably pick up a second hand machine for dirt cheap example, I was able to pick up two Dell optiplex 755 and a 19- inch monitor for only $130.00 dollars with pretty good specs as well

> Ok - wipe those commercial OSes and force yourself to learn Unix. You don't know what you are missing and your AI will be much better for it. No offense.]  

I think this is the best advice to** force **your self to learn how Linux is used and get the knowledge needed to advance your Unix skills, learning by trial and error, is the only way to really learn how things work

---

### Post by HermanAB on 2017-02-26
AI and robotics are all Linux.  You better dive in and get used to it.

---

### Post by sohappy on 2017-02-27
Thanks for the advice.  Having trouble with the link, jdpfu.com seems to be down (connection timeout).

---

### Post by mastablasta on 2017-02-27
link working fine for me.

Linux is the OS you are actually encouraged to "hack". you can slim it down or bloat it up as you go. it is flexible and because of that it can be slimmed down and made to run on a lot of things. so you can have this small yet powerfull OS available to you.

in your case i start first with Virtualbox. it's offers a safe way to experiment in: [SIZE=2]http://www.psychocats.net/ubuntu/virtualbox
[/SIZE]

---

### Post by sohappy on 2017-02-27
Ummm, dumb question, would a bootable USB [like this]("http://www.ebay.com.au/itm/Linux-Ubuntu-16-04-LTS-On-Bootable-USB-flash-drive-32-64-bit-/222306086615") work - I guess most importantly, would I be able to access a partition on my hard drive to install additional software?

---

### Post by TheFu on 2017-02-27
> **sohappy said:**
> Thanks for the advice.  Having trouble with the link, jdpfu.com seems to be down (connection timeout).

Try using a google cache or **the way-back machine**. Some countries block that website. Don't know why. I think it is safe for kids.

That server was unavailable for about 3 minutes last night.
```
=== Time for Backups to blog41 === 
StartTime 1488179114.00 (Mon Feb 27 02:05:14 2017)
EndTime 1488179273.29 (Mon Feb 27 02:07:53 2017)
ElapsedTime 159.29 (2 minutes 39.29 seconds)

```
My monitoring didn't alarm on any other issues.  Daily, automatic, backups for that VM happens at 2:05am and usually take 1-4 minutes.

The network hasn't been down at all in the last week according to my network logs.  The prior week, those logs show:
```
Period 20170220-062611  - 20170226-062412
  Total Time: 8640 (min) 144.00 (hrs)
  Percent Up Time: 99.47 % 
  Percent Down Time: 0.53 % 
  Total Down Time: 46 min or 0.77 hrs
 Currently: UP

```
It is running on a 12.04 server inside a KVM VM. With support ending in a month, it will be migrated to something newer which is supported. I don't touch non-LTS releases, so 16.04 is the current plan.

As for a bootable USB drive.  Make your own. Definitely no need to pay $30 for it.  Use something like **yumi** to make any 2G or larger USB2 flash drive into a bootable Linux system. [https://www.pendrivelinux.com/yumi-multiboot-usb-creator/](https://www.pendrivelinux.com/yumi-multiboot-usb-creator/) it is the Windows tool that has never let me down, unlike many of the others.  If you have 4+G on that flash drive, you can load up 20+ different Linux OSes and try them all out.  Very handy.  OTOH, if you go with virtualization, you can try out almost every Linux distro out there.  None of this costs **any** money.  Just download the ISO files for each distro you want to try. Yumi can do that for you too.

  IMHO, running on HW is overrated. If you are not a gamer, there really isn't any reason if you don't REQUIRE direct HW access for some reason.  Solid virtualization can provide 95-98% of native performance for the types of workloads you plan to run. It is only the high-end graphics stuff where extra work and specific GPU hardware + passthru is desirable.  And just to be extremely clear, you don't need that sort of GPU passthru setup if you don't FPS game.  Most games work just fine inside a VM running locally and many work fine over a network connection.  When you get into the real-world, all your server access will be remote.

For people new to Linux, mounting a disk appears to be a non-trivial thing. Accessing disks is easy, but really integrating it into your desired setup will be non-trivial off a USB flash drive. This is because the power to mount is the power to destroy (*write that down*).  Plus, Linux uses Unix file systems, not Windows file systems.  FAT/NTFS file systems are fine for data, but nothing else. For programs and HOME, you must (well ... not really, but it will be a huge, huge, huge, hassle especially for someone new) use a file system that supports Linux permissions. That would normally be ext4 or xfs (if you have 20TB of data or more).  Ext4 can handle huge data too, but xfs will be a tiny bit faster and has a long history of dealing with huge data. The point is that flash storage really isn't the best solution for running a Linux OS long term. It is fine to get your toes wet for a few weeks, but nothing can compare to a full install (25G) running inside a VM or on real hardware.

The other folks here are giving great advice too, BTW.  there are lots and lots of options. Which ever you feel the most comfortable using **is** the correct answer.  Virtualization is the least risk - basically zero risk to the existing hardware and OS.  On Windows, virtualbox is pretty stable and easy to use. I used to give presentations around the world about optimizing virtualbox performance without going too crazy.  There are lots and lots of youtube videos with how-tos for setting up virtualbox. It is really very simple for someone going into the field you are.  Just beware that virtual machines don't have direct access to hardware and only so-so access over USB2 devices. That could become important later.

Sorry for rambling. I'm a very fast typist. Hopefully, I didn't leave out any important words.  ;)

---

### Post by HermanAB on 2017-02-27
+10 for Virtualbox on Windows with Linux in a VM.

---

### Post by oldrocker99 on 2017-02-27
You should know that VirtualBox doesn't (for me, anyway) boot from a USB, but boots from the .iso on your hard drive.

---

### Post by sohappy on 2017-03-11
Sorry, been busy the last week or two.
I'm getting a Raspberry Pi3 kit just to play around with (course doesn't start for a while, and I've wanted to play with Pi anyway).  Looks like maybe I [should have ordered a Pi2]("https://wiki.ubuntu.com/ARM/RaspberryPi") but [ubuntu-16.04-preinstalled-server-armhf+raspi3.img.xz]("http://www.finnie.org/software/raspberrypi/ubuntu-rpi3/ubuntu-16.04-preinstalled-server-armhf+raspi3.img.xz") might work?
Do you guys think learning on a Pi will be useful (I assume it will be), or is it not good for much other than setting up Kodi?
Would you think I can run [ROS]("http://www.ros.org/install/") using the Pi3 distribution?

Another question, does anyone know of a Linux group in/around Sydney that has meetings and wouldn't mind a newbie showing up for advice?  .... Scratch that, I guess I should make that a new post!

PS- I still can't get to [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) but have saved google's cached version.

James

---

### Post by TheFu on 2017-03-11
Raspberry Pis are fine, but limited.  I have a v2 Pi. It runs Kodi.  Nothing is really special about it, except that the hardware is fixed and people know it.  In most of the how-tos I see for it, written by next to complete noobs, there are unneeded, wasted, useless, steps. Sometimes a blind squirrel finds a nut.  It is a normal computer and happens to run Linux. Which release you choose is completely up to you.  Most are just shoved onto a SDHC and booted. No boot manager.  I use dd to do it and find it frustrating that every distro wastes my time with some extra program that needs to be downloaded just to 'dd' some bits onto an SD card.

A raspberry pi v3 is much better (for certain terms of better) than a v2 Pi. Faster, more capable, and where I am, cheaper because the supply is higher.

There are hundreds of great things you can do with a Raspberry Pi. Many are overkill and many others are just terrible ideas, but you can do it. Good uses for a Pi are those that don't need much I/O or CPU.  A home DNS/Proxy server (pi-hole) is a nice thing, provided the Pi is wired connected to the network, not wifi.  A home email, web, calendar, music, and perhaps web server is another project. None of those things need much I/O or CPU. For robotics stuff, the $5 Pi-Zero is probably sufficient.  Of course, a media player is a popular use for Pis too, but that's only because video decoding is HW supported by the GPU. Without that and these little machines cannot handle any hidef content - they just don't have enough CPU. Note that I said media player, not media server. Media servers should be able to transcode video on-the-fly to whatever codec is needed by the different client devices. No Pi can do that and the disk I/O limitations are terrible on all Pis.

I don't know anything about ROS. It may work. Just make certain it is compiled for a compatible ARM system. x86 versions will not work. 

For finding local Linux groups, use google. Search for "LUG" - "**Linux Users Group**" - that is the normal name - with the town / state / country.   There is probably a robotics-centric group at a University there. [http://www.slug.org.au/index.html](http://www.slug.org.au/index.html)  Also check all local universities.  3 of ours have ACTIVE linux groups.

blog.jdpfu.com has been up all this time except a few minutes nightly for backups. Try a different browser? If you tell me an exact time, I can look into the server logs to see what might be the issue.  The google-cache version should be sufficient. I don't change that page too often. Recent changes have only been for places to find training.

---

