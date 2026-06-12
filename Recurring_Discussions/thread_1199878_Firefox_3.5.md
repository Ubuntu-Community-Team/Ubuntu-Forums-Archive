---
title: "Firefox 3.5"
date: 2009-06-29
forum: Recurring Discussions
---

### Post by samh785 on 2009-06-29
Will the repositories update the version of firefox on my computer when 3.5 is released tomorrow?

---

### Post by WRDN on 2009-06-29
Providing the package is in the repositories, then you will be notified of the update by the Update Manager.

---

### Post by Irony on 2009-06-29
No.

Ubuntu is on a 6 month cycle - or a 3 year cycle if you are with LTS.

The reason for not immediately updating is that it allows the developers to test whether programs will actually work.

No doubt, when the time comes, instructions will appear on this forum for those who want to test 3.5.

---

### Post by Simian Man on 2009-06-29
Ubuntu usually doesn't bother to provide updates for new versions and features.  Only bugfixes are pushed through as updates.

---

### Post by cariboo on 2009-06-29
If you are running Jaunty, Firefox 3.5 has been in the repositories for quite a while.

---

### Post by XCan on 2009-06-29
Wouldn't Firefox get updated if the current version has some serious security flaws though?

---

### Post by philcamlin on 2009-06-29
> **XCan said:**
> Wouldn't Firefox get updated if the current version has some serious security flaws though?

yes because bugfixes are updates...

if its got issues their going to fix it not update it :popcorn:

---

### Post by scrooge_74 on 2009-06-29
Hum, I followed instructions here in the forum and I'm already using 3.5 with ubuntu 8.04

---

### Post by binbash on 2009-06-29
Firefox 3.5 3.6 daily PPA guide : 

[http://www.ubuntu-inside.me/2009/05/daily-firefox-35-36-repository-for.html](http://www.ubuntu-inside.me/2009/05/daily-firefox-35-36-repository-for.html)

---

### Post by XCan on 2009-06-29
> **philcamlin said:**
> yes because bugfixes are updates...

if its got issues their going to fix it not update it :popcorn:

True that. :) However, in my experience, packages aren't updated to fix only general bugs, they have to be security related.

---

### Post by xavierp94 on 2009-06-30
Firefox 3.5 is out!

---

### Post by haakon on 2009-06-30
> **Simian Man said:**
> Ubuntu usually doesn't bother to provide updates for new versions and features.  Only bugfixes are pushed through as updates.

An unfortunate way to put it, I think. It's not about not "bothering" (which sounds lazy and arbitrary), it's about a conscious distro policy.

---

### Post by StuM on 2009-06-30
> **cariboo907 said:**
> If you are running Jaunty, Firefox 3.5 has been in the repositories for quite a while.

The only Firefox-3.5 I can find in the repositories hasn't been updated since 3.5b4.  All of the Release Clients and todays offcial release haven't appeared.  The one in the repository also appears under its working name of Shiretoko.

I'd like to know what is the easiest way (for a relative linux newbie like myself) to install the latest 3.5 version, as available on the firefox site.

---

### Post by susanpenter on 2009-06-30
> **StuM said:**
> The only Firefox-3.5 I can find in the repositories hasn't been updated since 3.5b4.  All of the Release Clients and todays offcial release haven't appeared.  The one in the repository also appears under its working name of Shiretoko.

I'd like to know what is the easiest way (for a relative linux newbie like myself) to install the latest 3.5 version, as available on the firefox site.

This is a really good idea, could some experienced person provide a talk through on how to compile the file once it is downloaded.

Thanks

---

### Post by cozmicharlie on 2009-06-30
> **susanpenter said:**
> This is a really good idea, could some experienced person provide a talk through on how to compile the file once it is downloaded.

Thanks

It is very simple - download the tar file from here 
[http://download.mozilla.org/?product=firefox-3.5&os=linux&lang=en-US](http://download.mozilla.org/?product=firefox-3.5&os=linux&lang=en-US)

Follow these instructions 
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

Worked fine for me.  You don't have to uninstall the old version.  All the add-ons will be available in 3.5 if you follow the instructions.

Enjoy!

---

### Post by carml on 2009-06-30
Are you sure you need the latest version?
If so download it,extract it e.g. to your desktop or to your home directory,then open a terminal and type```
cd /TheDirectoryYouDecided/firefox
``` then type ```
sudo ./run-mozilla.sh
```. It should configure and install the software,I downloaded it,but I didn't install it now. ):P

---

### Post by Lasiaf on 2009-06-30
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)
worked for me
thanks coz

---

### Post by susanpenter on 2009-06-30
> **carml said:**
> Are you sure you need the latest version?
If so download it e.g. to your desktop or to your home directory,then open a terminal and type```
cd /TheDirectoryYouDecided
``` then type ```
sudo ./run-mozilla.sh
```. It should configure and install the software,I downloaded it,but I didn't install it now. ):P

I'm afraid it didn't work I just got an error code saying command not found.

---

### Post by xavierp94 on 2009-06-30
> **susanpenter said:**
> I'm afraid it didn't work I just got an error code saying command not found.

It should work unless you change the name of the folder that contains firefox.

---

### Post by kxmas on 2009-06-30
> **haakon said:**
> An unfortunate way to put it, I think. It's not about not "bothering" (which sounds lazy and arbitrary), it's about a conscious distro policy.


A conscious effort to not bother updating the firefox 3.5 package which is already in universe?  [http://packages.ubuntu.com/jaunty/firefox-3.5]("http://packages.ubuntu.com/jaunty/firefox-3.5")

I see no reason why they would not backport today's release.  I don't expect them to update to the firefox meta package to force an upgrade, but updating a package that currently exists seems reasonable.

---

### Post by tanha on 2009-06-30
> **cozmicharlie said:**
> It is very simple - download the tar file from here 
[http://download.mozilla.org/?product=firefox-3.5&os=linux&lang=en-US](http://download.mozilla.org/?product=firefox-3.5&os=linux&lang=en-US)

Follow these instructions 
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

Worked fine for me.  You don't have to uninstall the old version.  All the add-ons will be available in 3.5 if you follow the instructions.

Enjoy!

For those who followed this method, do your plugins, like flashplugin-nonfree, work?

---

### Post by Lasiaf on 2009-06-30
> **tanha said:**
> For those who followed this method, do your plugins, like flashplugin-nonfree, work?

mine worked

---

### Post by tanha on 2009-06-30
> **Lasiaf said:**
> mine worked

I followed the [manual method]("https://help.ubuntu.com/community/FirefoxNewVersion#Manual%20Install"). It "worked," but with exceptions: 1. "about:plugins" yeilds "No plugins are installed" 2. the following errors are produced when opening firefox > Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64

(firefox-bin:8569): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libnodoka.so: wrong ELF class: ELFCLASS64

(firefox-bin:8569): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libnodoka.so: wrong ELF class: ELFCLASS64
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
LoadPlugin: failed to initialize shared library /var/lib/flashplugin-installer/npwrapper.libflashplayer.so [/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-sun-1.6.0.13/jre/lib/amd64/libnpjp2.so [/usr/lib/jvm/java-6-sun-1.6.0.13/jre/lib/amd64/libnpjp2.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /var/lib/flashplugin-installer/npwrapper.libflashplayer.so [/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-cone-plugin.so [/usr/lib/totem/gstreamer/libtotem-cone-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-gmp-plugin.so [/usr/lib/totem/gstreamer/libtotem-gmp-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-mully-plugin.so [/usr/lib/totem/gstreamer/libtotem-mully-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so [/usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-sun-1.6.0.13/jre/lib/amd64/libnpjp2.so [/usr/lib/jvm/java-6-sun-1.6.0.13/jre/lib/amd64/libnpjp2.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /var/lib/flashplugin-installer/npwrapper.libflashplayer.so [/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-sun-1.6.0.13/jre/lib/amd64/libnpjp2.so [/usr/lib/jvm/java-6-sun-1.6.0.13/jre/lib/amd64/libnpjp2.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /var/lib/flashplugin-installer/npwrapper.libflashplayer.so [/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-cone-plugin.so [/usr/lib/totem/gstreamer/libtotem-cone-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-gmp-plugin.so [/usr/lib/totem/gstreamer/libtotem-gmp-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-mully-plugin.so [/usr/lib/totem/gstreamer/libtotem-mully-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so [/usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-sun-1.6.0.13/jre/lib/amd64/libnpjp2.so [/usr/lib/jvm/java-6-sun-1.6.0.13/jre/lib/amd64/libnpjp2.so: wrong ELF class: ELFCLASS64]
 2. my nodoka theme doesn't look right anymore. I'm using Jaunty 64-bit. Has anyone else experienced this?

---

### Post by scrooge_74 on 2009-06-30
The pluggins I had to manually link them like in the old firefox versions when there where no packages for JVM or flash and you had to uncompress and install files by hand

---

### Post by tanha on 2009-06-30
Problem "solved." It was the standard download (i686) that Firefox provides that doesn't play well with my jaunty amd64 install. I compiled 3.5 from source and now everything works. 
"About Shiretoko" = "Mozilla/5.0 (X11; U; **Linux x86_64**; en-US; rv:1.9.1) Gecko/20090630 Shiretoko/3.5" instead of the "i686 (x86_64)" that gets installed by downloading the package from [http://download.mozilla.org/?product=firefox-3.5&os=linux&lang=en-US](http://download.mozilla.org/?product=firefox-3.5&os=linux&lang=en-US)

---

### Post by xavierp94 on 2009-06-30
If you use the Ubuntuzilla script it can upgrade your installation of Firefox to the newest and backup the one installed by default.
[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

---

### Post by tanha on 2009-06-30
> **xavierp94 said:**
> If you use the Ubuntuzilla script it can upgrade your installation of Firefox to the newest and backup the one installed by default.
[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

Please, correct me if I'm wrong, but from what I can see, ubuntuzilla will install the default i686 app and not build it from the source which would yield the x86_64 version, right? Cause right now, the default version from the repositories is "Mozilla/5.0 (X11; U; **Linux x86_64**; en-US; rv:1.9.0.11) Gecko/2009060309 Ubuntu/9.04 (jaunty) Firefox/3.0.11" (and, I was only able to match this by compiling from the source).

---

### Post by xavierp94 on 2009-06-30
> **tanha said:**
> Please, correct me if I'm wrong, but from what I can see, ubuntuzilla will install the default i686 app and not build it from the source which would yield the x86_64 version, right? Cause right now, the default version from the repositories is "Mozilla/5.0 (X11; U; **Linux x86_64**; en-US; rv:1.9.0.11) Gecko/2009060309 Ubuntu/9.04 (jaunty) Firefox/3.0.11" (and, I was only able to match this by compiling from the source).
It's downloading the official package from Mozilla. It will install whatever version your computer is compatible as long as you install the correct deb.
[http://sourceforge.net/projects/ubuntuzilla/files/](http://sourceforge.net/projects/ubuntuzilla/files/)


In the FAQ'S they have the following posted.
> 64 bit users would see *x86_64*, 32 bit users would see *i686*.

---

### Post by susanpenter on 2009-06-30
> **tanha said:**
> For those who followed this method, do your plugins, like flashplugin-nonfree, work?

I tried this method and I lost all connection to the internet.  I have reverted back to Swiftfox 3.5 RC2 until I can find a safe way to get the real thing installed.

I'm rather disappointed after all the hype.  Things like this are the last hurdle Ubuntu has to overcome to convert the masses away from MS Windows.

---

### Post by tanha on 2009-06-30
> **xavierp94 said:**
> It's downloading the official package from Mozilla. It will install whatever version your computer is compatible as long as you install the correct deb.
[http://sourceforge.net/projects/ubuntuzilla/files/](http://sourceforge.net/projects/ubuntuzilla/files/)


In the FAQ'S they have the following posted.

So, if I understand it correctly, [it will install the 32 bit version, since that's the only one that's compiled for linux]("http://ubuntuzilla.wiki.sourceforge.net/#tochome27")... So, the trade off is that you get the upgrade but you lose the 64 bit app. doesn't seem right....

---

### Post by tanha on 2009-06-30
> **susanpenter said:**
> I tried this method and I lost all connection to the internet.  I have reverted back to Swiftfox 3.5 RC2 until I can find a safe way to get the real thing installed.

I'm rather disappointed after all the hype.  Things like this are the last hurdle Ubuntu has to overcome to convert the masses away from MS Windows.

Try this: 

in the url, enter ```
about:config
```

in the filter, enter ```
dns
```, enter

double click ```
network.dns.disableIPv6
```, which makes it "true"

should work, i think.

---

### Post by kendoori on 2009-06-30
+1 on the Ubuntuzilla script. Seemed like the easiest way to deal with this. Flash didn't work,  but I went to Adobe site and installed latest from there. Also Tagsifter, a plug-in I use all the time was disabled and marked as incompatible. So word to wise, if you use lots of extensions (add-ons etc...) check first.

---

### Post by pablo180 on 2009-06-30
I just did it like I would have in Windows, hit Help>Check for updates

First I had to do:

```
gksudo firefox
```


But it worked perfectly. It just downloaded and installed the update itself. Flash works OK, haven't checked all Add Ons but most seem to work OK. 

Glad really as I was never going to be able to have Firefox 3.5 on Intrepid from the repos. It's ironic that in Windows, updating a browser or other program is easy, but in Ubuntu, and despite the repos, you need to update your whole OS to get the latest programs.

---

### Post by andrew-sayers on 2009-06-30
Alexander Sack (the Ubuntu Firefox lead) has posted a [blog entry]("http://www.asoftsite.org/s9y/archives/160-FAQ-Where-can-I-get-firefox-3.5-for-Ubuntu.html") describing FF 3.5 in Ubuntu.

Short version: If you're on Jaunty, install Firefox 3.5 and wait a day or three for full-flavoured Foxy goodness.

I would also add: Higher-hassle solutions (like installing from source) will only buy you a small amount of time, and could cause all sorts of problems if you do it wrong.

	- Andrew

---

### Post by lovinglinux on 2009-06-30
For instructions on how to install Firefox 3.5 or upgrade the 3.0.11 version, check the [color=#CC0000]**Firefox Alternatives & Newer Versions**[/color] section of the [**[color=#CC0000]Firefox optimization and troubleshooting thread[/color]**](http://ubuntuforums.org/showthread.php?t=1193567).

For a list of other threads talking about the same subject, visit [http://ubuntuforums.org/showthread.php?t=1200781](http://ubuntuforums.org/showthread.php?t=1200781)

---

### Post by bonfire89 on 2009-07-01
mmm... some flash files that wouldn't play in 3.0... now play... I like.

---

### Post by tanha on 2009-07-01
> **andrew-sayers said:**
> Alexander Sack (the Ubuntu Firefox lead) has posted a [blog entry]("http://www.asoftsite.org/s9y/archives/160-FAQ-Where-can-I-get-firefox-3.5-for-Ubuntu.html") describing FF 3.5 in Ubuntu.

Short version: If you're on Jaunty, install Firefox 3.5 and wait a day or three for full-flavoured Foxy goodness.

I would also add: Higher-hassle solutions (like installing from source) will only buy you a small amount of time, and could cause all sorts of problems if you do it wrong.

	- Andrew

Thanks for the link :)

---

### Post by alexcckll on 2009-07-02
Are regular LTS-LTS end-users like me going to see this Firefox upgrade in our Update Managers soon?  Or will I have to wait till next year?

---

### Post by pablo180 on 2009-07-02
> **alexcckll said:**
> Are regular LTS-LTS end-users like me going to see this Firefox upgrade in our Update Managers soon?  Or will I have to wait till next year?

More like never. I'd still be using Firefox 2 if I hadn't updated the whole system. 

Luckily though you can just update through firefox Help > Check for Updates, I'm not sure if this will work in Hardy, but I don't see why not. 

It'll then download and install everything itself.

---

### Post by alexcckll on 2009-07-02
> **pablo180 said:**
> More like never. I'd still be using Firefox 2 if I hadn't updated the whole system. 

Luckily though you can just update through firefox Help > Check for Updates, I'm not sure if this will work in Hardy, but I don't see why not. 

It'll then download and install everything itself.
I was meaning when the next LTS version comes out... and has been certified on Thinkpad R61is..... 

I wouldn't feel comfy away from the official system libraries.  So - looks like i'll have to wait till next October, and reinstall.

Or maybe I ought to save up and buy a new laptop then - I bought this preinstalled.

How safe is the full OS update through Update Manager?  Is it bulletproof?

---

### Post by scrooge_74 on 2009-07-02
So far an old T43 I have,went from 7.04 to 8.04 no glitches

---

### Post by brad1138 on 2009-07-02
Well I installed 3.5 through SPM, (clicked Firefox-3.5 package, it selected a few others and then clicked apply) but now when I click my FF icon I still get 3.0.11, What did I do wrong?

Thanks,
Brad

---

### Post by scrooge_74 on 2009-07-02
Maybe you have both versions installed, but you are still aiming for the older one

---

### Post by Spike-X on 2009-07-03
> **pablo180 said:**
> I just did it like I would have in Windows, hit Help>Check for updates

First I had to do:

```
gksudo firefox
```


But it worked perfectly. It just downloaded and installed the update itself. Flash works OK, haven't checked all Add Ons but most seem to work OK. 

I tried that, and it told me no updates were available.

---

### Post by Spike-X on 2009-07-03
> **brad1138 said:**
> Well I installed 3.5 through SPM, (clicked Firefox-3.5 package, it selected a few others and then clicked apply) but now when I click my FF icon I still get 3.0.11, What did I do wrong?

Thanks,
Brad

Synaptic seems to be installing 3.5 separately, rather than as an upgrade. Go to Applications>Internet, and you should see something called Shiretoko. That's your FF 3.5.

---

### Post by square_monkey on 2009-07-03
Shiretoko is the testing version of Firefox 3.5, that's why it has a separate package. If you install this you'll have to explicitly run ```
firefox-3.5
``` Clicking your existing Firefox icons or loading with ```
firefox
``` is likely to run 3.0.* . You can verify this with ```
which firefox
```

Hopefully the firefox package will be updated to 3.5.

Bear in mind you may find problems with 3.5. If you can't fix them, you should be able to go back to 3.0.* easily.

---

### Post by ClintAtComputer on 2009-07-04
It looks like we just got some security updates to 3.0.11, but still no 3.5.

---

### Post by philinux on 2009-07-04
Just to correct some FUDD in this thread.

Please click the backports link below in my signature.

Extract
This is where Ubuntu Backports comes in. The Backports team believes that the best update policy is a mix of Ubuntu's security-only policy AND providing new versions of some programs. Candidates for version updates are primarily desktop applications, **such as your web browser**, word processor, IRC client, or IM client. These programs can be updated without replacing a large part of the operating system that would affect stability of the whole system.

---

### Post by Justin Trouble on 2009-07-04
> **philinux said:**
> Just to correct some FUDD in this thread.

Please click the backports link below in my signature.

This is wrong, unless something has changed?
Alexander Sack has said that Firefox 3.5 will be in Jaunty-updates: [http://www.asoftsite.org/s9y/archives/160-FAQ-Where-can-I-get-firefox-3.5-for-Ubuntu.html](http://www.asoftsite.org/s9y/archives/160-FAQ-Where-can-I-get-firefox-3.5-for-Ubuntu.html)

---

### Post by Andy06 on 2009-07-07
> Just to correct some FUDD in this thread.

No its accurate. Backports seem to be pretty useless if you intend to keep up with latest version (feature version) of programs.

FFv3.5 was pushed out now as a regular jaunty update due to 3.5b4 being in the jaunty repos (and only to those users who have the shiretoko beta installed). However, Hardy and Intrepid users will not get it since there is no 3.5b4 in repos, I checked already. No backports yet. They have to wait longer.

Another example is Pidgin, I don't get any version updates despite having backports enabled, probably because they replaced pidgin in karmic so again, no backports. You will have to manually go into the repos and install it anyway even if backporting worked instantaneously with new version, but then that would not be very different than Windows, and would be slower than windows.

---

### Post by nanotube on 2009-08-14
> **EApubs said:**
> Actually you can install the genuine,latest firefox on ubuntu using ubuntuzilla

[http://www.earth-org.com/blogs/2009/08/install-genuine-firefox-3-5-latest-on-ubuntu/](http://www.earth-org.com/blogs/2009/08/install-genuine-firefox-3-5-latest-on-ubuntu/)

the instructions on that blog are wrong. you shouldn't run ubuntuzilla with sudo.

why not link directry to [http://ubuntuzilla.sourceforge.net](http://ubuntuzilla.sourceforge.net) which is certain to have correct instructions, instead of some random blog post? :)

---

### Post by lovinglinux on 2009-08-14
> **nanotube said:**
> the instructions on that blog are wrong. you shouldn't run ubuntuzilla with sudo.

why not link directry to [http://ubuntuzilla.sourceforge.net](http://ubuntuzilla.sourceforge.net) which is certain to have correct instructions, instead of some random blog post? :)

+1 for that

---

### Post by colau on 2009-08-15
Easiest way to install firefox-3.5!
[firefox-3.5]("http://www.psychocats.net/ubuntu/firefox")

---

### Post by oren tal on 2009-08-28
one question, I can get from this thread the instruction to install firefox 3.5.


However I just want to know if Ubuntu do it automatically eventually?


This point is unclear to me.

I know that I can already right now upgrade my firefox, but I wonder if after they finish to check all the bug all user are updated automatically.

---

### Post by alphacrucis2 on 2009-08-28
> **oren tal said:**
> one question, I can get from this thread the instruction to install firefox 3.5.


However I just want to know if Ubuntu do it automatically eventually?


This point is unclear to me.

I know that I can already right now upgrade my firefox, but I wonder if after they finish to check all the bug all user are updated automatically.

FF 3.5 is already the default in Karmic Koala alpha 4. I don't know if there are any plans to backport it to Jaunty.

---

### Post by oren tal on 2009-08-28
> **alphacrucis2 said:**
> FF 3.5 is already the default in Karmic Koala alpha 4. I don't know if there are any plans to backport it to Jaunty.

the words (Karmic Koala) you are using don't say much to me.
I mean I don't know what is  " Karmic Koala alpha 4".

I am currently using ubuntu 9.04, and it has firefox 3.0.XX (don't remember the number in the XX).

I want to know if it eventually will update my firefox or I will have to do it manually.

I can know form this thread how to do it manually but if Ubuntu will eventually update my firefox then I will wait for it.

---

### Post by XCan on 2009-08-28
Karmic is Ubuntu 9.10. Usually packages are only upgraded in a new release. Thus, if you continue to use 9.04 you may very well never get upgraded to Firefox 3.5.

---

### Post by wirate on 2009-08-28
shiretoko is firefox 3.5 and its in the repos

---

### Post by oren tal on 2009-08-28
> **XCan said:**
> Karmic is Ubuntu 9.10. Usually packages are only upgraded in a new release. Thus, if you continue to use 9.04 you may very well never get upgraded to Firefox 3.5.

so do I have to upgrade it manually?

---

### Post by ssdt on 2009-08-28
And also the update will take you to Sheirtoko one, not the one with Firefox logo in it.

---

### Post by 3rdalbum on 2009-08-28
> **oren tal said:**
> so do I have to upgrade it manually?

No, you don't upgrade it, you install the new version alongside the Ubuntu version.

---

### Post by pablo180 on 2009-08-28
> **oren tal said:**
> one question, I can get from this thread the instruction to install firefox 3.5.


However I just want to know if Ubuntu do it automatically eventually?


This point is unclear to me.

I know that I can already right now upgrade my firefox, but I wonder if after they finish to check all the bug all user are updated automatically.

No. And this is one of the biggest drawbacks I have found with Ubuntu. Ubuntu does not add support for new versions of browsers. To get Firefox 3 I had to upgrade from Hardy Heron (8.04) to Intrepid Ibex (8.10), only to discover that to get Firefox 3.5 I had to upgrade again to Jaunty Jackalope (9.10), this is despite 8.10 supposedly being a long term support version. 

I was lucky with Firefox 3.5, I just ran gksudo Firefox and click Help>Check For Updates and it installed 3.5 on 8.10 automatically, although it doesn't seem to be working that great. I don't get the new tab thing like on IE, the restore tabs box doesn't appear and some pages don't render correctly (odd grey lines but the same sites work fine on 3.5 on windows). 

On Windows you just download and install the latest version of Firefox, on Ubuntu you either have to follow blog guides for workarounds, or upgrade your whole OS and take the risk of losing all your data.

It a bit of a joke to have to jump through hoops just to get the latest version of a web browser, kind of like Microsoft saying you need Vista to run IE7, Windows 7 to run IE8 etc. 

Now I dread the announcements of a new version of Firefox, as it means much hassle for me. I have been doing it since Breezy Badger (5.10), and it hasn't got any easier.

---

### Post by XCan on 2009-08-28
MS did say that to begin with iirc about the IE browsers. ;) But anyway, I agree that major softwares should be considered to being rolled out in older Ubuntu releases, but that's a different discussion. However, nothing is stopping you from heading to Mozilla's homepage to download the Linux version, much like you do on Windows.

---

### Post by pablo180 on 2009-08-28
> **XCan said:**
> MS did say that to begin with iirc about the IE browsers. ;) But anyway, I agree that major softwares should be considered to being rolled out in older Ubuntu releases, but that's a different discussion. However, nothing is stopping you from heading to Mozilla's homepage to download the Linux version, much like you do on Windows.

Yes I do remember them saying that, but then backtracking. 

It isn't really the same, on Windows installing the new version of Firefox replaced the old one, adds it to all the relevant areas and makes it work like the old one. Besides on Windows it updates automatically, or by a click.  

On Ubuntu it just adds it, the launcher will need to be re-done (because it will point to the old version), Firefox will be installed, but parts of the OS will have no idea that it is there. You just seem to be basically running the browser rather than installing it. I tried it that way once, never again. Not to mention the advantage that Synaptic has over Windows being totally negated. 

I agree it is a big topic regarding new versions of software on older releases, but the browser? Arguably the most important piece of software on the OS, and it's main selling point, that cannot be easily updated? That cannot really be justified outside of the 1990s.

---

### Post by oren tal on 2009-08-30
> **pablo180 said:**
> Yes I do remember them saying that, but then backtracking. 

It isn't really the same, on Windows installing the new version of Firefox replaced the old one, adds it to all the relevant areas and makes it work like the old one. Besides on Windows it updates automatically, or by a click.  

On Ubuntu it just adds it, the launcher will need to be re-done (because it will point to the old version), Firefox will be installed, but parts of the OS will have no idea that it is there. You just seem to be basically running the browser rather than installing it. I tried it that way once, never again. Not to mention the advantage that Synaptic has over Windows being totally negated. 

I agree it is a big topic regarding new versions of software on older releases, but the browser? Arguably the most important piece of software on the OS, and it's main selling point, that cannot be easily updated? That cannot really be justified outside of the 1990s.
maybe this should be a note to the developer.

Maybe someone can give this complain to the developer of Ubuntu so that they will fix it and make it easier to upgrade firefox.

---

### Post by efrenefren on 2009-09-01
i read somewhere that firefox 3.5 is already in the universe repos and you can install it with:

[HTML]sudo apt-get install firefox-3.5[/HTML]

---

### Post by ghostborg on 2009-09-23
Yes, but again as the person above stated you are running along not replacing. This leads to confusion.

---

### Post by mikewhatever on 2009-09-23
To all those complaining, I strongly suggest, start packaging. It actually kills two birds with one shot, first, you are getting productive, second, dealing with frustration effectively. It is all up to you.

That fact that a bug report was filed on launchpad, doesn't mean Firefox-3.5 is broken in Ubuntu. IMO, it isn't, and keep repeating the same thing over and over only makes the claim less and less convincing.

> **efrenefren said:**
> i read somewhere that firefox 3.5 is already in the universe repos and you can install it with:

[HTML]sudo apt-get install firefox-3.5[/HTML]

That is correct, but apparently not good enough to certain users.

---

### Post by pablo180 on 2009-09-23
> **mikewhatever said:**
> That is correct, but apparently not good enough to certain users.

That doesn't work in anything other than Jaunty, everything else gives you:

```
E: Couldn't find package firefox-3.5
```

Which is the problem.

---

### Post by mikewhatever on 2009-09-23
The problem is, that's the way Ubuntu works, while you expect something else. I've already suggested a solution above, and another one is, use what suits you best. Oddly enough, some people are never ever satisfied, no matter what they get. Is it part of our nature to complain? It doesn't seem to part of mine.

---

### Post by pablo180 on 2009-09-24
> **mikewhatever said:**
> The problem is, that's the way Ubuntu works, while you expect something else. I've already suggested a solution above, and another one is, use what suits you best. Oddly enough, some people are never ever satisfied, no matter what they get. Is it part of our nature to complain? It doesn't seem to part of mine.

I'm sure that many people said the same thing about Windows once, 'A BSOD, random restarting, an application not working that was working yesterday, slow performance...Hey, that's just how Windows works!'

Thankfully complaints, and competition to some extent, gained us all improvements in Windows. Otherwise we'd all still be using Window ME. Having to upgrade your whole OS just to update software may be how Ubuntu works, but it is not how it *should* work. 

As for learning how to package things myself, I moved to Ubuntu to make things easier for myself, not harder. Suggestions like that are why Ubuntu and Linux in general are, and will continue to be, the preserve of geeks and techies, whilst the other 99% of the world just want to *use* a computer not spend hours trying to get a piece of software working and then find out a few weeks later they need to do it again!

Problems like this, which are major, are why I don't think Ubuntu will ever get much higher than it's current 0.28% market share.

---

### Post by mikewhatever on 2009-09-24
You are right about Windows, pretty much all one could do was to complain. With Microsoft controlling every thing, users didn't have any choice. That's not the case with Linux. While all major distros (Debian, Fedora, Suse, Ubuntu) and their derivatives work the same, releasing new versions every now and again, there are also rolling release distros. Lets not argue about advantages and disadvantages of the two approaches. We are never going to agree and will just waste the time in pointless bickering. I don't think Ubuntu is going to switch, and you can either accept the way it works or use a rolling release distro. Complaining is also an option, but I think that mind set is from Windows.

---

### Post by pablo180 on 2009-09-25
> **mikewhatever said:**
> You are right about Windows, pretty much all one could do was to complain. With Microsoft controlling every thing, users didn't have any choice. That's not the case with Linux. While all major distros (Debian, Fedora, Suse, Ubuntu) and their derivatives work the same, releasing new versions every now and again, there are also rolling release distros. Lets not argue about advantages and disadvantages of the two approaches. We are never going to agree and will just waste the time in pointless bickering. I don't think Ubuntu is going to switch, and you can either accept the way it works or use a rolling release distro. Complaining is also an option, but I think that mind set is from Windows.

I don't know, I think that Ubuntu could use both methods. At the moment I used Ubuntu Tweak to easily access Third Party debs, which is simpler and far easier to use than Synaptic. I don't know why Ubuntu can't add an option to Synaptic, or Add Remove programs to do something similar. Those that wish to update their OS every six months to get the latest software, can do, whereas those that would like to use their LTS OS for it's lifespan can also do so *and* get the latest software, such new versions of Firefox, by ticking an option in Synaptic. 

Perhaps they will do that with their new version of Synaptic that they are working on. 

As for the idea that you shouldn't complain about something because it is free, complaining is the only way to get improvements with free products, they're not relying on sales to gauge things. Mozilla have got it right and understand the value of customer feedback.

---

### Post by mikewhatever on 2009-09-25
Well, what's wrong with Ubuntu Tweak updating things for you? I was going to suggest you start a third party project to bring Ubuntu software uptodate, but apparently there is an easy to use tool already. That's not simply complaining, that's complaining for the sake of complaining. :) Perhaps instead, you could help develop and promote Ubuntu Tweak.
On the other hand, if the latest software is very important to you, Ubuntu is not the distro.

I hold the opinion, that one is entitled to his or her share of rants and complains about anything and everything. It's part of human nature. That said, getting involved into things you want done is much more productive and mature in the open source movement. Complaining is inefficient. There used to be a flood of complains in the past about Ubuntu being brown, with similar arguments about market share and global adoption. Well, the complains died out, and Ubuntu is still brown.

---

### Post by pablo180 on 2009-09-26
> **mikewhatever said:**
> Perhaps instead, you could help develop and promote Ubuntu Tweak.

On the other hand, if the latest software is very important to you, Ubuntu is not the distro.

Ubuntu Tweak is good, but it isn't really made for updating software, it is just an add on to it, and it means that I still have to try and track down the PPA's for myself, although they do have a share option so presumably hard to find PPA's will get added to the main list eventually. It isn't perfect by any means, if I wanted to add firefox, I'd have to find the PPA, a PITA in itself :confused:. Then go through all the reload repositories, update etc. 

In windows I go to the firefox website, download, install, done. In fact firefox updates itself so I wouldn't even need to do that. 

As for getting involved with Ubuntu Tweak, this is another big problem with Ubuntu and Linux. I am not a techie, I am not a programmer or a developer, I am an end user so cannot contribute to anything other than use cases. Does that mean I shouldn't be using Ubuntu? Or that I shouldn't be complaining and should consider myself lucky to be allowed to use it? Ubuntu is a vehicle, I shouldn't need to be a mechanic to use it, it should just do what it is meant to. If I, and people like me, didn't use Ubuntu, it would drift into obscurity like all the other distros. 

As for other distros, I have used them, it is Ubuntu or nothing. Most others are unusable for the average user, anything that needs that much command line input belongs in the 1980s.  

It is all something of a moot point anyway, Ubuntu Software Store should resolve all of these problems, in Ubuntu Nerdy Nymph 11.04. So clearly they are listening and trying to move into a more complete OS. 

Until then expect more and more 'how do I install Firefox 4, OpenOffice 4, Thunderbird' etc threads every six months, because, as 70% of PC users still using XP demonstrates, some people are happy with things the way they have set them up and don't want to completely change their PC, just to install a new browser.

I used to recommend Ubuntu a lot, I don't anymore because if I cannot get things working properly, what chance do average users have who don't care about how Linux works, they just want to log into their online banking? :(

---

### Post by mikewhatever on 2009-09-26
> **pablo180 said:**
> ...

In windows I go to the firefox website, download, install, done. In fact firefox updates itself so I wouldn't even need to do that. 

Comparing Ubuntu to Windows is probably unavoidable, but expecting the same behavior isn't very smart. They are not the same, period.


> As for getting involved with Ubuntu Tweak, this is another big problem with Ubuntu and Linux. I am not a techie, I am not a programmer or a developer, I am an end user so cannot contribute to anything other than use cases. Does that mean I shouldn't be using Ubuntu? Or that I shouldn't be complaining and should consider myself lucky to be allowed to use it? Ubuntu is a vehicle, I shouldn't need to be a mechanic to use it, it should just do what it is meant to. If I, and people like me, didn't use Ubuntu, it would drift into obscurity like all the other distros.

You don't have to be a coder to get involved in a software project. There is usually much more to do then edit source code, like translating, promoting, making usability suggestions, etc etc. It's not a problem at all, in fact, helping people use the software, is also a good way to get involved. If you have to ask me, you can use Ubuntu as much as you want, as well as complain about it. I do consider myself lucky to use Ubuntu, it's great and does what it's meant to do very well. Apparently, you want it to be a free version of Windows, and for that, yes, you have to be a mechanic.
 

> As for other distros, I have used them, it is Ubuntu or nothing. Most others are unusable for the average user, anything that needs that much command line input belongs in the 1980s.  

It is all something of a moot point anyway, Ubuntu Software Store should resolve all of these problems, in Ubuntu Nerdy Nymph 11.04. So clearly they are listening and trying to move into a more complete OS. 

Until then expect more and more 'how do I install Firefox 4, OpenOffice 4, Thunderbird' etc threads every six months, because, as 70% of PC users still using XP demonstrates, some people are happy with things the way they have set them up and don't want to completely change their PC, just to install a new browser.

Can you elaborate a bit on how the Software Store is going to solve the problem we've been discussing.I've googled, but couldn't find anything about it. Anyway, I guess you and your friends are stuck with Windows till Nerdy Nymph.:)

> I used to recommend Ubuntu a lot, I don't anymore because if I cannot get things working properly, what chance do average users have who don't care about how Linux works, they just want to log into their online banking? :(

Are you saying people couldn't do online banking before Firefox3.5? :)

---

### Post by pablo180 on 2009-09-26
> **mikewhatever said:**
> Comparing Ubuntu to Windows is probably unavoidable, but expecting the same behavior isn't very smart. They are not the same, period.

A common misconception, but they are. Sure, they may not work the same way under the hood, but to the user there should little discernible difference in everyday tasks between OS's. For example a Mac user would be able to install software on a Windows PC, and vice versa. Not so easy with Linux, despite Synaptic, which is brilliant. A computer is first and foremost a tool, like a coffee machine, a printer or a phone. One can reasonably expect them to work in the same way, at least for fundamental tasks. 

> **mikewhatever said:**
>  Apparently, you want it to be a free version of Windows, and for that, yes, you have to be a mechanic.

I don't want a free version of windows, and I think you are confusing cost with value, I didn't want something cheaper, I wanted something better. I moved to Ubuntu because it is better than Windows, easier to customise, safer, faster, has better effects than Vista (Win7), was more stable, includes a web server, and came with the option to learn about something new. When I purchased this computer I had the choice between Vista and Ubuntu, I chose Ubuntu even though both options were the same price. It wasn't 'free' in that sense, but I thought that Ubuntu would be worth more to me than Vista. I wasn't wrong but it does have its drawbacks for a mainstream OS. 

> **mikewhatever said:**
>  Can you elaborate a bit on how the Software Store is going to solve the problem we've been discussing.

It doesn't specifically state anywhere that Ubuntu Software Store will do that, but reading between the lines on the wiki it sounds as if they are going to allow third parties to offer and even sell their products through Ubuntu Software Store, so presumably that will include new versions. There is also mention of it linking in with Launchpad, so hopefully, and if nothing else, that will include searching for PPAs.

> **mikewhatever said:**
> Are you saying people couldn't do online banking before Firefox3.5? :)

No, but many banks and other websites require the latest versions of browsers, this computer came with Gutsy Gibbon and Firefox 2 had I not upgraded the OS twice, (And I am still two behind the latest OS) I'd still be using it, might not be a problem now, but in future....

I like my computer running as it is, everything pretty much works, but to get the latest software I have to upgrade, even though upgrading invariably breaks something that worked perfectly before, be it Compiz, Networking, Printing, Wireless, Sound etc, something always breaks. 

For me this is the biggest problem with Ubuntu. You know it is going to be a hassle and a long journey through many, many *How To's*, but you have very little choice other than to upgrade then go through the hassle of trying to get your computer working like it did before. That said I recently installed Windows 7 and that was just as much hassle, however Microsoft don't expect me to do it every six months, just to get the newest version of Firefox. 

Until Ubuntu gets over these problems, it is never going to become a true mainstream OS, which is a shame because it is great in most respects, it just has some major flaws.

---

### Post by mikewhatever on 2009-09-27
I've been doing a bit of searching and reading online about the rolling release thing, and it appears, this isn't Ubuntu specific, but rather Linux specific as a whole. I don't know enough to explain, but if you look for a rolling release distro, there is very little to be found. I know about Arch and PClinux, and saw suggestions about Linux Mint. Arch is relatively hard to use, but you should definitely take a look at the other two. They shouldn't be hard to use at all.

---

### Post by Chame_Wizard on 2009-09-28
> Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.4pre) Gecko/20090923 Ubuntu/8.10 (intrepid) Shiretoko/3.5.4pre


It's crash different times a day.

*using temporary Pentium 3 Coppermine at home and P4 at intern-ship* :lolflag:

---

