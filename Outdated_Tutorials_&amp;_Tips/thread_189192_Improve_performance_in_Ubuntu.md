---
title: "Improve performance in Ubuntu"
date: 2006-06-04
forum: Outdated Tutorials &amp; Tips
---

### Post by xXx 0wn3d xXx on 2006-06-04
This is an index of threads on how to get the best performance out of your Ubuntu machine.

**[COLOR="Red"]Warning:[/COLOR]** These tutorials may cause harm to your system if you do not follow them correctly. Please remember to _carefully_ follow and read the guides. Thank you.

[ Use InitNG as a replacement for standard Init.](wiki.ubuntu.com/InitNG)

[ Speed up Firefox ](http://ubuntuforums.org/showthread.php?t=181107)
[url=http://ubuntuforums.org/showthread.php?t=157560]
  Custom compile a new kernel. [/url] You can also use [ this tutorial. ](http://ubuntuforums.org/showthread.php?t=85064)

[ Make sure DMA is enabled. ](wiki.ubuntu.com/DMA)

[ Use Prelink to make applications start faster. ](http://ubuntuforums.org/showthread.php?t=74197)

[ Pick the kernel that's right for your processor. ](http://ubuntuforums.org/showthread.php?t=85917)

[ Disable uneeded services from starting. ](http://ubuntuforums.org/showthread.php?t=89491)

[ Use Swiftfox, a faster Firefox for Intel and AMD processors. ](http://ubuntuforums.org/showthread.php?t=142798)

[ Tweak your ext3/reisers filesystem for enhanced performance. ](http://ubuntuforums.org/showthread.php?t=107856)

[ Clean up unnecessary files ](http://ubuntuforums.org/showthread.php?t=140920)

[ XML Optimization ](http://gnomefiles.org/app.php?soft_id=1397) Thanks to orvils for the link and informmation.

_Tips from me:_
Install preload "sudo apt-get install preload."
Use the latest drivers for your video card.
Use XFCE as your Desktop Enviroment.
Use Abiword instead of Open Office

---

### Post by GoA on 2006-06-05
How is the preload application used? Does it work automatically?

---

### Post by elemental666 on 2006-06-06
Before doing anything to tweak the perfomance of my ubuntu install, I'd like to get some benchmarks so I can see what kind of performace increase I'm getting.  So how does one go about getting these benchmarks?

---

### Post by bluevoodoo1 on 2006-06-06
[QUOTE=elemental666]Before doing anything to tweak the perfomance of my ubuntu install, I'd like to get some benchmarks so I can see what kind of performace increase I'm getting.  So how does one go about getting these benchmarks?[/QUOTE]

Here's a video card related one...
[http://ubuntuforums.org/showthread.php?t=157429](http://ubuntuforums.org/showthread.php?t=157429)

It's still in development, but it's pretty neat.

---

### Post by elemental666 on 2006-06-06
Thanks blue, I"ll check it out...

Also, found this HOwto to get me started... just in case anyone else feels the same...

[http://www.tldp.org/HOWTO/Benchmarking-HOWTO.html](http://www.tldp.org/HOWTO/Benchmarking-HOWTO.html)

---

### Post by ago on 2006-06-06
Consider also runit instead of initng

[http://smarden.org/runit/](http://smarden.org/runit/)
[http://os.newsforge.com/article.pl?sid=06/05/03/2126252&from=rss](http://os.newsforge.com/article.pl?sid=06/05/03/2126252&from=rss)

---

### Post by JSchwage on 2006-06-06
What about better alternatives to OpenOffice? I've actually noticed it takes longer for OO to start up than Firefox on my old Compaq Presario 1200. I think you should mention Scribus or something similiar. ;)

---

### Post by itomeshi on 2006-06-06
[QUOTE=JSchwage]What about better alternatives to OpenOffice? I've actually noticed it takes longer for OO to start up than Firefox on my old Compaq Presario 1200. I think you should mention Scribus or something similiar. ;)[/QUOTE]

Why not just tweak OpenOffice? The default memory management settings literally throttle OpenOffice into oblivion.

Open up writer, and go to Tools > Options. Go to memory in the sidebar.

Set number of undo steps to 30-40 max, have it use 64MB or more (128, if your system can afford it (at least 512mb total ram) helps greatly), boost memory per object to 5.0 MB.

Need a visual example? Try [http://openoffice.blogs.com/openoffice/memory/index.html]("http://openoffice.blogs.com/openoffice/memory/index.html"), which I found via Google.

I wouldn't do the JRE trick that page mentions unless you REALLY never use those aspects. Still, the memory tweak alone is an impressive boost.

---

### Post by JSchwage on 2006-06-06
[QUOTE=itomeshi]Why not just tweak OpenOffice? The default memory management settings literally throttle OpenOffice into oblivion.

Open up writer, and go to Tools > Options. Go to memory in the sidebar.

Set number of undo steps to 30-40 max, have it use 64MB or more (128, if your system can afford it (at least 512mb total ram) helps greatly), boost memory per object to 5.0 MB.

Need a visual example? Try [http://openoffice.blogs.com/openoffice/memory/index.html]("http://openoffice.blogs.com/openoffice/memory/index.html"), which I found via Google.

I wouldn't do the JRE trick that page mentions unless you REALLY never use those aspects. Still, the memory tweak alone is an impressive boost.[/QUOTE]
The only problem is that I'm on an old AMD K6 with 192MB of RAM. OO takes about 20 seconds to fully load. I'm not as much worried about how much memory it's using when it's actually loaded.

---

### Post by itomeshi on 2006-06-06
[QUOTE=JSchwage]The only problem is that I'm on an old AMD K6 with 192MB of RAM. OO takes about 20 seconds to fully load. I'm not as much worried about how much memory it's using when it's actually loaded.[/QUOTE]

On my Centrino 1.4Ghz, 512MB of RAM, etc., it normally takes about 10-12 seconds to load. After this, it is about 3-4. Even if you can only boost it wo 32 or 48 (from 19), it will help.

How do web-based word processors (like [Writely]("http://www.writely.com/")) or stand alone solutions like AbiWord perform on your machine?

---

### Post by dtfinch on 2006-06-07
Firefox already has this fix, but Thunderbird can see a great improvement if you disable pango. I use a shell script for this, which my thunderbird launcher points to:

#!/bin/sh
MOZ_DISABLE_PANGO=1 mozilla-thunderbird

I assume you can also just add MOZ_DISABLE_PANGO=1 to /etc/environment to make the change global.

---

### Post by ago on 2006-06-07
Also, if you are after performance or you have an old pc or you do not like bloat, you should seriously consider xubuntu (xfce) instead of ubuntu (gnome). Not only it is faster, I personally like it better. Xubuntu is a light and fast desktop manager based on xfce and it comes only with packages that can be considered fairly light and with few dependencies, no OO for instance.

---

### Post by saracen on 2006-06-07
So the repos on alioth are down and i can't get to Trigger's blog where the initng debs are usually announced.  Does anyone have a copy of the initng 0.6.0 debs?

---

### Post by adamkane on 2006-06-07
All you need to do is:

Intel Pentium:
```

sudo apt-get install linux-686 linux-headers-686

``` 
AMD K Series (Duron, Athlon, Sempron):
```

sudo apt-get install linux-k7 linux-headers-k7

``` 

Reboot.

This will install the correct kernel files for your system, and your system will be much more responsive, and you will be able to run amaroK without slowing down your system!

Disabling services, etc., is unnecessary, and may cause needless headaches for new users.

Definitely use Swiftfox rather than Firefox. Swiftfox is sooo easy to setup:
[http://www.getswiftfox.com/]("http://www.getswiftfox.com/")

---

### Post by itomeshi on 2006-06-07
[QUOTE=adamkane]Disabling services, etc. is unnecessary, and may cause needless headaches for new users.[/QUOTE]

For new users, yes... it is a dangerous trick. Even using a program like Bootup Manager, it's very easy to cause issues that may kill your system.

However, if you know what you're doing, are not afraid to reload, and have a good reference list, it can provide a significant speed and security boost. Fewer running services reduces your potential attack footprint - it is likely that every service in every OS has undiscovered vulnerabilities, so just disable that which you're certain you don't need.

Another speedup I recommend, especially on low RAM systems? Kill the wallpaper and choose a SIMPLE theme and screensaver. These eat up RAM on any OS, and rarely get swapped out - they're always being called on. So while the lagoon is a great spoof of OSX wallpaper, and the tree is one of the most are inspiring edited photos I've seen, I don't need to see it every day.

---

### Post by ubuntu_demon on 2006-06-07
thnx for the index :)

You should add a **warning in bold letters** at the top of your post. Some of the things you suggest can seriously harm the system of a new user.

I don't think the ipv6 suggestion speeds up the network for most of us. Maybe it does for some. See this post :
[http://ubuntuforums.org/showpost.php?p=478267&postcount=8](http://ubuntuforums.org/showpost.php?p=478267&postcount=8)
Also this is a guide for breezy but edwing suggests how to do it in Dapper :
[http://ubuntuforums.org/showpost.php?p=1100830&postcount=49](http://ubuntuforums.org/showpost.php?p=1100830&postcount=49)

---

### Post by fgr on 2006-06-07
[QUOTE=JSchwage]What about better alternatives to OpenOffice? I've actually noticed it takes longer for OO to start up than Firefox on my old Compaq Presario 1200. I think you should mention Scribus or something similiar. ;)[/QUOTE]

I use for text: AbiWord, easy and fast

---

### Post by Triton on 2006-06-07
Looking for more info on **RUNIT**.  I've tried InitNG and everytime I install it, it blows up my system.  Very frustrate with it.  Would like to try it but I looking for a How-To for 
Dapper/Kubuntu.

---

### Post by JSchwage on 2006-06-07
[QUOTE=itomeshi]On my Centrino 1.4Ghz, 512MB of RAM, etc., it normally takes about 10-12 seconds to load. After this, it is about 3-4. Even if you can only boost it wo 32 or 48 (from 19), it will help.

How do web-based word processors (like [Writely]("http://www.writely.com/")) or stand alone solutions like AbiWord perform on your machine?[/QUOTE]
Well I haven't been able to try anything else as I'm waiting for my Belkin USB ethernet adapter to arrive from NewEgg. I'm waiting on installing any packages until I have an internet connection on it since it would be like heck trying to satisfy all the dependencies. ;)

But I'll let you know how AbiWord, Scribus, Writely, and some others perform once I get that ethernet adapter.

---

### Post by enopepsoo on 2006-06-07
I read a cool post on slashdot today.  There is a debian package named "deborphan" that  lists orphaned packages.  So do this:
```
sudo apt-get install deborphan
```
and that will list all of your orpaned packages, so do this to remove them all
```
sudo apt-get remove `deborphan`
```
and that should get rid of any packages your system is not using.  It is not really a performance boost, but under the wider umbrella of "optimizing."
Happy Ubuntuing.

---

### Post by xXx 0wn3d xXx on 2006-06-07
[QUOTE=Triton]Looking for more info on **RUNIT**.  I've tried InitNG and everytime I install it, it blows up my system.  Very frustrate with it.  Would like to try it but I looking for a How-To for 
Dapper/Kubuntu.[/QUOTE]
I saw an interesting article about Runit on linux.com and have been thinking about trying it. I also have problems with InitNG and in response to the thread above, a guide on deporphan is in Clean up unnecessary files.

---

### Post by dr_d on 2006-06-08
Thanks heaps to the person who posted this howto. I am now making full use of my dual core processor.

Cheers!

---

### Post by snipe122 on 2006-06-08
a better OpenOffice is StarOffice, much more stable and better integration to MS Office...

---

### Post by elemental666 on 2006-06-08
OpenOffice and StarOffice share a past don't they?  Seems like Sun aquired a copy of the source and closed it somehow or other... Anyway at the very least StarOffice used to be free, moneywise and otherwise.  I remember using it way back in the day, when Broadband was just getting setup in the major cities of the US.  Buncha turn coats... BAH! $70...  

heh... wow, I just realized that going open platform has jaded me.  I can live with it tho...

bah!

> Historical background

StarDivision, the original author of the StarOffice suite of software, was founded in Germany in the mid-1980s. It was acquired by Sun Microsystems during the summer of 1999 and StarOffice 5.2 was released in June of 2000. Future versions of StarOffice software, beginning with 6.0, have been built using the OpenOffice.org source, APIs, file formats, and reference implementation. Sun continues to sponsor development on OpenOffice.org and is the primary contributor of code to OpenOffice.org. CollabNet hosts the website infrastructure for development of the product and helps manage the project.

The OpenOffice.org source code includes the technology which Sun Microsystems has been developing for the future versions of StarOffice(TM) software. The source is written in C++ and delivers language-neutral and scriptable functionality, including Java(TM) APIs. This source technology introduces the next-stage architecture, allowing use of the suite as separate applications or as embedded components in other applications. Numerous other features are also present including XML-based file formats based on the vendor-neutral OpenDocument standard from OASIS and other resources.

A FAQ addresses the changing differences between OpenOffice.org and StarOffice.


Fine, I'll stop using OOo now too! Bloated anyway!

>    6.

      Differences between StarOffice and OpenOffice.org
          * The source code available at OpenOffice.org does not consist of all of the StarOffice code. Usually, the reason for this is that Sun pays to license third-party code to include in StarOffice that which it does not have permission to make available in OpenOffice.org. Those things which are or will be present in StarOffice but are not available on OpenOffice.org include:
                o Certain fonts (including, especially, Asian language fonts)
                o The database component (Adabas D)
                o Some templates
                o Extensive Clip Art Gallery
                o Some sorting functionality (Asian versions)
                o Certain file filters
                o Commercial spell checker, synonym dictionary
                o Management tools 
      For more information on the current features of OpenOffice.org, please see the "Features" page.
      A detailed comparison datasheet is available at Sun Microsystem's web site about OpenOffice.org. 


---

### Post by snipe122 on 2006-06-08
of course if you have to pay for it its crap, but for me (student) its free... and its definetely more stable. and of course they share the same background.

---

### Post by sumadartson on 2006-06-09
This worked wonderfully... Just enabled prelinking and swapped my kernel to a k7 one. Performance increase is tangible.

Now, my life would be complete if I could only get a composite manager running on a dual screen ati (9200se) setup.

On the other hand, I'm definitely going nvidia for my next machine

---

### Post by snipe122 on 2006-06-09
=D>  nVidia =D>  :mrgreen:

---

### Post by SentientFluid on 2006-06-18
[QUOTE=enopepsoo]I read a cool post on slashdot today.  There is a debian package named "deborphan" that  lists orphaned packages.  So do this:
```
sudo apt-get install deborphan
```
and that will list all of your orpaned packages, so do this to remove them all
```
sudo apt-get remove `deborphan`
```
and that should get rid of any packages your system is not using.  It is not really a performance boost, but under the wider umbrella of "optimizing."
Happy Ubuntuing.[/QUOTE]

I'd suggest being careful with this as it uninstalled a lot of gstreamer stuff on my system... stuff that I was actually using.

---

### Post by lzap on 2006-06-18
Ubuntu already use readahead, its a same program as "preload". No need to install then...

---

### Post by xXx 0wn3d xXx on 2006-06-18
[QUOTE=lzap]Ubuntu already use readahead, its a same program as "preload". No need to install then...[/QUOTE]
Yes Ubuntu does use readahead but only at boot. Basically while one process is booting, so is the next one, making that first process start slower. Turning readahead off is really the same as having it on because the first process is taking all the cpu, the seconds process doesn't start as fast but the first does. Readahead is only at boot time. Preload keeps commonly used applications and stuff in your memory, increasing startup times for that application. It learns what you use.

---

### Post by inovermyheadd on 2006-06-18
hey I tried to see if DMA was enabled, because my cd drive is acting screwy so far in dapper, but I don't even have a dev/hdc

is this weird?

Here is the wiki I tried to use:


[HTML]To enable DMA, you need to use the hdparm command and the configuration file hdparm.conf.

These instructions assume that you are trying to enable DMA on hdc, usually the CD-rom drive.

   1.

      See the what the settings are on /dev/hdc
          *

               sudo hdparm /dev/hdc
               

   2.

      If you get a line like  using_dma    =  1 (on), DMA is already enabled. Skip to step 4 to see if it has been enabled at boot time.
   3.

      Enable DMA on /dev/hdc
          *

               sudo hdparm -d1 /dev/hdc
               

   4.

      You have now enabled DMA for the drive. However, in order for the settings to be automatically applied at boot there you need to edit the /etc/hdparm.conf script. To do this use this command: sudo gedit /etc/hdparm.conf

Add the following to the end of your hdparm.conf

/dev/hdc {
dma = on
}

(another way of avoiding editing of the hdparm.conf file is to simply run sudo hdparm -d1 -k1 /dev/hdc to keep the DMA flag).
[/HTML]

---

### Post by lzap on 2006-06-19
[QUOTE=xXx 0wn3d xXx]Yes Ubuntu does use readahead but only at boot. Basically while one process is booting, so is the next one, making that first process start slower. Turning readahead off is really the same as having it on because the first process is taking all the cpu, the seconds process doesn't start as fast but the first does. Readahead is only at boot time. Preload keeps commonly used applications and stuff in your memory, increasing startup times for that application. It learns what you use.[/QUOTE]
Thanks. I see. I will check the preload out, I hope it wont eat much memory...

---

### Post by sejjiin on 2006-06-23
[QUOTE=adamkane]All you need to do is:

Intel Pentium:
```

sudo apt-get install linux-686 linux-headers-686

``` 
AMD K Series (Duron, Athlon, Sempron):
```

sudo apt-get install linux-k7 linux-headers-k7

``` 

Reboot.

This will install the correct kernel files for your system, and your system will be much more responsive, and you will be able to run amaroK without slowing down your system!

Disabling services, etc., is unnecessary, and may cause needless headaches for new users.

Definitely use Swiftfox rather than Firefox. Swiftfox is sooo easy to setup:
[http://www.getswiftfox.com/]("http://www.getswiftfox.com/")[/QUOTE]
Hi, I'm brand new to linux, running xubuntu.

Does installing the Pentium kernel files also speed up Celeron systems or is there another package like this for Celerons?  Mine is 450 and based on Pentium 2/3 (don't know which).

Seperate question - why does doing this cause amaroK to not slow down the system?  Won't it still have to install KDE packages?

---

### Post by TheTux on 2006-06-24
does it support celeron m? is celeron m part of 686 family?i've installed the 686 kernel image...i dont think there is improvement..previously i had installed the 2.6.15-25-386 via automatic update..and it does not perform well in aiglx as the default one(2.6.15-23-386 which is dapper's default  )...is it okay to remove the 686 kernel image?

---

### Post by ago on 2006-06-30
Other tip: use dash as /bin/sh

dash is a posix compliant shell that is smaller and (much) faster than bash. By redirecting sh most scripts will run faster while the login shell will remain unchanged

```

sudo apt-get install dash
sudo dpkg-reconfigure dash

```

Answer Yes to the question 'Install dash as /bin/sh?'

---

### Post by Rui Pais on 2006-06-30
[QUOTE=ago]Other tip: use dash as /bin/sh

dash is a posix compliant shell that is smaller and (much) faster than bash. By redirecting sh most scripts will run faster while the login shell will remain unchanged

```

sudo apt-get install dash
sudo dpkg-reconfigure dash

```

Answer Yes to the question 'Install dash as /bin/sh?'[/QUOTE]

Hi,
i tried this, but some scripts fails or output errors like:
> [[: not found

---

### Post by billyevil on 2006-07-06
Textmaker office isn't a bad alternative to openoffice.. it costs some money but not a whole lot.. you can download the 30 day trial at their site.. seems to work fine in xubuntu.. just downloaded the .tgz file, extracted it to a folder, then clicked on the file named tml inside the folder and it installed and was running in no time.. really a nice fast word processor.. worthwhile if you don't mind spending a few bucks..

---

### Post by rohan! on 2006-07-10
> **inovermyheadd said:**
> hey I tried to see if DMA was enabled, because my cd drive is acting screwy so far in dapper, but I don't even have a dev/hdc

is this weird?


the likelyhood is that your cd drive is a different device, mine for example is /dev/hda (this is because my hard drive's /dev/sda) what you want to do is enter the command:
```
cat /etc/fstab
```
[you'll get output something like this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
**/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0**

```

the bit you want is the line that has the mount point /media/cdrom0 on it. The last line in mine.

so just go through the guide using the other device name :)

hope that helps

---

### Post by rohan! on 2006-07-10
sorry, i don't know how to delet posts

```
~$ cd pub
~/pub$ more beer
```

---

### Post by ubuntu_demon on 2006-07-10
This is only for desktops and not for servers.

here's an interesting spec for Edgy :
[https://wiki.ubuntu.com/CFQbyDefault](https://wiki.ubuntu.com/CFQbyDefault)

[quote=Rationale]
In Dapper and previous releases, there has been no default scheduler set at install time, thus the system defaults to the native Linux scheduler. A number of users (including this spec's author) have encountered temporary system lockups when entering Gnome(/KDE/other wm) due to the system load. Enabling CFQ as the default scheduler fixes these lockups. Other major distributions, like Red Hat, also enable CFQ by default.
...
...
...
[/quote]

You can find the related HOWTO on this page :
[https://wiki.ubuntu.com/JoeyStanford/UbuntuFAQs](https://wiki.ubuntu.com/JoeyStanford/UbuntuFAQs)

I've tested it and it worked for me (I can use the terminal almost right away instead of having to wait for a couple of seconds).

---

### Post by scubanator87 on 2006-07-12
This definatly shed time off my bootup for my lappy which is a plus since i just completely migrated it to linux :) got tired of windows and all its...restrictions/shortcommings keep up the good work!

---

### Post by ubuntu_demon on 2006-07-14
Here's an optimization to make gnome feel faster :

Faster gnome menus 
[http://www.ubuntuforums.org/showthread.php?t=215119](http://www.ubuntuforums.org/showthread.php?t=215119)

---

### Post by ubuntu_demon on 2006-07-14
This is regarding vm.swappiness.

In my personal experiences the default vm.swappiness=60 is okay for most users who don't like tweaking. 

If you need more speed you might want to reconsider using a lighter desktop environment such as fluxbox or icewm like I explain here :
[http://www.ubuntuforums.org/showpost.php?p=1254289&postcount=13](http://www.ubuntuforums.org/showpost.php?p=1254289&postcount=13)
which is part of this thread :
[http://www.ubuntuforums.org/showthread.php?t=213694](http://www.ubuntuforums.org/showthread.php?t=213694)

But if you just like tweaking : here we go :).

If you have on average a lot of memory free (or used for cache) you probably want to prevent your system to start swapping. This is done by setting vm.swappiness to 0. In my personal experiences this is what you want for Xubuntu with 512 mb of memory or more and for Ubuntu (gnome) with more than 512 mb of memory.

$sudo sysctl vm.swappiness=0
sets your swappiness variable to 0
To get turn your swap off (and get everything which is needed back into memory)
$sudo swapoff -a
To turn it back on (being empty and it should stay almost empty because of vm.swappiness=0)
$sudo swapon -a

If you like your new settings you can make it more permanent by adding this line :
```

vm.swappiness=0

```

to /etc/sysctl.conf by using your favorite editor :
$sudo gedit /etc/sysctl.conf

After reboot vm.swappiness is 0

Additional information :

In my case I have 1 gb of memory and a large part isn't used (or only used for cache) I choose to prevent swapping as much as possible by vm.swappiness=0. For 512 mb of memory this is also the best setting if you use xubuntu and be careful (about not using too much memory).

This was the best setting for laptop with only 64 mb of memory running icewm / fluxbox : vm.swappiness=100. Because with that amount of memory swapping is needed anyway so better to do it as soon as possible.

In cases between 128 mb and 512 mb of memory you need to try and tweak and find out what works best for you. You can use "$free -m" to see whether swap is used.

-If you (almost) succeed in not using swap at all then set vm.swappiness to 0

-if your computer still needs to swap much set vm.swappiness to 100

-if you have little memory and don't notice any difference go for vm.swappiness=60

You can find more information about "free -m" and swappiness here : [http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

### Post by ubuntu_demon on 2006-07-14
I added a blog entry about performance tweaks right here :
[http://ubuntudemon.wordpress.com/2006/07/14/desktop-performance-tweaks/](http://ubuntudemon.wordpress.com/2006/07/14/desktop-performance-tweaks/)

---

### Post by mrbaz on 2006-07-18
.folder

---

### Post by ubuntu_demon on 2006-07-23
digg my blog entry :
[http://digg.com/linux_unix/Ubuntu_Desktop_performance_tweaks](http://digg.com/linux_unix/Ubuntu_Desktop_performance_tweaks)

---

### Post by ago on 2006-07-24
> **Rui Pais said:**
> Hi,
i tried this, but some scripts fails or output errors like:

That's because some scripts are not Posix compliant (dash is). The scripts should be fixed, there is nothing wrong with dash, other than it is lighter and faster and therefore better suited as /bin/sh...

Anyway dash is going to be the default /bin/sh in Edgy (not login shell though, I persoanlly like zsh for that)...

---

### Post by takayuki on 2006-08-12
newbie here with an AMD duron processor.  if i do a "sudo apt-get install linux-k7 linux-headers-k7", is there any way this will mess up my current xfce system?

how noticable is the speed improvement over the standard headers?

thanks,

takayuki

---

### Post by ubuntu_demon on 2006-08-12
> **takayuki said:**
> newbie here with an AMD duron processor.  if i do a "sudo apt-get install linux-k7 linux-headers-k7", is there any way this will mess up my current xfce system?

how noticable is the speed improvement over the standard headers?

thanks,

takayuki

There's a noticable difference between linux-386 and linux-686 (especially if your processor supports SMP).

I don't know how big the difference wil be on your machine. This can't mess up your system. You should try it.

---

### Post by klabelkholosh on 2006-08-21
Hi, a question.. I just upgraded to the AMD-optimized kernel with "sudo aptitude install linux-k7" but after rebooting, the Software Updates panel wants to install:
  linux-image-2.6.15-26-386
  linux-image-386
  linux-restricted-modules-2.6.15-26-386
  linux-restricted-modules-386

I'm guessing this shouldn't be as I have an AMD chip? Is this normal or is there any way to tell dapper to stop asking me to install these guys? :)

---

### Post by jimmygoon on 2006-08-21
> **ubuntu_demon said:**
> There's a noticable difference between linux-386 and linux-686 (especially if your processor supports SMP).

I don't know how big the difference wil be on your machine. This can't mess up your system. You should try it.

I've had linux-686 randomly mess up my friend's pc to the point where it wouldn't make it through the boot up procedure and we had to choose 386 in grub and then remove linux-686... oh well...

---

### Post by dog on 2006-08-22
> **klabelkholosh said:**
> Hi, a question.. I just upgraded to the AMD-optimized kernel with "sudo aptitude install linux-k7" but after rebooting, the Software Updates panel wants to install:
  linux-image-2.6.15-26-386
  linux-image-386
  linux-restricted-modules-2.6.15-26-386
  linux-restricted-modules-386

I'm guessing this shouldn't be as I have an AMD chip? Is this normal or is there any way to tell dapper to stop asking me to install these guys? :)

When you upgrade to a new kernel, you haven't deleted the old (386) versions - thet are still on your computer so updates will be broadcast for them. If you are happy with the k7 versions then:
sudo apt-get remove linux-386
should delete them

---

### Post by klabelkholosh on 2006-08-23
Hey thanks dog! :) that seems to have fixed it.

---

### Post by VCSkier on 2006-08-26
first of all, thanks for the great advice and links.  i'm excited about getting all of these up and running.  i've got a couple simple questions though, because i'm a slow learner...

first of all, what would be the proper/ideal way to use xfce.  would it be beneficial simply to install the xfce package on my current ubuntu (gnome) setup, or to reap the benefits, would i need to start w/ a clean xubuntu setup/install?

secondly, i have no idea what video card drivers i am using, nor do i know how to check.  my laptop houses a 2-3 year old ati radeon mobility (9000, i think).  i have done nothing to install drivers of any sort beyond the default install process.  how should i go about checking to see if i have the proper/latest drivers installed?

again, thanks!

---

### Post by Cubiq on 2006-08-29
sorry if I'm a little off-topic... I finally installed xgl+compiz and to my great surprise gnome is now faster. Is anyone else experiencing better performance after installing xgl+compiz?

---

### Post by sumadartson on 2006-08-29
> **Cubiq said:**
> sorry if I'm a little off-topic... I finally installed xgl+compiz and to my great surprise gnome is now faster. Is anyone else experiencing better performance after installing xgl+compiz?

Of course. You're no longer hogging the processor for your basic graphic needs, everything is done using your graphics card, which would otherwise just be bored out of its skull. The effect is especially noticeably if you turn off a lot of the effects from Compiz.

---

### Post by Cubiq on 2006-08-29
> **sumadartson said:**
> Of course. You're no longer hogging the processor for your basic graphic needs, everything is done using your graphics card, which would otherwise just be bored out of its skull. The effect is especially noticeably if you turn off a lot of the effects from Compiz.

Impressive, I thought that compiz would have killed my gnome, instead it seems that the GPU can easily handle the whole desktop on its shoulders ;) I think that a note to xgl+compiz should be added in the first post as an optimization tip (if your gpu can handle it).

---

### Post by DMAthlon on 2006-08-29
WOW! i actually noticed a difference! thanks!!!

---

### Post by Metacarpal on 2006-08-30
> **Cubiq said:**
> Impressive, I thought that compiz would have killed my gnome, instead it seems that the GPU can easily handle the whole desktop on its shoulders ;) I think that a note to xgl+compiz should be added in the first post as an optimization tip (if your gpu can handle it).

That raises a question I've had - what are the sys requirements for xgl/compiz?

---

### Post by ~LoKe on 2006-08-30
> **Cubiq said:**
> Impressive, I thought that compiz would have killed my gnome, instead it seems that the GPU can easily handle the whole desktop on its shoulders ;) I think that a note to xgl+compiz should be added in the first post as an optimization tip (if your gpu can handle it).

If I recall correctly, XGL was intended to boost performance.  Compiz is just some nice eye candy that works off of it.

---

### Post by ShagzModo on 2006-08-30
I am running Xubuntu on a laptop with 128MB of RAM memory...
It runs great.... the only thing i miss is a nice signal strenght indicator for my network connection that is installed with the GNOME desktop environment. I would always recommand giving xubuntu a try. I have it installed after i installed the regular GNOME Ubuntu, so i can choose to switch sessions. Picasa and other memory consuming apps run fine...

all the best

---

### Post by shunthemask on 2006-08-30
I don't know about anybody else, but compiz threw me into dependency hell.  XGl, on the other hand, makes my system much, much faster as well as xfce (which I also installed after the normal ubuntu install, so I could switch sessions if necessary).

---

### Post by VCSkier on 2006-11-02
How can this thread be updated for edgy?  What here is obsolete and what is still applicable.  Is there anything that could be added now?

By the way, this thread has been very valuable to me.  Thanks!

---

### Post by goldenatom on 2006-11-03
I think they all still apply. I haven't tried the XML optimizations though. I'm not sure that messing around with Init is really needed anymore either.

---

### Post by civilian on 2006-11-18
Sweet great links, I had been looking for different guides to optimize my system.

---

### Post by flameproof on 2006-11-21
do those tips also apply for 6.10 Edgy?

---

### Post by GaryAndersonMissed on 2007-01-02
Thanks for the suggestions and all the comments in this thread.  I used the ati dapper wiki [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.29.6_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.29.6_drivers_in_Ubuntu_Dapper_Manually) to update my video driver, and am now using the kernel that is correct for my machine.  The ubuntu community is AWESOME!

---

### Post by Lucifiel on 2007-04-14
Thank you for the suggestions in this thread. :) 

I'm currently trying to figure out how to use InitNG and hopefully, things will go smoothly. :)

---

### Post by neoaddict on 2007-04-14
As far as I know, development on InitNG has stopped and Upstart is the better alternative, and it is implemented by default in Edgy and Feisty.

---

### Post by Lucifiel on 2007-04-15
> **neoaddict said:**
> As far as I know, development on InitNG has stopped and Upstart is the better alternative, and it is implemented by default in Edgy and Feisty.

Oohhh... all right, man! :) 

Still, I've only managed to shave off 10 seconds and my boot-time is around 1 minute. WindowsXP , in comparison, takes between 20 to 30 seconds only.

---

### Post by gijsterbeek on 2007-04-18
I just *removed* readahead as well as preload from my Kubuntu 6.10 box. Strangely, this reduced my boottime from 1:11 with readahead enabled to 0:51 without it. 

So I guess Edgy with Upstart doesn't benefit by readahead. On the other hand, It could be that my box doesn't have enough I/O speed to make readahead worthwile. I run Kubuntu on a AMD Athlon 1.2 GHz processor, with 786 MB of RAM.

---

### Post by shawnrgr on 2007-04-24
How do these tips work with feisty?

---

### Post by Seisen on 2007-04-26
I'm trying them right now and I will let you know.

---

### Post by shawnrgr on 2007-04-28
bump

---

### Post by Metacarpal on 2007-04-29
> **Seisen said:**
> I'm trying them right now and I will let you know.

Let's just hope the utter silence after this post isn't an indication that Seisen destroyed his system with these tweaks. ;)

---

### Post by mgigirey on 2007-05-12
Check also this about swappiness [www.serbuntu.net/ubuntu/tips/swappiness]("www.serbuntu.net/ubuntu/tips/swappiness")

---

### Post by Shpongled303 on 2007-07-19
> **itomeshi said:**
> Set number of undo steps to 30-40 max, have it use 64MB or more (128, if your system can afford it (at least 512mb total ram) helps greatly), boost memory per object to 5.0 MB.

Thanks so much, I never knew it set the RAM usage so low... Wow.

This was very helpful, love this website. :D

---

### Post by Quintin Riis on 2007-07-28
> **ShagzModo said:**
> I am running Xubuntu on a laptop with 128MB of RAM memory...
It runs great.... the only thing i miss is a nice signal strenght indicator for my network connection that is installed with the GNOME desktop environment. ...$ sudo apt-get install nm-applet ; nm-applet

---

### Post by janz84 on 2008-05-19
I think the tweak is not so great:

> jkz@jkz-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3884       3852         31          0         55       2947
-/+ buffers/cache:        849       3034
Swap:         6236          0       6236


---

### Post by srigelsford on 2008-07-18
> **sejjiin said:**
> Hi, I'm brand new to linux, running xubuntu.

Does installing the Pentium kernel files also speed up Celeron systems or is there another package like this for Celerons?  Mine is 450 and based on Pentium 2/3 (don't know which).

Seperate question - why does doing this cause amaroK to not slow down the system?  Won't it still have to install KDE packages?

Hi, I have trawled Google to no avail. I am running Intel Centrino Duo. Which kernel should I be installing? 
Currently running Hardy 2.6.24-19-generic


Thanks.

---

### Post by VCSkier on 2008-07-19
I seem to recall reading somewhere that installing the processor-class-specific-kernels is no longer helpful; I believe they patch the generic kernel to work optimally on all compatible processors.

---

### Post by Quintin Riis on 2008-07-19
> **janz84 said:**
> I think the tweak is not so great:Why do you paste output of free -m?

---

### Post by jpeddicord on 2008-08-13
Moved to Outdated. Many things/links here are not relevant to current versions of Ubuntu, so do anything listed with extreme caution.

---

### Post by Izek on 2008-10-30
> **jacobmp92 said:**
> Moved to Outdated. Many things/links here are not relevant to current versions of Ubuntu, so do anything listed with extreme caution.

You mean like DMA? (since dev/hdc doesn't exist for me?)

---

### Post by lawalsulaiman on 2008-12-04
Hi all,
pls. I want to install and configure cache_manager, squid guard and Danguardian on Ubuntu 8.04 desktop version. pls. I need a relevant document on how to achieve that.

thanks.

Lawal Sulaiman
UDU, Sokoto
Nigeria

---

### Post by HotShotDJ on 2008-12-04
SquidGuard: [https://help.ubuntu.com/community/SquidGuard](https://help.ubuntu.com/community/SquidGuard)
DansGuardian: [https://help.ubuntu.com/community/Servers/DansGuardian](https://help.ubuntu.com/community/Servers/DansGuardian)
Cache Manager:  Isn't that part of Squid? See SquidGuard above.

(I didn't realize that this was an out-of-date thread.  lawalsulaiman, for future, you should start your own thread for support rather than appending a thread with a completely different topic)

---

### Post by dannytatom on 2008-12-05
I just installed preload, is it still usefull or should I just get rid of it? ;o

---

### Post by adambh on 2009-04-06
> **itomeshi said:**
> Why not just tweak OpenOffice? The default memory management settings literally throttle OpenOffice into oblivion.

Open up writer, and go to Tools > Options. Go to memory in the sidebar.

Set number of undo steps to 30-40 max, have it use 64MB or more (128, if your system can afford it (at least 512mb total ram) helps greatly), boost memory per object to 5.0 MB.

Need a visual example? Try [http://openoffice.blogs.com/openoffice/memory/index.html]("http://openoffice.blogs.com/openoffice/memory/index.html"), which I found via Google.

I wouldn't do the JRE trick that page mentions unless you REALLY never use those aspects. Still, the memory tweak alone is an impressive boost.


I adjusted the memory, it more than halved the time OO takes to load, brilliant!

---

### Post by kpkeerthi on 2009-04-07
> **dannytatom said:**
> I just installed preload, is it still usefull or should I just get rid of it? ;o

preload is not required. The kernel does it already (buffers and caches)

---

### Post by Grievous on 2009-04-12
Doing some of the steps now.  :guitar:

---

### Post by archolman on 2009-04-12
[SIZE=3]
itomeshi & adambh

 Just tried the OpenOffice tweaks, & set the  systray starter, & it opens as slick as you like!

Thanks, [/SIZE][SIZE=3]             [/SIZE][SIZE=3]:lolflag:[/SIZE]

---

### Post by n8bounds on 2009-07-16
[IMG]http://wackyiraqi.com/wtf/i_support_this_post.jpg[/IMG]

---

### Post by weishigoname on 2010-03-11
thanks

---

### Post by andso on 2010-07-17
and the file /etc/hosts
a french discussion for example:
[http://forum.ubuntu-fr.org/viewtopic.php?id=241092](http://forum.ubuntu-fr.org/viewtopic.php?id=241092)
that's sometimes incredible

---

### Post by karthibala on 2010-07-26
thanks for your awesome information about improving performance ubuntu.its a good post.its great and working good.








-------------------------------------------
[Restaurants in Kanyakumar]("http://www.sangamgrouphotels.com")

---

### Post by Goolie on 2010-07-26
bookmarked, thx OP =D

---

