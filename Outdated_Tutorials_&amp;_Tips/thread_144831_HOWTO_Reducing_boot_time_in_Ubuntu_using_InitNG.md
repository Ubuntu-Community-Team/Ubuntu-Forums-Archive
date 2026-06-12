---
title: "HOWTO: Reducing boot time in Ubuntu using InitNG"
date: 2006-03-15
forum: Outdated Tutorials &amp; Tips
---

### Post by Trigger|Debian on 2006-03-15
Hi all!

For we have an outdated howto in this forum which is always found by the users I open this thread here.

For information how to install Initng on Ubuntu please read this wiki page: [https://wiki.ubuntu.com/InitNG](https://wiki.ubuntu.com/InitNG)
When you find problems with Initng please open a ticket at [http://initng.thinktux.net/](http://initng.thinktux.net/) and I will try to solve it upstream.

Now try to reboot. :) 
Last step: Tell me what happened.[/INDENT]

When you are running 0.5.5 or 0.6.0 please execute "sudo ng-update a system/modules/depmod system" - otherwise you will have problems with the volatile kernel modules.
[U]
NEWS[/U]
initng 0.6.0 and initng-ifiles is out. [http://triggerit.tr.funpic.de/blog/?p=40](http://triggerit.tr.funpic.de/blog/?p=40) should give you all the Information you need.
Most important part: First install the initnng-ifiles package and afterwards the Initng package!

P.S: More Information will follow here...

---

### Post by yanns on 2006-03-22
Hi!

I'm using initng for bootin.g.

I am now testing it to start / stop services manually.

I tried "sudo ngstart daemon/vmware"
And the result is:

```
This terminal has 80 cols and 24 rows

 Next Generation init Control. version ( 0.5.5 )
 [http://initng.thinktux.net](http://initng.thinktux.net)
 Author: Jimmy Wennlund <jimmy.wennlund@gmail.com>

Starting service:


Warning, service "daemon/vmware" is in status: "DAEMON_FAIL_STARTING"


   [ERROR] -->> Service "daemon/vmware" was failed, but found.
Will not make an attempt to reset service state and try again


Trying to start "daemon/vmware" again ...

Starting service:

   [ERROR] -->> Failed to start service, "daemon/vmware" (DAEMON_WAITING_FOR_START_DEP)

   [ERROR] -->> Failed to start service, "daemon/vmware" (DAEMON_FAIL_STARTING)
```

```
$ sudo ngc -L
[...]
10:19:56 vmware                                : FREEING
10:20:06 deamon/vmware                         : FREEING
10:20:11 daemon/vmware                         : LOADING
10:20:11 daemon/vmware/vmnet                   : LOADING
10:20:11 daemon/vmware/vmnet                   : DAEMON_WAITING_FOR_START_DEP
10:20:11 daemon/vmware/vmnet                   : DAEMON_WAITING_FOR_START_DEP
10:20:11 daemon/vmware                         : DAEMON_WAITING_FOR_START_DEP
10:20:11 daemon/vmware                         : DAEMON_WAITING_FOR_START_DEP
10:20:11 daemon/vmware/vmnet                   : DAEMON_LAUNCH
10:20:11 daemon/vmware/vmnet                   : DAEMON_RUNNING
10:20:11 daemon/vmware/vmnet                   : DAEMON_RUNNING
10:20:11 daemon/vmware                         : DAEMON_LAUNCH
10:20:11 daemon/vmware                         : DAEMON_FAIL_STARTING
10:20:11 daemon/vmware                         : DAEMON_FAIL_STARTING
10:20:11 daemon/vmware/vmnet                   : DAEMON_FAIL_STARTING
10:20:12 daemon/vmware                         : FREEING
10:20:13 daemon/vmware                         : LOADING
10:20:14 daemon/vmware                         : DAEMON_WAITING_FOR_START_DEP
10:20:14 daemon/vmware                         : DAEMON_WAITING_FOR_START_DEP
```

I dunno what's happening... :(
(sudo /etc/init.d/vmware start is ok)

---

### Post by Zeroangel on 2006-03-22
Will the 386 deb package work with the 686 and K7 kernels?

---

### Post by yanns on 2006-03-22
Yes, it's working.
(tested with 686)

---

### Post by Trigger|Debian on 2006-03-22
[QUOTE=Zeroangel]Will the 386 deb package work with the 686 and K7 kernels?[/QUOTE]
Sure.
The Kernel has nothing todo with the user space in this case.

@yanns: IIRC the vmware script is completely broken. Maybe you want to open a ticket at [http://initng.thinktux.net/](http://initng.thinktux.net/)

---

### Post by zgerrz on 2006-03-23
Is there any way to easily modify exactly what InitNG is loading at startup? Such as being able to configure which modules or loading through a config text file?

Also, to upgrade InitNG, could I just use sudo dpkg -i newInitNGversion to upgrade InitNG to the latest version, or have there been problems in upgrading this way? I'd rather not have to reconfigure my loading settings again after an upgrade.

---

### Post by Trigger|Debian on 2006-03-24
Modules loading has nothing to do with Initng directly. You want to have a look at /etc/modules for such things.
If you meant services and daemons: yes, for sure. Everything happens in /etc/initng. There are two runlevels by now. system.runlevel and default.runlevel. This are the files you want to edit. Normally you use "ng-update" (see man "ng-update") but you can also edit them by hand.

Yes, upgrading works via "dpkg -i ...". If you have a running Initng the next reboot can be broken sometimes because of an API change - but I think I have a solution for this with the next release.

---

### Post by zgerrz on 2006-03-24
Ok, now I understand a lot more about configuring InitNG, thanks.

You mentioned it's best to configure the default runlevel. Is it still OK to play around with the system runlevel? For example, I would rather not run ntpdate because if my internet is down, it still continues to attempt to synchronize with the time server anyway.

---

### Post by ninocass on 2006-03-26
is it possible to enable bluetooth;s sdpd to run on startup?

---

### Post by zi99y on 2006-03-27
Having some problems after installing version 0.5.5

When I boot up with the specified bootloader that I have changed for initng, it will crash 50% through bootup on the system/coldplug/scsi line.

I've tried all key combinations I can think of but the only thing I can do at this stage is press ctrl-alt-delete to shutdown/reboot. 

Can anyone tell me where I can look for relevant logs or any other ideas for tracking down the culprit? 

thanks

---

### Post by Trigger|Debian on 2006-03-28
[QUOTE=ninocass]is it possible to enable bluetooth;s sdpd to run on startup?[/QUOTE]
Try to add daemon/bluetooth/sdpd

@zi99y Please try 0.6.0 and if you stillhave the same problem open a ticket on the upstream website.

---

### Post by zi99y on 2006-03-28
Good timing! thanks chief, I'll give it a go tonight and report back.

---

### Post by ninocass on 2006-03-29
worked a treat managed to get my boot time down to less than a minute

now just to figure out what this error means

```

Message from syslogd@localhost at Wed Mar 29 16:01:13 2006 ...
localhost InitNG: "initng_reload.c", write_file() #229 FAIL: Could not open '/usr/var/initng_db_backup.v13' for writing


```

thanks

---

### Post by Trigger|Debian on 2006-03-29
This mean you are running 0.5.5 (I hope this is correct) and should update to 0.6.0. ;)
See first post.

---

### Post by foxy123 on 2006-03-29
I tried 0.60 on Dapper.
1. I had to add gdm manually.
2. I had to change speedstep.
3. I removed debian-ifupdown
3. klogd and cupsd failed to start.

Apart from that it works fine. So the question is what is wrong with cupsd and klogd. klogd did not work in 0.55, but cupsd did.

---

### Post by zi99y on 2006-03-29
Tried the latest version, get a different error when booting and the machine completely freezes now, so I have to hard- reboot. Don't have the time to experiment for now (I've been tinkering constantly and need to do proper work!) Will give it a go another time and report my findings.

---

### Post by yanns on 2006-03-30
Tried 0.6 version with Breezy, and it works very well.

---

### Post by Limulus on 2006-03-30
I've been updating the Wiki and I was just wondering; why is there no PPC version? Is one planned?

---

### Post by idlewild on 2006-03-31
Edit: Apologies for the double posting

---

### Post by idlewild on 2006-03-31
Working well on Dapper. I had to add gdm and NetworkManager to get that started and remove debian-ifupdown though CPU scaling worked out of the box.

Cheers Tigger

---

### Post by glennric on 2006-03-31
I booted with initng, and tried switching to a console with Ctrl-Alt-F2 and then switching back with Ctrl-Alt-F8 and noticed that this does not work.  I had to use ngc -r gdm to restart gdm.  I also tried Ctrl-Alt-Backspace and a similar problem occured.  Does anyone know how to fix this?  Is this an initng bug?  I looked on the bug list and didn't see anything.

---

### Post by Limulus on 2006-04-01
[QUOTE=idlewild]Working well on Dapper. I had to add gdm and NetworkManager to get that started and remove debian-ifupdown though CPU scaling worked out of the box.[/QUOTE]

Cool; I updated the wiki based on your report :)

P.S. Aaarrggh!  My eyes!  What happened to the forum theme?!? X_X

---

### Post by idlewild on 2006-04-01
bootchart isn't working for me under initng. Whats the best way to setup bootchart to boot as early on as possible?

---

### Post by benplaut on 2006-04-02
working great over here, with an up-to-today dapper.

Thank you Trigger!

---

### Post by Haegin on 2006-04-02
[QUOTE=glennric]I booted with initng, and tried switching to a console with Ctrl-Alt-F2 and then switching back with Ctrl-Alt-F8 and noticed that this does not work.[/QUOTE]

Surely you mean Ctrl-Alt-F7 to switch back to GUI?

---

### Post by glennric on 2006-04-02
[QUOTE=Human Prototype]Surely you mean Ctrl-Alt-F7 to switch back to GUI?[/QUOTE]

Actualy I was trying to use Ctrl-Alt-F8 and that was my problem there.  But Ctrl-Alt-Backspace is where the real problem is.  It doesn't successfully restart gdm.  It just stops and I have to use Ctrl-Alt-F2 to get to a console and restart gdm from there.

---

### Post by idlewild on 2006-04-03
To get Dapper's NetworkManager 6.1 to correctly spawn wpa_supplicant (required to connect to any wireless network) I had to change NetworkManager.i to execute /usr/local/sbin/NetworkManager instead of /usr/sbin/NetworkManager.

---

### Post by ChillMonkey on 2006-04-05
most everything works great right away on a mostly default Breezy for me, in addition to the directions on the wiki I added *daemon/NetworkManagerDispatcher* and *daemon/NetworkManager* to get things working.

My wifi card doesn't come up at boot though, so i'm currently trying to fix that. if I manually start *daemon/cardmgr* the card comes to life and NetworkManager takes over. neither *net/eth0* or *system/ifupdown-debian* seem to make a difference.


any tips?

---

### Post by daedalusman on 2006-04-05
Great little program, I got my boot time down to less then a min and it feels so much faster now when it boots. I have only one proble so far with it, cpu freq scaling doesn't work. I am using 0.6.0 and did exactly what the guide says, but my cpu runs at 2.2GHz all the time, it usually runs at 1.0GHz when idle. How can I get this working correctly, do I have to change a setting or what? Thanks for any help and for the great little program.

---

### Post by ncappel1 on 2006-04-06
I am thinking about installing InitNG, but am hesitant because I have many papers to write in the coming weeks. Is it safe to install or do I run significant risk of messing up my boot process resulting in me not being able to get work done until I fix any potential problems?

in short, if I need to do work for upcoming finals, would people recomend me to wait until the summer, when I have more time to fiddle?

---

### Post by verbalshadow on 2006-04-06
ncappel: so long as you add the InitNG stuff to the grub file and don't remove anything( i.e. follow the directions) you will always have the regular boot.

---

### Post by robtotheb on 2006-04-11
Can I safely remove INitiNG using Synaptic?

---

### Post by Limulus on 2006-04-12
[QUOTE=robtotheb]Can I safely remove INitiNG using Synaptic?[/QUOTE]
Yes! :)  In fact, that is a recommended step for upgrading (see [https://wiki.ubuntu.com/InitNG](https://wiki.ubuntu.com/InitNG))

---

### Post by IsSuE on 2006-04-12
i just installed initNG and when i boot, it fails after short time with an error in modprobe: could not load hw_random or something like this. any hints how to fix it?

---

### Post by stc on 2006-04-13
Hi folks!
I have a problem whit ubuntu dapper drake (current) and InitNg 0.6.0. :( 
Cupsd don't start!!!!:confused: 
root@ubuntu:/etc/initng/daemon# ngc --start daemon/cupsd
This terminal has 113 cols and 24 rows

 Next Generation init Control. version ( 0.6.0 )
 [http://initng.thinktux.net](http://initng.thinktux.net)
 Author: Jimmy Wennlund <jimmy.wennlund@gmail.com>

Starting service:

   [ERROR] -->> Failed to start service, "daemon/cupsd" (DAEMON_WAITING_FOR_START_DEP)


How are the DEP?

thanks ;) 

stc
Do YOU have this problem ?

---

### Post by daedalusman on 2006-04-13
Can anyone help me out here, I can't get cpu frequency scalling working. I have enabled both speedstep and powernowd but to no avail. I really don't have a clue at this point. My hardware is listed in my sig. Thanks for any help.

---

### Post by Haegin on 2006-04-24
Hi, I am having problems with HALD, MPD and GDM (and poss others) not loading on startup despite having added them and despite them starting successfully when i try to start them manually (using "sudo ngstart hald" for example)

Any body else having probs and how do I fix them?

---

### Post by Trigger|Debian on 2006-04-24
[QUOTE=Human Prototype]Hi, I am having problems with HALD, MPD and GDM (and poss others) not loading on startup despite having added them and despite them starting successfully when i try to start them manually (using "sudo ngstart hald" for example)[/QUOTE]
Try to check with "ngc -s" which service is failing and which services are just waiting for dependencies.

@all: Tomorrow I will release a nice .deb for 0.6.2 :-)

---

### Post by Haegin on 2006-04-24
Ok, very odd.
mpd is the only one that has reported failing and it reports:
"DAEMON_FAIL_START_RCODE"
whatever that may mean...

---

### Post by Parkotron on 2006-04-29
```
         | sysvinit |  initng
---------|----------|----------
Start Up |   41s    |   31s
Shutdown |   22s    |   15s
```I just installed 0.6.0 and gave it a try. To be entirely honest, the speed increase was not as drastic as I was hoping for, but a 25% percent reduction in startup time is certainly a major improvement. 

There are, however, some serious problems:
[list]
[*]system/speedstep (and therefore daemon/powernowd) refuse to start, which is quite a drag. So much for the "Cool 'n Quiet" on my Athlon64 3000+. It's looking for /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor which does not exist on my system.


[*]Console 1 (Ctrl+Alt+F1) is no longer usable as a console.


[*]Also, net/dsl-provider is failing everytime. This is to be expected, because I no longer use pppoe, but I can't for the life of me find anything containing the term "dsl-provider" in /etc/initng. I've tried removing it with "sudo ng-update d net/dsl-provider", but I am told that it is missing from all runlevels. What exactly is going on here? It's adding 6 full seconds to my startup.[/list]
I realise that the technology is still young, and I like where it's headed, but if it's to be included in Edgy as some have been suggesting, it still needs a lot more pollish. It's certainly a cleaner system to work with, though.

I was also wondering what kind of relative time reductions other people were seeing? Before and after times would be great. Personally, I timed from the GRUB menu to the appearance of the KDM window.

---

### Post by Trigger|Debian on 2006-04-29
@Parkotron net/dsl-provider is started by net/all froem net/net.i (I guess you have configured the interface in /etc/network/interfaces?).

system/speedstep: I don't know why Ubuntu has always problems here, but if omeone finds out what's up there I'm happy to apply it upstream...

console one: this is blocked by Initng right now, that's correct. The main reason is, that a lot of output when starting and stopping a service goes to tty1. We are working on a nicer solution...

---

### Post by Parkotron on 2006-04-29
Thanks for the reply, Trigger.
```
                       NVIDIA Software Installer for Unix/Linux


  WARNING: Skipping the runlevel check (the utility `runlevel` failed to run).

                                           OK



  NVIDIA Software Installer for Unix/Linux                              www.nvidia.com


```
It seems that the NVIDIA driver installer doesn't like InitNG. Shortly after this warning appeared, the installation failed. I rebooted with sysvinit, installed the driver, and rebooted back into InitNG and everything was fine, but this is a bit of any inconvenience.

Obviously, the NVIDIA installer is depending on the 'runlevel' command, which returns "unknown" when run under InitNG. Is this an issue with the installer, InitNG or both?

---

### Post by Trigger|Debian on 2006-04-29
"runlevel -- find the current and previous system runlevel. [...] Runlevel can be used in rc scripts as a substitute for the System-V who -r command."

Hehe, it is definitely a SysV-only tool which doesn't work with Initng. Can you tell me what "runlevel" delivers for you, when you run it with Initng? maybe we need to write a wrapper for it...

---

### Post by Parkotron on 2006-04-30
Under SysVInit:```
[13:43:09] ~ $ runlevel
N 2

```
Under InitNG:```
[13:32:49] ~ $ runlevel
unknown

```
The 'runlevel' command determines the run level information from '/var/run/utmp', so I've also attached a tarball containing two versions of the utmp file: one under each init system. I'm not sure if that's useful to you or not.

================================================

I've also run across some unusual behaviour from the ngc executable. ngc always requires root privileges to run, even when using options that don't change the system. For example, the -h, -S, -l, -L options all require root access, which does make any sense as they only return information. I've never seen any program require root access just to get help before. 'ngc -h' also refuses to run if the system was not initialised with InitNG.

The ng-update executable performs as expected in all the above cases, so this must be a bug in ngc and not a InitNG policy. It appears that ngc is checking for root access and a running InitNG system, before looking at the command line arguments to determine whether that's really necessary.

================================================

While rummaging around in /etc/initng looking at different services and removing those that I don't need on my system, I came up with a feature idea. In addition to the "need =", "use =", etc. lines, .i files could contain an "description =" line. 

The description would be two or three sentences explaining what that service or daemon does and the local url of relevant documentation. An option could then be added to ngc to display this information when a service name is specified.There are two obvious uses for this: semi advanced users (like myself) trying to decided which services can be removed for performance reasons and users with failed services that they don't understand. For example, the user notices that system/speedstep failed to load, but has no idea what speedstep is or how to fix it, so they run 'ngc --desc /system/speedstep' to get relevant information. This information would also be very handy if/when a GUI interface to InitNG is created.

Of course, this brings localisation issues so "desc_en =", "desc_de =", "desc_es =" etc. may be required. Obviously this is a low priority feature, especially considering the relative infancy of InitNG, but it would be another major improvement over the old init system.

================================================

Lastly, I just like to point out that even though I've been pointing out flaws and suggesting improvements, I'm very impressed with InitNG. The performance increases are nice, but more than anything I'm impressed with how clean everything is and how easy it is to work with. I'd really like to see it in Edgy, if only because of the increase in developer attention that would bring.

---

### Post by Trigger|Debian on 2006-05-01
Nice suggestions. Could you copy and paste the different suggestions and open tickets here: [http://www.initng.org/newticket](http://www.initng.org/newticket)?
This way there is a much bigger chance things will be changed.

---

### Post by Jingo on 2006-05-02
Just added the experimental repository to my sources.list.

InitNg 6.3 depends on libc6 (>=2.3.6-6).. breezy uses libc6 2.3.5 !
Is this really nescessary ?
What can I do?
Would you mind compiling for Ubuntu too?

And... anyone tried on Dapper ? Any speed increase?

---

### Post by ncappel1 on 2006-05-02
Just rebooted with initNG 0.6.0, worked perfectly. Boot time has been drastically reduced. There were no problems at all. Thank you very much!

---

### Post by Haegin on 2006-05-02
Dapper seems to have a similar problem with 0.6.3 as the version of the library has been edited by ubuntu so it ichucks up "Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu17 is to be installed".
I think the InitNG team are working on a fix for it.

---

### Post by Resurrection on 2006-05-03
[QUOTE=ncappel1]Just rebooted with initNG 0.6.0, worked perfectly. Boot time has been drastically reduced. There were no problems at all. Thank you very much![/QUOTE]

Same here.  Followed the steps in the wiki and they went off without a hitch.  Boot time cut down 25% to 50%.

Maybe I'll time it between the two (with initNG and without) just because I'm bored.....:-D 

Edit:  Yep I timed it.  Kernel 2.6.12-10-386 (from CD, not compiled) :  97 secs
                             With initNG:  62 secs

10 minutes of install work or less saves me 30secs or about 30% of my boot time, and thats on an old slow computer.

Thanks for this.

Specs of my machine:
HP 510n (about 5 year old machine)
Intel 1.2 Celeron
512 Mb
2 hard drives :  80 Gb (windows) and 40 Gb (Ubuntu)
nVidia 5500 GeForce FX
Ubuntu Breezy

---

### Post by foxy123 on 2006-05-07
yes, a repo version has a dependency problem with Dapper and the downloadable version is outdated :(

---

### Post by Jingo on 2006-05-15
Anything new! still see dependancy problem.

Trigger are you working on it?

---

### Post by Haegin on 2006-05-15
Please say you are...InitNG is too good to miss out on but I cant get it working properly on my machine...

---

### Post by conor on 2006-05-23
InitNG is working on my system but I have a few questions.  Let me preface this with 'I am a technical noob' in the sense that I have used Linux almost two years now and used Ubuntu for most of that time but just do not know the inner workings of the system all that much.  That said, I have no idea what scripts I should be starting with (I am going for a very light xubuntu system).  

Also, I cannot seem to get my ndiswrapper driver to start, I have net/all net/wlan0 net/dhclient and daemon/cardmgr running.  Any suggestions?

---

### Post by Jingo on 2006-05-25
Trigger: Did you stop support for Ubuntu?

Anyone else managed to compile ?
Latest initng needs cmake 2.2 or newer.. breezy has 2.0.5 !!

---

### Post by dabear on 2006-06-04
[http://blog.space-based.de/category/linux/debian/](http://blog.space-based.de/category/linux/debian/)

The repos have changed, but I have two issues:
1)I am not able to find the gpg key

2) initng depends on a version of libc not in the repos, I temporarily overrun the procsss by manually downloading the packages and running
> 
 dpkg --force-depends -i initng-ifiles_0.0.5-2_all.deb  initng_0.6.7-1_i386.deb

> 
dpkg: initng: dependency problems, but configuring anyway as you request:
 initng depends on libc6 (>= 2.3.6-6); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.


edt: and does anyone know how I add support for my battery? I don't know what the boot script's name is.

---

### Post by blueie on 2006-06-05
Hi,

anyone got Initng to work on Dapper with 915resolution support?

Tried initng on breezy a couple of months ago, but quit using it since my resolution got f***ed up.... (using 1400*1050 on intel chipset)

---

### Post by Jingo on 2006-06-07
Anyone got it working under Dapper at all?

I tried compiling it myself (0.6.7) but for some reason it halted at "8% filldev" and have to power off my computer!!

Did you have success with the --force-depends ?

---

### Post by dabear on 2006-06-07
[QUOTE=Jingo]
Did you have success with the --force-depends ?[/QUOTE]
Yeah, worked fine, except that I got a broken catch. Oh, and some stuff like cpu scaling and battery monitor didn't work, although I added their daemons.
 I don't really care anymore, windows had to come back to my laptop, so ubuntu had to ](*,)

---

### Post by D!mon on 2006-06-07
I've compiled and installed 0.6.7+0.0.5 succesfully, but my system fails to start with initNG :( Where can I find initng log to post it here?

---

### Post by Dutch_Wolf on 2006-06-09
I just installed it with the help of the debian repos this is how I did it.

First add these lines to /etc/apt/sources.list
```

deb http://debian.space-based.de/debs/ experimental main
deb-src http://debian.space-based.de/debs/ experimental main

```
Then excute these two lines as with sudo (or as root)
```

apt-get update
apt-get install initng-ifiles

```
Now comes the interesting part
```

sudo apt-get build-dep initng
fakeroot apt-get --compile source initng

```
The first line will get the packages needed to build initng, the second line will get the source and compile initng, making it into a package instalable by dpkg.

(Actually there will be to packages one inting_[version].deb and another initng-dev_[version].deb you only need initng_[version].deb)

Hope this helps some people.

---

### Post by drizek on 2006-06-09
thanks, i just randomly searched for initng on the forum hoping to find a helpfull post and im going to try your method now(i just hope i dont break anything ;))

---

### Post by toaste on 2006-06-11
YAHOO!  Thanks to a little tweaking, I managed to get initng installed, working, and *unbreak the package in synaptic/aptitude!*

**Micro-howto:**

DISCLAIMER!  This worked for me and I haven't seen any ill effects of forcing the dependency problem to go away.  But I take no responsibility for what you do to your system as a result of this guide.  I'm far from being a Linux guru, so double check this before following along!

I installed the debs manually as per [dapbear's post]("http://ubuntuforums.org/showpost.php?p=1093826&postcount=55")

Now we have to cover up the fact that libc6 isn't quite the right version.
```
sudo gedit /var/lib/dpkg/status
```
now search for the entry for the initng package, and change the line:
```

#original:
Depends: libc6 (>= 2.3.6-6), udev
#change to this:
Depends: libc6 (>= 2.3.6), udev
```

After this, aptitude should believe that the installed libc6 version is more than sufficient for initng, and you can get on with more important things.

Like figuring out what daemons need to be loaded to make your sound, accelerated graphics, and networking work!


Thanks to chameleon_789 for the thread on broken packages on apt that showed me where the config file for package dependencies slept: [http://ubuntuforums.org/showthread.php?t=187293&highlight=ignore+broken+package](http://ubuntuforums.org/showthread.php?t=187293&highlight=ignore+broken+package)

As an aside, I hate the way apt deals with broken packages; it ought to complain bitterly about broken-ness, but shouldn't block updates or installs unless the package to be updated depends on a broken package!

---

### Post by drizek on 2006-06-11
I got it installed just fine and it takes a good 30 seconds off my boottime. It gives an error when it is supposed to load hald though, so my pcmcia card wont work, making it pretty damn useless to me. Anyone know a fix?

---

### Post by jerrygofixit on 2006-06-19
sudo apt-get build-dep initng
Reading package lists... Done
Building dependency tree... Done
E: Build-Depends dependency for initng cannot be satisfied because the package cmake cannot be found

Sorry, I don't have cmake(apparently, nor do I know what it is/does), wasn't in the repos, tried getting it from the website but my noobishness proceeds me. Can anyone give me a hand?

---

### Post by xXx 0wn3d xXx on 2006-06-19
[QUOTE=jerrygofixit]sudo apt-get build-dep initng
Reading package lists... Done
Building dependency tree... Done
E: Build-Depends dependency for initng cannot be satisfied because the package cmake cannot be found

Sorry, I don't have cmake(apparently, nor do I know what it is/does), wasn't in the repos, tried getting it from the website but my noobishness proceeds me. Can anyone give me a hand?[/QUOTE]
Do you have the multiverse and universe reporitories enabled ? If not, follow the directions that can be found [ here. ](http://www.psychocats.net/ubuntu/sources.php)

---

### Post by kocio on 2006-06-19
OK, I have both needed packages installed (initng-ifiles from repository and initng build from source package), but I have problems when booting with initng:

1. Machine @work, error messages at start (from ngc -s in 0.6.7):
 * default : START_DEPS_FAILED
 * daemon/acpid : DAEMON_FAIL_START_RCODE
 * daemon/hald : DAEMON_START_DEPS_FAILED
 * net/all : SERVICE_START_DEPS_FAILED
 * net/lo : SERVICE_START_DEPS_FAILED
 * system/ifupdown-debian : SERVICE_FAIL_START_RCODE
 * daemon/cupsd : DAEMON_START_DEPS_FAILED

Also GNOME desktop is almost not usable at all @work, it claims HAL is not working too.

2. Machine @home, error messages at start (from ngc -s in 0.6.7):
 * default : START_DEPS_FAILED
 * net/all : SERVICE_START_DEPS_FAILED
 * net/lo : SERVICE_START_DEPS_FAILED
 * system/ifupdown-debian : SERVICE_FAIL_START_RCODE

But Gnome works @home as expected, just the network is down.

Can anybody tell me how to check what's wrong and how to "debug" these errors? Both machines are Ubuntu Dapper with current updates.

---

### Post by givré on 2006-06-19
Ok,
so first, we need to know what is your runlevel: copy here your /etc/initng/system.virtual and your /etc/initng/default.runlevel.
To have more debug information, copy here the result of ```
sudo ngc -l
```

---

### Post by kocio on 2006-06-19
Default config files were not changed in any way on neither machine. 

Thank you very much for the hint with "ngc -l", however! I've found (@home) that there were some files missing. After creating folder "/etc/network/run/" and touching file "ifstate" inside it, networking ("eth0") got started, and when file "/var/run/network/ifstate" automagically appeared, also "lo" interface became running, and the next booting showed no error. However when rebooting system, initng stops for 15 s showing an error with alsa (probably missing /etc/asound.state - I've tried just touching it, but that caused errors during start).

So I think the problems in (my) Dapper are missing folder "/etc/network/run/" and file "/etc/asound.state", containing probably mixer configuration. If these problems can be reproduced on fresh Dapper system, I think some packages for Ubuntu should be tweaked to run smooth with initng, and these issues should be added on Ubuntu InitNG Wiki page.

I will check @work machine soon.

**UPDATE:**

I was playing with @work machine and found that:
* "hald" requires starting "acpi", but I had ACPI support turned off in BIOS; turning it on resolved problem, but I don't think this is sane, IMHO hald should be available even if the computer doesn't use ACPI at all
* it's sufficient just to "mkdir /etc/network/run/" and the network starts up
* "system/alsasound/mixerstate" service have to be "ubuntized", since it looks for two files in wrong places: "/etc/asound.state" (Dapper holds it as "/var/lib/alsa/asound.state") and "/usr/sbin/alsactl" ("/sbin/alsactl" in Dapper); removing this service is the simplest way to start with no errors

So, I'd like to ask how should we deal with these problems? Should we better have "ubuntized" package or report it as bugs upstream?

---

### Post by givré on 2006-06-20
Okay, great job man, so here my sugestion too:

- Dapper don't need ifupdown-debian, this is a debian-only script (and for breezy), so we should say to remove it from the runlevel

- We have to tell the initng dev that dapper work with /var/lib/alsa/asound.state and /usr/sbin/alsactl, it's quite simple to change. In fact i changed it at the beginning, but i didn't remember it.

- For the hal thing, if you disable acpi, you have to remove acpid from the runlevel, initng work with two way of dependency : need and use; need require script, but use require them only if they are in the runlevel, and acpid is use by hald.

EDIT: /var/lib/alsa/asound.state is not a problem, it will create the corresponding /etc/asound.state
but alsatcl is an issue, i will contact the initng guys.

---

### Post by givré on 2006-06-20
I just created a package to add the usplash support in intng. This is not compile by default, and so i compile it from the source and make a quick package (with checkinstall, so quite bad:no dependency rule)
IMPORTANT: You will need at least initng-0.6.7 install

[U]So how to have real usplash with initng (not just the image :cool: )
[/U]
1: First download the package attach, extract it and install it.

2: Change your kernel line:
```
sudo gedit /boot/grub/menu.lst
```
At the end, in your intng entry change the option of your kernel line to something like that
```
ro quiet init=/sbin/initng-usplash splash
```

3: To have usplash at shutdown, add usplash to the runlevel
```
sudo ng-update a usplash
```

4: Restart and enjoy.

I need your feedback. If this work for you, i will add this to the wiki page

---

### Post by drizek on 2006-06-20
thanks. Ill try that out in a little while.

---

### Post by kocio on 2006-06-21
givré, I have tried initng-usplash package and it works. My notes:

* system starts with splash Ok, but I have some minor issues:
 - I just don't like two lines introducing init ("InitNG...." and "by...") - they're harmless, but IMHO not needed here, at least the second one
 - there's inconsistency in messages we should consider: "Checking foobar... ok" vs. "system/foobar UP" - it just looks different; BTW: do you know how to prepare l10n of init/initng/initng-splash?
 - something more annoying: after keymaps are up, initng-usplash goes to text mode for a while and prints something about 3 services, however it's too fast to write it down; anyway the text mode should not be visible at all

* when rebooting system first shows nice splash, but every time the graphic gets immediately screwed and due to some errors it goes back to text mode again; if I know where to look what went wrong, I'll post you some details about it

* probably not related to that, but we have more file mislocations in .i scripts: 
 - system/alsasound/cards: bash_helper[system/alsasound/cards]: line 5: /usr/sbin/lsmod: No such file or directory
 - system/alsasound/cards: bash_helper[system/alsasound/cards]: line 5: /usr/sbin/modprobe: No such file or directory
 - daemon/acpid/modules: bash_helper[daemon/acpid/modules]: line 23: /usr/sbin/modprobe: No such file or directory

* probably also not directly realated to initng, but sometimes everything gets veeery slooow, and some lines scrolling looks like done pixel-by-pixel, not line-by-line - it also happens sometimes with plain init; any idea what could it be?

I suppose we should have Ubuntu package of initng with different default.runlevel, suited for our needs (removed debian specific services) and reflecting original Ubuntu init services as close as it's possible (for example starting gdm is default on desktop). Do you plan to prepare such packages or maybe are you in contact with the packager? If I can help somehow just tell me. :)

---

### Post by givré on 2006-06-21
> **kocio]givré, I have tried initng-usplash package and it works. My notes:

 - something more annoying: after keymaps are up, initng-usplash goes to text mode for a while and prints something about 3 services, however it's too fast to write it down said:**
> 
That's right, text mode reappear when console-screen is up. In fact the same thing appear with init, but screen is black, it's could be good if the same thing could be done with initng, i'll fill a bug (when i'll have time :cool: )
[QUOTE=kocio]
* when rebooting system first shows nice splash, but every time the graphic gets immediately screwed
Are you using aiglx, it appears that the patch they add to gnome-session make the problem. try to reboot with *sudo reboot* to be sure  
> **kocio]
and due to some errors it goes back to text mode again said:**
> 
Yes i don't know what is the problem there. Normaly initng have is own killall, so usplash is not kill by killall at shutdoown, but it seams that the problem is something else.

[QUOTE=kocio]
* probably not related to that, but we have more file mislocations in .i scripts: 
 - system/alsasound/cards: bash_helper[system/alsasound/cards]: line 5: /usr/sbin/lsmod: No such file or directory
 - system/alsasound/cards: bash_helper[system/alsasound/cards]: line 5: /usr/sbin/modprobe: No such file or directory
 - daemon/acpid/modules: bash_helper[daemon/acpid/modules]: line 23: /usr/sbin/modprobe: No such file or directory
We definitly need ubuntu specific package, that something me and others request for a long time to trigger (the debian packager of initng), and he said that he will done it, but we are still waiting, join #initng on irc.freenode.net to ask it, if more people ask for it, it will accelerate the process.
> **kocio]
* probably also not directly realated to initng, but sometimes everything gets veeery slooow, and some lines scrolling looks like done pixel-by-pixel, not line-by-line - it also happens sometimes with plain init said:**
> Can't say, what is your graphical card? for nvidia and ati card, you will need to add system/module/depmod to your runlevel
[QUOTE=kocio]
I suppose we should have Ubuntu package of initng with different default.runlevel, suited for our needs (removed debian specific services) and reflecting original Ubuntu init services as close as it's possible (for example starting gdm is default on desktop). Do you plan to prepare such packages or maybe are you in contact with the packager? If I can help somehow just tell me. :)
Definitly, but my knowladge to packaging is too small for that, trigger is the man for that, and we could help him if he want. join #initng, he will probably be there.

---

### Post by ashrack on 2006-06-22
Got initNG working great. But the problem I have now is with the repos:

whenever I do 'apt-get update' this is the error I get:
```
W: GPG error: http://debian.space-based.de experimental Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EB020D4677AFC5B7
W: You may want to run apt-get update to correct these problems

```

where to find this GPG key??

---

### Post by givré on 2006-06-22
I had the usplash HowTo to the wiki page.
[https://help.ubuntu.com/community/InitNG](https://help.ubuntu.com/community/InitNG) 8) 
This begin to be really cool, we just need a real ubuntu package now ;)

---

### Post by haani on 2006-06-22
when i install initng and i reboot my Video drivers and wireless doesnt work and the laptop goes really slow!! it takes about 5 mins till i see all my icons and panels!!

---

### Post by givré on 2006-06-22
Did you follow the howto in the wiki for 0.6.7?
[https://help.ubuntu.com/community/InitNG](https://help.ubuntu.com/community/InitNG)
If yes, to see the error you have , do ngc -l in a terminal.
Also check in /etc/initng/default.runlevel that you have system/modules/depmod

---

### Post by drizek on 2006-06-23
[QUOTE=ashrack]Got initNG working great. But the problem I have now is with the repos:

whenever I do 'apt-get update' this is the error I get:
```
W: GPG error: http://debian.space-based.de experimental Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EB020D4677AFC5B7
W: You may want to run apt-get update to correct these problems

```

where to find this GPG key??[/QUOTE]

doesnt matter. you will just have to press yes  every time you install a package from that distro.

---

### Post by givré on 2006-06-23
Ok, i just updated the wiki, because of an **important problem** with modprobe, the path is different between ubuntu and debian, and that could cause some failure.
If you already install initng-ifile 0.5 from the repository, execute the command
```
sudo ln -s /sbin/modprobe /usr/sbin/modprobe
```
yeah, that's a bad fix, but that's easyer than changing all the ifiles 8) 

@haani : Your problem is probably because of that, try it

---

### Post by haani on 2006-06-23
still the same problem i installed initng_0.6.7-1_i386 with force install becasue it wouldnt install noramal way gives this error```
dpkg: dependency problems prevent configuration of initng:
 initng depends on libc6 (>= 2.3.6-6); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.

```

than i did this as mentioned by toaste

```
Now we have to cover up the fact that libc6 isn't quite the right version.
Code:

sudo gedit /var/lib/dpkg/status

now search for the entry for the initng package, and change the line:
Code:

#original: Depends: libc6 (>= 2.3.6-6), udev #change to this: Depends: libc6 (>= 2.3.6), udev


```

after i followed the instructions on [https://help.ubuntu.com/community/InitNG](https://help.ubuntu.com/community/InitNG)

and i have noticed no increase in boot time it takes the same amount of time to boot as it did before takes about 20 sec to boot in normal so i dont see no point in installin this?

---

### Post by givré on 2006-06-23
20 second is already quite fast, not sure that you can do faster than that.
The bigger improvement you can see is on breezy, but because they improve a lot the boot process in dapper, it's already quite fast.
But anyway, for me with dapper,
normal boot = 1min (until gdm)
initng boot = 35 s (until gdm)
At shutdown :
normal = 20 s
initng = 4 s (no kidding, it's there that you can see the power of initng)

1. See that you don't have an error at boot time : sudo ngc -L
2. Did you the modprobe thing ?

---

### Post by givré on 2006-06-23
Just add a link in the wiki to a package of ining-conf-gtk, a great apps made by Daniel Malmgren to configure InitNG. Tell me how do you find it.

I also clean a bit the wiki, i don't think we need all this deprecated information. Say me if i was wrong.

---

### Post by haani on 2006-06-23
[QUOTE=givré]20 second is already quite fast, not sure that you can do faster than that.
The bigger improvement you can see is on breezy, but because they improve a lot the boot process in dapper, it's already quite fast.
But anyway, for me with dapper,
normal boot = 1min (until gdm)
initng boot = 35 s (until gdm)
At shutdown :
normal = 20 s
initng = 4 s (no kidding, it's there that you can see the power of initng)

1. See that you don't have an error at boot time : sudo ngc -L
2. Did you the modprobe thing ?[/QUOTE]

yes i did the modprobe thing but still the same problem!!

---

### Post by sewpafly on 2006-06-24
I'm having a couple of problems with initng.  I followed the wiki instructions to the letter but I'm still having some issues.

First, my wifi is not working anymore.  (I originally followed [this guide]("http://ubuntuforums.org/showthread.php?p=1071920&mode=linear") to get it working.)  So looking through this thread I thought I might be able to handle it, but instead I'm seeing these problems when I do a 'ngc -L'.
```

 14:36:48 S net/lo                              : SERVICE_FAIL_START_RCODE
 14:36:48 D daemon/cupsd                        : DAEMON_START_DEPS_FAILED
 14:36:48 D daemon/hpiod                        : DAEMON_START_DEPS_FAILED
 14:36:48 D daemon/hpssd                        : DAEMON_START_DEPS_FAILED
 14:36:48 S system/speedstep                    : SERVICE_FAIL_START_RCODE
 14:36:50 V system                              : START_DEPS_FAILED
 14:36:52 R default                             : START_DEPS_FAILED
 14:37:50 D daemon/dhcdbd                       : DAEMON_FAIL_START_TIMEOUT_PIDFILE
 14:37:50 D daemon/NetworkManager               : DAEMON_START_DEPS_FAILED
 14:37:50 D daemon/NetworkManagerDispatcher     : DAEMON_START_DEPS_FAILED
```

(2) When I pull up a terminal after startup I get this message:
```

Message from syslogd@localhost at Sat Jun 24 14:37:50 2006 ...
localhost InitNG: "/home/xxxxx/initng-0.6.7/plugins/daemon/initng_daemon.c", timeout_DAEMON_WAIT_FOR_PID_FILE() #765 FAIL: Service "daemon/dhcdbd" wait for pidfile timed out! Will kill daemon now.

Message from syslogd@localhost at Sat Jun 24 14:37:50 2006 ...
localhost InitNG: "/home/xxxxx/initng-0.6.7/plugins/daemon/initng_daemon.c", kill_daemon() #973 FAIL: Trying to kill a service (daemon/dhcdbd) with a pid (3575), but there exists no process with this pid!
```

Third, I tried to reload with sysvinit (the kernel entry without the init=/sbin/initng) and the wireless still doesn't work.  Do I need to add net/all back to the default run level stuff for that to work?

Fourth, it looks like there's a problem when I shutdown/reboot (when my fat32 partition is unmounted).  I say this because I see a fail on shutdown of unmounting the drives and a couple text files that I had written to that drive don't exist but I have a series of fsck####.rec.  I haven't looked in depth at this issue, but I think that it's related to the initng stuff because I hadn't seen this problem before.  But that's just speculation.  Where would I find a log of the shutdown steps?

Any ideas?

---

### Post by givré on 2006-06-24
Ok, so apparently, you have two problem net/lo and 

- For the first one, be sure that you don't comment the line about lo in /etc/network/interfaces. It should look something like that 
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
# auto eth1

# iface eth1 inet dhcp

```
If it's not that, past there the result of 'ngc -l' (more information, but past only things about net/lo)

- So now for dhcbd, in fact you are probably one of the first in dapper to try this script, so apparently, it's not working great. Before 0.6.7, one gui in the wiki write a script to launch this daemon, but in the latest version, initng' guis provide a script for that, and i belived that we didn't need to change things. Apparently that's not yet the case. So try to change  /etc/initng/daemon/dhcdbd.i to that ```
daemon daemon/dhcdbd {
        need = system/bootmisc daemon/hald;
        use = system/modules system/coldplug;

        script daemon = {
                exec /sbin/dhcdbd --no-daemon --system
        };
}
```
If it works, i will change the wiki to add that

---

### Post by sewpafly on 2006-06-25
So, the dhcdbd script worked (apparently anyway, I don't know what that service is for).  But now I'm getting this error, and it appears I'm just getting the last error sent to the console.
```
Message from syslogd@localhost at Sat Jun 24 21:50:58 2006 ...
localhost InitNG: "/home/xxxxx/initng-0.6.7/plugins/daemon/initng_daemon.c", timeout_DAEMON_WAIT_FOR_PID_FILE() #765 FAIL: Service "daemon/NetworkManager" wait for pidfile timed out! Will kill daemon now.

Message from syslogd@localhost at Sat Jun 24 21:50:58 2006 ...
localhost InitNG: "/home/xxxxx/initng-0.6.7/plugins/daemon/initng_daemon.c", kill_daemon() #973 FAIL: Trying to kill a service (daemon/NetworkManager) with a pid (3724), but there exists no process with this pid!
```

I wasn't sure from your comment about how the interfaces should look, so I'm pasting it in it's entirety. ( removed blank lines )
```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0
auto eth0
iface eth0 inet dhcp
iface eth1 inet dhcp
wireless-essid myessid
auto eth2
iface eth2 inet dhcp
auto ath0
iface ath0 inet dhcp
auto wlan0
iface wlan0 inet dhcp
auto eth1
```

ngc -l
```
 21:49:53               net/lo : *OUTPUT*
/sbin/ifup: failed to open statefile /var/run/network/ifstate: No such file or directory
 21:49:53               net/lo : SERVICE_FAIL_START_RCODE
 21:49:53         daemon/cupsd : DAEMON_START_DEPS_FAILED
 21:49:53         daemon/hpiod : DAEMON_START_DEPS_FAILED
 21:49:53         daemon/hpssd : DAEMON_START_DEPS_FAILED
 21:49:53           system/usb : SERVICE_DONE
 21:49:53     system/speedstep : *OUTPUT*
/bin/cat: /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor: No such file or directory
bash_helper[system/speedstep]: line 1: /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor: No such file or directory
 21:49:53     system/speedstep : SERVICE_FAIL_START_RCODE
 21:49:53 daemon/syslogd/prepare : SERVICE_DONE
 21:49:53       daemon/syslogd : DAEMON_RUNNING
 21:49:53       virtual/syslog : PROVIDED
 21:49:53         daemon/klogd : DAEMON_RUNNING
 21:49:53       system/anacron : SERVICE_DONE
 21:49:53 daemon/NetworkManager/prepare : SERVICE_DONE
 21:49:54 system/alsasound/cards : SERVICE_DONE
 21:49:54     system/alsasound : SERVICE_DONE
 21:49:55 daemon/acpid/modules : *OUTPUT*
FATAL: Error inserting asus_acpi (/lib/modules/2.6.15-25-386/kernel/drivers/acpi/asus_acpi.ko): No such device
 21:49:55 system/alsasound/mixerstate : SERVICE_DONE
 21:49:55       system/urandom : SERVICE_DONE
 21:49:55   system/laptop-mode : SERVICE_DONE
 21:49:55               system : START_DEPS_FAILED
 21:49:55          daemon/dbus : DAEMON_RUNNING
 21:49:55 daemon/acpid/modules : *OUTPUT*
FATAL: Error inserting ibm_acpi (/lib/modules/2.6.15-25-386/kernel/drivers/acpi/ibm_acpi.ko): No such device
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.15-25-386/kernel/drivers/acpi/toshiba_acpi.ko): No such device
 21:49:56 daemon/acpid/modules : SERVICE_DONE
 21:49:56         daemon/acpid : DAEMON_RUNNING
 21:49:57          daemon/hald : DAEMON_RUNNING
 21:49:57       system/keymaps : SERVICE_DONE
 21:49:57              default : START_DEPS_FAILED
 21:49:57        daemon/dhcdbd : DAEMON_RUNNING
 21:49:57 system/console-screen : *OUTPUT*
]RSetting up general console font ... 
set_kernel_font: Invalid argument
 failed.
Setting up per-VC fonts ... 
/dev/tty2, /dev/tty3, /dev/tty4, /dev/tty5, /dev/tty6, [9;30][14;30]KDSKBENT: Invalid argument
failed to bind key 18 to value 61604
KDSKBENT: Invalid argument
failed to bind key 46 to value 61602
 21:49:59 system/console-screen : SERVICE_DONE
 21:50:58 daemon/NetworkManager : DAEMON_FAIL_START_TIMEOUT_PIDFILE
 21:50:58 daemon/NetworkManagerDispatcher : DAEMON_START_DEPS_FAILED
```

---

### Post by newman on 2006-06-25
I tried InitNG, but couldn't get madwifi ath0 working and gave up...

---

### Post by givré on 2006-06-25
@sewpafly
- For the network manager, follow that [https://help.ubuntu.com/community/WifiDocs/NetworkManager#dapper](https://help.ubuntu.com/community/WifiDocs/NetworkManager#dapper) to configure your /etc/network/interfaces. It will not work until you don't comment the line of the interface you want to control with NM.
You will probably have always the pidfill error, but anyway, the daemon is running so that's fine. I will try to find a better solution after

- For net/lo, in fact, this one is launch by cupsd, but the cupsd script is deprecated, so we need to change it:
```
sudo gedit /etc/initng/daemon/cupsd.i
```Change the line ```
need = system/bootmisc net/lo;
```to```
need = system/bootmisc virtual/net;
```
That should be ok (it works for me)

Say me how it works, i will change the wiki if it's ok

---

### Post by sewpafly on 2006-06-25
Well it appears that nothing changed in the 'ngc -l' output (below).  But I'm attaching a picture of the network Manager that it appears to be running and seeing the networks, however when I choose mine, I still can't access the internet.  I don't know if this is a question for a different thread, but since the net/lo issues still don't seem to be resolved, I think that there is still something here that needs to be fixed.  Also, why would the network manager start when the ngc -l says that it failed?
```
 12:19:51               net/lo : *OUTPUT*
/sbin/ifup: failed to open statefile /var/run/network/ifstate: No such file or directory
 12:19:51     system/speedstep : *OUTPUT*
/bin/cat: /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor: No such file or directory
bash_helper[system/speedstep]: line 1: /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor: No such file or directory
 12:19:51               net/lo : SERVICE_FAIL_START_RCODE
 12:19:51     system/speedstep : SERVICE_FAIL_START_RCODE
 12:19:51         daemon/hpiod : DAEMON_START_DEPS_FAILED
 12:19:51         daemon/hpssd : DAEMON_START_DEPS_FAILED
 12:19:51         daemon/cupsd : DAEMON_START_DEPS_FAILED
 12:19:51 daemon/syslogd/prepare : SERVICE_DONE
 12:19:51       daemon/syslogd : DAEMON_RUNNING
 12:19:51       virtual/syslog : PROVIDED
 12:19:51         daemon/klogd : DAEMON_RUNNING
 12:19:51 daemon/NetworkManager/prepare : SERVICE_DONE
 12:19:51           system/usb : SERVICE_DONE
 12:19:51       system/anacron : SERVICE_DONE
 12:19:52 system/alsasound/cards : SERVICE_DONE
 12:19:52     system/alsasound : SERVICE_DONE
 12:19:52 system/alsasound/mixerstate : SERVICE_DONE
 12:19:52 daemon/acpid/modules : *OUTPUT*
FATAL: Error inserting asus_acpi (/lib/modules/2.6.15-25-386/kernel/drivers/acpi/asus_acpi.ko): No such device
 12:19:52       system/urandom : SERVICE_DONE
 12:19:53   system/laptop-mode : SERVICE_DONE
 12:19:53               system : START_DEPS_FAILED
 12:19:53 daemon/acpid/modules : *OUTPUT*
FATAL: Error inserting ibm_acpi (/lib/modules/2.6.15-25-386/kernel/drivers/acpi/ibm_acpi.ko): No such device
 12:19:54          daemon/dbus : DAEMON_RUNNING
 12:19:54 daemon/acpid/modules : *OUTPUT*
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.15-25-386/kernel/drivers/acpi/toshiba_acpi.ko): No such device
 12:19:54 daemon/acpid/modules : SERVICE_DONE
 12:19:54         daemon/acpid : DAEMON_RUNNING
 12:19:54       system/keymaps : SERVICE_DONE
 12:19:54 system/console-screen : *OUTPUT*
]RSetting up general console font ... 
set_kernel_font: Invalid argument
 failed.
Setting up per-VC fonts ... 
/dev/tty2,  12:19:55          daemon/hald : DAEMON_RUNNING
 12:19:55              default : START_DEPS_FAILED
 12:19:55        daemon/dhcdbd : DAEMON_RUNNING
 12:19:55 system/console-screen : *OUTPUT*
/dev/tty3, /dev/tty4, /dev/tty5, /dev/tty6, [9;30][14;30] 12:19:55 system/console-screen : SERVICE_DONE
 12:20:56 daemon/NetworkManager : DAEMON_FAIL_START_TIMEOUT_PIDFILE
 12:20:56 daemon/NetworkManagerDispatcher : DAEMON_START_DEPS_FAILED

```

---

### Post by givré on 2006-06-25
- Ok i underdstand the problem, it's because hpiod also have need=/net/lo.
But anyway, changing that to virtual/net is not in fact the better thing, because it need only lo and not all the network. So we will change that with something more elegant.
The problem is that /net/all script test if /var/run/network/ exist, but not /net/lo, and not everybody need net/all (like you), so we have to change /net/lo:
```
sudo gedit /etc/initng/net/net.i

```
In service net/lo, change 
```
exec start = /sbin/ifup lo;
exec stop = /sbin/ifdown lo;
```
to
```
script start = {
	mkdir -p /var/run/network
	/sbin/ifup lo;
};
script stop = {
	/sbin/ifdown lo;
};
```
I will report that to the initng guys.
And change also, what you change before in cupsd.i from virtual/net to virtual/net/lo (they just change that in svn)

- I have also a solution to the pidfile problem with NM, in fact initng don't search in the good place. Let's change that
```
sudo gedit /etc/initng/daemon/NetworkManager.i
```
And change ```
pid_file = /var/run/NetworkManager.pid;
```
to ```
pid_file = /var/run/NetworkManager/NetworkManager.pid
```

Yeah, lot's of thing to change, but that's still a beta soft :cool:

---

### Post by sewpafly on 2006-06-25
Wireless is working!  (For some reason though, after I applied your changes, the scripts weren't creating the NetworkManager directory.  After I created the /var/run/NetworkManager directory it started working without any problems.)

The other problems that I see in the ngc -l are:
```
 18:02:42     system/speedstep : *OUTPUT*
/bin/cat: /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor: No such file or directory
bash_helper[system/speedstep]: line 1: /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor: No such file or directory
 18:02:42     system/speedstep : SERVICE_FAIL_START_RCODE

 18:02:43 daemon/acpid/modules : *OUTPUT*
FATAL: Error inserting asus_acpi (/lib/modules/2.6.15-25-386/kernel/drivers/acpi/asus_acpi.ko): No such device

 18:02:43 daemon/acpid/modules : *OUTPUT*
FATAL: Error inserting asus_acpi (/lib/modules/2.6.15-25-386/kernel/drivers/acpi/asus_acpi.ko): No such device

 18:02:44 daemon/acpid/modules : *OUTPUT*
FATAL: Error inserting ibm_acpi (/lib/modules/2.6.15-25-386/kernel/drivers/acpi/ibm_acpi.ko): No such device
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.15-25-386/kernel/drivers/acpi/toshiba_acpi.ko): No such device

 18:02:46 system/console-screen : *OUTPUT*
]RSetting up general console font ... 
 18:02:47 system/console-screen : *OUTPUT*
set_kernel_font: Invalid argument
 failed.
Setting up per-VC fonts ... 
/dev/tty2, /dev/tty3, /dev/tty4, /dev/tty5, /dev/tty6, [9;30][14;30] 18:02:49 system/console-screen : SERVICE_DONE
 18:02:49              default : START_DEPS_FAILED

```

Is this something I should be worried about?  Is it fixable?

---

### Post by souled on 2006-06-25
Using ctrl+shift+backspace kills the xserver, but it will not restart it... Is there a fix for this?

---

### Post by Burke on 2006-06-25
Well, my boot is actually still 44 seconds with initNG -- about the same as init.

I had a look at ngc -l, and I noticed quite a few errors.

```

FATAL: Error inserting ibm_acpi (/lib/modules/2.6.15-25-k7/kernel/drivers/acpi/ibm_acpi.ko): No such device
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.15-25-k7/kernel/drivers/acpi/toshiba_acpi.ko): No such device
FATAL: Error inserting asus_acpi (/lib/modules/2.6.15-25-k7/kernel/drivers/acpi/asus_acpi.ko): No such device
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-25-k7/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
/dev/hda2 was not cleanly unmounted, check forced.

```

(if it matters, these are in reverse chronological order)

So, I have ndiswrapper listed in /etc/modprobe.d/blacklist, but it's loading here. Why? How do I disable it? Why are all these acpi modules failing? (I have a Gateway MX7525 notebook). I assume most are not there, so how do I disable them? (I'm booting with noapic if that makes a difference...) Also, when I shut down, /dev/hda2 (/boot) appears to not be cleanly unmounted. Why?

Finally, why does this still take 44s on my AMD Athlon64 4000+? (running dapper32)

Thanks for helping, I'm pretty clueless about this stuff.

I posted my whole ngc -l below in case it's relevant.


Thanks again!


```
 initNGControl (0.6.7 ) by Jimmy Wennlund http://www.initng.org/


 hh:mm:ss    service           :  STATUS
 ------------------------------------------------------
 21:34:15 system/initial/loglevel : SERVICE_DONE
 21:34:15 system/initial/mountvirtfs : *OUTPUT*
mount: proc already mounted
mount: sys already mounted or /sys busy
mount: according to mtab, none is already mounted on /sys
 21:34:15 system/initial/mountvirtfs : SERVICE_DONE
 21:34:15 system/udev/mountdev : SERVICE_DONE
 21:34:15 system/initial/filldev : *OUTPUT*
Mounting devpts at /dev/pts ...
Mounting devshm at /dev/shm ...
 21:34:15 system/initial/filldev : SERVICE_DONE
 21:34:15    system/udev/udevd : DAEMON_RUNNING
 21:34:15 system/udev/set_hotplug : SERVICE_DONE
 21:34:18  system/udev/filldev : SERVICE_DONE
 21:34:18          system/udev : UP
 21:34:18       system/initial : UP
 21:34:18      system/hostname : *OUTPUT*
Setting hostname to 'burke-gw-ubuntu'
 21:34:18        system/sysctl : SERVICE_DONE
 21:34:18      system/hostname : SERVICE_DONE
 21:34:18 system/mountroot/check : *OUTPUT*
Checking root filesystem ...
Filesystem seems mounted read-only. Skipping journal replay.
Checking internal tree..finished
Reiserfs super block in block 16 on 0x304 of format 3.6 with standard journal
Blocks (total/free): 16079056/9934906 by 4096 bytes
Filesystem is clean
Reiserfs super block in block 16 on 0x304 of format 3.6 with standard journal
Blocks (total/free): 16079056/9934906 by 4096 bytes
Filesystem is clean
Done checking root file system.
 21:34:23 system/mountroot/check : SERVICE_DONE
 21:34:23 system/mountroot/rootrw : *OUTPUT*
/dev/hda4 on / type reiserfs (rw,noatime,data=writeback)
 21:34:23 system/mountroot/rootrw : SERVICE_DONE
 21:34:24     system/mountroot : *OUTPUT*
Mounting / rw ...
Mounting /proc rw ...
 21:34:24     system/mountroot : SERVICE_DONE
 21:34:24       system/checkfs : *OUTPUT*
Checking file systems
 21:34:24 system/modules/depmod : *OUTPUT*
Found modules.dep, skipping depmod ...
Module dependencies up to date ...
 21:34:24       system/checkfs : *OUTPUT*
open /dev/sdb1:No such file or directory
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hda2 was not cleanly unmounted, check forced.
/dev/hda2: 40/68272 files (10.0% non-contiguous), 36578/136521 blocks
/sbin/fsck died with exit status 1
 21:34:26       system/checkfs : SERVICE_DONE
 21:34:26       system/mountfs : *OUTPUT*
Mounting local filesystems
mount: special device /dev/sdb1 does not exist
/dev/hda2 on /boot type ext2 (rw)
code 96
 21:34:27       system/mountfs : SERVICE_DONE
 21:34:27     system/rmnologin : SERVICE_DONE
 21:34:27          system/swap : SERVICE_DONE
 21:34:29 system/modules/depmod : SERVICE_DONE
 21:34:29       system/modules : *OUTPUT*
Loading module "lp" ...
 21:34:29 system/modules/usbcore : SERVICE_DONE
 21:34:29       system/modules : *OUTPUT*
Loading module "psmouse" ...
Loading module "sbp2" ...
Loading module "sr_mod" ...
Loading module "ndiswrapper" ...
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-25-k7/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
 21:34:29       system/modules : SERVICE_DONE
 21:34:31         system/clock : SERVICE_DONE
 21:34:31      system/bootmisc : SERVICE_DONE
 21:34:31       daemon/getty/2 : DAEMON_RUNNING
 21:34:31       daemon/getty/3 : DAEMON_RUNNING
 21:34:31       daemon/getty/4 : DAEMON_RUNNING
 21:34:31       daemon/getty/5 : DAEMON_RUNNING
 21:34:31       daemon/getty/6 : DAEMON_RUNNING
 21:34:31           daemon/gdm : DAEMON_RUNNING
 21:34:31      virtual/getty/2 : PROVIDED
 21:34:31      virtual/getty/3 : PROVIDED
 21:34:31      virtual/getty/4 : PROVIDED
 21:34:31      virtual/getty/5 : PROVIDED
 21:34:31      virtual/getty/6 : PROVIDED
 21:34:31           virtual/dm : PROVIDED
 21:34:31         daemon/getty : UP
 21:34:31           system/usb : SERVICE_DONE
 21:34:31 system/alsasound/cards : SERVICE_DONE
 21:34:31     system/alsasound : SERVICE_DONE
 21:34:31 daemon/syslogd/prepare : SERVICE_DONE
 21:34:31       daemon/syslogd : DAEMON_RUNNING
 21:34:31       virtual/syslog : PROVIDED
 21:34:31         daemon/klogd : DAEMON_RUNNING
 21:34:32       system/anacron : SERVICE_DONE
 21:34:32 system/alsasound/mixerstate : SERVICE_DONE
 21:34:32       system/urandom : SERVICE_DONE
 21:34:32 daemon/acpid/modules : *OUTPUT*
FATAL: Error inserting asus_acpi (/lib/modules/2.6.15-25-k7/kernel/drivers/acpi/asus_acpi.ko): No such device
 21:34:32            device/lo : NIC_UP
 21:34:32               net/lo : SERVICE_DONE
 21:34:32 daemon/acpid/modules : *OUTPUT*
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.15-25-k7/kernel/drivers/acpi/toshiba_acpi.ko): No such device
 21:34:33          daemon/dbus : DAEMON_RUNNING
 21:34:33          device/eth0 : NIC_UP
 21:34:33   system/laptop-mode : SERVICE_DONE
 21:34:33 daemon/acpid/modules : *OUTPUT*
FATAL: Error inserting ibm_acpi (/lib/modules/2.6.15-25-k7/kernel/drivers/acpi/ibm_acpi.ko): No such device
 21:34:34 daemon/acpid/modules : SERVICE_DONE
 21:34:34         daemon/acpid : DAEMON_RUNNING
 21:34:35          daemon/hald : DAEMON_RUNNING
 21:34:35       system/keymaps : SERVICE_DONE
 21:34:35 system/console-screen : *OUTPUT*
]RSetting up general console font ...
 21:34:36             net/eth0 : SERVICE_DONE
 21:34:36          virtual/net : PROVIDED
 21:34:36     virtual/net/eth0 : PROVIDED
 21:34:36              net/all : SERVICE_DONE
 21:34:36 system/console-screen : *OUTPUT*
Setting up per-VC fonts ...
/dev/tty2, /dev/tty3, /dev/tty4, /dev/tty5, /dev/tty6, [9;30][14;30] 21:34:37 system/console-screen : SERVICE_DONE
 21:34:37               system : UP
 21:34:37              default : UP


```

---

### Post by givré on 2006-06-26
For all :```
 FATAL: Error inserting ibm_acpi (/lib/modules/2.6.15-25-k7/kernel/drivers/acpi/ibm_acpi.ko): No such device
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.15-25-k7/kernel/drivers/acpi/toshiba_acpi.ko): No such device
FATAL: Error inserting asus_acpi (/lib/modules/2.6.15-25-k7/kernel/drivers/acpi/asus_acpi.ko): No such device
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-25-k7/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

```Are not fatal if you don't have one of this type of laptop, don't worry about them, they don't take time.

@sewpafly : good news guy. also, for the speedstep problem, if your processor don't support it, remove it from the runlevel 'sudo ng-update del speedstep'. If you could have speedstep, what is your processor?

@burke : /dev/hda2 is check, it's why it's longer than expected, but if it's not unmount cleanly, that's quite bad. Try to reboot and see if you have some error at shutdown.

---

### Post by sewpafly on 2006-06-26
givré - I have a AMD64 processor (using the 386 kernel) so I don't think that I need the speedstep module and I'll remove it with a 'ng-update del speedstep' correct?  But this leads to hopefully my last question, if I change kernels (either grabbing the k7 or compiling my own) will anything with initng have to change?

Thanks for all your time and help!

---

### Post by givré on 2006-06-26
Well the only thing you will have to change again is your kernel line in grub, and tht's all. When it's well configurate, it should always work.
In fact it's the only problem of initng, configuration, because systems and distribution are so different that it's hard to have something to run them all, but when it's done, it's fast as the leopard :cool:

---

### Post by Dubbayoo on 2006-06-26
I got this to work although it killed the working 3D (fgl_glxgears) and openoffice with my Radeon 8500. It's faster but the speedup isn't worth losing that.

---

### Post by givré on 2006-06-26
Which driver do you use for your radeon?
I'm quite sure we can get it working with initng.

EDIT : and do you see some error when you do 'sudo ngc -l'

---

### Post by Dubbayoo on 2006-06-26
[QUOTE=givré]Which driver do you use for your radeon?
I'm quite sure we can get it working with initng.

EDIT : and do you see some error when you do 'sudo ngc -l'[/QUOTE]

I use the fglrx driver. Also, now I see sshd isn't starting. This is a definite dealbreaker. 

Pastebin is just hanging.
-----------------------

sudo ngc -l
 initNGControl (0.6.7 ) by Jimmy Wennlund [http://www.initng.org/](http://www.initng.org/)


 hh:mm:ss    service           :  STATUS
 ------------------------------------------------------
 18:15:13 system/initial/loglevel : SERVICE_DONE
 18:15:14 system/initial/mountvirtfs : *OUTPUT*
mount: sys already mounted or /sys busy
mount: according to mtab, none is already mounted on /sys
mount: proc already mounted
 18:15:14 system/initial/mountvirtfs : SERVICE_DONE
 18:15:14 system/udev/mountdev : SERVICE_DONE
 18:15:14 system/initial/filldev : *OUTPUT*
Mounting devpts at /dev/pts ...
Mounting devshm at /dev/shm ...
 18:15:14 system/initial/filldev : SERVICE_DONE
 18:15:14    system/udev/udevd : DAEMON_RUNNING
 18:15:14 system/udev/set_hotplug : SERVICE_DONE
 18:15:19  system/udev/filldev : SERVICE_DONE
 18:15:19          system/udev : UP
 18:15:19       system/initial : UP
 18:15:19      system/hostname : *OUTPUT*
Setting hostname to 'ubu-6'
 18:15:19      system/hostname : SERVICE_DONE
 18:15:19        system/sysctl : SERVICE_DONE
 18:15:19 system/mountroot/check : *OUTPUT*
Checking root filesystem ...
/dev/sda1: clean, 145446/4300576 files, 1604560/8598783 blocks
Done checking root file system.
 18:15:19 system/mountroot/check : SERVICE_DONE
 18:15:19 system/mountroot/rootrw : *OUTPUT*
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
 18:15:19 system/mountroot/rootrw : SERVICE_DONE
 18:15:19     system/mountroot : *OUTPUT*
Mounting / rw ...
Mounting /proc rw ...
 18:15:19     system/mountroot : SERVICE_DONE
 18:15:19 system/modules/depmod : *OUTPUT*
Found modules.dep, skipping depmod ...
Module dependencies up to date ...
 18:15:19       system/checkfs : *OUTPUT*
Checking file systems
 18:15:19       system/checkfs : SERVICE_DONE
 18:15:19       system/mountfs : *OUTPUT*
Mounting local filesystems
/dev/hda1 on /data type ext3 (rw)
code 32
 18:15:19       system/mountfs : SERVICE_DONE
 18:15:19     system/rmnologin : SERVICE_DONE
 18:15:19          system/swap : SERVICE_DONE
 18:15:21 system/modules/depmod : SERVICE_DONE
 18:15:21       system/modules : *OUTPUT*
Loading module "lp" ...
 18:15:21 system/modules/usbcore : SERVICE_DONE
 18:15:21       system/modules : *OUTPUT*
Loading module "psmouse" ...
 18:15:21 system/modules/capability : SERVICE_DONE
 18:15:21       system/modules : *OUTPUT*
Loading module "sbp2" ...
Loading module "fuse" ...
Loading module "fglrx" ...
 18:15:21       system/modules : SERVICE_DONE
 18:15:23         system/clock : SERVICE_DONE
 18:15:23      system/bootmisc : SERVICE_DONE
 18:15:23       daemon/getty/2 : DAEMON_RUNNING
 18:15:23       daemon/getty/3 : DAEMON_RUNNING
 18:15:23       daemon/getty/4 : DAEMON_RUNNING
 18:15:23       daemon/getty/5 : DAEMON_RUNNING
 18:15:23       daemon/getty/6 : DAEMON_RUNNING
 18:15:23           daemon/gdm : DAEMON_RUNNING
 18:15:23      virtual/getty/2 : PROVIDED
 18:15:23      virtual/getty/3 : PROVIDED
 18:15:23      virtual/getty/4 : PROVIDED
 18:15:23      virtual/getty/5 : PROVIDED
 18:15:23      virtual/getty/6 : PROVIDED
 18:15:23           virtual/dm : PROVIDED
 18:15:23         daemon/getty : UP
 18:15:23           system/usb : SERVICE_DONE
 18:15:23 daemon/syslogd/prepare : SERVICE_DONE
 18:15:23       daemon/syslogd : DAEMON_RUNNING
 18:15:23       virtual/syslog : PROVIDED
 18:15:23         daemon/klogd : DAEMON_RUNNING
 18:15:23 daemon/NetworkManager/prepare : SERVICE_DONE
 18:15:23       system/anacron : SERVICE_DONE
 18:15:23       system/urandom : SERVICE_DONE
 18:15:23 system/alsasound/cards : SERVICE_DONE
 18:15:23     system/alsasound : SERVICE_DONE
 18:15:23          daemon/dbus : DAEMON_RUNNING
 18:15:23        daemon/dhcdbd : *OUTPUT*


 ** "/data/initng-0.6.7/plugins/simple_launcher/initng_simple_launcher.c", simple_exec_fork()  line:189:
 18:15:23 -- FAIL:      ERROR!


 ** "/data/initng-0.6.7/plugins/simple_launcher/initng_simple_launcher.c", simple_exec_fork()  line:190:
 18:15:23 -- FAIL:      Can't execute source /usr/sbin/dhcdbd!
 18:15:23 daemon/acpid/modules : *OUTPUT*
FATAL: Error inserting asus_acpi (/lib/modules/2.6.15-25-686/kernel/drivers/acpi/asus_acpi.ko): No such device
 18:15:23            device/lo : NIC_UP
 18:15:23 system/alsasound/mixerstate : SERVICE_DONE
 18:15:24               net/lo : SERVICE_DONE
 18:15:24 daemon/acpid/modules : *OUTPUT*
FATAL: Error inserting ibm_acpi (/lib/modules/2.6.15-25-686/kernel/drivers/acpi/ibm_acpi.ko): No such device
 18:15:24   system/laptop-mode : SERVICE_DONE
 18:15:24 daemon/acpid/modules : *OUTPUT*
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.15-25-686/kernel/drivers/acpi/toshiba_acpi.ko): No such device
 18:15:24 daemon/acpid/modules : SERVICE_DONE
 18:15:24         daemon/acpid : DAEMON_RUNNING
 18:15:24       system/keymaps : SERVICE_DONE
 18:15:24 system/console-screen : *OUTPUT*
]RSetting up general console font ...
set_kernel_font: Invalid argument
 failed.
Setting up per-VC fonts ...
/dev/tty2, /dev/tty3, /dev/tty4, /dev/tty5, /dev/tty6, [9;30][14;30] 18:15:25 system/console-screen : SERVICE_DONE
 18:15:25               system : UP
 18:15:26          daemon/hald : DAEMON_RUNNING
 18:15:27          device/eth1 : NIC_UP
 18:15:27             net/eth1 : SERVICE_DONE
 18:15:27          virtual/net : PROVIDED
 18:15:27     virtual/net/eth1 : PROVIDED
 18:15:28             net/eth2 : SERVICE_FAIL_START_RCODE
 18:15:28          virtual/net : NOT_PROVIDED
 18:15:28     virtual/net/eth2 : NOT_PROVIDED
 18:15:30             net/ath0 : SERVICE_FAIL_START_RCODE
 18:15:30          virtual/net : NOT_PROVIDED
 18:15:30     virtual/net/ath0 : NOT_PROVIDED
 18:15:31            net/wlan0 : SERVICE_FAIL_START_RCODE
 18:15:31          virtual/net : NOT_PROVIDED
 18:15:31    virtual/net/wlan0 : NOT_PROVIDED
 18:15:31              net/all : SERVICE_DONE



steve@ubu-6:~$
Message from syslogd@ubu-6 at Mon Jun 26 18:16:24 2006 ...
ubu-6 InitNG: "/data/initng-0.6.7/plugins/daemon/initng_daemon.c", timeout_DAEMON_WAIT_FOR_PID_FILE() #765 FAIL: Service "daemon/dhcdbd" wait for pidfile timed out! Will kill daemon now.

Message from syslogd@ubu-6 at Mon Jun 26 18:16:24 2006 ...
ubu-6 InitNG: "/data/initng-0.6.7/plugins/daemon/initng_daemon.c", kill_daemon() #973 FAIL: Trying to kill a service (daemon/dhcdbd) with a pid (3818), but there exists no process with this pid!

---

### Post by sewpafly on 2006-06-26
This error looks really similar to the error that I was getting.  Givré gave me a good tip [here]("http://ubuntuforums.org/showpost.php?p=1178425&postcount=85") in the last part of the message.

---

### Post by givré on 2006-06-27
```
18:15:21 system/modules : *OUTPUT*
Loading module "sbp2" ...
Loading module "fuse" ...
Loading module "fglrx"
```
As you can see your driver is load so normaly that should be ok, if not, say me which howto you follow?

Also i see that you use fuse, probably to have write access of an NTFS partition, if it is the case and only if you mount an NTFS partition at boot (it's not the case apparently), you have to be sure that fuse is load before moutfs.
That's quite easy to do that, In /etc/initng/system/checkfs.i, add system/modules to your use= line, i will add that to the wiki

```
** "/data/initng-0.6.7/plugins/simple_launcher/initng_simple_launcher.c", simple_exec_fork() line:190:
18:15:23 -- FAIL: Can't execute source /usr/sbin/dhcdbd!
```
Change your dhcbd script as mention by sewpafly

---

### Post by Dubbayoo on 2006-06-27
I installed fuse but it didn't work. I really just need ntfs-read anyway so I could disable that. A more important problem is that I use nfs frequently and that isn't working. What do I need to start and in what order for nfs (ubuntu is a client only) to work? 
I wish this script would detect which services/daemons you are using when it is first installed and configure those to start by default. Then instruct how to tune initng from that point.

---

### Post by Brando569 on 2006-06-27
initng doesnt work at all for it, it will run then it just freezes. i cant post any errors or anything becuase bootlogd doesnt seem to want to work, its in the correct run level (S) and i enabled it in the config file but it still doesnt wanna work...

---

### Post by givré on 2006-06-27
There is no S runlevel in initng, runlevel AND script are totaly different from sysvinit.
But, anyway, to have some debuging information, you could look at /var/log and search for syslog. There is in fact information about the 6 last day there, try to find the log of your initng boot and post it here.
Also i'd like to know the moment when it freeze, is it durring the kernel lauch(stop at mounting root file), during initng process, or during X start.

---

### Post by givré on 2006-06-27
[QUOTE=Dubbayoo]I installed fuse but it didn't work. I really just need ntfs-read anyway so I could disable that. A more important problem is that I use nfs frequently and that isn't working. What do I need to start and in what order for nfs (ubuntu is a client only) to work? [/QUOTE]
Ask at #initng on freenode for that, it's totaly out of my competance, i don't use nfs at all. I could try to look at it, but can promise you something

---

### Post by givré on 2006-06-27
@Dubbayoo : Ok i think i found what you need, look at /etc/initng/system/netmount.i to see if it is what you look at (seems so) 
```
sudo ng-update add system/netmount
```to add it but i'm sure you know that better than me now 8) 
I encourage you to use initng-conf-gtk, you will be able to see all the script provide by initng, and by double-cliking them, you will see what they do.

---

### Post by Brando569 on 2006-06-27
[QUOTE=givré]There is no S runlevel in initng, runlevel AND script are totaly different from sysvinit.
But, anyway, to have some debuging information, you could look at /var/log and search for syslog. There is in fact information about the 6 last day there, try to find the log of your initng boot and post it here.
Also i'd like to know the moment when it freeze, is it durring the kernel lauch(stop at mounting root file), during initng process, or during X start.[/QUOTE]

its during the initng process, it loads a few things then just freezes. ill get back to this later im compiling a kernel w/fbsplash support :D

---

### Post by matthis on 2006-06-27
Hi,

I'm trying to get initng to work. It seems to boot fine except that I cannot get network going. I have followed the wiki instructions and added daemon/NetworkManager, but to no avail. WHen I check manually with ifconfig it says "no network devices".
I am using pppoe to connect to the internet, would this require additional steps?

Thanks

---

### Post by givré on 2006-06-27
daemon/NetworkManager is **only** if you use [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager) 
If you don't use it, net/all (it's in by default), should be ok.
What is the name of the interface you use?
Also be sure that it is set to auto in /etc/network/interfaces, if you don't now how to do that, just past the file, i will help you

EDIT: i was just thinking that if you follow the wiki, you commented lines in /etc/network/interfaces, so just uncomment them and reboot. I changed a bit the wiki so people don't get confuse

---

### Post by Dubbayoo on 2006-06-27
When I look in initng-conf-gtk for daemon/nfs and doubleclick it the box says "**Don't know where to locate file!**". What file is it looking for?
In  /etc/initng/daemon/nfsd.i there is:
--------------------------
#!/sbin/itype
# This is a i file, used by initng parsed by install_service

daemon daemon/nfsd {
        need = system/initial daemon/portmap virtual/net;
        pid_of = rpc.nfsd;
        exec daemon = /usr/sbin/rpc.nfsd;
-----------------------

There is no such file as /usr/sbin/rpc.nfsd. Is what it wants? What should it be? It looks like the normal nfs-common service uses:
/usr/sbin/rpc.gssd
/usr/sbin/rpc.idmapd
/sbin/rpc.statd
/sbin/rpc.lockd

There is no /usr/sbin/rpc.mountd either which mountd seems to want. 

----------------------------

Is there an easy way to undo all this initng stuff and go back to the ubuntu defaults? I don't have the time nor the patience to track down why all these things aren't working. I would just rather wait til this is a bit more polished. I need my computer to work. I can wait 20 more seconds for a working system.

---

### Post by givré on 2006-06-28
nfsd is something else, you should add netmount to mount nfs filesystem as i said before.
But if you don't have the patience to configure all that stuff, ok there is nothing easier to return to sysvinit, just remove init=initng in /boot/grub/menu.lst and remove all the initng package.

EDIT: also, please could you test netmount before, so i could add it to the wiki if it works. Thank you so much

---

### Post by matthis on 2006-06-28
Thank you givre for you help about network!
Now pppoe is working automatically; the only change I made was to remove the debian-ifupdown service.

EDIT: Oops I spoke too quickly, I had forgotten to add init=/sbin/init again... ;)
So, now network interfaces are found with ifconfig, but the dsl-provider seems not to be handled correctly. "Plog" spits out "authentification failed". Here is my /etc/network/interfaces file.

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

mapping hotplug
script grep
map usb0

iface usb0 inet static
address 192.168.129.1
netmask 255.255.255.0

auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf


Thanks for any help!

---

### Post by givré on 2006-06-29
hi matthis, sorry for the delay, i didn't notice that you edit your post.
I don't use pppoe so i might be not really useful, but check that you don't have in sysvinit a script that launch a daemon to manage your pppoe (it's the case for ppp so probably for pppoe), for that, try to search a script in /etc/init.d which could be call pppoe or something like that.
I don't have the solution, but i can give the key to find it.

---

### Post by matthis on 2006-07-01
Thanks!! Removing ppp from /etc/init.d solved my problem!!

---

### Post by givré on 2006-07-01
Can you explain more please, i'd like to add something about pppoe on the wiki, but i don't really understand how removing /etc/init.d/ppp can make it working.
Are you sure you started initng?

---

### Post by WishMaster on 2006-07-01
> dpkg-deb: building  packet `initng' in `../initng_0.6.7-1_i386.deb'.
dpkg-deb: building  packet `initng-dev' in `../initng-dev_0.6.7-1_i386.deb'.
 signfile initng_0.6.7-1.dsc
gpg: WARNING: unsafe ownership on configuration file `/home/bert/.gnupg/gpg.conf'
gpg: skipped "Armin Berres <a.berres@onlinehome.de>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available

bert@UbuntuBert:~/initng-0.6.7/initng-0.6.7$ sudo dpkg -i initng_0.6.7*.deb && sudo apt-get install initng-ifiles dpkg: error by initng_0.6.7*.deb (--install):
 couldn't open archive: unknown file or map
Errors by:
 initng_0.6.7*.deb

got this while following [https://help.ubuntu.com/community/InitNG](https://help.ubuntu.com/community/InitNG)

---

### Post by menaar on 2006-07-02
[QUOTE=WishMaster]got this while following [https://help.ubuntu.com/community/InitNG](https://help.ubuntu.com/community/InitNG)[/QUOTE]



Go back one directory, to where the deb files are located.
And run sudo dpkg - etc... again.

The secret key message, I think you can ignore.

---

### Post by WishMaster on 2006-07-02
okay, that worked :)

Initng is slower here then the default boot-up :?
Also, my resolution is f*cked up. It should be 1400*1050, now it is 1024*786 :evil:

Uninstall it is

---

### Post by menaar on 2006-07-02
[QUOTE=WishMaster]okay, that worked :)

Initng is slower here then the default boot-up :?
Also, my resolution is f*cked up. It should be 1400*1050, now it is 1024*786 :evil:

Uninstall it is[/QUOTE]

That's odd. Mine worked ok. My resolution doesn't get more the 1024*786 anyways.
The bootup seems a bit faster.

Report it as a bug. here. [http://www.initng.org/newticket](http://www.initng.org/newticket)

---

### Post by johlin on 2006-07-02
I can't get this to work either. One time, it started and logged in but gdm couldn't do anything and I couldn't see the background/panels (I could see the outlines of the panels but nothing more). The other time, when I had bootsplash enabled, it went straight to the sh shell without root filesystem mounted.
Also, I can't install the package. Even when I've lowered so that it depends on the libc6 version that ubuntu has, it still won't install.

So give up. I can live with a few seconds extra startup time.

---

### Post by Cris987 on 2006-07-04
When i try to install the packages using apt-get, the terminal returns a message requiring a special key. What's wrong?

---

### Post by givré on 2006-07-04
[QUOTE=Cris987]When i try to install the packages using apt-get, the terminal returns a message requiring a special key. What's wrong?[/QUOTE]
Don't worry, it's just a warning.

---

### Post by matthis on 2006-07-04
Dear Givre, I am checking my configuration /changes I made so that I can report them clearly to you; it will post as soon as I find more time.
Sorry for the delay

---

### Post by givré on 2006-07-04
That's fine, take your time :cool:

---

### Post by H.E. Pennypacker on 2006-07-04
> One time, it started and logged in but gdm couldn't do anything and I couldn't see the background/panels (I could see the outlines of the panels but nothing more)

This seems to be describing the same situation I am facing.  The laptop starts up, and takes me to the log-in screen (GDM).  I log-in, and you'd expect Gnome to load, and everything to show up fine.  Gnome (the background, panels, desktop icons, etc.) does show up, but it disappears after a few seconds.  After that, all I see a blank screen.  I believe it is white.

To solve this problem, I go into the default log-in, but it doesn't have initNG.

Is there a way to solve this issue?

---

### Post by givré on 2006-07-04
ah ah, i think i know what is the problem.
Do you use aiglx, or anything which require extra kernel module? (aiglx require linux-dri-module).
If this is the case, i know what is the poblem. This package work the same way as linux-restricted-module, ie, it lauch lrm-manager at startup to load the module (linux-dri-module launch ldm-manager).
So we have to change one script.
```
sudo gedit /etc/initng/system/modules.i
```
you will see there something like that
```
if [ -x /sbin/lrm-manager ]
then
        /sbin/lrm-manager --quick
fi
wait
```
that load the linux restricted module. We will use the same structure to load the ldm. So add that, just after
```
if [ -x /sbin/ldm-manager ]
then
	echo "Loading DRI..."
	/sbin/ldm-manager --quick
fi
wait
```
i add an echo to check that it works (see ngc -l)
retsart and that should work.

---

### Post by H.E. Pennypacker on 2006-07-04
givre, I am not exactly sure what I was doing, but your instructions worked.  How did you know what the problem was?  

By the way, yes, I do use Compiz/AIGLX.  How did you know that?

Was all this a mistake a I made, or was this a problem with AIGLX or initNG?  I believe I followed all the installation steps of AIGLX and initNG.

---

### Post by givré on 2006-07-04
In fact i had the same problem a long time ago. 
You need the latest DRM to get running aiglx, and this one are provided by the package linux-dri-module. To load the module easily at startup, it use the same type of script as linux-restricted-module use (ldm-manager for one and lrm-manager for the other). So to load them, you just has to duplicate the script which load lrm in initng, and replace lrm by ldm.
All problems have a solution.

---

### Post by yawie on 2006-07-05
I had trouble to get sources from the repository (Unable to find expected entry main/sources/Sources in Meta-index file (malformed Release file?)
I just did by hand what apt-get source do automatically

```
mkdir initng && cd initng
wget http://debian.space-based.de/debs/pool/main/i/initng/initng_0.6.7-1.diff.gz
wget http://debian.space-based.de/debs/pool/main/i/initng/initng_0.6.7-1.dsc
wget http://debian.space-based.de/debs/pool/main/i/initng/initng_0.6.7.orig.tar.gz

dpkg-source -x initng_0.6.7-1.dsc
cd initng-0.6.7/
sudo apt-get install cmake dpatch fakeroot
dpkg-buildpackage -rfakeroot -uc -b
cd ..

after you can do and follow the wiki
sudo dpkg -i initng_0.6.7*.deb

```

I will tell you soon if initng works. Hope this helps.

---

### Post by yawie on 2006-07-05
It sounds working :D
Fuse is also working with [givré]("http://ubuntuforums.org/showthread.php?p=1187702&highlight=fuse%2A#post1187701")'s tweak.
It goes from 1min5s with init V to 39 secondes with ining (from the time I choose the entry in grub to the end of gnome loading).
Pretty nice. I will look forward tweaking a bit and removing some useless services I have (like bittorrent tracker, hplip as I have no HP...)

I have an athlon X2, I removed speedsptep because it has failed to load. Do you know how the frequency change is taken into account (and if it is)?
Thanx

---

### Post by lepre on 2006-07-05
installed on xubuntu and seems to work. but i get some tweak to do (it start with ubuntu gdm now instead of xubuntu, on shutdown it wait 15 sec for me to read, why not just press a key option?)
the boot time is 36 vs 27

---

### Post by givré on 2006-07-06
Yeah, initng is still a beta, so some tweeks are needed, but when it's done, it's fligh. Don't hesitate to ask question if you have troubles. We can do everything with initng

---

### Post by anodizer on 2006-07-06
I installed and configured it using the wiki page, but when I boot using InitNG it hangs at "system/sysctl" point. Why is that?

---

### Post by givré on 2006-07-06
well, /etc/initng/system/systclt show me,
```
service system/sysctl {
	need = system/initial;
	exec start = /sbin/sysctl -n -e -q -p;
}
```
But don't be confuse by hanging process. Due to the asynchrone start, when a service hang, you could be sure that a lot other run behind(that's not the case with sysvinit).

EDIT:givré, why you do like to confuse people

---

### Post by anodizer on 2006-07-06
What's this piece of code? Should I paste it somewhere? (initng noob here ;p)

---

### Post by givré on 2006-07-06
no sorry :) , that's just the sysctl initng script, the idea behind this post was just to show you that it's quite easy to know what do a script: just go to /etc/initng. But i'm not sure it was a good idea. :cool: 
Anyway, if it hangs during something like 1 or 2 s, that's quite normal. If it really take time, have a look at ```
sudo ngc -l
```to see if you have some error, and report them here if you don't know how to solve them

---

### Post by anodizer on 2006-07-06
It booted normally this time, without changing anything. The problem now is that Xgl or compiz is so slow, the desktop is unusable. I don't know if this is a initng bug or a compiz one, but it doesn't happen if I boot with the classic method.

---

### Post by givré on 2006-07-06
1. Ok i know what was your sysclt pb, it hangs because it checks root file system, just like normal boot do (every 30 boot).
2. What is your graphic card, how did you set XGL/compiz (which howto did you follow). As i said, when can do **everything** with initng, so that's not an issue, just need some configuration

---

### Post by H.E. Pennypacker on 2006-07-07
> **lepre said:**
> installed on xubuntu and seems to work. but i get some tweak to do (it start with ubuntu gdm now instead of xubuntu, on shutdown it wait 15 sec for me to read, why not just press a key option?)
the boot time is 36 vs 27

It waits 15 seconds to give you the opportunity to review the errors that it displays.  You're having the same issue as me.  Presumably, if there are no errors displayed, you will not be waiting 15 seconds.

givre, my problem relates to eth0, which I don't use regularly.  When shutting down, a message comes up at the end, and it says something about eth0.  When I do sudo ngc -l, I don't get any errors related to eth0.

givre, one more thing, how do I remove entries from start-up using initNG?  A lot of people are saying they removed this and that, but as far as I know, you can't removing anything from start up using initNG.  I believe you can only do that with BUMPS.

Thanks a lot, givre.  I am in awe of your knowledge.  :)

---

### Post by anodizer on 2006-07-07
> **givré said:**
> 1. Ok i know what was your sysclt pb, it hangs because it checks root file system, just like normal boot do (every 30 boot).
2. What is your graphic card, how did you set XGL/compiz (which howto did you follow). As i said, when can do **everything** with initng, so that's not an issue, just need some configuration

1. Yeah that must be the case, when I booted without initng it made the checkdisk. But initng should display something about checking root fs.

2. ATi Radeon 9600XT and I'm using the method with the .Xsession file in my /home.
Here's the script:
```
#!/bin/sh
# Start up Xgl, compiz, and GNOME
# Run Xgl server on :1, on top of normal X
Xgl :1 -fullscreen -ac -accel xv -accel glx:pbuffer &
# Tell subsequent X programs to access the Xgl server at :1
DISPLAY=:1
# Start Compiz window manager
gnome-window-decorator &
compiz gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher &
# Start GNOME 
exec gnome-session

```

Everything starts up, just waaay slow.

---

### Post by foxy123 on 2006-07-07
thanks a lot for the wiki, its great. Now I am almost back to InitNG, which I used on Breezy but abandoned after switching to Dapper development release while ago.

I've got still one problem:

[CODE11:44:23 D daemon/klogd                        : DAEMON_FAIL_START_RCODE
][/CODE]

I have no idea why it fails. I looked into the startup script and it seems fine to me though I am not a techie at all. Any help?

```
~$ sudo ngc -l | grep klog
 11:44:22         daemon/klogd : DAEMON_RUNNING
 11:44:23         daemon/klogd : DAEMON_FAIL_START_RCODE

```
and also this:
```
 11:44:27       system/keymaps : SERVICE_DONE
 11:44:27 system/console-screen : *OUTPUT*
]RSetting up general console font ...
set_kernel_font: Invalid argument
 failed.
Setting up per-VC fonts ...

```

---

### Post by givré on 2006-07-12
Ok guys, sorry for the delay.
We will take that in order.

@H.E. Pennypacker:

- First think thank you you to contributing to the wiki :-D .

- I can't really help you more. You could have log at shutdown in the syslog file that you will find in /var/log. You could also try to restart eth0 in your currant session and see what's happens. 
```
sudo ngrestart net/eth0
```

- Managing runlevel in initng is the easier thing you can do. In fact you have three way to do that:
1. You can edit manually the runlevels file, default.runlevel & system.virtual (equivalent to /etc/rcS.d) in /etc/initng. I don't really recommand it.
2. You can add/remove service with ng-update via a terminal.ex:
```
sudo ng-update add daemon/samba
sudo ng-update del daemon/mysql
```
3. Last one, and the better, you can manage it easily with the initng-conf-gtk GUI (link in the wiki). select show>runlevel editor and you will be able to manage easily your runlevel and even create a new runlevel.


@anodizer

- Yeah i agree with you with the checkdisk, but jimmy pass only few days to make the usplash plugin, so he didn't really take time to the detail.

- Check first that your ati's acceleration is running well with initng
```
fglrxinfo
``` if it's ok, i don't know what could be the problem. If it's not come back to see me, i'll try to help you (even if it's will quite hard, i don't have neither nvidia/ATI graphic card 8) )

@foxy123

- For klogd, do you have some debuging information after the FAIL message?

- 'set_kernel_font: Invalid argument' is not a problem, i also have this error. That's not an initng problem.

---

### Post by givré on 2006-07-14
Wiki update. I add fuse+aiglx. This begin to be really long, if you have some idea to get it more usuable, i'm open.

---

### Post by foxy123 on 2006-07-28
> **givré said:**
> - For klogd, do you have some debuging information after the FAIL message?

- 'set_kernel_font: Invalid argument' is not a problem, i also have this error. That's not an initng problem.

I have put 'ngc -l' output on pastecode [http://pastecode.com/2112](http://pastecode.com/2112)

The strange thing is that in line 95 it says that the daemon is running, but in line 108 that it failed.

---

### Post by Don_DiZzLe on 2006-07-29
I get this after inputting the deb & src-deb repositories and updating:


Fetched 1958B in 8s (224B/s)
Failed to fetch [http://debian.space-based.de/debs/dists/experimental/Release](http://debian.space-based.de/debs/dists/experimental/Release)  Unable to find expected entry  main/source/Sources in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Jingo on 2006-08-01
I think InitNG is not cleanly unmounting my drives. Anyone seeing this too?

Everytime Initng shutdowns/reboot (succesfully) the next startup gives me this:

```

dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  71:49/00, 72:42/00, 73:4d/00, 74:5f/00, 75:53/00, 76:45/00, 77:52/00
  , 78:56/00, 79:49/00, 80:43/00, 81:45/00
  Not automatically fixing this.
/dev/hda2: 7005 files, 1051677/1167624 clusters
/dev/hda8: clean, 30/40160 files, 18877/80293 blocks
Replaying journal..
Trans replayed: mountid 1173, transid 298978, desc 8004, len 21, commit 8026, next trans offset 8009
Trans replayed: mountid 1173, transid 298979, desc 8027, len 1, commit 8029, next trans offset 8012
Trans replayed: mountid 1173, transid 298980, desc 8030, len 1, commit 8032, next trans offset 8015
Trans replayed: mountid 1173, transid 298981, desc 8033, len 1, commit 8035, next trans offset 8018
Trans replayed: mountid 1173, transid 298982, desc 8036, len 1, commit 8038, next trans offset 8021
Trans replayed: mountid 1173, transid 298983, desc 8039, len 8, commit 8048, next trans offset 8031
Trans replayed: mountid 1173, transid 298984, desc 8049, len 1, commit 8051, next trans offset 8034
Trans replayed: mountid 1173, transid 298985, desc 8052, len 1, commit 8054, next trans offset 8037
Trans replayed: mountid 1173, transid 298986, desc 8055, len 1, commit 8057, next trans offset 8040
Trans replayed: mountid 1173, transid 298987, desc 8058, len 1, commit 8060, next trans offset 8043
Trans replayed: mountid 1173, transid 298988, desc 8061, len 1, commit 8063, next trans offset 8046
Reiserfs journal '/dev/hda7' in blocks [18..8211]: 11 transactions replayed
Checking internal tree..finished
Reiserfs super block in block 16 on 0x307 of format 3.6 with standard journal
Blocks (total/free): 6428000/3634336 by 4096 bytes
Filesystem is NOT clean
/dev/hda5: clean, 101581/1281696 files, 738611/2560351 blocks
Reiserfs super block in block 16 on 0x307 of format 3.6 with standard journal
Blocks (total/free): 6428000/3634336 by 4096 bytes
Filesystem is NOT clean

```

This is my fstab:
```

proc            /proc           proc    defaults        0       0
/dev/hda9       /               reiserfs noatime         0       1
/dev/hda8       /boot           ext3    noatime,noauto         0       2
/dev/hda7       /home           reiserfs noatime         0       2
/dev/hda1       /media/hda1     ntfs    defaults,noauto,nls=utf8,umask=007,gid=46,users 0       1
/dev/hda2       /media/hda2     vfat    defaults,noauto,utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda5     ext3    defaults,noauto        0       2
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

If I boot normally, there is no problem, and the journal is not replayed!

Where to look?

---

### Post by HonorSystem on 2006-08-06
Hi, I'm using a fresh Dapper (AMD64) install (kind of a linux newbie, but not hopeless) and I decided to apply various tweaks from the improving performance thread ([http://www.ubuntuforums.org/showthread.php?t=189192](http://www.ubuntuforums.org/showthread.php?t=189192)) which included installing and setting up InitNG.  I followed the wiki to the letter and everything worked as expected.  In the end I decided that I would leave InitNG for later down the road after reading about so many people having trouble with various services not working.

In short, I'm trying to fully remove InitNG from my system, but I'm not entirely sure how to.

After everything was set up, I ran an upgrade through ubuntu's built-in update notifier and downloaded/installed various newer versions of things.  One of which was version 0.6.7-2 of initng and initng-ifiles.  I hope that didn't screw anything up.  So, to uninstall InitNG, I figured I could use synaptic to "completely remove" both initng and initng-ifiles which is what I did.  I then edited my grub list to remove the duplicate entry with the init=/sbin/initng addition.

The problem now is that when I boot I still have no usplash (i tried reinstalling usplash via synaptic) and I could swear that it is still booting slightly faster, but I'm not sure.  How can I check to really really make sure InitNG is uninstalled completely and how can I get my lovely usplash working again?

Sorry for the length of this.  Just trying to be thorough.  And thanks in advance!

---

### Post by foxy123 on 2006-08-06
> **HonorSystem said:**
> Hi, I'm using a fresh Dapper (AMD64) install (kind of a linux newbie, but not hopeless) and I decided to apply various tweaks from the improving performance thread ([http://www.ubuntuforums.org/showthread.php?t=189192](http://www.ubuntuforums.org/showthread.php?t=189192)) which included installing and setting up InitNG.  I followed the wiki to the letter and everything worked as expected.  In the end I decided that I would leave InitNG for later down the road after reading about so many people having trouble with various services not working.

In short, I'm trying to fully remove InitNG from my system, but I'm not entirely sure how to.

After everything was set up, I ran an upgrade through ubuntu's built-in update notifier and downloaded/installed various newer versions of things.  One of which was version 0.6.7-2 of initng and initng-ifiles.  I hope that didn't screw anything up.  So, to uninstall InitNG, I figured I could use synaptic to "completely remove" both initng and initng-ifiles which is what I did.  I then edited my grub list to remove the duplicate entry with the init=/sbin/initng addition.

The problem now is that when I boot I still have no usplash (i tried reinstalling usplash via synaptic) and I could swear that it is still booting slightly faster, but I'm not sure.  How can I check to really really make sure InitNG is uninstalled completely and how can I get my lovely usplash working again?

Sorry for the length of this.  Just trying to be thorough.  And thanks in advance!
add 'splash' in the end of the line...

---

### Post by vorpalblade on 2006-08-23
Hello,
I recently installed initng and have been enjoying it except for one very strange behavior I am observing. When I try and run a program that requires 3d graphics acceleration (such as planet penguin racer, unreal tournoment 2004 or any GL screensaver) get get many copies of the following error message:

FGLTexMgr: open of shared memory object failed (Permission denied)
__FGLTexMgrCreateObject: __FGLTexMgrSHMmalloc failed!!!
fglX11AllocateManagedSurface: __FGLTexMgrCreateObject failed!!

In the case of planet penguin racer or the screensavers this mearly casues them to perform very slowly (~2 fps), in the case of ut2004 it casues a segfault.

Interestingly, al these problems dissapear if the program in question is run as root, or if the system is booted with plain old system V init.
 
I am running an up-to-date version of dapper, my graphics card is a raedeon 9600xt.
flgrxinfo yields:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.5814 (8.25.18 )

Any help in resolving this issue would be greatly appriciated,

---

### Post by Evil_Donkey on 2006-08-24
> **vorpalblade said:**
> Hello,
I recently installed initng and have been enjoying it except for one very strange behavior I am observing. When I try and run a program that requires 3d graphics acceleration (such as planet penguin racer, unreal tournoment 2004 or any GL screensaver) get get many copies of the following error message:

FGLTexMgr: open of shared memory object failed (Permission denied)
__FGLTexMgrCreateObject: __FGLTexMgrSHMmalloc failed!!!
fglX11AllocateManagedSurface: __FGLTexMgrCreateObject failed!!

In the case of planet penguin racer or the screensavers this mearly casues them to perform very slowly (~2 fps), in the case of ut2004 it casues a segfault.

Interestingly, al these problems dissapear if the program in question is run as root, or if the system is booted with plain old system V init.
 
I am running an up-to-date version of dapper, my graphics card is a raedeon 9600xt.
flgrxinfo yields:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.5814 (8.25.18 )

Any help in resolving this issue would be greatly appriciated,

I have the exact same problem. Most 3D things seem to be really slow unless run as root or using system v init. I've spent many hours trying to fix it but with no luck. What the ef?
Here's my fglrxinfo:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200 Series DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.27.6)

From what I gather, it has something to do with DRI not loading, but I dunno.

---

### Post by Kratos on 2006-08-29
I just installed Initng and followed the instructions completely, but, for some reason, KDM refuses to start. I tried using replacing "sudo ng-update add daemon/gdm" with "sudo ng-update add daemon/kdm" and I got:

"Warning: "daemon/kdm" already installed in runlevel "default""
 
So, maybe this isn't the right command? Help would rock.

Kratos

EDIT: I ran "sudo ngc -s" and noticed this.

```
15:52:43 D daemon/gdm                          : DAEMON_FAIL_START_LAUNCH
```

Any ideas?

---

### Post by subiet on 2006-09-07
When i shut down my system, i see some error regarding eth1, eth2 shutting down, for which i have to wait for 15 secs, is there a way to disable that. coz that error is not causing me any problems,  i am able to use my internet connection thru eth0 via a adsl modem perfectly fine, coz if i have to wait for 15 seconds at shutdown, what is the poin in booting up fast. rest of the initng works perfectly, with aiglx and ntfs tweak, the speed is good too.

one more thing, is there a way to speed up "mounting root file system process".

---

### Post by lepre on 2006-09-07
> **subiet said:**
> When i shut down my system, i see some error regarding eth1, eth2 shutting down, for which i have to wait for 15 secs, is there a way to disable that. coz that error is not causing me any problems,  i am able to use my internet connection thru eth0 via a adsl modem perfectly fine, coz if i have to wait for 15 seconds at shutdown, what is the poin in booting up fast. rest of the initng works perfectly, with aiglx and ntfs tweak, the speed is good too.

one more thing, is there a way to speed up "mounting root file system process".

i have the same problem, it start net/all (lo, eth0/1/2 and others), but i have only eth0 so obviously the others fail, and the same is at shutdown. we must disable net/all and set net/eth0 i think, but i don't know how to do it. :-k

---

### Post by lepre on 2006-09-09
> **subiet said:**
> When i shut down my system, i see some error regarding eth1, eth2 shutting down, for which i have to wait for 15 secs, is there a way to disable that. coz that error is not causing me any problems,  i am able to use my internet connection thru eth0 via a adsl modem perfectly fine, coz if i have to wait for 15 seconds at shutdown, what is the poin in booting up fast. rest of the initng works perfectly, with aiglx and ntfs tweak, the speed is good too.

ok, i solved that the "hard" way, surely there's a better one, but it's working and i gained 5sec in boot time too!

in /etc/network/ there is a file named interfaces, make a backup of that and change it.
i modified mine from this:
```

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface dsl-provider inet ppp
provider dsl-provider

iface eth0 inet dhcp

auto eth0

```
to this:
```

auto lo
iface lo inet loopback

iface dsl-provider inet ppp
provider dsl-provider

iface eth0 inet dhcp

auto eth0

```

i only need lo and eth0, because i have an ethernet router.
(i think i could delete dsl-provider too but it didn't give any error so i left it in)

reboot and at next start you'll have only net/whatyouneed :D

---

### Post by subiet on 2006-09-09
> **lepre said:**
> i have the same problem, it start net/all (lo, eth0/1/2 and others), but i have only eth0 so obviously the others fail, and the same is at shutdown. we must disable net/all and set net/eth0 i think, but i don't know how to do it. :-k

well i found a very simple and safe way to do it, and did it too, here is how, i am assuming that you need only eth0

sudo ng-update del net/all default
sudo ng-update add net/eth0 default

the commands are self explainatory

---

### Post by lepre on 2006-09-09
> **subiet said:**
> well i found a very simple and safe way to do it, and did it too, here is how, i am assuming that you need only eth0

sudo ng-update del net/all default
sudo ng-update add net/eth0 default

the commands are self explainatory

great, i'll try that want since it's less destructive than the method i posted above :D 

i tryed to modify the script net/all to start only eth0 but i couldn't get it to be saved.

anyway, thank you :KS

---

### Post by tjvdberg on 2006-09-09
So far the only problem I'am having is that my Wifi (Intel ipw3945) won't start.

The start command is

```
/sbin/ipw3945d-$(uname -r) --quiet
```

Could someone explain to me how to make it start with initng boot ?
I can start it manualy after I'm in gnome.

---

### Post by lepre on 2006-09-09
> **tjvdberg said:**
> So far the only problem I'am having is that my Wifi (Intel ipw3945) won't start.

The start command is

```
/sbin/ipw3945d-$(uname -r) --quiet
```

Could someone explain to me how to make it start with initng boot ?
I can start it manualy after I'm in gnome.


i think you can try to edit the file named net.i in /etc/initng/net/

---

### Post by tjvdberg on 2006-09-10
Well I tried to do this, but I'am not realy an expert in linux. So I tried doing it, but it didn't work :(

```
#!/sbin/itype
# This is a i file, used by initng parsed by install_service

service net/all {
	stdall = /dev/null;
	need = system/bootmisc;
	use = system/ifupdown-debian;
	use = system/modules system/coldplug daemon/cardmgr;
	script start = {
		mkdir -p /var/run/network
		for i in $(/usr/bin/awk '$0~/^auto / { for (i=2; i<=NF; i++) print $i }' /etc/network/interfaces)
		do
			ngc -u net/${i}
		done
		wait
	};
	script stop = {
		for i in $(/usr/bin/awk '$0~/^auto / { for (i=2; i<=NF; i++) print $i }' /etc/network/interfaces)
		do
			ngc -d net/${i}
		done
		wait
	};
}

service net/lo {
	need = system/bootmisc;
	use = system/ifupdown-debian;
	use = system/modules system/coldplug;
	exec start = /sbin/ifup lo;
	exec stop = /sbin/ifdown lo;
}

daemon daemon/ipw3945 {
	daemon = /sbin/ipw3945d-$(uname -r)
	daemon_args = --quiet
	pid_file = /var/run/ipw3945d.pid
}

service net/* {
	stdall = /dev/null;
	need = system/bootmisc;
	use = system/ifupdown-debian;
	use = system/modules system/coldplug daemon/cardmgr;
	provide = virtual/net virtual/net/${NAME};
	script start = {
		# Put up the interface
		/sbin/ifup ${NAME}
		# Check so its up
		/sbin/ifconfig ${NAME} | /bin/grep -qe "inet addr" -e "inet6 addr" || exit 1
		exit 0
	};
	script stop = {
		set -e
		# Shut down.
		/sbin/ifdown ${NAME}
		# Check so its down.
		# /sbin/ifconfig ${NAME} | /bin/grep -qe "inet addr" -e "inet6 addr" && exit 1
		exit 0
	};
}

```

---

### Post by lepre on 2006-09-10
i would try just with :

service net/mine {
exec start = /sbin/ipw3945d-$(uname -r) --quiet
}

i think you also need some of these use/need voice, but i can't help :(

---

### Post by tjvdberg on 2006-09-10
I fixed it :)

This is my code of ipw3945.i in the daemon folder
```
#!/sbin/itype
# This is a i file, used by initng parsed by install_service

daemon daemon/ipw3945 {
	need = system/bootmisc system/modules/depmod;
	script daemon = {
/sbin/ipw3945d --quiet --log-file=/var/log/ipw3945d --timeout=1
wait
exit 0
};
}

```

---

### Post by lepre on 2006-09-10
great :)

---

### Post by deaderthanyou on 2006-09-11
> **Jingo said:**
> I think InitNG is not cleanly unmounting my drives. Anyone seeing this too?

I am having this exact same problem.  Has anyone found a fix for this yet?  I have everything else working perfectly.

---

### Post by aceracer24 on 2006-09-15
Why am I getting this error?

```
** "/home/david/compile/initng-0.6.7/plugins/simple_launcher/initng_simple_launcher.c", simple_exec_fork()  line:189:
 12:45:38 -- FAIL:      ERROR!
```

This is the directory that I compiled InitNG, it should not beven be seeing or using it...

ANd i am also getting this:

```
12:46:39        daemon/dhcdbd : DAEMON_FAIL_START_TIMEOUT_PIDFILE
 12:46:39 daemon/NetworkManager : DAEMON_START_DEPS_FAILED
 12:46:39              default : START_DEPS_FAILED
```

Network seems to work just fine so I don't know what the errors mean.

---

### Post by aceracer24 on 2006-09-15
> **Jingo said:**
> I think InitNG is not cleanly unmounting my drives. Anyone seeing this too?

Everytime Initng shutdowns/reboot (succesfully) the next startup gives me this:

```

dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  71:49/00, 72:42/00, 73:4d/00, 74:5f/00, 75:53/00, 76:45/00, 77:52/00
  , 78:56/00, 79:49/00, 80:43/00, 81:45/00
  Not automatically fixing this.
/dev/hda2: 7005 files, 1051677/1167624 clusters
/dev/hda8: clean, 30/40160 files, 18877/80293 blocks
Replaying journal..
Trans replayed: mountid 1173, transid 298978, desc 8004, len 21, commit 8026, next trans offset 8009
Trans replayed: mountid 1173, transid 298979, desc 8027, len 1, commit 8029, next trans offset 8012
Trans replayed: mountid 1173, transid 298980, desc 8030, len 1, commit 8032, next trans offset 8015
Trans replayed: mountid 1173, transid 298981, desc 8033, len 1, commit 8035, next trans offset 8018
Trans replayed: mountid 1173, transid 298982, desc 8036, len 1, commit 8038, next trans offset 8021
Trans replayed: mountid 1173, transid 298983, desc 8039, len 8, commit 8048, next trans offset 8031
Trans replayed: mountid 1173, transid 298984, desc 8049, len 1, commit 8051, next trans offset 8034
Trans replayed: mountid 1173, transid 298985, desc 8052, len 1, commit 8054, next trans offset 8037
Trans replayed: mountid 1173, transid 298986, desc 8055, len 1, commit 8057, next trans offset 8040
Trans replayed: mountid 1173, transid 298987, desc 8058, len 1, commit 8060, next trans offset 8043
Trans replayed: mountid 1173, transid 298988, desc 8061, len 1, commit 8063, next trans offset 8046
Reiserfs journal '/dev/hda7' in blocks [18..8211]: 11 transactions replayed
Checking internal tree..finished
Reiserfs super block in block 16 on 0x307 of format 3.6 with standard journal
Blocks (total/free): 6428000/3634336 by 4096 bytes
Filesystem is NOT clean
/dev/hda5: clean, 101581/1281696 files, 738611/2560351 blocks
Reiserfs super block in block 16 on 0x307 of format 3.6 with standard journal
Blocks (total/free): 6428000/3634336 by 4096 bytes
Filesystem is NOT clean

```

This is my fstab:
```

proc            /proc           proc    defaults        0       0
/dev/hda9       /               reiserfs noatime         0       1
/dev/hda8       /boot           ext3    noatime,noauto         0       2
/dev/hda7       /home           reiserfs noatime         0       2
/dev/hda1       /media/hda1     ntfs    defaults,noauto,nls=utf8,umask=007,gid=46,users 0       1
/dev/hda2       /media/hda2     vfat    defaults,noauto,utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda5     ext3    defaults,noauto        0       2
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

If I boot normally, there is no problem, and the journal is not replayed!

Where to look?


I'd also like to know this. I am having the same problems. Using reiserfs for all of my drives except /boot. 

Here is my fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb4       /               reiserfs defaults        0       1
/dev/hda2       /boot           ext2    defaults        0       2
/dev/hdb1       /home           reiserfs defaults        0       2
/dev/hdb3       /usr            reiserfs defaults        0       2
/dev/hdb2       /var            reiserfs defaults        0       2
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/md0	/media/raid	reiserfs defaults	0	2
/dev/hda4	/media/share	reiserfs defaults	0	2
```

No reply, not shocking. ANyway, I ended up solving all my problems myself with teh help of qupad on freenode.net.

---

### Post by MaleqAlhaq on 2006-09-21
> **aceracer24 said:**
> I'd also like to know this. I am having the same problems. Using reiserfs for all of my drives except /boot. 
[...]
No reply, not shocking. ANyway, I ended up solving all my problems myself with teh help of qupad on freenode.net.
Hi!

Though I'm still stuck with the dependency issues (which I will tackle tomorrow, hopefully), it would be nice, if you would post your sollution to that problem, as it seems quite common...
Thank you!

---

### Post by hyper_ch on 2006-09-22
I downloaded the newest version and also have dependency issues:

> 
hyper@hyper-linux:~/Desktop/initng$ dpkg -i *all.deb
dpkg: requested operation requires superuser privilege
hyper@hyper-linux:~/Desktop/initng$ sudo dpkg -i *all.deb
Password:
Selecting previously deselected package initng-ifiles.
(Reading database ... 118517 files and directories currently installed.)
Unpacking initng-ifiles (from initng-ifiles_0.0.5-2_all.deb) ...
Setting up initng-ifiles (0.0.5-2) ...
system.virtual already exists, skipping...
default.runlevel already exists, skipping...
Done generating files.

hyper@hyper-linux:~/Desktop/initng$ sudo dpkg -i *i386.deb
Selecting previously deselected package initng.
(Reading database ... 118527 files and directories currently installed.)
Unpacking initng (from initng_0.6.7-1_i386.deb) ...
dpkg: dependency problems prevent configuration of initng:
 initng depends on libc6 (>= 2.3.6-6); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
dpkg: error processing initng (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 initng
hyper@hyper-linux:~/Desktop/initng$


any suggestions?

---

### Post by moore.bryan on 2006-10-08
*when following the [wiki instructions]("http://ubuntuforums.org/showpost.php?p=1173519&postcount=80"), there's no initng entry in the status file... ideas?*

---

### Post by notarikon on 2006-10-08
Okay, well it installed fine, boots *very* quick (<20 secs) but there's a slight problem ...

I log in and get my taskbar and menu, etc., but there is no desktop - no icons, no right click, etc. I can still open windows such as home and firefox from the menu, but nothing can be added to or seen on the background. Any ideas?

Only other issue was a problem with eth0 but that was fixed using the guide.

---

### Post by battletux on 2006-10-12
Ok so I am following the Wiki guide but i am getting the following error:

```
dpkg-deb: building package `initng' in `../initng_0.6.7-1_i386.deb'.
dpkg-deb: building package `initng-dev' in `../initng-dev_0.6.7-1_i386.deb'.
 signfile initng_0.6.7-1.dsc
gpg: WARNING: unsafe ownership on configuration file `/home/andmck/.gnupg/gpg.conf'
gpg: skipped "Armin Berres <a.berres@onlinehome.de>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available

```

Any ideas?

---

### Post by Killerah on 2006-10-21
I'm getting the same problem, any help would be nice.

---

### Post by crispibits on 2006-10-22
> **aceracer24 said:**
> No reply, not shocking. ANyway, I ended up solving all my problems myself with teh help of qupad on freenode.net.

I'm really glad you solved all the problems with reiserfs yourself.  Any chance you could actually give something back to the forums and say how you did it please?

Thanks,
Crispibits

---

### Post by ahaslam on 2006-10-23
> **battletux said:**
> Ok so I am following the Wiki guide but i am getting the following error:

```
dpkg-deb: building package `initng' in `../initng_0.6.7-1_i386.deb'.
dpkg-deb: building package `initng-dev' in `../initng-dev_0.6.7-1_i386.deb'.
 signfile initng_0.6.7-1.dsc
gpg: WARNING: unsafe ownership on configuration file `/home/andmck/.gnupg/gpg.conf'
gpg: skipped "Armin Berres <a.berres@onlinehome.de>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available

```

Any ideas?

I'm also getting this exact problem - secret key :-k . I have also tried installing the .deb, but get the 'libc6' dep error.

Any help would be appreciated ;)

Tony.

***EDIT:***

I found some newer ubuntu deb's here: [http://download.initng.org/debs/ubuntu/](http://download.initng.org/debs/ubuntu/)

They install without probs ;)

---

### Post by glotz on 2006-10-25
Hi there. Installed according to [https://help.ubuntu.com/community/InitNG](https://help.ubuntu.com/community/InitNG)

When I boot with it, it fails to start X however. I'm using an older nvidia card and use glx-nvidia-legacy driver. (external kernel module or some such...) I guess I should somehow include that to some startup file but how is a mystery to me.

Thanks for any advice! Keep it simple please, I'm pretty fresh with Linux. :-D

---

### Post by glotz on 2006-10-28
boomp! Anybody?

---

### Post by whomever21 on 2006-12-06
Excellent thread. Helped me through about a thousand other issues I was having, but these last two are stubborn. 

I keep getting an error from system/alsasound/mixerstate. ngc -l reports 

 ------------------------------------------------------
     system/alsasound | SERVICE_DONE (after 1 seconds)
 system/alsasound/mixerstate : ERROR: Cannot find alsactl, did you forget to install media-sound/alsa
 system/alsasound/mixerstate : -utils?
 system/alsasound/mixerstate | SERVICE_FAIL_START_RCODE
       system/urandom | SERVICE_DONE (after 1 seconds)
 daemon/acpid/modules : FATAL: Error inserting asus_acpi (/lib/modules/2.6.15-27-386/kernel/dr
 daemon/acpid/modules : ivers/acpi/asus_acpi.ko): No such device
 system/ifupdown-debian | SERVICE_DONE (after 1 seconds)
----------------------------------------

I tried ng-update d alsasound after noticing that alsact1 is, in fact, missing, but that didn't work. Alsa-utils was already installed, reinstalling didn't help, and I'm out of ideas. 

The other problem involves the keyboard. Certain keys ('c' and '.' among others) don't work unless I hit them twice after each reboot. So to spell carrot, I'll have to type ccarrot--only the second 'c' takes. I don't know enough about the init process to even begin to parse this weirdness.

Any ideas?

---

### Post by whomever21 on 2006-12-06
OK--I fixed the ALSA problem by going into /etc/initng/default.runlevel and removing system/alsasound/mixerstate manually. I haven't noticed any errors or loss of functionality as a result, but I'm still having trouble with the keyboard. 

ngc -l reports:

------------------------------------------------------
 daemon/acpid/modules : FATAL: Error inserting hotkey (/lib/modules/2.6.19/kernel/drivers/acpi
 daemon/acpid/modules : /hotkey.ko): No such device
       system/keymaps : Problem when loading /etc/console/boottime.kmap.gz, use install-keymap
            device/lo | NIC_UP
          device/eth0 | NIC_UP
----------------------------------------------------

There are other acpi errors:

------------------------------------------------------
 daemon/acpid/modules : FATAL: Error inserting ibm_acpi (/lib/modules/2.6.19/kernel/drivers/ac
 daemon/acpid/modules : pi/ibm_acpi.ko): No such device
               net/lo | SERVICE_DONE (after 2 seconds)
       virtual/net/lo | PROVIDED (after 9 seconds)
 daemon/acpid/modules : FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.19/kernel/driver
 daemon/acpid/modules : s/acpi/toshiba_acpi.ko): Unknown symbol in module, or unknown
 daemon/acpid/modules : parameter (see dmesg)
 daemon/acpid/modules | SERVICE_DONE (after 3 seconds)
         daemon/acpid | DAEMON_RUNNING
   system/laptop-mode | SERVICE_DONE (after 3 seconds)
------------------------------------------------------

Removing acpi from default.runlevel does away with the ibm_acpi error, but, with or without system/keymaps, it merely changes the keymap error from "FATAL" to:

 ------------------------------------------------------
       system/keymaps : Problem when loading /etc/console/boottime.kmap.gz, use install-keymap
          daemon/hald | DAEMON_RUNNING (after 1 seconds)
            device/lo | NIC_UP
          device/eth0 | NIC_UP
------------------------------------------------------

/etc/console/boottime.kmap.gz exists, but I tried running /usr/sbin/install-keymap anyway. Unfortunately, it asks me which keymap file to install. # man keymap-install tells me where the keymaps live (/usr/share/keymaps) but even if I knew which keymap to install, I neither know how nor whether I should edit system/keymaps.i to point to the one I want. 

Any help would be appreciated.

---

### Post by 09adi09 on 2007-02-06
could use some help here!
i did ccmake .. for initng-ifiles but when i do make it gives the following error.what to do?
Also if the whole thing does not work or my system gets screwed because of this,how do i revert to my original configuration?

.:[10:53:16]:. 0.02  $ sudo make
[  0%] Building C object tools/CMakeFiles/install_service.dir/install_service.o
/home/aditya/initng-ifiles-0.0.7/tools/install_service.c:34:26: error: initng-paths.h: No such file or directory
/home/aditya/initng-ifiles-0.0.7/tools/install_service.c:73: error: ‘INITNG_PLUGIN_DIR’ undeclared here (not in a function)
make[2]: *** [tools/CMakeFiles/install_service.dir/install_service.o] Error 1
make[1]: *** [tools/CMakeFiles/install_service.dir/all] Error 2
make: *** [all] Error 2

---

### Post by effenberg0x0 on 2007-04-12
I'm trying to use InitNG on my Ubuntu Edy notebook for a while and I cannot find a way to get over this problem. This is what I see when I boot (yes, I did had to take notes of all this in on paper and retype it all, and there might be errors in this transcription, but please, consider helping me lol)...

System/Swap [SERVICE_FAIL_START_RCODE]
System/bootmisc [SERVICE_START_DEPS_FAILED]
Daemon/acpcid/modules [SERVICE_START_DEPS_FAILED]
Daemon/dbus [DAEMON_START_DEPS_FAILED]
Daemon/Syslogd [DAEMON_START_DEPS_FAILED]
Daemon/Syslogd/Prepare [DAEMON_START_DEPS_FAILED]
Net/All [SERVICE_START_DEPS_FAILED]
System/Urandoml [SERVICE_START_DEPS_FAILED]
Daemon/Getty/2 to 6 [DAEMON_START_DEPS_FAILED]
Net/Lo [SERVICE_START_DEPS_FAILED]
System/Keymap [SERVICE_START_DEPS_FAILED]
System/Usb  [SERVICE_START_DEPS_FAILED]
System/Alsasound  [SERVICE_START_DEPS_FAILED]
System/Alsasound/cards  [SERVICE_START_DEPS_FAILED]
System/Alsasound/mixerstate  [SERVICE_START_DEPS_FAILED]
System/laptop-mode  [SERVICE_START_DEPS_FAILED]
Daemon/klogd [DAEMON_START_DEPS_FAILED]
Daemon/gdm [DAEMON_START_DEPS_FAILED]
Daemon/cupsd [DAEMON_START_DEPS_FAILED]
Daemon/hpiod [DAEMON_START_DEPS_FAILED]
Daemon/hpssd [DAEMON_START_DEPS_FAILED]
Daemon/acpid [DAEMON_START_DEPS_FAILED]
Daemon/hald [DAEMON_START_DEPS_FAILED]
System/Console-Screen [SERVICE_START_DEPS_FAILED]
Default [START_DEPS_FAILED]

At this point, nothing else happens, I do not get to Gnome or the console and all I can do is CTRL+ALT+DEL...

Any ideas will be very appreciated.
Thanks,
Effenberg

---

### Post by torena on 2007-04-26
> **effenberg0x0 said:**
> I'm trying to use InitNG on my Ubuntu Edy notebook for a while and I cannot find a way to get over this problem. This is what I see when I boot (yes, I did had to take notes of all this in on paper and retype it all, and there might be errors in this transcription, but please, consider helping me lol)...

System/Swap [SERVICE_FAIL_START_RCODE]
System/bootmisc [SERVICE_START_DEPS_FAILED]
Daemon/acpcid/modules [SERVICE_START_DEPS_FAILED]
Daemon/dbus [DAEMON_START_DEPS_FAILED]
Daemon/Syslogd [DAEMON_START_DEPS_FAILED]
Daemon/Syslogd/Prepare [DAEMON_START_DEPS_FAILED]
Net/All [SERVICE_START_DEPS_FAILED]
System/Urandoml [SERVICE_START_DEPS_FAILED]
Daemon/Getty/2 to 6 [DAEMON_START_DEPS_FAILED]
Net/Lo [SERVICE_START_DEPS_FAILED]
System/Keymap [SERVICE_START_DEPS_FAILED]
System/Usb  [SERVICE_START_DEPS_FAILED]
System/Alsasound  [SERVICE_START_DEPS_FAILED]
System/Alsasound/cards  [SERVICE_START_DEPS_FAILED]
System/Alsasound/mixerstate  [SERVICE_START_DEPS_FAILED]
System/laptop-mode  [SERVICE_START_DEPS_FAILED]
Daemon/klogd [DAEMON_START_DEPS_FAILED]
Daemon/gdm [DAEMON_START_DEPS_FAILED]
Daemon/cupsd [DAEMON_START_DEPS_FAILED]
Daemon/hpiod [DAEMON_START_DEPS_FAILED]
Daemon/hpssd [DAEMON_START_DEPS_FAILED]
Daemon/acpid [DAEMON_START_DEPS_FAILED]
Daemon/hald [DAEMON_START_DEPS_FAILED]
System/Console-Screen [SERVICE_START_DEPS_FAILED]
Default [START_DEPS_FAILED]

At this point, nothing else happens, I do not get to Gnome or the console and all I can do is CTRL+ALT+DEL...

Any ideas will be very appreciated.
Thanks,
Effenberg

I'm getting exactly the same errors, words for words.  I was just about to resign myself to writing it all down on paper as well so I'm glad I checked here first.  :P

I saw those errors until I enabled initng-usplash, and now I can't see anything that's going on in the background until my usb keyboard is initialized which is usually too late to see these errors show up.

Torena

---

### Post by torena on 2007-04-26
Well I found on [http://www.initng.org/](http://www.initng.org/) that there are new repositories from 4/6/07:

> deb [http://debian.mawk.org/debian/](http://debian.mawk.org/debian/) sid main
deb-src [http://debian.mawk.org/debian/](http://debian.mawk.org/debian/) sid main

Once I aptitude update'd I got the notification of a newer version of initng available.  I installed it, rebooted, and this time I booted right into Gnome!  The only problem is that I had no network connection.  Tried restarting networking but got an error:

> torena@starbuck:~$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces...                                          
ifdown: failed to open statefile /var/run/network/ifstate: No such file or directory
ifup: failed to open statefile /var/run/network/ifstate: No such file or directory

Now I'm at a loss of what to do.

Torena

---

### Post by Carcass on 2007-04-27
Hi :) 

but instead of (for example) **ng-update add daemon/gdm** there isn't a single command to update file in a single time??

If I use the command **genrunlevel --all** at reboot  initng not arrive at login and some service is deprecated .....:( 

any idea ???

at the end I have this

Failing services:

runlevel/default

daemon/kdm (but I don't use kdm, gdm, and so on....)

net/dsl-provider

---

### Post by Carcass on 2007-04-28
up :confused:

---

### Post by Jarn on 2007-07-04
I installed initng via the instructions here: [https://help.ubuntu.com/community/InitNG](https://help.ubuntu.com/community/InitNG)

The difference is, seriously, insane. However, when I boot it says that it failed to start cups and some other things related to printing (HP apps whose names I forget) and then if I try to print anything the program that I print in freezes and I have to kill it.

I can start CUPS myself and it works but that is a bit of a hassle.

---

### Post by matt1606 on 2007-09-01
Hello!

I'm having a strange looking problem with initng. I'm currently using NetworkManger for my network connection. The deamon is loaded correctly douring boot process, but gdm daemon is not. After a minute or two I recieve na error saying: 'Error Starting the Gnome Settings Daemon' and my desktop loads. When I unplug my RJ45 cable douring boot everything is working correctly so does when I'm not loading the NetworkManager daemon at all. I don't get other error messages using initng. What's the reason?


Here is the full error message:

There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

My problem ended unexpectedly while I've occasionally built and installed newer NetworkManager packages (v. 6.5.1). So this was rather NM problem  than initNG or GNOME. But I observe that booting ubuntu twice (one after another) with initNG causes the same problem. When I boot using default init and then initNG everything works well. Still no idea why (??).

---

### Post by andrek on 2008-01-26
As someone said before, the difference is insane!
But I've got one problem - at shutdown/restart, it waits extra 15seconds just to let me see an error - 
daemon/gdm - DAEMON_FAIL_START_SIGNAL
What's going on? gdm works great.. System would close in 2 seconds without that annoying stop.. Help anyone? :)

edit:
Nevermid, i dit:
ng-update del gdm
ng-update add gdm
and the problem disappeared

---

### Post by markp1989 on 2008-01-28
i have installed initng on gusty, and it boots alot faster, well it seems to.

i cannot get bootchart to time my boot with initng, anyone know a fix?

---

### Post by phenest on 2008-01-28
It would be nice to see an updated HowTo for InitNG.

I have been trying to get this to work to no avail. I've installed it and added the necessary to the grub menu and it boots ok. But... I don't get any GUI. I added daemon/gdm but it stops at a bash prompt.

:confused:

---

### Post by Carcass on 2008-01-29
[http://www.debianclan.org/index.php?option=com_content&task=view&id=85&Itemid=38&lang=en](http://www.debianclan.org/index.php?option=com_content&task=view&id=85&Itemid=38&lang=en)

this is a very good howto writed..........

---

### Post by BatPenguin on 2008-01-29
So are you using this on Gutsy? And works fine? What sort of time difference are we talking about...my Gutsy starts up pretty fast (less than a minute) as it is, what do you think the difference would be with this? Thanks.

---

### Post by glotz on 2008-01-29
Gutsy uses upstart making this obsolete I believe. [http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

---

### Post by markp1989 on 2008-03-06
i have installed initng, and it definatly boots faster, but bootchart doesnt work no more, anyideas why, and how i get it to work?

---

### Post by nguyenthetam on 2008-03-26
IntNG is not needed on Ubuntu now
More info: [https://help.ubuntu.com/community/InitNG](https://help.ubuntu.com/community/InitNG)

---

### Post by palito1980 on 2008-05-30
My problem with Initng is that my system, after I have done the change into Initng, is in English while originally it was in Polish. Anyone know how to change it?

---

### Post by psyke83 on 2008-06-01
> **palito1980 said:**
> My problem with Initng is that my system, after I have done the change into Initng, is in English while originally it was in Polish. Anyone know how to change it?

Don't use InitNG, it's obsolete. Ubuntu (since 6.10) has switched to a new daemon called upstart.

[http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

---

### Post by palito1980 on 2008-06-03
It may be obsolete but my system starts much much faster and information given during boot is much more clear. I just cannot figure out the way how to make it boot my ubuntu into Polish language

---

### Post by ukripper on 2008-06-03
> **glotz said:**
> Gutsy uses upstart making this obsolete I believe. [http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

I agree! upstart is already used by 7.10 +.

---

### Post by palito1980 on 2008-06-09
> **ukripper said:**
> I agree! upstart is already used by 7.10 +.

It may use upstart but as for me initNG is better.System starts faster. My machine is rather slow and faster boot, on initNG, is very visible.Problem is that is boots into english but I want it in Polish.How can I change it?

---

### Post by ukripper on 2008-06-09
> **palito1980 said:**
> It may use upstart but as for me initNG is better.System starts faster. My machine is rather slow and faster boot, on initNG, is very visible.Problem is that is boots into english but I want it in Polish.How can I change it?

I am glad it works for you. But I rather use which is supported by my kernel and clearly initng ain't supported in 2.6.25-4

---

### Post by markp1989 on 2008-09-20
i used to autologin when using the old init without gdm.

using this how to.
> Autologin

Automatically logging in to your computer will make your start sequence seem faster, especially if you want your machine to go straight to a desktop. To build an autologin in Ubuntu, you'll need to install some software, and compile a program.

First,

sudo aptitude install build-essential

That installs the toolchain, which is not part of a default Ubuntu system. Next, open a text file called "autologin.c" and copy this into it.

int main() {
	execlp( "login", "login", "-f", "insert_login_name", 0);
}

Now compile the program and put it in the /usr/local/sbin/ directory.

sudo gcc -o /usr/local/sbin/autologin autologin.c

Next, tell Ubuntu to run that program when it gets to the tty1 login screen. We can do that from /etc/event.d/tty1, so edit that with

sudo nano -w /etc/event.d/tty1

Change this line

exec /sbin/getty 38400 tty1

to

exec /sbin/getty -n -l /usr/local/sbin/autologin 38400 tty1


then add

if [ -z "$DISPLAY" ] && [ $(tty) == /dev/tty1 ]; then
       startx
fi

to ~/.profile
 


how can i do a similar thing using init ng?

---

