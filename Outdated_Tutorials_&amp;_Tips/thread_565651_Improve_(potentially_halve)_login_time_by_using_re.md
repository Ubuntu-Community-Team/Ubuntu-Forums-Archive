---
title: "Improve (potentially halve) login time by using readahead"
date: 2007-10-02
forum: Outdated Tutorials &amp; Tips
---

### Post by jdong on 2007-10-02
**NOTE: This tip NO LONGER APPLIES to Ubuntu 9.10 and higher** -- these releases use a new "sreadahead" subsystem that takes care of reprofiling automatically whenever the bootup sequence changes (and also monthly).


[SIZE="5"]PREFACE[/SIZE]:

It has been well-documented that Ubuntu's readahead system during boot significantly cuts down on boot time by reducing hard disk seeking via  precaching commonly-used files during bootup. This feature, however, only lasts up to the GDM screen. The average modern PC should be able to boot Ubuntu from GRUB to the GDM screen in under 30 seconds -- roughly half of what it would be if readahead were to be turned off.

For me, I start a lot of things when I log into my GNOME session. My laptop
boots from GRUB to GDM in about 14 seconds, but from the moment I log in to a full desktop is nearly 40 seconds, most of the time the disk is seeking like crazy. This led me to wonder, is it possible to extend readahead's benefits to accelerate the login sequence?

[SIZE="5"]RISK/KNOWLEDGE DISCLAIMER:[/SIZE]
This guide asks you to use the command-line to issue some commands, and uses the readahead-list and readahead-watch applications to profile a bootup. Changes to the system are easily reversible and the worst negative impact would be a reduction in login speed (the irony!). Of course, since you will be doing some things with root access, failure to correctly type in some commands may lead to permanent damage to your software or data. These changes are unsupported by Ubuntu developers.

[SIZE="5"]SYSTEM SPECS:[/SIZE]
Ubuntu Gutsy on Core Duo 1.66GHz with 1GB RAM. Slow laptop 5400RPM drive. **You probably shouldn't try this unless you have more than 512MB RAM.**

System was rebooted cleanly and I inputted my login when all disk activity stopped. Then, I logged in and waited for all disk activity to stop again. This login time is what I aim to reduce.

On my particular system, with a highly customized GNOME session, this login time without optimization is: 40 seconds. A subsequent login (where everything would be cached, ideal boot speed with disk bottleneck removed) takes: 13 seconds. I will try to get as close to that as possible!


[SIZE="5"]
PART 1: Profile Login Sequence[/SIZE]

First, we need to ask readahead to monitor a login sequence and make note of all the files read during this period. Advanced users may point out that during bootup, there is a GRUB argument "profile" that causes Ubuntu to optimize bootup. We will need to essentially manually replicate what this boot option does, but save the output to a different file.

First, let's store our readahead list into a ~/.readahead directory.

```

mkdir ~/.readahead

```

Now, log out, and press CTRL+ALT+F1 to log into a terminal. Start the profiler:

```

sudo readahead-watch -o ~/.readahead/gnome.root /

```

This will grind the disk for a while (up to a few minutes) then it will return you to a command prompt. The profiler is now in the background watching all actions. Now, without logging out, go to your GDM prompt (ALT+F8 ) and log in normally.

after you are fully logged in, press CTRL+ALT+F1 to go back to your terminal, then run:
```

sudo killall readahead-watch
sudo chown jdong:jdong ~/.readahead -R

```

Replace jdong:jdong with your user and group name. Now, we need to go prune this list a bit. Especially if you have large files on your desktop (like a 1GB AVI), the login sequence may touch it, causing readahead to think it should load the whole thing into memory! In a terminal, run:

```

cat ~/.readahead/gnome.root | xargs -i ls -lk {} | sort -rn -k +5 | less

```

This will display all the files readahead wants to cache, sorted by largest file first. The 5th column (before date) is the size of the file in KB. Make sure there's nothing glaringly large. If it's bigger than 10,000KB or so, it's probably not worth preloading. You can remove unwanted files from the preload list by opening ~/.readahead/gnome.root in your favorite editor, and deleting its line.

** If you have home on a different partition as root, you should repeat Part 1 for each partition, replacing gnome.root with a different name, and replacing the mountpoint / with each interested mountpoint. **


[SIZE="5"]PART 2: Hooking this into the login sequence.[/SIZE]

Next, we need to tell Ubuntu to do this readahead on every login. I am going to use /etc/X11/Xsession.d for this, but if you have another preferred way to execute things before everything loads, be my guest!

Create a file called **/etc/X11/Xsession.d/00readahead** and put this in it:
```

for list in ~/.readahead/*; do
  readahead-list $list &
done

wait

```

Save the file. Now, you can reboot to try it out. You will notice the login
"hang" at the orange screen while the disk works without much grinding, then once that is done the bootup should soar as if it were a fully cached login. This brings my login session to around 30 seconds, a notable improvement.

[SIZE="5"]PART 3: Hook into bootup sequence[/SIZE]

Often times, we don't log in immediately when the prompt comes up. We might be getting a cup of coffee, or an entire lab might be turned on before students arrive. It makes sense to cache a login as a part of bootup. Open up /etc/rc.local in your favorite text editor, and before the exit 0 statement, add:
```

for list in /home/jdong/.readahead/*; do
  readahead-list $list
done

```

Note you need to hard-code a particular user in there, and this time we don't background it. (We could, but there is not much motivation to)

Now, reboot, and wait for all disk activity to stop before logging in. This
time, I get a login speed of 19 seconds.

You might have two common questions at this point:

1. How much time does it take to call readahead again on files that have been cached once already? **About 0.05 seconds to call readahead on the same list a second time**

2. How much overhead does it add to bootup if the background readahead was still going, and you tried to log in? ** About 2 seconds on my setup**


[SIZE="5"]CONCLUSION:[/SIZE]

In my case, applying this readahead hack lead to a 10-second improvement in login speed in the worst-case scenario, and a remarkable doubling in login speed when the system idles at the login prompt for a few seconds.

This is a pretty appreciable improvement and it would be nice if a nicer version of this hack can be added to Ubuntu. The basic idea should be fairly simple to adapt to an /etc/readahead/readahead.gnome file representative of the default system and hooked by an Xsession.d script.

[size=5]Potential follow-ups?[/size]

Many more applications come to mind as taking a long time to load while the disk grinds (Firefox? Openoffice? Eclipse?). You can use a procedure very similar to this to write a "wrapper script" that first performs a readahead-list call on a list, then call the application with the original arguments. I'd be interested to hear of any improvements gained by that method.

[size=5]Undoing This Tip[/size]

Remove, remove, remove! Delete the ~/.readahead directory, delete /etc/X11/Xsession.d/00readahead, and delete the line you added to /etc/rc.local

---

### Post by maharbA on 2007-10-02
F8) = F8

---

### Post by jdong on 2007-10-02
Thanks, fixed.

---

### Post by maharbA on 2007-10-02
WOW!

Great how-to. I only did the first 2 parts (since I auto login to my main user there's no wait before login -- should I go ahead and do part 3?) but *hot damn* my login is fast. Ubuntu already beat XP (about 1/5 the time) but now I'm up and running less than a minute after hitting the power button.

PS: When I did this, CTRL+ALT+F7 got me back into the wonderful world of X -- not CTRL+ALT+F8

This should DEFINITELY be a part of all future Ubuntu releases.

---

### Post by jdong on 2007-10-02
> **maharbA said:**
> WOW!

Great how-to. I only did the first 2 parts (since I auto login to my main user there's no wait before login -- should I go ahead and do part 3?) but *hot damn* my login is fast. Ubuntu already beat XP (about 1/5 the time) but now I'm up and running less than a minute after hitting the power button.

PS: When I did this, CTRL+ALT+F7 got me back into the wonderful world of X -- not CTRL+ALT+F8

This should DEFINITELY be a part of all future Ubuntu releases.

I am thrilled it worked miracles for you. There's a bunch of network-related operations in my login sequence (remember -- heavily customized) so the average user should see much BETTER improvements than what I listed.

If you auto-login, there is no reason to do part 3. That's more for people who find themselves booting up and having the computer wait for you to log in.

---

### Post by jimbren on 2007-10-04
Sweet.  I'm assuming that the file 
```
/gnome.root /
```
is just your output file, is that right?

I'm running Kubuntu, and I just want to make sure I don't need to change anything.

If my thinking is correct, I could either leave the filename alone, since it really doesn't matter, or change it to kde.root 

and have the same impact, is that correct?

thanks,

jimbo

---

### Post by jdong on 2007-10-04
gnome.root is just an arbitrary name, you can call it whatever you want. This procedure works with whatever login session you use.

---

### Post by smartboyathome on 2007-10-05
Thanks for this howto! It worked great for me! Before it took ~30 seconds to go from Login Screen (with no disk usage) to Desktop (with no disk usage). Now, it is very quick!

---

### Post by brazzmonkey on 2007-10-07
i wish i could claim such results on my machine, but i think readahead kind of misbehaves here : it actually slows down things very much (i noticed very high disk activity, so i suspect there's something wrong with caching - may i add there's no big file to be cached, but there seems to be a lot of small files).
note that this does not seems specific to this trick, because last time i added "profile" to my kernel grub entry (in order to speed up next booting processes using readahead), my bootcharts jumped from 60-65 seconds, to somewhere near 200 seconds. Culprit was : readahead. it would generate high disk activity for about 140 seconds.

maybe my ubuntu installation is getting old and messy&#8230;

---

### Post by jdong on 2007-10-07
Hmm, how much RAM do you have?

Also, have you used the last command in part 1 to check what sizes are the files Readahead wants to load? I suspect there's some sort of large ISO image or something that Readahead is thinking it should load into RAM, but it really shouldn't.

---

### Post by brazzmonkey on 2007-10-08
hi jdong,
i have 2gb of RAM. surely i removed the biggest files as you advised to (there was a few files ranging from 10mb to 35mb), no big deal, though.

i don't know why there are so many other files cached, especially files i barely use (nvidia-settings, ktorrent for instance). they're not loaded during login so i don't understand why readahead would cache them.

---

### Post by jdong on 2007-10-08
> **brazzmonkey said:**
> hi jdong,
i have 2gb of RAM. surely i removed the biggest files as you advised to (there was a few files ranging from 10mb to 35mb), no big deal, though.

i don't know why there are so many other files cached, especially files i barely use (nvidia-settings, ktorrent for instance). they're not loaded during login so i don't understand why readahead would cache them.


That's pretty odd... Are you sure between the time you started readahead-watch and logging in, there wasn't anything running in the background that was accessing the disk? Could just be bad luck and the profiling caught a flurry of background activity.

---

### Post by brazzmonkey on 2007-10-08
yes, i'm sure there was no background activity.
FYI, i use kubuntu 7.04, if that matters.

attached you'll find the output of the sorting command, for my / (i have a dedicated partition for /home, too).
you'll see there quite a bunch of files which are to be cached (some are very big, indeed&#8230;).

i suspect some files are already being cached while logging in, that would explain why there are so many references to programs that are not running&#8230;

one advice when caching files from /home : empty your trash bin before caching, or remove any reference to trashed files beforehand.

just my &#8364; 0.02.

---

### Post by foxy123 on 2007-10-10
I have upgraded to Gutsy and tried this method (in Feisty I just used to do profiling during the boot). In Feisty I could boot up in 35-37 sec but now it is 1 min, even after the optimisation from this thread. I have attached my bootcharts from both Feisty and Gutsy.

---

### Post by DDM on 2007-10-13
According to bootchart, readahead actually COSTS me 10 seconds on my desktop using Gutsy. I'll try the process again and hopefully it'll work.

---

### Post by jdong on 2007-10-13
Bootchart does not always reflect actual boot times you experience as a user (GDM is spawned at S13, while bootchart is stopped at S99) -- use the old-fashioned stopwatch method to time your bootups

---

### Post by DDM on 2007-10-13
Yeah I realized after I posted it that I wasn't accounting for post-gdm times. Anyways, this did wonders for my 2 year old laptop, not so much for my pretty new desktop.

---

### Post by jdong on 2007-10-13
The faster seek-times your disk has, and the more heuristics your disk has to minimize seeking when given a huge number of IO Requests, the less this hack will do.

(Note specifically relating to the rc.local hack, bootchart will count all of the GNOME prefetching towards the boottime, which of course will inflate that number)

---

### Post by Hakimio on 2007-10-26
I have the same problem as brazzmonkey has.
No background activity (even prevented tracker from starting and removed all the icons from the desktop) and the file is REALLY BIG. I am using Ubuntu 7.04.
I have attached the generated file.
BTW: I have 1GB of RAM.

---

### Post by JSorrell on 2007-10-27
Your guide didn't halve my login time. It eliminated it almost entirely. I went from upwards of 10 seconds or more to roughly one second. This is with 2 gigs of RAM.

Absolutely fantastic.

---

### Post by Hakimio on 2007-10-27
> **JSorrell said:**
> Your guide didn't halve my login time. It eliminated it almost entirely. I went from upwards of 10 seconds or more to roughly one second. This is with 2 gigs of RAM.

Absolutely fantastic.
What version of Ubuntu do you use?

---

### Post by jdong on 2007-10-27
Hakimio, you might just be starting up way too many things at startup for this hack to work for you.... it seems to be loading Firefox, Switfox, Skype, etc etc etc.

---

### Post by Rinzwind on 2007-10-27
Good evening.

Gutsy: boottime from GRUB showing 0 seconds up to the startup sound inside GNOME ending: 43 seconds. 

BRB after doing these changes.

argh. it'll take a bit longer. I don't seem to have a working tty1 :X wtf.

---

### Post by Hakimio on 2007-10-27
> **jdong said:**
> Hakimio, you might just be starting up way too many things at startup for this hack to work for you.... it seems to be loading Firefox, Switfox, Skype, etc etc etc.
The thing is, I don't start anything except gnome :/ Can it be related to preloader? BTW, does it go to the background instantly after issueing *sudo readahead-watch -o ~/.readahead/gnome.root /* for you? For me it waits few minutes while my hdd is working and only then goes to the background...

---

### Post by JSorrell on 2007-10-27
> **Hakimio said:**
> What version of Ubuntu do you use?

7.10

---

### Post by Hakimio on 2007-10-27
> **Rinzwind said:**
> 

argh. it'll take a bit longer. I don't seem to have a working tty1 :X wtf.

Offtopic, but... I guess you are experiencing [this](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910) bug.

---

### Post by Rinzwind on 2007-10-27
> **Hakimio said:**
> Offtopic, but... I guess you are experiencing [this](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910) bug.

Yes I allready found that on these forums :) But I can't remember why I put vga=791 inside that (it was to fix something :P )

But I did all above and it is not much: 42 seconds :(

The gnome.root has the following:

> /lib/ld-2.6.1.so
/lib/libncurses.so.5.6
/lib/libpam.so.0.81.6
/lib/security/pam_unix.so
/lib/terminfo/l/linux
/lib/tls/i686/cmov/libc-2.6.1.so
/lib/tls/i686/cmov/libdl-2.6.1.so
/lib/tls/i686/cmov/libnsl-2.6.1.so
/lib/tls/i686/cmov/libnss_compat-2.6.1.so
/lib/tls/i686/cmov/libnss_files-2.6.1.so
/lib/tls/i686/cmov/libnss_nis-2.6.1.so
/etc/group
/etc/ld.so.cache
/etc/shadow
/etc/locale.alias
/etc/nsswitch.conf
/etc/sudoers
/etc/pam.d/common-auth
/etc/pam.d/sudo
/etc/localtime
/usr/lib/gconv/gconv-modules.cache
/bin/more
/usr/lib/locale/en_US.utf8/LC_ADDRESS
/usr/lib/locale/en_US.utf8/LC_COLLATE
/usr/lib/locale/en_US.utf8/LC_CTYPE
/usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
/usr/lib/locale/en_US.utf8/LC_MEASUREMENT
/usr/lib/locale/en_US.utf8/LC_MONETARY
/usr/lib/locale/en_US.utf8/LC_NAME
/usr/lib/locale/en_US.utf8/LC_NUMERIC
/usr/lib/locale/en_US.utf8/LC_PAPER
/usr/lib/locale/en_US.utf8/LC_TELEPHONE
/usr/lib/locale/en_US.utf8/LC_TIME
/usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
Should that be more? 
Cuz these are all very small fries :)


I think I did it wrong. I killed it before logging in.
(can you say OOPS).

Brb gonna do it again :D

---

### Post by Rinzwind on 2007-10-27
41 seconds :P

gnome.root has 1418 files but not alot of improvement is speed :(

Pity :)

---

### Post by jdong on 2007-10-27
> **Hakimio said:**
> The thing is, I don't start anything except gnome :/ Can it be related to preloader? BTW, does it go to the background instantly after issueing *sudo readahead-watch -o ~/.readahead/gnome.root /* for you? For me it waits few minutes while my hdd is working and only then goes to the background...

This will indeed conflict with preload -- preload must be correlating your login with launching your favorite apps, which is why it's prefetching so much.

It is supposed to take a few minutes before it goes into the background.

---

### Post by Hakimio on 2007-10-28
> **jdong said:**
> This will indeed conflict with preload -- preload must be correlating your login with launching your favorite apps, which is why it's prefetching so much.
Yup, preload was causing this. I think you should definitely write about this issue in the "how to".
Anyway, readahead trick didn't really help, but removing preload (stupid thing - not gonna use it ever again) reduced my login time by 5 seconds, it now takes ~5 seconds and I don't see any side effects of not having preload.

---

### Post by gregili on 2007-10-28
Before this how to about 35 secs.
After the reboot it did about 8 secs after the login screen.

Really nice ! Thanx...

---

### Post by loadeddreams on 2007-10-29
I mkdir readahead, issue sudo readahead-watch -o readahead/gnome.root, I then login and sudo killall readahead-watch 
but there is never a gnome.root file inside of my readahead directory.... just empty file.

readahead-watch did spin the disk the first time ran for about 30 seconds, but from then on it runs instantly.

why is there no gnome.root file?

EDIT: well, using the full directory (/home/user/readahead/gnome.root) seemed to work. not sure why it didn't before, considering I was in my home dir, used sudo and issued it to readahead/gnome.root
but whatever :)

---

### Post by jdong on 2007-10-29
Try using the full path to your home directory. Relative paths might not work (look for /gnome.root to confirm that suspicion)

---

### Post by loadeddreams on 2007-10-29
yep, you were exactly right. using relative path didn't work, but /gnome.root was empty as well. either way I have it solved now :)
thanks for the very quick response, and this is a very great post. It worked wonders, even on my very slim laptop setup.

The biggest improvement I saw was with my icons. I use a custom icon pkg that was taking a while to load at start, and I could definitely feel an improvement.

---

### Post by nickless on 2007-10-30
Aww man... I had the same problem missing the gnome.root, but I decided to work on it today. So I log in this morning only to find using compiz my window borders are lost! I really didn't do anything else yesterday... what the hell?
EDIT: Ok fixed that... Compiz disabled Window Decoration... what a way to start the day :mad:

---

### Post by trishacupra on 2007-11-19
[QUOTE=jdong]

Now, log out, and press CTRL+ALT+F1 to log into a terminal. Start the profiler:

```

sudo readahead-watch -o ~/.readahead/gnome.root /

```

[/QUOTE]

I have a n00bie question. I bet it's painfully obvious but I don't have any experience with this.

I logged out and pressed  CTRL+ALT+F1, but all I got was a black screen and a flashing cursor. I couldn't type anything. I gave it a while, but nothing changed, so I had to power down manually. I restarted, tried again, but the same thing happened.

What's supposed to happen when I click  CTRL+ALT+F1?

BTW, I'm not pressing the +. Just holding down the CTRL, ALT and F1 buttons together.

---

### Post by ayates on 2007-11-19
Looks like you might have this bug - [https://bugs.launchpad.net/bugs/129910](https://bugs.launchpad.net/bugs/129910)

---

### Post by trishacupra on 2007-11-19
Thanks. At least now I know I have a real bug, and I'm not just a n00b. :)

---

### Post by double1116 on 2007-11-30
Hello, thanks for the tip. I modified your 00readahead script to include recording and filtering the list when "profile" is in the kernel command line.

```


# This script will provide readahead support for an Xsession.
# Place in /etc/X11/Xsession.d/00readahead

# Added by Pat Double

# Check that the package is still installed
if [ -x /sbin/readahead-list ] && [ -x /sbin/readahead-watch ]; then

if grep -qs "profile" /proc/cmdline; then

	# Prepare directory
	[ -d $HOME/.readahead ] || mkdir $HOME/.readahead
	rm $HOME/.readahead/* 2>/dev/null

	# Start future job that will either wait for user (if zenity or xmessage is available) or 30s to save readahead lists
	cat >/tmp/${USER}.readahead.sh <<EOF
#!/bin/sh
if [ -x /usr/bin/zenity ]; then
	sleep 5s
	/usr/bin/zenity --info --text="Your session is being profiled for future speed improvements. Please click OK when your desktop has finished loading."
elif [ -x /usr/bin/xmessage ]; then
	sleep 5s
	/usr/bin/xmessage -center -buttons "Stop" "Your session is being profiled for future speed improvements. Please click Stop when your desktop has finished loading."
else
	sleep 30s
fi

# Stop watching
killall /sbin/readahead-watch
while pidof readahead-watch >/dev/null; do sleep 1s; done

# Filter out large or unuseful files
for F in ${FILES}; do
	while [ ! -e \${F} ]; do sleep 1s; done
	TSZ=0
	while read L; do
		[ -r "\${L}" ] || continue
		[ "\${L#/tmp/}" = "\${L}" ] || continue
		[ "\${L#/var/tmp/}" = "\${L}" ] || continue
		[ "\${L#/var/cache/}" = "\${L}" ] || continue
		LSZ=\$(stat "\${L}" --printf "%s")
		[ \${LSZ} -lt 8000000 ] || continue
		echo "\${L}"
		TSZ=\$(( \${TSZ} + \${LSZ} ))
	done <\${F} >> $HOME/.readahead/\${F#/tmp/${USER}.}
	rm \${F}
	logger -i -t "readahead" "Will readahead \${TSZ} bytes for \${F#/tmp/${USER}.}"
done
rm \$0
EOF
	chmod +x /tmp/${USER}.readahead.sh
	/tmp/${USER}.readahead.sh &

	# Start watching
	FILES="/tmp/${USER}.root"
        /sbin/readahead-watch -o /tmp/${USER}.root /
	if mountpoint -q /home; then
		FILES="${FILES} /tmp/${USER}.home"
                /sbin/readahead-watch -o /tmp/${USER}.home /home
	fi


elif [ -d $HOME/.readahead ]; then

	# Do not background readahead-list as several partitions on the same disk may be
	# referenced and concurrent instances will cause thrashing
	for list in $HOME/.readahead/*; do
	  readahead-list $list
	done
fi

fi # package existance check



```

---

### Post by jdong on 2007-11-30
Wow, very nice man, that's quite a polished solution. Thanks for posting it :)

---

### Post by double1116 on 2007-12-03
> **jdong said:**
> Wow, very nice man, that's quite a polished solution. Thanks for posting it :)

I should've done some more testing. For some reason the sub-shell would not continue after 'xmessage'. I updated my previous post so I think it should work now.

---

### Post by durand on 2007-12-04
Nice Howto! Works really well here. Hardy with I gig of ram. Forgot to time the original time, but its seems about 40% faster. Thanks.

---

### Post by Rufe0 on 2007-12-05
When I go into the terminal and press alt+f8 I get a crash, even if I have typed no commands. I can recover it by opening another terminal and restarting X. In my system log the last error is  Invalid position buffer, using LPIB read method instead .
Any ideas?

---

### Post by reacocard on 2007-12-14
Works wonderfully! I didn't time it but login after a cold boot is at least as fast as a cached login was before.

EDIT: did some experimenting with openoffice, using readahead shows no improvement in start times:

uncached:
before: ~10s
using readahead-list && oowriter: ~10s
using readahead-list & oowriter: ~11s
using readahead-list & sleep 1 && oowriter: ~10s

cached:
before: ~3s
using readahead-list && oowriter: ~3s
using readahead-list & oowriter: ~3s
using readahead-list & sleep 1 && oowriter: ~4s

the list generated is attached if anyone is interested.

(Note to those wanting to do this sort of testing: doing 'echo 1 > /proc/sys/vm/drop_caches' as root lets you empty your caches without rebooting.)

---

### Post by foxy123 on 2007-12-20
>  If you have home on a different partition as root, you should repeat Part 1 for each partition, replacing gnome.root with a different name, and replacing the mountpoint / with each interested mountpoint. 

Should I then merge root and user? How can I do it?

---

### Post by durand on 2007-12-20
No, you should leave them as separate files, named gnome.root and gnome.home or whatever you like. Thinking about it, you could merge them together. cat file1 >> file2 and then both files are merged.

---

### Post by jdong on 2007-12-21
Whether or not you should merge them depends on your setup:

If the partitions are on the same physical device, merge them together into one file.

If they are on different physical devices, keep it separate -- they will be read in parallel and hence speed things up.

---

### Post by durand on 2007-12-21
> **jdong said:**
> Whether or not you should merge them depends on your setup:

If the partitions are on the same physical device, merge them together into one file.

If they are on different physical devices, keep it separate -- they will be read in parallel and hence speed things up.

Ah, thats clever!

---

### Post by Nimaran on 2008-01-01
I'm confused ALT+F8 resizes my selected window. Is their another shortcut to do what you said?

---

### Post by kiddo on 2008-01-05
I have saved 20 seconds on my already "as optimized as I can" login, going from 34 seconds to 14 seconds, with specto+composited metacity+awn on startup. It is relieving. Thank you for this tutorial.

You've got to propose this being in ubuntu (or gnome) by default! Has any work been done towards that? I can't help (lack of time), but I would happily subscribe to a launchpad blueprint or mailing list thread if there is one.

---

### Post by Mazza558 on 2008-01-05
I get as far as 

> Now, without logging out, go to your GDM prompt (ALT+F8 ) and log in normally.

...but I never get back to GDM, it just shows some of the things that started when logging in.

---

### Post by kiddo on 2008-01-05
> **Mazza558 said:**
> ...but I never get back to GDM, it just shows some of the things that started when logging in.

Note that it is not always the screen #8. For me, it is always #7. You should try 
CTRL+ALT+F7, CTRL+ALT+F9 or even CTRL+ALT+F10

---

### Post by [h2o] on 2008-01-09
I am a bit confused about this "if you have /home on another partition than root then ..."-part.
I have two partitions, /home and /, what commands should I use for part 1?

My first thought was that I should just replace "/" with "/home" and the resulting list filename when running this command:
sudo readahead-watch -o ~/.readahead/gnome.root /

Am I correct?

---

### Post by jdong on 2008-01-09
readahead-watch will not jump across filesystems. So you need to call it twice, once on / and once on /home, saving each to a different filename. Then you need to paste the contents of the two together into one file so that it can all be read at once.

---

### Post by [h2o] on 2008-01-09
Hmm, I kept them as two separate files and logged in. It went faster alright, but the large "GNOME could not load properly ..." error window showed up and it didn't load my theme (default ubuntu human theme) but a blue theme which I guess is the default GNOME theme.
I'll try to reboot and see if the problem automagically goes away. But any ideas on what might have caused it are welcome.

EDIT: Nevermind, a reboot fixed it. I shaved bootup time with 20 seconds. From ~90 to ~70.
Thanks a lot :)

---

### Post by reacocard on 2008-01-20
I've done some more application testing, this time with firefox, which happily does see some improvement! Here's the charts:

uncached:
before: ~8s
using readahead-list && firefox: ~6s

cached: no difference, ~4s

the list generated is attached if anyone is interested.

I have also worked out a simple way to integrate this into your application startup: Make a bin/ directory in your home folder, and make sure that that folder is first in $PATH. Then just put in a script like this:

```
#!/bin/sh
readahead-list ~/.firefox.list
exec firefox "$*"
```

save, make it executable (chmod +x), and that's it! from now on, launching firefox will run through that script first, allowing you to have readahead without affecting anyone else on the system.

---

### Post by firestormx37 on 2008-01-23
Thank You.  It works great.  

Just a note:  When I would press either CTRL + ALT + F7 or F8, the system would hang.  I found that F9 did work though.  This seems like a problem with my, as I would think that I would be able to jump back into one of the existing sessions.  If anyone has any ideas, please let me know.  If anyone else runs into this when following the steps, then try out CTRL + ALT + F9 to get back from the terminal.

---

### Post by ssc351 on 2008-01-27
Ya I am having a couple of problems...I can't get back to GDM prompt after the first step.  if i use ctl atl f8 the system hangs, I can use ctl alt f7 but that just returns me back to the session I was just in without having to do a login.  I tried just continuing on, but i get an error saying that there is no readahead process to kill.  Any ideas?

---

### Post by Fin_Bhera on 2008-02-01
This tutorial worked great, cut my time from GDM to usability by almost half.  However, the third step, editing the rc.local file, doesn't seem to do anything... The script isn't executing on the login screen.  Any ideas?

---

### Post by firestormx37 on 2008-02-01
For anyone wondering about the CTRL ALT F7, F8, F9, etc, I found that when I installed the nvidia drivers released by nvidia, I was then able to switch back and forth between sessions.  I can't be certain that this will work for anyone else, because I am not really sure why it worked for me.  But it is something to try if you are interested.

---

### Post by jdong on 2008-02-02
> **Fin_Bhera said:**
> This tutorial worked great, cut my time from GDM to usability by almost half.  However, the third step, editing the rc.local file, doesn't seem to do anything... The script isn't executing on the login screen.  Any ideas?

That scripts runs in the background. It basically starts prefetching while the GDM screen is waiting for your input. If you're like me and power up, then get a cup of coffee, this could mean that your login can be done in under 5 secs when you get back, thanks to everything being prefetched already in the background.

---

### Post by kiddo on 2008-02-03
> **jdong said:**
> That scripts runs in the background. It basically starts prefetching while the GDM screen is waiting for your input. If you're like me and power up, then get a cup of coffee, this could mean that your login can be done in under 5 secs when you get back, thanks to everything being prefetched already in the background.

I'd chime in here, because I find that script to be anormally quiet. I am not able to actually notice this background preloading (I see no hdd activity at gdm). This is much different from the days I had simply installed "preload" from the repositories, which was eating the hard drive for 10 seconds at gdm and yeld no significant login time reduction...

also, a question: would this whole trick work with automatic gdm sessions? For example, my parents' computer logs in automatically, gdm doesn't even show up. Would using this readahead trick make sense?

edit: I registered a blueprint for this [https://blueprints.launchpad.net/ubuntu/+spec/login-readahead](https://blueprints.launchpad.net/ubuntu/+spec/login-readahead) hopefully it will get noticed?

---

### Post by jdong on 2008-02-03
> **kiddo said:**
> I'd chime in here, because I find that script to be anormally quiet. I am not able to actually notice this background preloading (I see no hdd activity at gdm). This is much different from the days I had simply installed "preload" from the repositories, which was eating the hard drive for 10 seconds at gdm and yeld no significant login time reduction...

It's the quietest form of disk activity (virtually seekless reading) so yes it is harder to notice being active, and I believe any other disk IO also takes priority over readahead requests so by the time the login screen shows up, readahead might be done.

[quote]
also, a question: would this whole trick work with automatic gdm sessions? For example, my parents' computer logs in automatically, gdm doesn't even show up. Would using this readahead trick make sense?
/QUOTE]

With this setup, it's FAR more important to get the session hook than the rc.local hook. The rc.local one is probably entirely useless for an auto login -- doesn't do anything useful but also doesn't hurt anything either.

---

### Post by Daveth on 2008-02-04
um, after having tried this about 5 times I still get an empty .readahead with no sign of gnome.root, despite giving it the full path to my /home. It does seem to "watch", does not complain there is no process to kill, so presumably kills it quietly (ninja-like!) but still yields no file to work on.

Any ideas - I cannot see what I am doing wrong.

---

### Post by noodles12 on 2008-02-04
thanks jdong. once again you've really helped me out! went from 40sec to 20sec. 


Its not related but did you customize your set-up o boot from grub to GDM in 14 sec? or is your hardware just amazing?

I got a Pentium M notebook with 768 mb RAM and it takes 47-50 sec boot-time. w/ the usplash fix.

---

### Post by jdong on 2008-02-05
> **noodles12 said:**
> 

Its not related but did you customize your set-up o boot from grub to GDM in 14 sec? or is your hardware just amazing?.


It took some tweaking, both stripping things out of rcS/rc2, disabling a good chunk of restricted modules, and then streamlining the login process to load fewer things by default.

But yeah, I can go from GRUB to a full desktop in just a tad over 20s

---

### Post by djbsteart1 on 2008-02-05
is this specific to gnome or can it be applied to kde or other desktop environments? also does it matter what distro it is on? i followed the guide on me ubuntu system and it was great, but would also like to try it on fluxbuntu and mandriva,

---

### Post by reacocard on 2008-02-05
> **djbsteart1 said:**
> is this specific to gnome or can it be applied to kde or other desktop environments? also does it matter what distro it is on? i followed the guide on me ubuntu system and it was great, but would also like to try it on fluxbuntu and mandriva,

It should work for anything. I have not tested this, but I see nothing that would cause it to fail with other environments.

---

### Post by djbsteart1 on 2008-02-06
ok thanks, ill give it a try when i get home, and report back. thanks again.

---

### Post by _Stevie_ on 2008-02-06
okay i tried that tweak and also put the readahead command in /etc/rc.local.
a small improvement seems noticable. but gnome still needs 30 seconds to load.
thats completely insane. does this issue exist in feisty too?

---

### Post by txhellkat138 on 2008-02-07
I have to say with all the crap I have running at startup its nice that I can now bootup in 15-20 seconds instead of a minute thank you very much for this walkthrough

---

### Post by _Stevie_ on 2008-02-07
15-20 seconds is amazing.
is it from grub into gnome?
or only gnome?

---

### Post by Stunts on 2008-02-17
Hi! I've followed this how-to (only the two first parts since I use auto login) and it worked very well! It decreased my boot time from GRUB to full working desktop from 61 seconds to 44! it was 16 second gain, excelent! 
Thank you very much!

---

### Post by Onesimus on 2008-02-17
I have been experiencing long login times (60s) ever since installing
Gutsy.  Despite searching on the forums for a solution this is the first
time I have come across this !  

Have read through the entire thread I am slightly confused (n00b).  I
grasp that the script by double1116 is sophisticated and elegant, but 
what does it replace in the original solution ?  

I have a separate /home partition but on the same physical disk, so do
I need to still run Part 1 twice ?

---

### Post by bornagainpenguin on 2008-04-04
> **Onesimus said:**
> I have been experiencing long login times (60s) ever since installing
Gutsy.  Despite searching on the forums for a solution this is the first
time I have come across this !  

Have read through the entire thread I am slightly confused (n00b).  I
grasp that the script by double1116 is sophisticated and elegant, but 
what does it replace in the original solution ?  

I have a separate /home partition but on the same physical disk, so do
I need to still run Part 1 twice ?

I would like to BUMP this as I have the same question...  Could someone (jdong perhaps?) make out some simple step by step instructions on how to go about this?  Thanks!

--bornagainpenguin

---

### Post by double1116 on 2008-04-04
> **bornagainpenguin said:**
> I would like to BUMP this as I have the same question...  Could someone (jdong perhaps?) make out some simple step by step instructions on how to go about this?  Thanks!

--bornagainpenguin

Simple steps:

1. Save the script I posted into /etc/X11/Xsessions.d
2. Reboot but type "e" (edit) on the grub line before booting. Add " profile". This will cause the boot and desktop login process to be profiled.
3. Login to your desktop session. Wait until things settle down, then click "okay" on the window to save the profile.
4. Reboot normally and it should be faster.

Note, I have had problems re-running my script with "profile" lately, I'm not sure what the problem is. It causes the KDM login to fail. YMMV.

The improvement in the script in /etc/X11/Xsessions.d is that it simplies the steps to make this happen.

---

### Post by bornagainpenguin on 2008-04-04
> **double1116 said:**
> Simple steps:

1. Save the script I posted into /etc/X11/Xsessions.d
2. Reboot but type "e" (edit) on the grub line before booting. Add " profile". This will cause the boot and desktop login process to be profiled.
3. Login to your desktop session. Wait until things settle down, then click "okay" on the window to save the profile.
4. Reboot normally and it should be faster.

Note, I have had problems re-running my script with "profile" lately, I'm not sure what the problem is. It causes the KDM login to fail. YMMV.

The improvement in the script in /etc/X11/Xsessions.d is that it simplies the steps to make this happen.

I'll definitely give that a whirl, and it DOES sound much more elegant now that you've laid it all out for me...but what I was actually asking about was how to redo step one in simple explanations when you have home in a separate partition /home?

Thanks again!

--bornagainpenguin

---

### Post by double1116 on 2008-04-04
> **bornagainpenguin said:**
> I'll definitely give that a whirl, and it DOES sound much more elegant now that you've laid it all out for me...but what I was actually asking about was how to redo step one in simple explanations when you have home in a separate partition /home?

Thanks again!

--bornagainpenguin

I have a separate /home partition. The script already handles that.

---

### Post by bornagainpenguin on 2008-04-04
> **double1116 said:**
> I have a separate /home partition. The script already handles that.

Oh okay.  Great!  So just follow the earlier instructions and I'm good?  Thanks again!

--bornagainpenguin

---

### Post by double1116 on 2008-04-04
> **bornagainpenguin said:**
> Oh okay.  Great!  So just follow the earlier instructions and I'm good?  Thanks again!

--bornagainpenguin

Yes, the previous instructions should work. After you do updates or things change, you may want to run with " profile" in the boot sequence again.

Please let me know either way if it works. Last time I tried it killed KDM, I'm not sure why.

---

### Post by bornagainpenguin on 2008-04-04
> **double1116 said:**
> Yes, the previous instructions should work. After you do updates or things change, you may want to run with " profile" in the boot sequence again.

Please let me know either way if it works. Last time I tried it killed KDM, I'm not sure why.

It worked great!  I'm seeing major improvements in booting speed--the biggest bottleneck I have left right now seems to be Compiz.  When I boot up and then log in everything is pretty quick, and I see GNOME snap into place immediately.  The problem is it seems GNOME or GTK or something is fighting with Compiz over who gets to draw the desktop, because it goes black and then redraws everything exactly as it should be in about three or four seconds later.

Strange...

Still I'll just have to do some more research and this is the best my Laptop has been in all my using of Linux on it...so it can only get better!

--bornagainpenguin

---

### Post by sdennie on 2008-04-18
Here is a small script I hacked together to do readahead on an application specific basis.  There are two ways to use it.  1) You can cause an application readahead to happen just before you start the app.  2) You can cause an application readahead to happen at login if you are already using the readahead stuff from jdong.

By default, the script is setup to do #1 but, there are instructions at the top for changing it to do #2 (it's just swapping comments).

The basic idea is put the script in your ~/bin directory, do a chmod +x on it and then run it as sudo with the name of an app.  For example, to generate a readahead list for firefox it's simply:

```

sudo ra-run.sh firefox

```

That will place a readahead list in either ~/.readahead-app or ~/.readahead depending on if you choose method #1 or #2 above.  If you choose method #2, you should be done and the next time you login, it will automatically readahead the app.  If you choose method #1, you will also need to make a symlink for the app that points to ra-run.sh.  For example, for firefox, you would do this:

```

ln -s ~/bin/ra-run.sh ~/bin/firefox

```

As long as you have /home/bin as the first entry in $PATH, that should make the symlink to ra-run.sh get executed when you run firefox (which will do a readahead-list for firefox before executing /usr/bin/firefox).

ra-run.sh
```

#!/bin/bash

# Uncomment the second RA_HOME if you are using the .readahead stuff from jdong
# and prefer to have commands cached at login/boot time
RA_HOME=$HOME/.readahead-app
#RA_HOME=$HOME/.readahead

if [ "$1" != "" ] ; then
    APP=`basename $1`
    APP_NAME=$APP
else
    # Called from a symlink.  Resolve it
    CMD=`basename $0`
    SCRIPT=`which $CMD`

    for i in `which -a $CMD` ; do
        if [ "$i" != "$SCRIPT" ] ; then
            APP_NAME=`basename $i`;
            APP=$i;
            break
        fi
    done
fi

RA_FILE=$RA_HOME/$APP_NAME

if [ -e $RA_FILE ] ; then
    # We've already made the readahead file.  Load it and exec the app
    readahead-list $RA_FILE
    exec $APP
else
    if [ "$USER" != "root" ] ; then
       echo "Error: The first time you run ra-run.sh for an app, you must run it with sudo."
       exit 1;
    fi

    mkdir -p $RA_HOME

    readahead-watch -o $RA_FILE /

    # This isn't optimal but, it accounts for apps that immediately go into the
    # background like oowriter
    echo "Running ra-run for $APP for the first time.  Please exit the app once it starts and wait up to 30 seconds for data to written."

    sudo -E -u $SUDO_USER $APP &

    sleep 30
    killall readahead-watch
    chown ${SUDO_USER}:${SUDO_USER} $RA_HOME -R
fi

```

Hopefully someone finds that useful.  Unfortunately the speedup of method #1 is negligible on fast hardware but, if you have a lot of RAM, method #2 can be useful to prime the cache at startup for apps that you are likely to use at some point.

---

### Post by jagrav on 2008-05-11
On a Dell Inspiron 6400 with 1 Gb RAM with Ubuntu Hardy, disabling readhead makes my GRUB to login prompt about 15 secs faster. But slows down the time from login to working Gnome desktop. 
On the other hand with readahead enabled time from GRUB to login prompt is about 15 secs slower. But this is more or less compensated by the reduced time from login to working desktop. 
So, in summary, with or without readahead, it is more or less the same.

---

### Post by xir_ on 2008-06-18
thumbs up from me i went from minutes to seconds. very cool

does the order in the file generated dictate boot sequence?

---

### Post by gruffy-06 on 2008-06-19
Cool. I had fewer problems with login times since then.

This led me on to further configuration. I ran readahead-watch, opened up every application in the GNOME menu, reinstalled a package using APT and then halted the system, thus creating the output file. I then reloaded the system and set up a GNOME session script to run readahead-list on the same output file every time I logged in. It felt a lot like Superfetch on Vista, with better efficiency and no constant slowdowns.

:KS:KS:KS

---

### Post by kiddo on 2008-06-19
doesn't having too much stuff prefetched by readahead harm performance? My understanding was that there was a certain "optimum" point where adding further preloading might make the performance curve go down?

---

### Post by gruffy-06 on 2008-06-19
Probably, kiddo. If there are loads of files being read by readahead at once, it could potentially cause disk access problems if there are other consumptive processes running at the same time. Systems with low memory might also suffer from preloaded applications if the cache is full.

I'm not too sure about the "optimum" performance though. Maybe trying different options might solve some performance problems. :-|

---

### Post by kiddo on 2008-06-19
you know, it would be so nice if there was a way to automate this whole deal, at least partly, and allow visualizing the profile file in a graphical manner (it's pretty darn hard to parse), or even click a button to "profile application X and add it to the list", and evaluate if the profile list would be too big (exceed the RAM or stuff like that).

---

### Post by ve1itas on 2008-06-24
> **double1116 said:**
> Simple steps:

1. Save the script I posted into /etc/X11/Xsessions.d
2. Reboot but type "e" (edit) on the grub line before booting. Add " profile". This will cause the boot and desktop login process to be profiled.
3. Login to your desktop session. Wait until things settle down, then click "okay" on the window to save the profile.
4. Reboot normally and it should be faster.

Note, I have had problems re-running my script with "profile" lately, I'm not sure what the problem is. It causes the KDM login to fail. YMMV.

The improvement in the script in /etc/X11/Xsessions.d is that it simplies the steps to make this happen.

hi,

i am using 8.04. is this still usable? also, i am guessing that the following line has an extra dot:
done <\${F} >> $HOME/.readahead/\${F#/tmp/${USER}.}
it should be:
done <\${F} >> $HOME/readahead/\${F#/tmp/${USER}.}
or is there a more updated version?

---

### Post by sarah.fauzia on 2008-06-24
I'm also using 8.04 Hardy Heron and this isn't working for me at all. It's a pity, because my tablet has 4 GB RAM. The profile starts--I know that because there is that few minute delay before I can go back and login--but that's the catch, I can't login again. It gets stuck on loading the /etc/rc.local file for more than ten minutes...perhaps longer, but I stopped waiting and did a hard reset. Then, after restarting the computer and auto-login, I go back to the terminal per the instructions and run the script to see the files readahead wants to cache. There I get stuck, again. It doesn't give me an option to get back to the terminal; after I scroll through the whole list (I think the largest file I noted was 3.5k? Most were only a few hundred K), it tells me ```
log: 
``` I don't know what to enter under that... So, again, I do a hard reset, because there's just no way to close it. Repeated this at least 3 times, each time with the same results.

Then, I created the /etc/X11/Xsession.d/00readahead, and copied and pasted, and restarted. No effect; even though I autologin I went ahead and did step 3, and it didn't help. I even tried doing it all from the terminal on my desktop (without accessing it from after logging out) and it didn't make the slightest difference.

I'm not trying to complain--I'm simply trying to supply as much information as possible so someone who knows better (than me, the newbie) can help me--and possibly other users under Hardy Heron--I understand this guide was written before 8.04?--figure this out, and benefit from faster logins! Thanks! :)

PS: Currently, my login time from the moment the ubuntu screen completes lighting up the blocks (for the lack of a better term) till the time I see the desktop is...40 seconds. So I really look forward to cutting that in half (or less!). Again, any help would be truly appreciated.

---

### Post by Falcorian on 2008-06-26
Thanks for the guide! Before and after (of course) I'm ~40 seconds GRUB to GDM. But before it was about 10 seconds for GDM to desktop, now it's ~2! :D

---

### Post by Mr. Picklesworth on 2008-06-29
Just want to throw in my thanks here. This had an amazing impact on my boot time. All that loading seems to have disappeared into the aether :P
Logging in is literally an instand process.

It would be pretty cool to see this sort of functionality implemented in the default GUI, perhaps a "preload desktop for x user", or "preload y session" option under the Login administration...

A few things:

 * Doing this messed up Beagle, which is understandable; it complained about index files being loaded wrong. I disabled Beagle and ran readahead-watch again, which seemed to solve the issue. After turning Beagle back on, I am not noticing any significant loss.

 * This line confused me: "If you have home on a different partition as root, you should repeat Part 1 for each partition, replacing gnome.root with a different name, and replacing the mountpoint / with each interested mountpoint." Yes, my /home is a partition of its own, so I ran readahead-watch a second time creating a file called gnome.home (hah, it tickles!) for /home. However, I was rather unsure of this... is that what you are telling me to do? I think what got me confused was that I should "repeat Part 1 for *each* partition"; as far as I am aware, /home can only be one partition. (Unless the user's home folder is multiple partitions, which would be plain nasty). Do you mean to say that step 1 should be repeated for any seperate permanent partitions on / if they exist? Why doesn't readahead-list cope with these mounted partitions itself?

 * Has anyone noticed oddities with Network Manager? I haven't done a huge ammount here yet, but I noticed that NM had actually not logged in to my network immediately. It *never* does that; the thing generally has a way of reading my mind and being connected to the Internet before I even think about it. Could just be a side-effect of the login process being so fast that I see the applet before it's ready. (Thing is, though, I manually told it to connect).


Does or can Readahead deal with files that are being loaded in patterns from particular directories? For example, I believe Tomboy will go through all of the notes in my .tomboy directory. Will readahead only remember to preload those ones that Tomboy loaded when I got it to watch activity, or is it clever enough to think "read everything in .tomboy"?

---

### Post by hihihi on 2008-07-09
xubuntu hardy 8.04 64bit
great job.
i also have /home as an own partition.
i did as jdong suggested.
it is working really good.
i do not use beagle, i find it a problematic peace of software.
i use tracker instead and there are no issues.
all in all,
very cool.
promp-time is being used usefully.
super again great how to and thanks.

---

### Post by picpak on 2008-07-29
This actually slowed things down. :( My startup used to be 40 seconds, now it's 50. Oh well.

---

### Post by Flag on 2008-08-07
Thanks for all this, but how can I check if my files are loaded ?
Ububuntu 8.04 64 bits fresh install, Acer Aspire 7520. 
Files in home/.readahead, merged home and root folder.
I don't see any improvement, from grub to gui 60 secs.,I read some of you do this in much less time, I'm jealous.

rgds

---

### Post by run1206 on 2008-08-12
i slowed down prior to the login (1:05 to 1:50) but after login is almost instant :shock: :shock: :D  
i guess i could work on sys-rc-conf for before the login...thanks :D

---

### Post by macvr on 2008-08-16
wow works....
 reduced my start up time by 25 secs!

---

### Post by AndEat on 2008-08-31
I tried this on Hardy_64

it worked well, but I could not connect to the internet at all

Network Manager showed 'no active device' and could not bring the networking down or up manually

Removing everything and rebooting, was slower but had no issues with networking. 

I am trying again and will see if this repeats

---

### Post by lifestream on 2008-11-01
... Went from 65 seconds to 40-45! Thank you so much *thumbs up!*

---

### Post by jdong on 2008-11-01
Two points of note:

(1) This procedure can in no way damage your system or change its behavior other than making startup take longer or shorter. It simply modifies a list of files that are read the first thing during bootup. If you're having weird networkmanager problems or something like that, it's extremely unlikely to be caused by this.

(2) In Intrepid, there is a new tweak to the default readahead lists in that they removed all the kernel modules from the readahead list (i.e. files ending in .ko) which is supposed to improve bootup speed -- rarely are all the kernel modules required during bootup, but they are all touched a little bit by udev. If you try filtering out *.ko, it might improve boot speed a bit too.

---

### Post by jw5801 on 2008-11-02
> **jdong said:**
> (2) In Intrepid, there is a new tweak to the default readahead lists in that they removed all the kernel modules from the readahead list (i.e. files ending in .ko) which is supposed to improve bootup speed -- rarely are all the kernel modules required during bootup, but they are all touched a little bit by udev. If you try filtering out *.ko, it might improve boot speed a bit too.

Good call, worthy of being added to the original post. Not applicable to using readahead for login, but could be useful while profiling the boot sequence. Could use the following to automate the filtering:
```
sed -i -e 's/^.*.ko$//' /etc/readahead/boot
```
Is there a way to tell sed to replace a pattern with a reverse line feed? That would be useful to prevent blank lines in the file.

If you want to get really finicky you could always leave in the modules you know you'll use. The command below should return a list of the kernel modules you're currently using which would be ready to add to a readahead list.
```
lsmod | sed 's/^\([a-zA-Z1-9]\{1,\}\).*/\1.ko/' | more +2 | xargs locate | grep $(uname -r)
```

---

### Post by jdong on 2008-11-02
Whoops! Of course in my sleep-deprived state I posted that tip to the wrong thread :)

---

### Post by shador on 2008-11-02
Well sadly I can't get this to work. Once I jump out of the GUI I don't seem to be able to get back. Not with Alt + F8  and not with /etc/init.d gdm start either. Though this is not a problem related to this topic maybe someone can help me figure out why it doesn't work and how I can correct it.

---

### Post by ShirishAg75 on 2008-11-03
Hi all, 
 Jon, I've a / and a /home on two different partitions. The other thing is mine is a ubuntu and an xubuntu (just in case GNOME dies or some other stuff like that) . So profiling /home is a good idea or not (in such a case)

Looking forward to your comments on the same. 

Also if I put the same code in /etc/rclocal file I don't get the GDM login screen :(

I haven't also found much of a difference while logging in, in fact seems a bit longer, attaching my gnome.root file just in case it helps. 

Dunno if its a bug or somethings have changed in Intrepid. There are 948 files but all are small.

---

### Post by dcstar on 2008-11-14
> **jdong said:**
> 
.........
Now, log out, and press CTRL+ALT+F1 to log into a terminal. Start the profiler:

```

sudo readahead-watch -o ~/.readahead/gnome.root /

```

This will grind the disk for a while (up to a few minutes) then it will return you to a command prompt. The profiler is now in the background watching all actions. Now, without logging out, go to your GDM prompt (ALT+F8 ) and log in normally.
.........
** If you have home on a different partition as root, you should repeat Part 1 for each partition, replacing gnome.root with a different name, and replacing the mountpoint / with each interested mountpoint. **
.........

Not really, the following code will profile "/" and "/home" into one file:

```

sudo readahead-watch -o ~/.readahead/gnome.root / /home

```

You should be able to append as many paths as you like and keep everything simple.

---

### Post by CancelloCornorosso on 2008-11-21
I just started playing around with readahead and I have got a question: why the profiles generated by readahead-watch cannot just be appended to etc/readahead/desktop?

---

### Post by jdong on 2008-11-21
> **CancelloCornorosso said:**
> I just started playing around with readahead and I have got a question: why the profiles generated by readahead-watch cannot just be appended to etc/readahead/desktop?

Well they can, but that hangs the boot at the first step for as much as 30 seconds, which might not be the behavior you want. It makes the user wait longer till he is able to type in his password. Even worse, by the time the system grinds through bootup to GDM it might've already "forgotten" (evicted out of RAM) everything it cached at bootup.

---

### Post by Vadi on 2008-11-21
Are these instructions still necessary, or does just installing readahead take care of this?

On ubuntu 8.10

---

### Post by jdong on 2008-11-21
> **Vadi said:**
> Are these instructions still necessary, or does just installing readahead take care of this?

On ubuntu 8.10

Readahead on all current versions of Ubuntu only is designed to accelerate GRUB -> GDM boot sequence. This HOWTO uses the same software to accelerate the GDM -> desktop login sequence. So yes, this is still applicable to Intrepid 8.10.

---

### Post by Vadi on 2008-11-21
Ah thanks. *readahead* seems to be installed by default in 8.10 so I'll apply the gdm->desktop thing.

---

### Post by Vadi on 2008-11-21
Oh, question - I use autologin. Will this work with it?

---

### Post by jdong on 2008-11-21
> **Vadi said:**
> Oh, question - I use autologin. Will this work with it?

yeah, it should still save you login time compared to a normal login the same way that the readahead at boot saves you time when you slurp up all the data in order beforehands rather than thrashing all over the disk as you suddenly realize you need to read a certain file to boot.

The BIGGEST time saving is realized when the system waits for the user to type in their password while in the background we can effectively pre-load their GNOME session from disk. But even without this advantage you should still shave a few seconds off login time.

---

### Post by ispy on 2008-12-23
I tried it.

I'm not sure if it worked though. I didn't notice a major difference in startup time, and the /.readahead directory is empty.

what's going on? I'm still at 1:15 from grub to the stoppage of disk usage. (I think that's what you'd call it...)

---

### Post by sh4d0w808 on 2009-01-02
Thanks jdong, it is a great howto! I applied it to my / and to my /home - I saved approx. 20 secs to use my computer! Keep up the good work!

---

### Post by macvr on 2009-01-15
this worked for me when my whole system[/ and /home] was in the same partition>
[http://ubuntuforums.org/showpost.php?p=5600179&postcount=97]("http://ubuntuforums.org/showpost.php?p=5600179&postcount=97")
it had reduced my BOOT time by 25secs....

BUT after i separated the / and /home partitions it worsens my boot times!!!
it takes 1:35 mins for me to use the system from the time i switch it on! i have autologin so didnt check the times till the loginwindow and after... is 1:35 mins a reasonable time for startup?
this happened in 8.04 itself... even after i have reinstalled 8.10 it seems to make my boots worse! 

```
sudo readahead-watch -o ~/.readahead/gnome.root /
sudo killall readahead-watch
sudo chown macvr:macvr ~/.readahead -R
sudo readahead-watch -o ~/.readahead/gnome.home /home
sudo killall readahead-watch
sudo chown macvr:macvr ~/.readahead -R

```
i know tht i have done chown twice! thought it might help !

i have removed the bigger files from the list , also added the 00readahead file... and also in the rc.local...

but nothing seems to help...! have i done it correctly?

anyway to make this work AGAIN ? previously it had reduced my boottimes but i dont understand why it worsens things now!

---

### Post by Ng Oon-Ee on 2009-01-17
Hmm, I have a separate /home/ partition and that doesn't seem to affect anything. Boot time is improved relative to no read-ahead. And did you logout before starting readahead-watch the second time?

---

### Post by macvr on 2009-01-17
> **Ng Oon-Ee said:**
> Hmm, I have a separate /home/ partition and that doesn't seem to affect anything. Boot time is improved relative to no read-ahead. And did you logout before starting readahead-watch the second time?
previously i did logout of the session , but not in the terminal... so this is what i'v done again...
```

mkdir ~/.readahead
sudo readahead-watch -o ~/.readahead/gnome.root /
sudo killall readahead-watch
sudo chown macvr:macvr ~/.readahead -R
[COLOR="Red"]logout[/COLOR]

sudo readahead-watch -o ~/.readahead/gnome.home /home
sudo killall readahead-watch
sudo chown macvr:macvr ~/.readahead -R
```

but my login time stays at 24secs both before and after i do this but the boot time worsens!

i'v tried using the part three of the guide too, but no use!
guess i'm one of the UNlucky ones!

---

### Post by macvr on 2009-01-18
ok... i'v done more googling and split the boot times

my total boot time from switching on is 1min35secs

till end of grub options:12s
boot according to bootchart:38s
[COLOR="Red"]??????????????[/COLOR]:[COLOR="DarkRed"]21s[/COLOR]< this increases when i use readahead
login after a logout:24 secs

ok, i'm just a noob but this may be a silly question !
why is there a gap of 21s? what happens during that time? its is this time which increases when i use the readahead

could someone look at the bootchart and check if anything can be improved?

is this bootup time normal ? its just that i hear startup times of 33 secs i'm wondering if my settings are correct!

---

### Post by Saghaulor on 2009-01-18
> **jdong said:**
> It took some tweaking, both stripping things out of rcS/rc2, disabling a good chunk of restricted modules, and then streamlining the login process to load fewer things by default.

But yeah, I can go from GRUB to a full desktop in just a tad over 20s

Jdong, could you post some specifics on the stripping, disabling, and streamlining that you did?

I have a slew of HP mini 1000's that I'm trying to optimize. They'll be used to connect via aircard to the internet for online charting by my nurses.

So obviously, I'd like them to be running as fast as possible.

---

### Post by zika on 2009-01-21
if I use the script "00readahead" provided by Pat Double I get empty ~/.readahead directory.
if I go "by the book (jdong)" I get gnome.root filled. 
if I use jdong's recipe and fill the gnome.root, subsequent use of pat's script (with "profile") erases gnome.root and does not create a new one. I get empty .readahead directory. 
so, I'm having trouble with pat's script. what am I doing wrong?

---

### Post by hardran3 on 2009-01-24
> **zika said:**
> if I use the script "00readahead" provided by Pat Double I get empty ~/.readahead directory.
if I go "by the book (jdong)" I get gnome.root filled. 
if I use jdong's recipe and fill the gnome.root, subsequent use of pat's script (with "profile") erases gnome.root and does not create a new one. I get empty .readahead directory. 
so, I'm having trouble with pat's script. what am I doing wrong?

I am having the exact same problem. Thanks to everyone who has contributed to this thread. Aside from this one small issue it is great. 35 seconds to desktop on my AA1.

---

### Post by zika on 2009-01-24
> **hardran3 said:**
> I am having the exact same problem. Thanks to everyone who has contributed to this thread. Aside from this one small issue it is great. 35 seconds to desktop on my AA1.
while researching about this problem I've timed my boot-up's and find out that using read-ahead I have boot-up's 10-15 seconds longer than without it. so, I've solved that problem ... :) 
I'm staying with read-ahead that comes with "profile" (when I think about it, I'm not aware of how to disable it now, once I've executed it ...?) on the kernel line (once in a while) and I've (temporarily) removed preload from the picture. that way I have (both read-ahead and preload prevented it) auto log-in and 10-15 second each day to spare ... ;) but it was a nice experiment in which I've learned a lot. thanks.

---

### Post by zika on 2009-01-28
I've been digging today. there is a /etc/readahead directory with two files:```
drwxr-xr-x   2 root  4096 2008-10-27 18:50 .
drwxr-xr-x 144 root 12288 2009-01-28 16:54 ..
-rw-r--r--   1 root 25727 2009-01-28 10:14 boot
-rw-r--r--   1 root  9998 2008-10-27 13:24 desktop
```boot is refreshed today after I added profile in the kernel line. how to refresh desktop? it is being read I guess but it is totally irrelevant to my machine today. it even has a wrong location (London) etc. is this the file we should refresh instead of ~/.readahead/gnome.root?
**update: **no, I was wrong. desktop is for the case /usr and /var are on different filesystems, if I got it right. sorry.

---

### Post by Xbehave on 2009-02-05
giving this another shot, last time readahead was hurting more than hurting. is there a way to make readahead nice AND ionice.

currently i autologin (but lock the screen) and launch a few apps in kde (.kde/Autostart) im adding this to the post login stuff so my applications launch faster (specifically i greped out firefox and openoffice) afterwards but i still want my desktop to be usable while stuff is being loaded in the background (hence i want to nice and ionice them)

---

### Post by jdong on 2009-02-05
If anything, you want readahead to be ioniced **AHEAD** of loading the rest of the desktop -- the whole premise of readahead is that random disk seeking reads are several orders of magnitude slower than consecutive disk reads, so you want to anticipate what random-order reads will occur, then do them all at once in sequential order, hoping that this saves you a bunch of seeking.

For this to work, readahead has to be the **ONLY** process actively accessing the disk during this period. Doing a background readahead along with some other disk-intensive process will make both processes take longer than they would by themselves -- a bad thing to do. This is the exact reason why at startup, readahead blocks the bootup process until it is fully complete.

---

### Post by Xbehave on 2009-02-05
is there a better tool to use to preload stuff to ram after boot then, i read around and readahead is the only* thing i saw that could do it manually for multiple programs. 

*well there are some openSuse scripts but the links were dead.

---

### Post by RainCT on 2009-02-23
Thanks for the tip, got it from 40s to below 30s! Now what really annoys me is that the BIOS takes 10 seconds to start up...

---

### Post by pah99 on 2009-03-16
Hey I have a question. I am running Jaunty and I started to go through various posts on how to reduce boot time. Anyway, after doing a bunch of stuff, I got it down to 12 something seconds. Then, I ran the "profile" thing for the kernel, and my boot time went up to about 40 seconds. Now, no matter what I do, it stays there. If I shut off readahead, then it goes down to 14.3 seconds, but I cant get it back to 12 seconds. I was wondering, isn't readahead supposed to cut down my boot time? If so, then what is going on? Any help is appreciated.

I have opened a new thread for this at [http://ubuntuforums.org/showthread.php?t=1100763](http://ubuntuforums.org/showthread.php?t=1100763).

---

### Post by grindboy on 2009-05-03
Did jdong's script on my EEEPC 900 running 9.04 Netbook Remix. I didn't get any dialogue box at the end and I haven't got a ~/.readahead directory! What did I do wrong?

I **only** did jdong's 4 steps are there things I should have done first?

Many Thanks

---

### Post by Tom_T on 2009-05-05
I added profile to my default entry in my menu.lst and now it takes longer to boot up. Also my desktop seems to take longer to appear..

I've checked the menu.lst and have removed profile.

Before I rebooted with profile I had 2 files in /etc/readahead

boot & desktop

Since I've run with profile they have gone ??
Where these the cache files ?? 
How do I recreate them ??

Thanks :)

---

### Post by zika on 2009-05-05
> **Tom_T said:**
> I added profile to my default entry in my menu.lst and now it takes longer to boot up. Also my desktop seems to take longer to appear..

I've checked the menu.lst and have removed profile.

Before I rebooted with profile I had 2 files in /etc/readahead

boot & desktop

Since I've run with profile they have gone ??
Where these the cache files ?? 
How do I recreate them ??

Thanks :)
You should put "profile" only once (that generates those two files) while booting with pressing E (for edit) while on the boot (grub) menu and then selecting the line where kernel You want to boot is and adding "profile" to the and of that line, press Enter and then B (for boot) and that is it. remove "profile" from menu.lst. the way You have done it now You are profiling at every boot which is wrong ... :)

---

### Post by Tom_T on 2009-05-05
Thanks for the reply zika

I have removed profile from my menu.lst, but boot & desktop have not been recreated in /etc/readahead/

Do I need to manually create the files for 'profile' to update ??

Thanks :)

---

### Post by zika on 2009-05-05
> **Tom_T said:**
> Thanks for the reply zika

I have removed profile from my menu.lst, but boot & desktop have not been recreated in /etc/readahead/

Do I need to manually create the files for 'profile' to update ??

Thanks :)
when You reboot machine, on grub menu navigate to kernel You want to use, click on E, navigate to line which lists that kernel, click on E, go to the end of the line, add "profile" (with space in front of it), click on Enter, then click on B, let it do its magic and enjoy ... :)

---

### Post by Tom_T on 2009-05-05
> **zika said:**
> when You reboot machine, on grub menu navigate to kernel You want to use, click on E, navigate to line which lists that kernel, click on E, go to the end of the line, add "profile" (with space in front of it), click on Enter, then click on B, let it do its magic and enjoy ... :)

Hi
I have tried exactly what you listed above and still nothing shows up in /etc/readahead

Any other ideas ??

Thanks :(

---

### Post by zika on 2009-05-05
> **Tom_T said:**
> Hi
I have tried exactly what you listed above and still nothing shows up in /etc/readahead

Any other ideas ??

Thanks :(
reinstall it (from synaptic, for example) ... ?

---

### Post by Tom_T on 2009-05-06
I've re installed and will try profiling again tonight.

Thanks

---

### Post by orethrius on 2009-05-06
I keep seeing people noting that they can't find .readahead, which is a hidden directory ("View > Show Hidden Files" to discover).  Could this be a similar issue in /etc/ ? (I don't use it myself so I really can't speak to the issue.)

---

### Post by zika on 2009-05-06
> **orethrius said:**
> I keep seeing people noting that they can't find .readahead, which is a hidden directory ("View > Show Hidden Files" to discover).  Could this be a similar issue in /etc/ ? (I don't use it myself so I really can't speak to the issue.)
or a simple ```
ls -lag /etc/readahead
```in Terminal window.

---

### Post by jw5801 on 2009-05-06
> **zika said:**
> or a simple ```
ls -lag /etc/readahead
```in Terminal window.

`ls -lag'? You know the `-g' overrules the `-l' right? :P

---

### Post by zika on 2009-05-06
> **jw5801 said:**
> `ls -lag'? You know the `-g' overrules the `-l' right? :P
mea culpa

---

### Post by Tom_T on 2009-05-06
I decided to reinstall Ubuntu 9.04 !!

Now I'm trying to tweak it..

When I boot with profile added to my kernel line, the /etc/readahead/boot file updates, but the /etc/readahead/desktop doesn't.

Is that normal ??

I'll follow the guide on the first post and see how I get on !

Thanks

---

### Post by Tom_T on 2009-05-06
Power on to Grub 2 seconds.

Grub to Login takes 30 seconds.

Login to a working desktop takes 15 seconds.

Total 47 seconds.

Is that about right for an Acer Aspire One D150 10.1" Screen ??

---

### Post by linooks on 2009-05-09
> **Tom_T said:**
> I decided to reinstall Ubuntu 9.04 !!

Now I'm trying to tweak it..

When I boot with profile added to my kernel line, the /etc/readahead/boot file updates, but the /etc/readahead/desktop doesn't.


It's the same here.

P.S.: Where does the red (Non)Smiley above come from?

---

### Post by zika on 2009-05-09
> **linooks said:**
> it's the same here.
+1

---

### Post by linooks on 2009-05-10
But:

Using of the profile boot option belongs to this tutorial: [http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)

Here we don't use it! We don't use the directory /etc/readahead at all.

---

### Post by weeman7007 on 2009-05-16
hi, i happen to use a solid state drive, would this method still improve the login time?

according to conky it takes about 24 seconds to boot to my desktop with everything loaded (auto login), bootchart says 11 seconds... thus login must take 13 seconds... which is poor in my opinion.

---

### Post by jdong on 2009-05-18
> **weeman7007 said:**
> hi, i happen to use a solid state drive, would this method still improve the login time?

according to conky it takes about 24 seconds to boot to my desktop with everything loaded (auto login), bootchart says 11 seconds... thus login must take 13 seconds... which is poor in my opinion.

I don't feel this style of readahead will help; what you need is more of a timeline watermarking type readahead like what sreadahead provides. I haven't looked too hard at that due to my lack of a SSD to test with.

---

### Post by weeman7007 on 2009-05-19
ok, thanks :) I shall do a bit of googling on sreadahead later then :)

---

### Post by macabro22 on 2009-06-24
Nice tweak. I experience great improvement in login time. It would be nice to have this by default in future versions. Thanks

---

### Post by DarkDead on 2009-11-01
Hi.

Karmic replaced readahead package by one called sreadahead.
Is it possible to profile the login sequence with this one?

Commands like sreadahead-watch and sreadahead-list don't exist.

---

### Post by zika on 2009-11-01
You all might want to read this thread: [http://ubuntuforums.org/showthread.php?t=1304952](http://ubuntuforums.org/showthread.php?t=1304952) which puts the dots on all i's from the discussion here ...

---

### Post by jdong on 2009-11-02
Yes. I'll edit the original description to reflect this, but in Karmic, sreadahead is an automatically re-profiling bootup IO accelerator and no longer needs tweaks like this.

---

