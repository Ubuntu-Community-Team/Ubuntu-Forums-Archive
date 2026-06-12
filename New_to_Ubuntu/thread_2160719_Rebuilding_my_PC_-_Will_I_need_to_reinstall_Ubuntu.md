---
title: "Rebuilding my PC - Will I need to reinstall Ubuntu? + parition question"
date: 2013-07-08
forum: New to Ubuntu
---

### Post by SBTlauien on 2013-07-08
I'm going to be getting some new PC parts in a couple of days and I need to know if I am going to need to reinstall Ubuntu.  I am currently running 12.04 Precise Pangolin Gnome on an older 64-bit OS with a Nvidia graphics card.  It runs fine, except that it crashes when I run certain applications, because my RAM is only 995.2MiB and the processor is a AMD Athlon 64 Processor 3800+.

I'll be keeping my 1tb hard drive because it is brand new, as well as my DVD drive, fans, and Power Supply.

My new PC will have a GIGABYTE GA-970A-D3 AM3+ motherboard, a AMD FX-6300 FX-Series Six Core processor, a EVGA GeForce GTX650Ti graphics card, and 16gb of RAM(two 8gb sticks).

When I power it up with my hard drive, will Ubuntu just simply ask to download new drivers and everything, or should I reinstall?

As far as my hard drive goes, I currently have two partitions that are each about 500gb and Ubuntu+everything is on one of the partitions(the second one).  I'd like to make one smaller partition for Ubuntu and programs, and the other(larger) partition for storage of data(pictures, music, movies, books).  What are good partition sizes for each partition, and how can I set it up so that my files in my Home Folder(Pictures, Documents, Music, Videos) will link to the data that's stored on the larger partition?

---

### Post by dargaud on 2013-07-08
In most cases you don't even notice hardware upgrades. The only time where you should reinstall is when going from 32 to 64-bits, but it's not your case. Give it a shot: backup your system and user directories, put your old drive in the new setup, make sure the BIOS sees it properly and boot: Linux will use whatever new drivers it needs. Afterward do a "aptitude update; aptitude full-upgrade". I have systems that have gone through 4 major upgrades and still the same install. One more reason not to stick with Windows...

---

### Post by grahammechanical on 2013-07-08
Ubuntu will not just do anything. Linux will try to run on the hardware and will make quiet a good job of it and Ubuntu will load and that is when you will notice that the video driver that worked on your old video card will not be able to run the new video card. In my opinion, that is.

I suggest that you activate the Nouveau open source driver. And then when you get to a desktop you can activate a proprietary driver that is applicable to the new video adapter. For the first boot, you could even use Recovery mode>Resume. That will load Ubuntu without activating a video driver. It will use a standard (basic) video mode compatible with the xserver. At least it will get you to a working desktop where you can then use Additional Drivers.

Do not forget, that one of the reasons we have newer versions of Ubuntu and that LTS have four point releases in 2 years is to bring in the latest Linux firmware to work the new hardware. The Linux kernel in 12.04 may work fine on this newer hardware but the Linux kernel in 12.04.2 may work better. There is a reason why the kernel has gone from 3.2.0 to 3.5.0. Incidently Ubuntu 13.04 has kernel 3.8.0 and Saucy Salamander (13.10) has 3.10.0 and will get 3.11.0

Improvements have also been made to video drivers, both proprietary and open source.

Regards

---

### Post by mastablasta on 2013-07-08
if you have proprietary drivers remove them first and run with opensource. 

then linux will check hardware on boot and load opensource drivers. then you install new proprietary drivers and that's it.

---

### Post by dannyboy79 on 2013-07-08
ensure your old PSU has the correct CPU power connectors for your new CPU and Motherboard, you'll most likely find it may not have the 6 or 8 PIN connector your new CPU requires. Also, does your current PSU have the correct GPU power connector for the 650ti?

Otherwise, you should be golden to just switch out everything and boot up the existing hard drive BUT as others said you should remove your current nvidia driver with either nouvue or vesa because with the 650 I am sure you can use the latest Nvidia stable driver to get the most out of the card I would go with what nvidia provides on their website or use x-swat ppa.

If you start playing around with partitions (shrinking where ubuntu lives) then I would most certainly make a backup image just in case something goes wrong.

---

### Post by BBQdave on 2013-07-08
> **grahammechanical said:**
> ...one of the reasons we have newer versions of Ubuntu and that LTS have four point releases in 2 years is to bring in the latest Linux firmware to work the new hardware. The Linux kernel in 12.04 may work fine on this newer hardware but the Linux kernel in 12.04.2 may work better. There is a reason why the kernel has gone from 3.2.0 to 3.5.0. Incidently Ubuntu 13.04 has kernel 3.8.0 and Saucy Salamander (13.10) has 3.10.0 and will get 3.11.0

Good information :)

And I would offer that it might be simplier to back up your data, and do a fresh install with your new hardware.

---

### Post by arpanaut on 2013-07-08
Be aware that the new motherboard may have uefi and you may need to change settings to legacy support (bios mode)
You may want to consider reinstalling to take advantage of the advancements of uefi, GPT partitioning. 
But that's your call.

---

### Post by SBTlauien on 2013-07-08
What are good partition sizes for a 1tb hard drive?

Maybe 100gb for the OS and programs, and then 900gb for storage...?  Is a SWAP even needed?

Also, would it be easy to link the folders in my "Home Folder" directly to the folders on the larger-storage partition?

---

### Post by dannyboy79 on 2013-07-08
i wouldn't ever install an OS on that large of a drive but if it's all you have then I would probably allocate 50gb for OS, 100gb of /home and the rest for storage. and yes, in linux you can create symlinks in your home directory that point to your storage partition where ever you choose to mount it.

---

### Post by SBTlauien on 2013-07-08
What's the difference between /home and the OS?

I plan on using this PC for Android App development and plan on putting a bunch large programs on it.

---

### Post by dannyboy79 on 2013-07-08
i prefer to have my /home/ partition separate so that in case I need to reinstall the OS i will only have to format the / partition and not my /home/ which is where all your customizations and app configs are saved. not to mention most times people store their documents, music, videos, pictures within /home/. it's really all a preference.

---

### Post by CaptainMark on 2013-07-08
100 gb and 50 gb is both waaay too much. I have 20gb partitioned for root, that amount is more than ill ever need, I have a load of applications installed and I'm only using 7gb. Having said that space is cheap these days so go for whatever you feel you can spare from your data partition

---

### Post by SBTlauien on 2013-07-08
When I create these partitions, will they be pre-defined in the installer?

So the / in the main OS, and the /home is the programs on the OS?

---

### Post by SBTlauien on 2013-07-08
Is root the same as / ?

---

### Post by oldfred on 2013-07-08
The root partition is / in the installer. I use a data partition and link folders from the data partition back into my /home. Since my /home is then so small, I leave it in / but separately back it up. All data is in my data partitions. Only user settings for programs and some user data like Firefox bookmarks and Thunderbird email are in /home, but I even move any similar hidden data folder if it starts to get large into my data partition. Programs themselves are in root.

       The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

---

### Post by mastablasta on 2013-07-09
home is sort of like My documents in windows. its where users settigns and files are stored.

/ or root is like C: in windows. it's where the main OS is located and all files connected to it. to change things at / you need super user privileges.

read more here: [https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

---

### Post by 3rdalbum on 2013-07-09
Actually, you can just install Ubuntu the ordinary way to the 1TB. No need for manual partitioning or a separate /home. You can if you want to, but a fresh install of Ubuntu will allow you to keep your existing /home even if it is in the same partition as /

---

### Post by dannyboy79 on 2013-07-09
> **3rdalbum said:**
> , but a fresh install of Ubuntu will allow you to keep your existing /home even if it is in the same partition as /
not true, a fresh install normally requires a format of whatever partition you choose to be your root partition (mount point being / ), and if your old /home/ is located within that partition that you're formatting to be your new /, then all that information will be deleted during the format.

If you have a current installation of ubuntu BUT want to partition your drive up differently than I would just suggest backing up whatever you feel is important to an external location and then format/partition however you want, then just paste back what you had saved off to an external location.

---

### Post by SBTlauien on 2013-07-09
I'm still a but confused on why there should be a / partition and a /home partition.  Is this because people don't want to reinstall programs after reinstalling thier OS?

If that's the case, then I'd rather / and /home be on the same partition, and then another partition just for my data(pictures, music, videos, books).

---

### Post by edb66083 on 2013-07-09
I have my / partition separate from my /home partition. That way, when I want to do a fresh install, I only have to reformat and install into the / partition. I leave the /home partition as it is. When installing, just label the /home partition as the /home partition, without formatting, and all your data will be intact.

One caveat, though. Generally, when I do a new install, I go into the /home directory and delete most of the hidden files (those that start with a '.'), which are the configuration files. If you don't delete some of those, it can mess up your new install sometimes.

The bottom line is that it is good practice to separate the / and /home partitions. And the / partition is just your OS, so you probably only need 20 GB max.

---

### Post by dannyboy79 on 2013-07-09
you can do it that way also, a bunch of symlinks in your /home/ directory pointing to the separate hard drive or partition where all your pics, music, videos, and books are stored.

it pretty much all preference and some people have explained why they do it the way they do it.

---

### Post by SBTlauien on 2013-07-09
So, what is a good size for a / partition that contains a /home directory?

I plan on using this PC for development and will be running Eclipse + many add-ons, as well as maybe some video editing software, image editing software(I have Corel PaintShop), audio editing software, and maybe more.

Maybe 100gb for the / partition that contains the /home directory?

---

### Post by dannyboy79 on 2013-07-09
it all depends on where you're going to store your beefy files. we could analyze this and that for days, weeks even but it just boils down to trying something and learning from it. 100GB for your / and /home/ is fine.

---

### Post by mastablasta on 2013-07-10
> **SBTlauien said:**
> I'm still a but confused on why there should be a / partition and a /home partition. Is this because people don't want to reinstall programs after reinstalling thier OS?


preety much. Hoe also ocntaines user settings an such. so if you tweak the programmes to your liking the tweaks are stored in /home.

> 
If that's the case, then I'd rather / and /home be on the same partition, and then another partition just for my data(pictures, music, videos, books).

sure. why not?


i ahve an old IDE disk for the OS (including /home) and new & big SATA for data.

that's the beautiy. you can set up linux preety much any way you want.

---

### Post by CaptainMark on 2013-07-10
> **SBTlauien said:**
> I'm still a but confused on why there should be a / partition and a /home partition.  Is this because people don't want to reinstall programs after reinstalling thier OS?

If that's the case, then I'd rather / and /home be on the same partition, and then another partition just for my data(pictures, music, videos, books).Just to clarify incase there's any confusion:

/ (Also known as the root, but not to be confused with the root user) is where all the operating system files are kept and programs themselves

/home (your home folder) is the where all of your personal data (Music,Video etc.) is stored and also where any configuration files for applications are stored

So if you're reinstalling a new system and you format / but not /home then when you boot up your new system all of your Pictures and Documents will still be there. All of your installed programs will be gone but of your preferences for the applications will be stored, so if you reinstall that application, it will return exactly as before. For example, I have the chromium browser installed and tweaked to my liking, if I reinstall today and format / then after the install chromium wont be installed, however if I simply reinstall the chromium browser from the software centre when I load it up it will still be tweaked to my liking even though the program got erased during the fresh install

---

