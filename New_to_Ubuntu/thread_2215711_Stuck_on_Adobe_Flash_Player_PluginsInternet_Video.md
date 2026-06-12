---
title: "Stuck on Adobe Flash Player Plugins/Internet Video"
date: 2014-04-08
forum: New to Ubuntu
---

### Post by elvis6 on 2014-04-08
I just installed Xubuntu, and for an entire day I have been attempting to get it to play streaming video online.
I have searched Google, Ask Ubuntu, Firefox Forums, Firefox Help, Adobe Sites, and find a lot of suggestions, and have tried virtually all of them, but nothing has worked. It amazes me, after searching, that there could be so many possible answers to one simple problem, based on so many people's suggestions. The most common suggestion is to get the tar.gz file and move it into the plugins folder. But that hasn't helped. Then I found out there's a whole archive of about 100 old versions of plug-ins, any of which could be the answer, and I have no idea which one to get.
I am a complete beginner on Ubuntu/Xubuntu, and hardly understand the Terminal language, and thoroughly confused.
If someone does not type out the _**exact **_commands for me, I am completely lost.
Too often, people imply the commands, and that doesn't help me. I need to know the exact commands.
Could someone please help me troubleshoot why my video/flash plugins don't seem to work.

---

### Post by blm-ubunet on 2014-04-08
IMO try to avoid flash when/where possible.
- install html5 player plugin for firefox (use the add-ons menu tools/add-ons) "YouTube ALL HTML5"
- opt into the html5 trial on youtube (just search for this page)

- install firefox add-on "FlashVideoReplacer"

This will not solve all the flash problems..

The adobe flash plug is "non-free" (free==FOSS free open source s/w) & is deprecated for linux..
The plug-in downloader/installer (flashplugin-installer) could still be install-able via synaptic package manager..it is for 12.04.
You have to select one of the extra multiverse repositories..

---

### Post by monkeybrain20122 on 2014-04-08
> **elvis6 said:**
> 
The most common suggestion is to get the tar.gz file and move it into the plugins folder. .

What???!!! I am wondering where did you find your advice. :) All you need to do is to install xubuntu-restricted-extras from synaptic (in the menu under System or something like that, it is the package manager), it will install flash and other media codecs.

---

### Post by monkeybrain20122 on 2014-04-08
> **blm-ubunet said:**
> 
- install firefox add-on "FlashVideoReplacer"


?? :confused: Which versions of Ubuntu and Firefox are you on and when was the last time you installed FlashVideoReplacer? That add-on has been removed by its developer more than two years ago.

There are however two greasemonkey scripts that do much the same as FVR 
[http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011)
[http://linternamagica.org/](http://linternamagica.org/)

> The plug-in downloader/installer (flashplugin-installer) could still be  install-able via synaptic package manager..it is for 12.04
Wrong. flash 11.2 will not get further version update, but it is still supported with security updates til 2017 and is installable in Ubuntu 13.10 and 14.04. It still works for most flash sites and definitely works on Youtube (Chrome has the latest flash bundled with it if that is required on rare occasions)

---

### Post by WogBoy on 2014-04-08
> What???!!! I am wondering where did you find your advice.

Yes I was given the same advice on another forum ( Mainly Windows), Download the flash player, Unrar it then copy the libflashplayer.so to the mozilla/plugins folder overwriting the old one..

---

### Post by monkeybrain20122 on 2014-04-08
> **WogBoy said:**
> Yes I was given the same advice on another forum ( Mainly Windows), Download the flash player, Unrar it then copy the libflashplayer.so to the mozilla/plugins folder overwriting the old one..

Well Windows is not the same as Linux. Why did you go to Windows forums for xubuntu advice? :)

---

### Post by su:bhatta on 2014-04-08
All you need to do is get the ubuntu-restricted-extras package, as pointed out by monkeybrain.

You can use Software-Center to get it, Synaptic to get it or if you are not afraid of Terminal

Just do:

> sudo apt-get install ubuntu-restricted-extras

If you want the latest Flash Player you will have to use Google Chrome Browser as Flash Player is not Updated since version 11.2 in Linux.
Chrome comes with its own latest Flash Player bundled.

Go to chrome site and download Chrome for Linux and install it using Software-Center.
Thats the easiest way.

---

### Post by carl4926 on 2014-04-08
> **bhattabhishek said:**
> All you need to do is get the ubuntu-restricted-extras package, as pointed out by monkeybrain.

You can use Software-Center to get it, Synaptic to get it or if you are not afraid of Terminal

Just do:



If you want the latest Flash Player you will have to use Google Chrome Browser as Flash Player is not Updated since version 11.2 in Linux.
Chrome comes with its own latest Flash Player bundled.

Go to chrome site and download Chrome for Linux and install it using Software-Center.
Thats the easiest way.

Even
```
sudo apt-get install xubuntu-restricted-extras
```

It's possible of course, that the OP is using an old machine that doesn't have CPU support for flash above version 10.3

---

### Post by JeQhdMD on 2014-04-08
Hopefully, you can undo any modifications you've already made to Xubuntu, including deleting the tar.gz file.   You shouldn't need to do ANY terminal commands.   Just go to the Ubuntu Software Center and search for "restricted-extras", and click on the install button.  Then you can use Firefox to view and stream media.  Super simple.   NO need at all for the terminal.

---

### Post by WogBoy on 2014-04-08
> Well Windows is not the same as Linux. Why did you go to Windows forums for xubuntu advice?

I am here now aint I lol. I was a member and they had a *comprehensive Linux section. *

---

### Post by blm-ubunet on 2014-04-08
@monkeybrain
> Wrong. flash 11.2 will not get further version update, but it ... 
What was wrong about stating that the flash plugin installer can still be installed via synaptic?

This is still the best advice:
> IMO try to avoid flash when/where possible.
- install html5 player plugin for firefox (use the add-ons menu tools/add-ons) "YouTube ALL HTML5"
- opt into the html5 trial on youtube (just search for this page)

---

### Post by kurt18947 on 2014-04-08
> **blm-ubunet said:**
> 

This is still the best advice:
                                                         IMO try to avoid flash when/where possible.
- install html5 player plugin for firefox (use the add-ons menu tools/add-ons) "YouTube ALL HTML5"
- opt into the html5 trial on youtube (just search for this page) 

Unfortunately there are useful (non-'adult') web sites with useful videos such as crafts tutorials that use flash.  If small sites with limited resources have something that mostly works, they're usually not in a hurry to re-do it.

---

### Post by elvis6 on 2014-04-08
I completely re-installed Xubuntu 13.10 in order to un-do any changes I made to the system, during my attempts to fix it, that may have been detrimental.
So after a clean re-install and a clean slate, I installed Xubuntu Restricted Extras through the software center. It told me that I needed to remove a couple Libav progams before I could install it, which I did. Then when I removed the 2 Libav programs, it told me I needed to remove some more programs, which I did.
So, after installing the Xubuntu Restricted Extras, it still did not work.
Then I installed the Youtube HTML5, and that did not work either.
I also tried the Flash Video Replacer, to no avail.
ALso, prior to installing the full Xubuntu version, I installed Xubuntu alongside Windows, as a dual/tryout period.
The video streaming worked then (but not now - in the "full version", so I don't think it's my PC, even though it is an older PC.
What else could it be ?

---

### Post by carl4926 on 2014-04-08
Post the result of

```
cat /proc/cpuinfo
```

---

### Post by sudodus on 2014-04-08
I am surprised that you had to uninstall the libav packages. Maybe you need to update/upgrade your system. Try the commands according to this list (originally by *oldfred*).

```
# This will reinstall if not current. (from my chroot procedure which does not have sudo on every line,
# so use the sudo -i first).
 
#if not chroot use: sudo -i

#houseclean
apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean

#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first

#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade

# fix Broken packages -f 
sudo apt-get -f install
dpkg --configure -a
```

If you remember which ***libav*** packages you removed, try to install them again (There are a lot available for installation, see this list (in 12.04))

```
libavahi1.0-cil               libavahi-ui-cil-dev           libavfilter2
libavahi-cil-dev              libavahi-ui-dev               libavfilter-dev
libavahi-client3              libavahi-ui-gtk3-0            libavfilter-extra-2
libavahi-client-dev           libavahi-ui-gtk3-dev          libavformat52
libavahi-common3              libavalon-framework-java      libavformat53
libavahi-common-data          libavalon-framework-java-doc  libavformat-dev
libavahi-common-dev           libavbin0                     libavformat-extra-53
libavahi-compat-libdnssd1     libavbin-dev                  libavidemux0
libavahi-compat-libdnssd-dev  libavc1394-0                  libavifile-0.7c2
libavahi-core6                libavc1394-dev                libavifile-0.7-dev
libavahi-core7                libavcodec52                  libavl1
libavahi-core-dev             libavcodec53                  libavl-dev
libavahi-glib1                libavcodec-dev                libavogadro1
libavahi-glib-dev             libavcodec-extra-53           libavogadro-dev
libavahi-gobject0             libav-dbg                     libav-source
libavahi-gobject-dev          libavdevice52                 libav-tools
libavahi-qt3-1                libavdevice53                 libavutil49
libavahi-qt4-1                libavdevice-dev               libavutil51
libavahi-qt4-dev              libavdevice-extra-53          libavutil-dev
libavahi-ui0                  libav-doc                     libavutil-extra-51
libavahi-ui0.0-cil            libavfilter0                  

```

---

### Post by sudodus on 2014-04-08
> **carl4926 said:**
> Post the result of

```
cat /proc/cpuinfo
```
+1

We need that information to give relevant help.

---

### Post by monkeybrain20122 on 2014-04-08
> **sudodus said:**
> I am surprised that you had to uninstall the libav packages. Maybe you need to update/upgrade your system. Try the commands according to this list


Installing restricted-extras removes the stripped libav packages and replaces them with the non stripped ones, so it would remove libavcodec53 and install libavcodec-extra-53 etc. It is the desired outcome, no cause for alarm.

---

### Post by sudodus on 2014-04-08
> **monkeybrain20122 said:**
> Installing restricted-extras removes the stripped libav packages and replaces them with the non stripped ones, so it would remove libavcodec53 and install libavcodec-extra-53 etc. It is the desired outcome, no cause for alarm.

Thank you for this information :-)

---

### Post by monkeybrain20122 on 2014-04-08
> **elvis6 said:**
> I completely re-installed Xubuntu 13.10 in order to un-do any changes I made to the system, during my attempts to fix it, that may have been detrimental.
So after a clean re-install and a clean slate, I installed Xubuntu Restricted Extras through the software center. It told me that I needed to remove a couple Libav progams before I could install it, which I did. Then when I removed the 2 Libav programs, it told me I needed to remove some more programs, which I did.
So, after installing the Xubuntu Restricted Extras, it still did not work.
Then I installed the Youtube HTML5, and that did not work either.
I also tried the Flash Video Replacer, to no avail.
ALso, prior to installing the full Xubuntu version, I installed Xubuntu alongside Windows, as a dual/tryout period.
The video streaming worked then (but not now - in the "full version", so I don't think it's my PC, even though it is an older PC.
What else could it be ?

Just to make sure that you have flash installed, can you open Firefox, from the menu go to Tools > Addons > Plugins and see that there is an entry for Shockwave flash and that it is activated?

YoutubeALlHTML5(the addon) will not work for 'all'  Youtube videos unless you disable flash completely (so it should work in case flash is set to 'never activated' in Firefox). As noted, there is no such thing as FlashVideoReplacer, it has discontinued more than 2 years ago, whatever you dug up from old archives is guaranteed not to work since Youtube has changed so much.

If flash worked when you dual booted with Windows that doesn't sound like a hardware problem. But are you sure that you were streaming with flash? Many Youtube videos,--not all,-- will work without flash, html5 would automatically kick in if it detects that flash is absent or disabled, you no longer have to 'opt in' to some html5 test, that info is as outdated as the FlashVideoReplacer. Since you didn't know about restricted extras how did you install flash when you dual booted? You might have been streaming with html5 all along.

---

### Post by elvis6 on 2014-04-08
> **carl4926 said:**
> Post the result of

```
cat /proc/cpuinfo
```

cpu family    : 15
model        : 4
model name    : Intel(R) Celeron(R) CPU 2.80GHz
stepping    : 1
microcode    : 0xd
cpu MHz        : 2792.875
cache size    : 256 KB
fdiv_bug    : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
bogomips    : 5585.75
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 32 bits virtual
power management:

> **monkeybrain20122 said:**
> Just to make sure that you have flash  installed, can you open Firefox, from the menu go to Tools > Addons  > Plugins and see that there is an entry for Shockwave flash and that  it is activated?

If flash worked when you dual booted with Windows that doesn't sound  like a hardware problem. But are you sure that you were streaming with  flash? Since you didn't know about  restricted extras how did you install flash when you dual booted? You  might have been streaming with html5 all along.

I did go to Tools-Addons-Plugins, and it notes Shockwave Flash 11.2.202.346 is up to date. And the "status" next to it says "Always Activate".
Regarding when I dual booted with Windows, I actually had the same problem originally. And I just started randomly trying suggestions I found all over the internet and forums, and I'm not sure which one worked. I don't know for sure it was flash, although I'm pretty sure, because those were the files I was mainly targeting - because often I would go to a site, and it would tell me I'd need to go to the Adobe site to download the flash plugin. I'd then go there and there was 4 options for Linux systems. I tried all 4, but all I did was download and extract them - not install them, because I could not find an installation or exe file in the folder.
So, I have no idea how it worked the first time, but it does show that it's possible on my PC apparently.

I also tried the Greasemonkey and LinternaMagica suggested in this thread, and they did not work.
All it did, was say that the youtube video is "waiting for plugin to load", but it never moves on from that status, and never plays.

---

### Post by sudodus on 2014-04-08
The CPU is OK, it should work with a current linux system.

---

### Post by mörgæs on 2014-04-08
Yes, it works but it's not strong. Celerons are choked-down Pentiums, and this one is about 10 years old. 

Celerons (and Pentiums) from that age are often accompanied by Intel 8xx chipsets which need special attention.

I think we would like the full hardware specifications. Please run
```
sudo lshw -sanitize > lshw.txt
```
and post lshw.txt in CODE tags.

---

### Post by elvis6 on 2014-04-08
> **mörgæs said:**
> Yes, it works but it's not strong. Celerons are choked-down Pentiums, and this one is about 10 years old. 

Celerons (and Pentiums) from that age are often accompanied by Intel 8xx chipsets which need special attention.

I think we would like the full hardware specifications. Please run
```
sudo lshw -sanitize > lshw.txt
```
and post lshw.txt in CODE tags.

When I type that in, it just says ```
PCI (sysfs)
``` for about 15 seconds, then flashes back to the command line.

---

### Post by elvis6 on 2014-04-08
I just had an idea, but I need help in applying it.
I have another PC, in which I installed the dual Windows & Xubuntu. And the video works perfectly on that, just like it did on this PC, when it ran on the dual Windows & Xubuntu. It wasn't until I switched from the dual OS on this PC, to replacing Windows completely with Xubuntu, that I started having major video issues.
Apparently, there is some software difference between the Xubuntu that runs dual with Windows, than there is when it's the exclusive OS. I know that, not just from experience with the videos, but just a general visual glance tells me there's software differences.
So, my question is, whether there is some kind of comparison or troubleshooting I can do, to see what the Xubuntu software has, or does not have, on the "working" system, that's different on the PC that doesn't work, to determine what is the difference that is the root cause of not playing videos on the one PC ?

Okay, I just checked the versions - and the PC with the dual OS's that's playing videos correctly, has Xubuntu version 12.04.4. While the PC that is running solely on Xubuntu, which the vids do NOT play on, is Xubuntu version 13.10
So, the older version is actually running better than the newer, as far as vids go

---

### Post by monkeybrain20122 on 2014-04-08
You can try this, first disable greasemonkey, close Firefox, then relaunch firefox from the terminal by just open the terminal and type 
```
firefox
```
Then go to a Youtube video that DOES NOT work with html5, e.g [http://www.youtube.com/watch?v=3nmnMtbzzjE](http://www.youtube.com/watch?v=3nmnMtbzzjE)
Now wait a little, if flash doesn't work, close Firefox, copy the error messages from the terminal and paste them here, maybe someone knowledgeable can tell you what happens.

---

### Post by carl4926 on 2014-04-08
> [COLOR=#000000]Apparently, there is some software difference between the Xubuntu that runs dual with Windows, than there is when it's the exclusive OS[/COLOR]NO No

> [COLOR=#000000]I just checked the versions - and the PC with the dual OS's that's playing videos correctly, has Xubuntu version 12.04.4. While the PC that is running solely on Xubuntu, which the vids do NOT play on, is Xubuntu version 13.10[/COLOR]This does matter

---

### Post by sudodus on 2014-04-09
> **elvis6 said:**
> ...
Okay, I just checked the versions - and the PC with the dual OS's that's playing videos correctly, has Xubuntu version 12.04.4. While the PC that is running solely on Xubuntu, which the vids do NOT play on, is Xubuntu version 13.10
So, the older version is actually running better than the newer, as far as vids go

Xubuntu 12.04.4 is the well debugged and polished long time support version (LTS), and it will be supported until April 2015 (one more year). At that time I think the new LTS version, 14.04 (to be released very soon) will be well debugged and polished.

---

### Post by monkeybrain20122 on 2014-04-09
> **sudodus said:**
> Xubuntu 12.04.4 is the well debugged and polished long time support version (LTS), and it will be supported until April 2015 (one more year). At that time I think the new LTS version, 14.04 (to be released very soon) will be well debugged and polished.

 I don't find 12.04 more polished or less buggy than 13.04 or 13.10. Not sure about xubuntu but if you use Ubuntu unity 7 is much better optimized and faster in Ubuntu 13.04 and 13.10 than unity5 in 12.04. My guess is that OP's problem could be due to incompatinility between new kernel and very old hardware, in that case it has nothing to do with bugs in 13.10.

P.S. Ubuntu 12.04 LTS is supported til 2017 (5 yrs), not sure about xubuntu but I think it should be the same. 12.04 is already old now, I cannot contemplate using it for another 3 years, I couldn't care less whether terribly outdated software is "supported" or not. But that is just me.:)

---

### Post by mörgæs on 2014-04-09
> **monkeybrain20122 said:**
> I don't find 12.04 more polished or less buggy than 13.04 or 13.10. Not sure about xubuntu but if you use Ubuntu unity 7 is much better optimized and faster in Ubuntu 13.04 and 13.10 than unity5 in 12.04. My guess is that OP's problem could be due to incompatinility between new kernel and very old hardware, in that case it has nothing to do with bugs in 13.10.



+1.
Elvis, we need the two outputs (that is, *files located in your home folder*) from lshw.

---

### Post by su:bhatta on 2014-04-09
> **monkeybrain20122 said:**
> 
P.S. Ubuntu 12.04 LTS is supported til 2017 (5 yrs), not sure about xubuntu but I think it should be the same. 12.04 is already old now, I cannot contemplate using it for another 3 years,

Xubuntu 12.04 is supported for 3 years only and will reach EOL in 2015.
The upcoming Xubuntu, Ubuntu Gnome, Lubuntu 14.04 LTS will reach EOL in 3 years too.

Refer: [http://xubuntu.org/news/12-04-release/](http://xubuntu.org/news/12-04-release/)

---

### Post by elvis6 on 2014-04-09
> **mörgæs said:**
> +1.
Elvis, we need the two outputs (that is, *files located in your home folder*) from lshw.

I'm sorry, I'm not understanding the "lshw" terminology. 
Is lshw the name of a subfolder, in my home folder ?

---

### Post by Coolgirl on 2014-04-09
google crome has some good players to play through that might avoid this problem.. hope this helps , thanks

---

### Post by Impavidus on 2014-04-09
> **elvis6 said:**
> 
```
sudo lshw -sanitize > lshw.txt
```
When I type that in, it just says ```
PCI (sysfs)
``` for about 15 seconds, then flashes back to the command line.
Indeed, but it also produced a file named lshw.txt, located in your home directory (~, also known as /home/yourusername). Post that file. The > is a shell redirect, sending the output to a file instead of the terminal.

---

### Post by elvis6 on 2014-04-10
> **Impavidus said:**
> Indeed, but it also produced a file named lshw.txt, located in your home directory (~, also known as /home/yourusername). Post that file. The > is a shell redirect, sending the output to a file instead of the terminal.

I see it now. Do you mean open the file, and copy and paste the whole thing ?
 Or attach the file ?
Also, I noticed something else. A strangely-named folder, not a file - but a folder, seemed to appear suddenly out of nowhere, inside my home folder. It happened around the time I typed that command, and wondered if it means anything. The folder is called : lIA_vUCOUV

---

### Post by sudodus on 2014-04-10
You can do either of it. But if you copy and paste, please put it within code tags!

Go Advanced, mark the whole batch of text from lshw, click on the # icon at the top of the editing window. Afterwards it should look like this
 
[noparse]```
output
```[/noparse]
 
to get output like this
 
```
output
```

---

### Post by sudodus on 2014-04-10
I don't know about that folder, but the name seems to be generated automatically (like a temporary folder). Check what it contains!

---

### Post by elvis6 on 2014-04-12
I have seemingly solved this problem, by replacing version 13.10, with version 12.04.4, which I just finished installing.
The video/flash seems to be working properly, and better for me, with the older system, actually.
Thanks everyone for all the good and helpful suggestions. I learned a lot, and I'm sure they will come handy in the future.

---

