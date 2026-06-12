---
title: "Prelinking Guide- Make Ubuntu Feel Faster"
date: 2005-10-11
forum: Outdated Tutorials &amp; Tips
---

### Post by poofyhairguy on 2005-10-11
**Disclaimer: Prelinking might break your system! Only consider for use if you can risk the chance that your install might mess up. Most of all make sure that it gets to run the whole thing through the first time you prelink. Stopping in the middle can lead to system failure. Prelinking is a powerful device and needs to be used with care.**


Originally written by Jdong.

**UPDATE 1/2/07**: Prelink is no longer necessary in Feisty. Feisty uses a new linking mechanism called DT_GNU_HASH which dramatically speeds up the linking process without the need for continuously running this prelink program. Again, **prelink is NOT useful starting  from Feisty**

**Reason to use Prelinking**

(from the Gentoo Linux Prelinking Guide)

Most common applications make use of shared libraries. These shared libraries need to be loaded into memory at runtime and the various symbol references need to be resolved. For most small programs this dynamic linking is very quick. But for programs written in C++ and that have many library dependencies, the dynamic linking can take a fair amount of time.

On most systems, libraries are not changed very often and when a program is run, the operations taken to link the program are the same every time. Prelink takes advantage of this by carrying out the linking and storing it in the executable, in effect prelinking it.

Prelinking can cut the startup times of applications. For example, a typical KDE program's loading time can be cut by as much as 50%. The only maintenance required is re-running prelink every time a library is upgraded for a pre-linked executable.

Yet there is a chance that prelinking might mess up something, so use at your own risk.

**How to enable prelink**

   1. Activate Ubuntu universe sources
   2. Put this command into terminal to install Prelink:

>           sudo apt-get install prelink



   3. Now put this command into the terminal:

>           sudo gedit /etc/default/prelink

   4. Change where it says "PRELINKING=unknown from unknown" to "yes"
   5. Adjust the other options if you know what the heck you're doing. If it looks foreign to you, the defaults work well.
   6. To start the first prelink (the longest one!), put this in terminal:

>           sudo /etc/cron.daily/prelink

**Automatic Prelinking After Program Are Installed**

One problem with prelinking in that when you install new programs those programs are not prelinked. So to avoid this problem when installing programs with apt-get or synaptic, use the directions below.

   1. Put this in terminal:

>           sudo gedit /etc/apt/apt.conf

   2. When the file opens in Gedit, put this line at the end of the file and save (even if the file has no content before you add the line):

>           DPkg::Post-Invoke {"echo Running prelink, please wait...;/etc/cron.daily/prelink";}


**General Notes About Prelinking**

In the future, prelink performs a quick prelink (a less-than-1-minute procedure on most systems) daily, usually at midnight. Every 14 days, or whatever you changed it to be, a full prelink will run.

If you just did a major apt-get upgrade that changed systemwide libraries (i.e. libc6, glibc, major gnome/X libs, etc etc etc) and experience cryptic errors about libs, rerun step 6.

To undo prelink, change step 4 from yes to no, then rerun step 6.

Prelinking will make the binaries it prelinks change, so it's not appropriate if you have tripwire or another checksum-based IDS system,  or if you do incremental or differential backups to save on space.

---

### Post by mlomker on 2005-10-11
> 
sudo gedit /etc/apt/apt.conf


Thanks for the guide!  I had installed prelinking but didn't know about the apt configuration.

Breezy amd64 does not appear to have an apt.conf file.  I did, however, find a /etc/apt/apt.conf.d directory that has similar scripts.  I created a new script called S99prelink and that appears to do the trick.

---

### Post by ubunxpm on 2005-10-13
I have a question. Eventhough prelinking sonds like a miracle tweak that would speed up most applications; since you noted to use this prelinking at one's own risk, I was wondering if prelinking would affect the stability of the whole operating system  negatively? I remember reading a similar thread for hoary but didn't perform the changes.  I am asking this because if it can speed up the system why isn't the ubuntu gets installed prelinking enabled off the bat and I would prefer the stability of ubuntu over the performance under any condition.  So please comment about this if you have experience from hoary or breezy's preview release. Thanks

---

### Post by mlomker on 2005-10-13
> So please comment about this if you have experience from hoary or breezy's preview release. Thanks

I ran prelinking on Hoary and now Breezy.  To be honest, I haven't noticed any performance difference...other than the few seconds **delay** while waiting for the prelinking to finish when I install packages now.  I certainly didn't run disk benchmarks before and after, but it doesn't seem like much to me.

---

### Post by ubunxpm on 2005-10-13
[QUOTE=poofyhairguy]Yet there is a chance that prelinking might mess up something, so use at your own risk.[/QUOTE]

Well, then it does not make a major difference in performance. Obviously a memory upgrade would do a whole lot more to the performance than prelinking. Did anything go wrong because of it where normally it wouldn't have?

---

### Post by poofyhairguy on 2005-10-13
[QUOTE=ubunxpm]Well, then it does not make a major difference in performance. Obviously a memory upgrade would do a whole lot more to the performance than prelinking. [/QUOTE]

Yes. Prelinking can help decrease the start up times for some applications. Its not a miracle tweak that makes everything faster, its just a way to get some applications to load faster.

---

### Post by PsyberOneZero on 2005-10-13
I started prelinking a few weeks ago in Breezy, the major differnece I felt was in opening OO.org apps for the first time, Writer went from ~10sec to 3-4sec, same for the rest OO.org, and Gimp.

Great tutorial poofyhairguy/jdong.

---

### Post by Kebabji on 2005-10-13
i can def see a dif in oo.org yayy thanks for the great tutorial

---

### Post by Saiboogu on 2005-10-13
Same here - improvement in apps like OOo and Gimp. That's enough for me - I don't need gaim to load faster, for example, because its already pretty quick - what makes this worthwhile is the savings on the larger apps. Great guide, thanks.

---

### Post by merlyn on 2005-10-16
[quote=mlomker]Thanks for the guide!  I had installed prelinking but didn't know about the apt configuration.

Breezy amd64 does not appear to have an apt.conf file. I did, however, find a /etc/apt/apt.conf.d directory that has similar scripts. I created a new script called S99prelink and that appears to do the trick.[/quote]

Could the steps you followed to do this be added to the original 'Howto'.

Cheers.

---

### Post by Leif on 2005-10-16
[QUOTE=ubunxpm] I am asking this because if it can speed up the system why isn't the ubuntu gets installed prelinking enabled off the bat and I would prefer the stability of ubuntu over the performance under any condition. [/QUOTE]

I tried prelinking in hoary, on two different systems, and each time something went wrong. I was able to un-prelink, but I did have a couple of minutes where everything was very broken.

---

### Post by Chareos on 2005-10-16
Right... what is something goes wrong ?

I mean... what happens if prelink brokes everything ?
And... is it possible undo to fail ?


Last question: is there a way to prelink (and keep prelinked) just a few applications ?

Let's say firefox, openoffice and some more ? (I know tehre was ooprelink, but what a about other apps ?)

---

### Post by steffen on 2005-10-22
Any way of prelinking openoffice.org2 only? That's the only app that takes ages to load, even with my tweaked memory settings in the prefs.

As far as I can see, the ooqstart only preloads ooo1, not 2

---

### Post by geearf on 2005-10-22
Prelinking my system breaks the postfix package, and then I have some messages like 
ldconfig: /usr/lib/libpostfix-util.so.1 is not a symbolic link

ldconfig: /usr/lib/libpostfix-global.so.1 is not a symbolic link

---

### Post by Mizzou_Engineer on 2005-10-22
You should ask one of the devs at [http://opensuse.org](http://opensuse.org) as they have prelinked only the KDE base, KDM, OOo, Mozilla, Firefox, and a couple other things in SuSE 10.0. 

But, the prelinking added about 30-45 sec. to the startup and shutdown and for some reason, it didn't seem to do much. OOo 2.0 runs faster un-prelinked here in Ubuntu than it did with pre-linking in SuSE.

---

### Post by jeffreyvergara.NET on 2005-10-24
installing and uninstalling programs seems to be slower than before, waiting for prelinking to finish tooks time to finish

---

### Post by zenrox on 2005-10-24
[QUOTE=jeffreyvergara.NET]installing and uninstalling programs seems to be slower than before, waiting for prelinking to finish tooks time to finish[/QUOTE]
 Thats the only downside but if you use apt-get it is faster with prelink has something to do with the was the console is implembented in the dialouge some how
but its ok with me tho it still get the job done:D

---

### Post by tonderai on 2005-10-28
> So please comment about this if you have experience from hoary or breezy's preview release. Thanks

I found the hard disk 'grind' from prelink and the resulting slowdown pretty annoying (esp. on laptop), outweighing small loadup time improvements. Some instability too, but I can't tell if that's linked to prelink.

PS The best way to speed up OpenOffice is to use Abiword/Gnumeric instead ;)

---

### Post by Rxke on 2005-10-29
Works great on an ancient Clamshell iBook! :D
Got a bit worried about the time it took for the initial prelink session, though, heehee. Took ages.
on a slower machine, the speedup is quite spectacular, thanks a lot!

---

### Post by geearf on 2005-10-30
[QUOTE=geearf]Prelinking my system breaks the postfix package, and then I have some messages like 
ldconfig: /usr/lib/libpostfix-util.so.1 is not a symbolic link

ldconfig: /usr/lib/libpostfix-global.so.1 is not a symbolic link
I can get rid of these by reinstalling postfix, but another prelink make them come back[/QUOTE]
please any ideas ?

---

### Post by tonderai on 2005-10-30
[QUOTE=geearf]Prelinking my system breaks the postfix package, and then I have some messages like 
ldconfig: /usr/lib/libpostfix-util.so.1 is not a symbolic link

ldconfig: /usr/lib/libpostfix-global.so.1 is not a symbolic link[/QUOTE]

I got this as well, but the only way I found to stop it was to stop prelinking and reinstall the postfix package.

---

### Post by geearf on 2005-10-30
Well it actually does not bother me too much, but I'd still like to fix it, so one in a while I reinstall the package, and prelink will kill it later :cool:

---

### Post by CHUCKYCHUCK on 2005-10-31
i have a question about undoing prelink, in the 1st post it's said that to undo prelink, i have to modify the option from "yes" to "no" in the /etc/default/prelink, and then execute /etc/cron ...
but i did some search, and i found that prelink can also be undone by the 'undo' option of prelink, ( prelink -u i remembered )
which method should i use ??

 ( i have no problems with prelink, just to know :) | except after the install of acroread, when prelinking took 45 minutes ............  for the others packages installations it just takes a few secondes but with acroread ... strange isn't it ?? )

thx

---

### Post by Sionide on 2005-11-01
Seems to be working fine for me. :) Thanks for the Guide guys.

---

### Post by herot on 2005-11-01
seems to be working but i dunno if it has sped things up too much more...
what sort of performance gain should i expect when using prelinking??

---

### Post by samwyse on 2005-11-01
Thanks, now I know why Fedora was much faster at starting X :)

---

### Post by Sionide on 2005-11-01
Prelinking after apt-get is taking ages - is it actually that essential seeing as the default config loads the prelink command at midnight every night??

---

### Post by xingmu on 2005-11-02
I love some of the HOWTO's that are on the forums.  But this last one makes me think there needs to be a warning system for HOWTO's.  Last night, just before sleeping, I saw this prelinking guide and decided to give it a try.  Being tired and lazy, I did a very stupid thing.  I was working off my laptop on battery-power.  Even though I knew I didn't have much time left, I ran the last step in the guide: sudo /etc/cron.daily/prelink.  In the middle of the process, my battery ran out and the laptop switched off.  I just shrugged my shoulders and went to bed.

This morning I woke up to a very ugly sight.  I booted up my computer and halfway through the boot-up started seeing numerous error messages:
/usr/bin/cut: cannot execute binary file
/bin/chmod: cannot execute binary file
....

Suffice to say, Ubuntu wasn't booting anymore.  I booted up in recovery mode and thought maybe if I ran prelink again, it'd all be ok?  No.  When running prelink, it had errors that bascially said all of my libraries did not have a valid ELF header.  I thought maybe I could just reinstall my binaries (and libraries?)...but of course apt-get wouldn't run either.  So I decided to just give up and reinstall Breezy.  Kinda sucked wasting my whole morning on that when I had more important things to do today.  

I know that I was dumb for doing a serious operation on low battery power.  BUT!  To be honest, I didn't realize that prelink was such a powerful operation.  I figured it was just like any other package and I could simply uninstall it if it messed up anything.  Besides my concern that dumb people like me might not realize there is serious risks with prelink, I am wondering how you would undo everything if you just didn't like prelink's effects.  Seems like the ideal HOWTO would tell you the risk level involved and "how to undo" as well.

---

### Post by poofyhairguy on 2005-11-02
[QUOTE=xingmu]I love some of the HOWTO's that are on the forums.  But this last one makes me think there needs to be a warning system for HOWTO's.  Last night, just before sleeping, I saw this prelinking guide and decided to give it a try.  Being tired and lazy, I did a very stupid thing.  I was working off my laptop on battery-power.  Even though I knew I didn't have much time left, I ran the last step in the guide: sudo /etc/cron.daily/prelink.  In the middle of the process, my battery ran out and the laptop switched off.  I just shrugged my shoulders and went to bed.

This morning I woke up to a very ugly sight.  I booted up my computer and halfway through the boot-up started seeing numerous error messages:
/usr/bin/cut: cannot execute binary file
/bin/chmod: cannot execute binary file
....

Suffice to say, Ubuntu wasn't booting anymore.  I booted up in recovery mode and thought maybe if I ran prelink again, it'd all be ok?  No.  When running prelink, it had errors that bascially said all of my libraries did not have a valid ELF header.  I thought maybe I could just reinstall my binaries (and libraries?)...but of course apt-get wouldn't run either.  So I decided to just give up and reinstall Breezy.  Kinda sucked wasting my whole morning on that when I had more important things to do today.  

I know that I was dumb for doing a serious operation on low battery power.  BUT!  To be honest, I didn't realize that prelink was such a powerful operation.  I figured it was just like any other package and I could simply uninstall it if it messed up anything.  Besides my concern that dumb people like me might not realize there is serious risks with prelink, I am wondering how you would undo everything if you just didn't like prelink's effects.  Seems like the ideal HOWTO would tell you the risk level involved and "how to undo" as well.[/QUOTE]


Sorry it messed up your system. Thanks for the suggestion, I juse added a disclaimer. I have never heard of such problems with it before and I promise if I knew that turning off you machine in the middle could mess up things I woulc have warned people.

---

### Post by samwyse on 2005-11-02
[QUOTE=Sionide]Prelinking after apt-get is taking ages - is it actually that essential seeing as the default config loads the prelink command at midnight every night??[/QUOTE]
I was wondering the same thing.

---

### Post by jeremy on 2005-11-02
Ubuntu is fast enough for me, but I did once speed up windows ME by doing a yoga course and slowing down my heartbeat!

---

### Post by xingmu on 2005-11-02
[QUOTE=poofyhairguy]Sorry it messed up your system. Thanks for the suggestion, I juse added a disclaimer. I have never heard of such problems with it before and I promise if I knew that turning off you machine in the middle could mess up things I woulc have warned people.[/QUOTE]

Cool, I saw it first thing when I loaded up this thread.  Thanks!  " If just one more person can be saved...."  :)

---

### Post by autocrosser on 2005-11-06
Just tried to get prelink & apt reported--

dean@Dual1:~$  sudo apt-get install prelink
Reading package lists... Done
Building dependency tree... Done
Package prelink is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


Anyone have any ideas??

---

### Post by geearf on 2005-11-07
post your source.list please.

---

### Post by autocrosser on 2005-11-09
sources.list---I'm running a PPC (Dual 1.25 Mirror-Door)

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free

---

### Post by Yagisan on 2005-11-09
[QUOTE=Sionide]Prelinking after apt-get is taking ages - is it actually that essential seeing as the default config loads the prelink command at midnight every night??[/QUOTE]It is rather important, especially if you are upgrading core system files (you want to make sure the right files are being used). If you don't have anacron installed, the midnight prelink run never gets done, if you turn the pc off before midnight.

You must be running running apt-get a lot. If you are tracking say dapper, I probally would not be prelinking my system, I'd only do it on a relatively unchanging system.

---

### Post by geearf on 2005-11-09
[QUOTE=autocrosser]
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
[/QUOTE]
I don't get why you only have the deb-src here, try adding the deb too and see how it works

---

### Post by Sionide on 2005-11-09
[QUOTE=Yagisan]If you don't have anacron installed, the midnight prelink run never gets done, if you turn the pc off before midnight.[/QUOTE]

I don't usually turn my PC off at night - I'll google for anacron but how can I make sure that it is running every day at midnight??

[QUOTE=Yagisan]You must be running running apt-get a lot.[/QUOTE]

Yeah, I tend to install new applications as I find out about them. It depends really.

---

### Post by autocrosser on 2005-11-09
Re-tried apt-get after I posted--pulled it just fine--don't know why I had the prob the first time:???: --let prelink do it's thing & went to bed--all was good this morning:cool: ---I leave the system up 24/7, so I'll post any items of interest--most large apps load 5/15 sec faster:smile: 
 
Thanks!!
 
 
[quote=geearf]I don't get why you only have the deb-src here, try adding the deb too and see how it works[/quote]

---

### Post by trinaryouroboros on 2005-11-09
poofyhairguy - you've made one Happy Dragon with this how-to!

Thank you!  

:KS

---

### Post by Yagisan on 2005-11-09
[QUOTE=Sionide]I don't usually turn my PC off at night - I'll google for anacron but how can I make sure that it is running every day at midnight??[/quote] If it isn't already installed ```
aptitude install anacron
``` will install it. It basically makes sure that any jobs that were missed due to the system being off, are done shortly after the system being powered on.

[QUOTE=Sionide]Yeah, I tend to install new applications as I find out about them. It depends really.[/QUOTE] Perhaps it would be better to disable prelink until you have a relatively unchanging system. Although on my system it only takes 1m 5s to run (it takes longer to run apt-get update on my system, 2m 14s)

---

### Post by ace2005 on 2005-11-20
Um.. I only see 

> ace@Linux:~$ sudo /etc/cron.daily/prelink

	

In konsole when i ran it, do i have to keep waiting until it says something like finished, its been like 5mins and there is little disk activity

Should i have done this from the command line with the X server off?

What about the xcomposite manager, do i have to turn off the transparency and fade ins and shadows off too??

and do i have to close all the programs and stuff like Opera, Juk Superkaramba, Firestarter, and Azureus???

---

### Post by bugmenot on 2005-11-28
[QUOTE=Chareos]Right... what is something goes wrong ?

Last question: is there a way to prelink (and keep prelinked) just a few applications ?

Let's say firefox, openoffice and some more ? (I know tehre was ooprelink, but what a about other apps ?)[/QUOTE]
I also want to prelink firefox and openoffice, but not the whole system. 
Does somebody know how to do that?

---

### Post by ace2005 on 2005-11-28
[QUOTE=ace2005]Um.. I only see 



In konsole when i ran it, do i have to keep waiting until it says something like finished, its been like 5mins and there is little disk activity

Should i have done this from the command line with the X server off?

What about the xcomposite manager, do i have to turn off the transparency and fade ins and shadows off too??

and do i have to close all the programs and stuff like Opera, Juk Superkaramba, Firestarter, and Azureus???[/QUOTE]


It took a while but it did finish but there was no output, does this mean it worked?

---

### Post by GoldBuggie on 2005-11-28
ace2005: Yes it means it worked!

[B]HowTo prelink only firefox(have not tested it but this should work in theory)
[/B]
The file that tells which directories that should be processed by prelink is the following:
```
sudo kate /etc/prelink.conf
``` 
Comment out the lines starting with **-l** by putting a **#** in front of that line. This way you can easily return to your previous state.

I've checked which files and directories firefox uses on my system(kubuntu 5.10 kde3.5) and having prelink traverse throu these directories should be sufficiant. So add the following to the above stated .conf file:
```
-l /usr/lib/mozilla-firefox
-l /usr/lib/gtk-2.0
``` Now there are more files that my firefox use *(/usr/lib/libcairo.so.2.2.3, /lib/tls/i686/cmov/libnss_nis-2.3.5.so ...)* but since I'm not sure which files that comes with your system I will not attempt to mention them here. Instead I think the 2 above directories should be the most imprtant ones.

If anyone knows of any important file that I should include that everyone uses then please let me know.

---

### Post by Sionide on 2005-11-29
[QUOTE=ace2005]It took a while but it did finish but there was no output, does this mean it worked?[/QUOTE]

Yep. No output is given. The first one will take the longest...

---

### Post by poofyhairguy on 2005-11-30
[QUOTE=GoldBuggie]ace2005: Yes it means it worked!

[B]HowTo prelink only firefox(have not tested it but this should work in theory)
[/B]
The file that tells which directories that should be processed by prelink is the following:
```
sudo kate /etc/prelink.conf
``` 
Comment out the lines starting with **-l** by putting a **#** in front of that line. This way you can easily return to your previous state.

I've checked which files and directories firefox uses on my system(kubuntu 5.10 kde3.5) and having prelink traverse throu these directories should be sufficiant. So add the following to the above stated .conf file:
```
-l /usr/lib/mozilla-firefox
-l /usr/lib/gtk-2.0
``` Now there are more files that my firefox use *(/usr/lib/libcairo.so.2.2.3, /lib/tls/i686/cmov/libnss_nis-2.3.5.so ...)* but since I'm not sure which files that comes with your system I will not attempt to mention them here. Instead I think the 2 above directories should be the most imprtant ones.

If anyone knows of any important file that I should include that everyone uses then please let me know.[/QUOTE]


Sweet. Does this work?

---

### Post by GoldBuggie on 2005-11-30
actually only the only library you need to use is probably /usr/lib/mozilla-firefox but the gtk library has /usr/lib/gtk-2.0/2.4.0/engines/libclearlooks.so which is what firefox uses so I included it. 

I'm going to run some tests this weekend with some different configs and a few more apps I'll return with the result as soon as I've done it. After that I can for sure tell you if more is needed.

---

### Post by Nutterpc on 2005-11-30
Can I also suggest setting prelink to use -amR

used it in my gentoo days, worked then, and it works now :)

Nice guide too, systems working well now

EDIT: Testing out prelink using -amR on Ubuntu.....will post back once I know how it goes

---

### Post by GoldBuggie on 2005-11-30
Ok tested with prelinking only firefox. Did some time testing as well. I will not post them since they will not show any improvement or chang on my system. Regardless of no prelinkning, full prelinking or only firefox. Maybe a test of seeing how the modules got loaded would be a better way but it would have taken more time for me :)

Anyway...I wanted to prelink firefox only(reduxing startup time at best). So prelinking is the way to go.

I first tried doing it the following way.
*sudo prelink -vm /usr/lib/mozilla-firefox/firefox-bin*

I got some trouble with not finding dependencies etc..so I tried doing a "*-l /usr/lib/mozilla-firefox/firefox-bin*" in *prelink.conf* but that didn't work as well. It seems prelink is bad at finding the dependencies so I have to manually add them.

On a *i686* kernel(which is what I use) you will get *39* dependencies from firefox. For a *i386* you will probably get *37* or *38.* *i686* brings a dependency on *linux-gate.so.1* which is a file that does not exist(only in memory somewhere, look it up for more detail). So prelinking firefox means prelinking the remaining *38* files and its possible dependencies. Here is what you should put in your [I]/etc/prelink.conf

[/I]```
####Firefox
-l /usr/lib/libz.so.1.2.3
-l /usr/lib/libfontconfig.so.1.0.4
-l /usr/lib/libgmodule-2.0.so.0.800.3
-l /usr/lib/libpango-1.0.so.0.1001.0
-l /usr/lib/libplc4.so
-l /usr/lib/libpangoft2-1.0.so.0.1001.0
-l /usr/lib/libnspr4.so
-l /usr/lib/libfreetype.so.6.3.5
-l /usr/lib/libplds4.so
-l /usr/lib/libgobject-2.0.so.0.800.3
-l /lib/ld-2.3.5.so
-l /usr/lib/libglib-2.0.so.0.800.3
-l /usr/lib/libexpat.so.1.0.0
-h /lib/tls/
-l /usr/lib/mozilla-firefox/libmozjs.so
-l /lib/libgcc_s.so.1
-l /usr/lib/libstdc++.so.6
-l /usr/lib/mozilla-firefox/libxpcom.so
-l /usr/lib/libatk-1.0.so.0
-l /usr/lib/libXfixes.so.3
-l /usr/lib/libXcursor.so.1
-l /usr/lib/libXrandr.so.2
-l /usr/lib/libXi.so.6
-l /usr/lib/libXext.so.6
-l /usr/lib/libXinerama.so.1
-l /usr/lib/libpng12.so.0
-l /usr/lib/libXdmcp.so.6
-l /usr/lib/libXau.so.6
-l /usr/lib/libX11.so.6
-l /usr/lib/libXrender.so.1
-l /usr/lib/libcairo.so.2
-l /usr/lib/libpangocairo-1.0.so.0
-l /usr/lib/libgdk-x11-2.0.so.0
-l /usr/lib/libgdk_pixbuf-2.0.so.0
-l /usr/lib/libgtk-x11-2.0.so.0
-l /usr/lib/libpango-1.0.so.0
-l /usr/lib/mozilla-firefox/firefox-bin
####Firefox
```

I was planning on trying some other software but at the moment it will not bring me anything since I will use the full prelink at this moment. Maybe in the future if there is some overwhelming demand on some software.

I went back to using the whole prelink since I felt my system wasn't as responsive as before(no scientific measurement only a feeling after have run prelink for quite a while) and I didn't want to go thrue which libraries would be best for kde.

---

### Post by Nutterpc on 2005-12-02
Well I can say that yes, by setting prelinking to -amR, does seem to take a little while for the system to adjust at first, but it does seem far more happy, the systems nice & snappy, unlike when you install stuff on Windoze :P

It works for me, works well, but YMMV

---

### Post by Rob2687 on 2005-12-03
I think -a broke something on my laptop. The updatenotifier process is now always at 60-70% CPU. I left it over night and it's still doing something.

---

### Post by Nutterpc on 2005-12-06
That does seem a bit odd

Even on my machine (Duron 1Ghz, 768Mb RAM, 80Gb HDD) it took a while when I added -a to the prelink config file

Try taking it out again, or ctrl + c it

---

### Post by viscount on 2005-12-14
Questions & more Questions

Does prelink automatically apply to every directory on the entire system?

I have several large exec fiels in my home folder that I would like prelinked
if they are not already being automatically prelinked.

Is it possible to manually prelink a single binary?

Is it possible to exclude certain programs that are known to be flakey with prelink?

---

### Post by poofyhairguy on 2005-12-14
[QUOTE=viscount]Questions & more Questions

Does prelink automatically apply to every directory on the entire system?

I have several large exec fiels in my home folder that I would like prelinked
if they are not already being automatically prelinked.

Is it possible to manually prelink a single binary?

Is it possible to exclude certain programs that are known to be flakey with prelink?[/QUOTE]

Ok, I know I made the guide but I really don't know details. I just converted a guide Jdong made for Warty.

Here is a page with WAY more details on prelink:

[http://www.gentoo.org/doc/en/prelink-howto.xml](http://www.gentoo.org/doc/en/prelink-howto.xml)

---

### Post by GoldBuggie on 2005-12-14
Viscount

All of the questions is answered yes. You have to edit the /etc/prelink.conf file.

You will also see what is beeing prelinked and not. Basically it is like this.

**-l <DIRECTORY or FILE>**
Will prelink that directory(and its subdirs) or given file.

**-b <DIRECTORY or FILE or *.FILETYPE>**
Will make prelink *NOT* include the dir. or file.

Problem with prelinking a single binary is that all its dependencies needs to be prelinked as well. So just pointing to a executable will in many cases not work since it will probably complain about not beeing able to find the dependency.

Like what I tried to do with firefox before. Just prelinking the binary doesn't work you must prelink all the files that the binary uses and depends upon.

---

### Post by DiskMan on 2006-01-26
I noticed that little fact myself when I did some tests using prelink, and didn't really notice any kind of 'real' speed boost other than my imagination. When I checked the prelink.cache, thats when I noticed that out of THOUSANDS of files [binary/lib] only a handful had actually been linked. Those that were linked, were small programs that didn't require much in order to run. Others such as Gnome/KDE/Xfce/etc were 'on their own' so to speak.

I wonder how many people actual notice that prelink does little or nothing on most machines out there. The main libs that I have on the 'blacklist' are standard GLIBC libraries, that if prelinked, would kill my box [trust me, I've tried it]. Most notable are libc.so and ld.so.

For most people, prelink is largely useless and does little, the rest is simply their imagination. Try running 'prelink -p', cache dump, it will show you whats being prelinked and whats not... the NOT part is going to be pretty large btw.  DiskMan

---

### Post by dcast on 2006-01-26
seems to work, thanks

---

### Post by sailor420 on 2006-03-23
FYI, you may find, as I did, that if you install this on a laptop or other machine that doesn't stay on that often, the resulting slowdown from the backed up cronjob running when the machine is turned on may not be worth the miniscule speed boost that prelinking provides.

---

### Post by MichaelZ on 2006-04-30
[quote=poofyhairguy]
**Automatic Prelinking After Program Are Installed**

One problem with prelinking in that when you install new programs those programs are not prelinked. So to avoid this problem when installing programs with apt-get or synaptic, use the directions below.
[...]
[/quote] 
Hello,

I have a question. In my system I do not have /etc/apt/apt.conf, but I have  a directory /etc/apt/apt.conf.d

Inside I have 5 files: 05aptitude, 10periodic, 20archive,70debconf and 99update-notifier.

To which file should I added:

> 
DPkg::Post-Invoke {"echo Running prelink, please wait...;/etc/cron.daily/prelink";}
 
Thank you very much.

Best wishes,
Michael

---

### Post by dresnu on 2006-05-20
> In my system I do not have /etc/apt/apt.conf
Just create that file by typing "sudo gedit /etc/apt/apt.conf" in the console, add that line inside and save the file.

---

### Post by MichaelZ on 2006-05-20
[quote=dresnu]Just create that file by typing "sudo gedit /etc/apt/apt.conf" in the console, add that line inside and save the file.[/quote] 
Hello,

Thank you very much for the help :).

Best wishes,
Michael

---

### Post by ozorba on 2006-06-02
I have experimented with prelinking. However I am running out of space and therefore want to revert back. 

How do I do that?

Thanks,
OZ

---

### Post by dresnu on 2006-06-02
[QUOTE=ozorba]I have experimented with prelinking. However I am running out of space and therefore want to revert back.[/QUOTE]

Check the last line of the first post in this thread. Also delete the line "DPkg::Post-Invoke {"echo Running prelink, please wait...;/etc/cron.daily/prelink";}" if you had inserted it in /etc/apt/apt.conf.

---

### Post by roostishaw on 2006-06-07
After I do  sudo /etc/cron.daily/prelink  it just keeps printing a y
Is it supposed to do this?

---

### Post by dresnu on 2006-06-08
Could you please copy/paste a line of example so I can understand what you 're talking about.

---

### Post by lyricmuse on 2006-06-30
Just did a fresh install of Dapper and prelinking.  I've noticed an excellent improvement in load times.  My sys specs are

2.4 ghz celeron (MSI socket 478)
768 ddr
200 gb hard drive
geforce 4 mx440 video 
creative live 5.1

I have wanted to try prelinking in the past but was afraid it would break my system.  I'm playing around with ubuntu so I thought I would give it a shot.  Thanks for the great tip.=D>

---

### Post by ubuntu_demon on 2006-07-14
I created a blog entry about Desktop performance tweaks and linked to this thread :
[http://ubuntudemon.wordpress.com/2006/07/14/desktop-performance-tweaks/](http://ubuntudemon.wordpress.com/2006/07/14/desktop-performance-tweaks/)

To digg it :
[http://digg.com/linux_unix/Ubuntu_Desktop_performance_tweaks](http://digg.com/linux_unix/Ubuntu_Desktop_performance_tweaks)

---

### Post by yaztromo on 2006-07-25
I just installed prelinking for the guide then did a prelink -p to see what was being prelinked and what wasn't. Firefox is was the program I wanted prelinking most for.

But i see this 

> /usr/lib/firefox/firefox (not prelinkable)

Pretty pointless if this is the case :-| .

I really think prelinking is a waste of time. For a start firefox doesn't get prelinked at all and the only 2 applications that start slightly faster are GIMP and OO.

---

### Post by GoldBuggie on 2006-07-25
>  But i see this 
 	Quote:
 	 	 		 			 				/usr/lib/firefox/firefox (not prelinkable) 			 		 	 	 
  Pretty pointless if this is the case  .

I really think prelinking is a waste of time. For a start firefox doesn't get prelinked at all and the only 2 applications that start slightly faster are GIMP and OO.

Look att the files that firefox needs prelinked instead. If I remember correctly there was one or two "null files". Don't remember what the files was called exactly but there are two modules that firefox gets for dependency that are virtual files and thus aren't really files. So when prelink says that firefox isn't prelink it just means that those two files aren't prelink, but the actual files are. So in practice firefox is prelink. Just ignore that message.

If the prelinking makes startup faster or not I leave to the subjective user.

---

### Post by yaztromo on 2006-07-25
I just installed prelinking then did a prelink -p to see what was being prelinked and what wasn't. Firefox was the program I wanted prelinking most.

But i see this 

> /usr/lib/firefox/firefox (not prelinkable)

Pretty pointless if this is the case :-| .

I really think prelinking is a waste of time. For a start firefox doesn't get prelinked at all and the only 2 applications that start slightly faster are GIMP and OO.

---

### Post by H Roark on 2006-08-02
Anyone see this before?

```
*** glibc detected *** free(): invalid pointer: 0xb7e2ec38 ***
/etc/cron.daily/prelink: line 53: 27838 Aborted                 
/usr/sbin/prelink -a $PRELINK_OPTS >>/var/log/prelink.log 2>&1
```

Maybe it's just me. A check of the log file it spits out reveals this in the last 2 lines...

```
/usr/sbin/prelink.bin: /usr/bin/mppdec: Symbol section index outside of section numbers
Prelink failed with return value 134
```

mppdec is used for playing music from the cmd line? never used it. I don't think sound converter or any of my audio programs need it, so if you have a tip on how to remove it; great.

Any other thoughts would be appreciated.

Thanks in advance,

Roark

**PS** - followed first post to a T. Issued this: *_sudo /etc/cron.daily/prelink_* and got the above results. Attached log file if that helps.

---

### Post by robert114 on 2006-08-05
I had this problem as well.
I've seem to fixed it for my machine by just completely removing the prelink program (including conf. files) and than just reinstalling it!

Right now my machine is prelinking and this seems to have solved my PC.

I don't know what has caused this problem! but for your info
I'm using the portback and a lot of other repo's maybe this causes my problem!

---

### Post by H Roark on 2006-08-06
Thanks Robert, I tried that but still doesn't work. Fails at the same part. I'm thinking I may have a memory issue at that address...

Anyway, thanks for the suggestion. Hope it helps someone else if they have similar issues.

---

### Post by robert114 on 2006-08-07
To bad, did you purge the program?

Maybe it helps if you un-prelink your machine first and then remove (purge) the program and then re-install it.

But i'm not very familiar with prelinking so it might cause other problems, be carefull!!!

---

### Post by H Roark on 2006-08-07
Robert,

I did the prelink undo command and then uninstalled the program. Tried re-installing it. Nothing. Same error.

So I'm thinking it's a hardware issue. Thanks again.

---

### Post by robert114 on 2006-08-08
Damn, to bad! :sad: I don't know anything else to look at!

---

### Post by mrvw0169 on 2006-08-10
Uh oh, I have a similar problem - except I ran my HD space to 0B free while downloading too many torrents at once and didn't pay attention during a prelink... So then prelink stopped/froze (left on for over an hour - usually takes 1 min) and won't continue even after freeing up space on / ...

So now I can't boot into the system (fsck segfaults) but I can boot into Recovery mode and luckily still be able to aptitude packages (but other commands won't work - they segfault too)... I've tried running prelink again (which works until the last line in the script where it uses awk but I think it's not needed anyway for prelink to work) both with turning prelink "yes" and "no" but my system is still broken...

I'll try to reinstall e2fsprogs once I get back to fix the fsck once I'm at my computer and maybe that works... But just wondering if there a quick way to do something like sudo aptitude reinstall base/* to get all the base packages reinstalled? Or another way to work around this without reinstalling Ubuntu (won't have time this whole week)?

---

### Post by xyz on 2006-10-16
Works like a charm here! Thank you [b]poofyhairguy's Avatar  	
poofyhairguy![/b]

I always get this:
> Running prelink, please wait...
/etc/default/prelink: line 41: syntax error near unexpected token `}'
/etc/default/prelink: line 41: `DPkg::Post-Invoke {"echo Running prelink, please wait...;/etc/cron.daily/prelink";}'

Is it normal? Should I remove all "unexpected tokens "}" on line 41"?
Thanks for reading.

---

### Post by John Nilsson on 2006-10-17
It seems you've put the 'Dpkg::Post-invoke...' line in the wrong file. It should be in /etc/apt/apt.conf not in /etc/default/prelink.

---

### Post by xyz on 2006-10-18
> **John Nilsson said:**
> It seems you've put the 'Dpkg::Post-invoke...' line in the wrong file. It should be in /etc/apt/apt.conf not in /etc/default/prelink.

Thanks for this, John.
For some odd reason I had the 'Dpkg::Post-invoke...' line in both /etc/apt/apt.conf AND /etc/default/prelink files. 
I've changed that and see what happens next time.
Good day!

---

### Post by xyz on 2006-10-20
> **John Nilsson said:**
> It seems you've put the 'Dpkg::Post-invoke...' line in the wrong file. It should be in /etc/apt/apt.conf not in /etc/default/prelink.
Thanks again John. I can now confirm that that was my problem.

---

### Post by Owdy on 2006-11-14
I used this tutorial to prelink [http://kudos.berlios.de/kf/kisimlar/tipsntrix.html#prelink](http://kudos.berlios.de/kf/kisimlar/tipsntrix.html#prelink)

Is uninstalling same way as in this tutorial? There are that extra '
sudo prelink -avmR' command.

---

### Post by kebajonathan on 2006-12-08
I'm just setting up a pc for my sister and using prelink with kde. I remenber that in gentoo, you had to tell KDE that it was prelinked by setting an option like KDE_IS_PRELINKED="true" in some file. Anyway, that file doesn't exist in Kubuntu so what I want to know is how to tell KDE it is prelinked and whether I need to... Do you know? THX for answers

---

### Post by ciscosurfer on 2006-12-08
@poofyhairguy,

How effective is prelinking on an Edgy system?

---

### Post by &amp;wi*m#~10+q on 2007-02-17
thanx :)

---

### Post by bks on 2007-03-17
This is perfect! I've been fighting with Wine and my latest error is a missing prelink. I will try this and hopefully it will work or at least I'll move on to the next error ](*,)

---

### Post by 98xj on 2007-04-19
just tried prelink with fawn, seems /etc/apt/apt.conf is now a apt.conf.d I put the prelink command into the 70debconf and don't see it run (I can run it from the shell) suggestions ?

---

### Post by llarmakarma on 2007-05-05
Hi, 

Thanks for the howto.

I am not too sure about the line about prelink not being useful on Feisty any more.

I still found a slight speedup running it o Feisty fawn.

Although, i did findit less of an improvement than when I ran prelink on breezy/edgy.

A google found the following information on the subject..

[http://dev.laptop.org/ticket/639](http://dev.laptop.org/ticket/639)

"I'm fairly sure that people are slightly wrong about Ubuntu Feisty.

Ubuntu Feisty is now using DT_GNU_HASH. Fedora Core 6 was the first to use this. It makes run-time linking go faster for apps that use long and highly redundant symbol names. C++ apps are often this way, 
...
[B]
Prelink thus makes much less of a difference. Run-time linking still isn't free though. The time has not been driven to zero, so prelink can still be useful. "[/B]

Regards

---

### Post by robert114 on 2007-05-06
Kebajonathan,

I've googled for the KDE_IS_PRELINKED="true" the only result that I found was in german (not my native language!) But from that forum post I assumed that you just have to enter the command as root in a terminal. I tried it here and didn't receive any error back!

So I think you don't have to edit a config file but you'll just have to enter the "KDE_IS_PRELINKED="true" command.
Correct me if I'm wrong!

Robert

---

### Post by factotum218 on 2007-05-06
great post didnt do much for my system in the gnome environment. after going back to xfce or openbox i did notice a bit of a difference.

I guess those days of eyeing up slackware for my box is coming.

---

### Post by nowshining on 2007-12-24
i'm using gutsy and just openend up gimp and doing it (found it off another site - about prelinking and tried it out) it started up super-fast :P no i don't have compiz on, i recommended this on P4 systems at least as it does help make things in Gutsy much faster..

---

### Post by cooldudevamsee on 2008-07-22
Thanks for the guide.

---

### Post by HellionDarkLord on 2010-01-12
I found this very interesting. so I tried it on my desktop with great results.  Just now I treid it with my laptop and the touchpad didn't like it at all.   So, I decided that I would ```
sudo apt-get remove prelink
```

then I decided that I would run auto clean and auto remove just to make sure that nothing was getting messed up with old packages and kernels.

That didn't work so well, so I commented out the option line that has the -mR options in it and it works beautifully.

thanks for the tip!!

About the prelink erroring after the laptop shut down while it was working this seems like a normal result to me.  Shutting a system down in the middle of any kind of update will cause the same kind of problems.

---

### Post by nxsty on 2010-10-14
Thanks for the guide!

I just wanted to add that this:
> UPDATE 1/2/07: Prelink is no longer necessary in Feisty. Feisty uses a new linking mechanism called DT_GNU_HASH which dramatically speeds up the linking process without the need for continuously running this prelink program. Again, prelink is NOT useful starting from Feisty
.. is **incorrect**.

GNU hash is unrelated to what prelink does and you can still run prelink on a modern linux system, allthough the performance gain is not as good as it used to be with the old SysV hash.

---

### Post by 3ntolo on 2011-04-08
Thanks for the guide!
I tried it and I noticed a sensible improvement on my netbook (Ubuntu 10.10)

Thanks again

---

