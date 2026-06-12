---
title: "Howto setup an Acer W5102WLMi"
date: 2006-10-02
forum: Outdated Tutorials &amp; Tips
---

### Post by Haegin on 2006-10-02
I have just brought a new laptop and thought I would post this guide explaining what I did to get it setup as I wanted. I have mine set up with a 20gb windows partition and the rest for ubuntu but I will explain how to devote the whole 100gb hard drive to ubuntu for those of you who want to.

Firstly get it unpacked from its box, pop the battery in and plug it into the wall. Then turn it on. Even if you don't want to use windows ever again. It will ask you some questions about setting up windows and you can plonk in whatever you want really - set your username, cringe when windows doesnt enforce a password, set your timezone and maybe do some network setup. Next it will get to the desktop and will try and sort some things out.

Acer include a program that sets up a whole load of things on your pc for you such as drivers and things. The last thing it does is ask you to burn a backup DVD (or 4 CDs) to recover your system. Do this and then decide if you want windows or not.

If you do want windows then keep reading this next bit. If you dont want your machine to be tainted then just skip down to the Linux section.

**Windows Setup**
Now mine came with Norton AntiVirus 2006 (90 day trial) so I installed that  before connecting to my home wireless network just to give a bit of security. I then downloaded spybot search and destroy from [www.safer-networking.org](www.safer-networking.org) and installed that before scanning (you can ignore the windows antivirus security center disabled alerts - thats just norton turning off the duplicate alerts and nothing to worry about). Make sure you update both Norton and Spybot regularly.

I next went into spybot and starting cutting out a load of rubbish from the startup list but this is one of the advanced things in spybot and if you do not know what you are doing then it's not recommended.

I then installed adaware from [www.lavasoft.de](www.lavasoft.de) just to bring my security suite up to full force. For those of you who are interested, when Norton expires I will remove it and install AVG Anti Virus from [http://free.grisoft.com](http://free.grisoft.com) as its free. I have not installed a dedicated firewall as Windows includes one by default and I find this to be fine when I am connected through a router with a hardware firewall.

I next installed my copy of Office XP Pro after removing MS Works 8 and then installed firefox, Gimp for windows and Gaim for windows. Hooray for opensource software!

That was all the software I can remember installing so just run windows updates and get your machine up to date before you pop the ubuntu cd in the drive and restart to install Linux!

**Installing Linux**
If you decided not to use windows then just pop the Ubuntu install CD in the drive and restart the computer and wait until you get to the live cd desktop.

Now we are ready to install so just click on the Install icon and run through the setup choosing your location, language and keyboard setup etc until you get to the partitioning section. Now I have 2 sections again, one for windows users and another for linux only users. Firstly the windows users:

**Partitioning to keep Windows**

I had a small (approx 5 gb) partition as the first partition on my hard drive - this is an Acer recovery partition which I deleted. I then moved the main windows partition to the beginning of the drive and resized it to 20Gb (20480 MB) as this was all I reckon I will need. I then created a 20Gb / partition, a 2gb swap partition and the rest was a /home partition.

Once done just click next.

**Partitioning without Windows**

This is much easier as you dont need to worry about Windows so delete all the partitions and create one for /, one for /home and one for swap. I recommend a 2Gb swap partition, a 30Gb / partition and the rest for /home.

Once done just click next.

**Continuing the install**

Now partitioning is done just assign each partition to a mount point (you don't have to mount the windows partition if there is one but as Acer format the drives as fat32 you can read and write it which is useful) and click next to format them if needed and install the system.

At the end it will ask you to restart so do so and watch as it boots into your new ubuntu install. If you decided to keep windows then you will notice it has a menu which you can decide to boot windows from if you wish to. For now boot into ubuntu and finish setting it up.

Firstly I recommend bringing the system up to date so add the extra repositories by editing /etc/apt/sources.list and then from a terminal run ```
sudo aptitude update && sudo aptitude dist-upgrade
```.

Now you can install whatever programs you want as you would with a normal Ubuntu install. I have not finished getting all the hot keys working and the camera will probably take some work so I plan on working on these and posting my success up here in the future.

For now I hope this is a help to somebody out there and if you have any questions please post them in a reply to this thread and don't email or PM me as then others can benefit from the answers as well.

**Questions**
Q. Did you use 32bit or 64bit?
A. I used Dapper 32bit

---

### Post by ppvanzella on 2006-10-02
Hey!
Are you installing it with the 64 bits version?
Did you make the VGA to work?
I'm running edgy right now, and almost everything works. The new synaptics drivers work, but the dapper ones are really bad.
Keep posting news ;)

---

### Post by Haegin on 2006-10-03
I am just using the 32bit version on dapper but I'm tempted to try edgy 64bit when it is released (first time I have ever waited for the release before upgrading). What are you running, 32 or 64bit? My vga is fine - I'm using the fglrx driver but the default was fine too. How is edgy? What does't work?
My touchpad is fine under dapper.

---

### Post by ppvanzella on 2006-10-03
I'm running egdy 64, and now the touchpad is working, but on dapper it would click to easly, what was a pain on the butt... I couldn't install the fglrx drivers, I'm using the radeon drivers, what is giving me indirect acceleration (better than nothing).
Sometimes it complains on the boot that it couldn't boot the ndiswrapper dirvers, though it connects to the wi-fi networks always.
I'm still working on it :P

---

### Post by 4tro on 2007-05-09
if you don't want to use windows, you should _never_ run through the install.

in stead you should deny the license, preferably in the shop where you bought the laptop, and repartition the hard-disk in the shop, using your favorite ubuntu disk 

This way Microsoft and the laptop-producer have to pay you back the costs of the windows. (unless they changed the EULA since Vista, and are being an ***)
 
it's all in the EULA of Microsoft, just look for it when you buy the laptop.

---

