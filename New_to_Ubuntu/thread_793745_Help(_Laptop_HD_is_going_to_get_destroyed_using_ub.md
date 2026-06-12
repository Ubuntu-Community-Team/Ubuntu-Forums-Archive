---
title: "Help:( Laptop HD is going to get destroyed using ubuntu/kununtu?"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by Kestol on 2008-05-14
Hellp-... I've read on a danish forum that my laptops hardisk is going to wear down by the use of ubuntu/kubuntu...
So i tryed to run the test that showed if my laptop was in danger:(

So i installed the following:

> sudo aptitude install smartmontools

and then i ran the command

> sudo smartctl -a /dev/sda | grep Load_Cycle_Count

So i remembered the last number and ran the last command after 15 minutes.. And i had an increase of 8... And i read that is way to much and that my harddisc will wear down using ubuntu...

What should i do:confused:
I read on the other forum that i had to change the bios and stuff like that.. BUt i didnt understand it that well... Well i've seen and changed bios before.. But only stuff like the launch options...

What to do? plz help.. I would really like to use linux:(

And another quick question...

For a laptop.. Should i choose ubuntu or kubuntu?
If both are good.. Wich one would you say i should use??? I'm new to linux...

Thx in advantage:KS

---

### Post by billgoldberg on 2008-05-14
> **Kestol said:**
> Hellp-... I've read on a danish forum that my laptops hardisk is going to wear down by the use of ubuntu/kubuntu...
So i tryed to run the test that showed if my laptop was in danger:(

So i installed the following:



and then i ran the command



So i remembered the last number and ran the last command after 15 minutes.. And i had an increase of 8... And i read that is way to much and that my harddisc will wear down using ubuntu...

What should i do:confused:
I read on the other forum that i had to change the bios and stuff like that.. BUt i didnt understand it that well... Well i've seen and changed bios before.. But only stuff like the launch options...

What to do? plz help.. I would really like to use linux:(

And another quick question...

For a laptop.. Should i choose ubuntu or kubuntu?
If both are good.. Wich one would you say i should use??? I'm new to linux...

Thx in advantage:KS

Ubuntu won't destroy your HD, that's just not true. I don't know what forums you frequent, but they are lying.

I suggest you use Ubuntu and leave Kubuntu be.There is more documentation available on Ubuntu, more people use it and it's better imho.

---

### Post by tjwoosta on 2008-05-14
ubuntu and kubuntu will not hurt your hardisk, nor any other part of your computer !

no more then windows or any other OS would anyway

(why would anybody make an OS that would damage hardware?)

---

### Post by Kestol on 2008-05-14
Well i found a little of it in english:

> A number of people are blogging about how running the latest version of Ubuntu Gutsy Gibbon on a laptop could possibly end up causing an early demise of the laptop hard disk. The problem is that the hard disk essentially consists of a spindle and a bunch of disks stacked one on top of the other which rotate at high speeds. Now as with all objects which have moving parts, hard disk also faces wear and tear. The problem faced by Ubuntu laptop users is the aggressive use of hard disk by Ubuntu thus shortening the life of the hard disk.

So:(

Also found this:
[http://chhamanator.wordpress.com/2008/03/06/harddisk-problem-in-ubuntu/](http://chhamanator.wordpress.com/2008/03/06/harddisk-problem-in-ubuntu/)

---

### Post by alienexplorers on 2008-05-14
Since using Ubuntu in 2006 I have gone through 4 hard drives.  Explain that!

---

### Post by peakshysteria on 2008-05-14
Ubuntu has gone Hardy Heron now you know. So Gutsy doesn't count anymore (my seven year old daughter is still running it though) :) And my machine uses less CPU under Ubuntu than it did in XP. And have less glitches and hickups. I'm new to linux. But I must say I'm impressed how smooth everything is running.

Never heard of an OS killing a HDD. Seem just not right.

---

### Post by Kestol on 2008-05-14
I know that... But the problem is still there nevertheless...
:(

The test still showed that something is wrong:(

---

### Post by tjwoosta on 2008-05-14
hmm..  

that is strange, ive never had any problems

maybe you would have better luck to post this in the hardware section?

---

### Post by nicedude on 2008-05-14
This post used to contain jokes as I thought Kestol was wrong about this.

I WAS WRONG KESTOL IS RIGHT IT IS A PROBLEM FOR SOME HARD DRIVE BRANDS WITH APM green mode crud

First follow Kestols first post above and install smartmon tools and test if this is affecting you, all you do is run the command he gives & write down number of cycle counts ( last number ) and then wait 10 minutes and run it again. The number should not increase but by much as an increase of 15 per hour is probably the upper limit for long hard drive health ( mine was going up 20 every 10 minutes sitting idle ). Some hard drives give 600,000 - 1,000,000 as the life of your drive so keep that in mind and do the math on how long yours will last at your current rate. 

SEE MY POST #56 for a script and directions to fix this situation so that your disk does not load cycle constantly.

Just read all the directions so that the fix will take affect and function as intended , it reduced my cycles from 20 per 10 minutes to 2 in 3.5 hours - which is fine as wine & should allow my hard disk to last much longer life span :-) .

Finally I must state that this is a Linux problem with these drives in general not an Ubuntu one so no fault of any of the developers on this. Just another case of manufacturers knowing there is a linux problem and not caring enough to fix it.

PLEASE HEED THIS WARNING AND CHECK YOUR SYSTEM OUT - THIS IS A REAL SITUATION FOR SOME HDD's

---

### Post by NIT006.5 on 2008-05-14
I do remember hearing about this just after Gutsy was first released (and there were threads about it on this forum) but I was under the impression that any such "bugs" had long been fixed. So provided you're up-to-date I would "think" that you'd be ok. However, I'm not qualified to say this, it's just what I "think".

---

### Post by NIT006.5 on 2008-05-14
More info:

[http://ubuntuforums.org/showthread.php?t=591503&highlight=load+cycle+count](http://ubuntuforums.org/showthread.php?t=591503&highlight=load+cycle+count)
[http://ubuntuforums.org/showthread.php?t=772159&highlight=load+cycle+count](http://ubuntuforums.org/showthread.php?t=772159&highlight=load+cycle+count)

Be careful before attempting any fixes though, and make sure you trust the person who posted the "fix". I would suggest checking up on bug reports and such to make sure that it's definitely the same problem and that you're doing the right thing to try and fix it. And also make sure that it hasn't already been fixed in any updates.

---

### Post by peakshysteria on 2008-05-14
Can you post the specs (hardware) of your machine and a bit more information (what distro are you running etc)?

And what do you usually use your machine for? Do you run some heavy processes?

And might someone familiar with smartmontools provide an answer?

---

### Post by NIT006.5 on 2008-05-14
More info:

[http://ubuntuforums.org/showthread.php?t=591503&highlight=load+cycle+count](http://ubuntuforums.org/showthread.php?t=591503&highlight=load+cycle+count)
[http://ubuntuforums.org/showthread.php?t=772159&highlight=load+cycle+count](http://ubuntuforums.org/showthread.php?t=772159&highlight=load+cycle+count)

Be careful before attempting any fixes though, and make sure you trust the person who posted the "fix". I would suggest checking up on bug reports and such to make sure that it's definitely the same problem and that you're doing the right thing to try and fix it. And also make sure that it hasn't already been fixed in any updates.

---

### Post by NIT006.5 on 2008-05-14
Sorry, no idea why/how my previous message got posted twice.

This would appear to be the official bug report:

[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/)

I still haven't been able to find out if this has been properly fixed in any updates though. Anyone know?

Please note that this did/does not only apply to Ubuntu, but other distros as well.

---

### Post by sunstriker on 2008-05-14
I think maybe if that laptop has little ram,Ubuntu might use the swap partition a lot. But so does windows (it has a swap file). 
About the Kubuntu/Ubuntu question. You can just use both. Just install ubuntu and after that you can install KDE(4) via apt-get. Ofcourse this way your installation will eat more harddrive but you can use both until you've decided which you like best... Just press on 'session' in the login screen and pick gnome or kde. You can also install xfce4 or whatever you want to try.
Kubuntu comes with kdm (kde display manager). This is the program that shows you the login screen. You can use kdm as well on ubuntu (which uses gdm, gnome display manager) by default.

---

### Post by peakshysteria on 2008-05-14
> **NIT006.5 said:**
> 

This would appear to be the official bug report:

[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/)

I still haven't been able to find out if this has been properly fixed in any updates though. Anyone know?

Please note that this did/does not only apply to Ubuntu, but other distros as well.

Not Ubuntu or linux related at all. As this say:

This problem has been confirmed in Ubuntu as well as in other distributions and on MacOS X and Windows.

---

### Post by kwacka on 2008-05-14
> **alienexplorers said:**
> Since using Ubuntu in 2006 I have gone through 4 hard drives.  Explain that!

I've been using Ubuntu on this laptop since 2006 too. I'm using the original disk that it came with. 

Surely this demonstrates that the common denominator that we ware aware of (the operating system) cannot be responsible for your failures, and we need to look elsewhere - manufacturer of disks, for example.

---

### Post by billgoldberg on 2008-05-14
> **peakshysteria said:**
> Not Ubuntu or linux related at all. As this say:

This problem has been confirmed in Ubuntu as well as in other distributions and on MacOS X and Windows.

If you use your computer your hard drive will slowly start to die, that's normal.

---

### Post by spiderbatdad on 2008-05-14
Using the same IBM thinkpad since 2005. No hardware changes.
Using Ubuntu since Breezy Badger. I have done a clean installation with every Distro upgrade. I leave this laptop on pretty much 24/7.
So, I can say Ubuntu/Linux has not harmed my laptop in any way...on the contrary, surely saved me from numerous viruses...some of which can damage hardware and render systems inoperable.

---

### Post by peakshysteria on 2008-05-14
Yep. 24/7 here as well. Haven't turned off my machine in three years. Been running dualboot Xp and Ubuntu. Now running Hardy (64 Bit) single boot.

---

### Post by coolen on 2008-05-14
This does not sound like a Linux-only issue. It's just a fact of computing. Parts cannot last forever, and using them often means they degrade faster. The workarounds seem to be concerned with getting the most out of your hardware, rather than fixing an existing issue.

Also, if I understand correctly, the number you mentioned increasing by 8 in 15 minutes sounds fairly reasonable. That means there were 8 windup/downs in that time (I think).

Anyway, I wouldn't worry about it. Backup your data often, but that's just good practice.

As for Ubuntu Vs Kubuntu, you can try both. KDE4 is looking sweet at the moment. It has a lot of cool, modern features. Gnome is more conservative, for many (very good) reasons. If you want something solid and comfortable, I'd go with Gnome (Ubuntu). For some nice bling, go with KDE4 (Kubuntu option). That, or install KDE4 on Ubuntu and enjoy the choice free software awards you :D

---

### Post by Kestol on 2008-05-14
Well thx everybody...:)
But to put my mind to peace... Would some of u people that use the OS try the test i posted? 
On a [COLOR="Red"]LAPTOP [/COLOR]:D

I mean the one in the first post...

If u dont want to browse here is what to do:

Install:
> sudo aptitude install smartmontools

Start command:
> sudo smartctl -a /dev/sda | grep Load_Cycle_Count

You will get something like:
> 193 Load_Cycle_Count        0x0012   093   093   000    Old_age   Always       -      [COLOR="Red"]72888[/COLOR]

Remember the red number... 
Wait 15 minutes and do the command again...

Post the increase here for me:)

Hope some people will try it:)

---

### Post by Dynaflow on 2008-05-14
I've actually put Ubuntu on a lot of random laptops, and the load-cycle count issue one of the first things I test for.  It's not so much an issue with Ubuntu or Linux as it is with the rather bizarre default settings that manufacturers program into their SATA hard drives.

Most laptop hard drives are made to last through about 600,000 load cycles.  Actually, they'll probably soldier on after that mark, but 600,000 is the tested limit.  Though your test of your drive's load cycle count isn't necessarily a great sample from a statistical point of view (you'd want to look at the pattern of load cycles over a period of weeks to get an accurate sample), if you are getting 8 cycles/15 minutes, assuming your computer is on six hours a day every day of the year, your hard drive shouldn't hit the testing limit for another seven and a half years (since it's already racked up about 70,000 or so cycles).

In other words, your computer will be incredibly obsolete by the time the drive wears out.

---

### Post by spiderbatdad on 2008-05-14
```
~$ sudo smartctl -a /dev/sda | grep Load_Cycle_Count
193 Load_Cycle_Count        0x0012   001   001   000    Old_age   Always - 1006632

```

Looks like 1,006,632 from here, and going strong.

15 minute interval:

```
:~$ sudo smartctl -a /dev/sda | grep Load_Cycle_Count
193 Load_Cycle_Count        0x0012   001   001   000    Old_age   Always - 1006657

```

So, 24 cycles in 15 minutes. :)

---

### Post by Kestol on 2008-05-14
Well actually this arent my results.. Just an example... Since i'm not fully running ubuntu before i know if it's serious or not...
Just the increase of 8 was from me...


> **spiderbatdad said:**
> ```
~$ sudo smartctl -a /dev/sda | grep Load_Cycle_Count
193 Load_Cycle_Count        0x0012   001   001   000    Old_age   Always -  1006632

```

Looks like 1,006,632 from here, and going strong.

Thx... What about in 15 minutes?

---

### Post by Dynaflow on 2008-05-14
Again, a fifteen-minute sample won't necessarily give you accurate information.  Read this if you want more detail on the issue:  [http://ubuntuforums.org/showthread.php?t=591503]("http://ubuntuforums.org/showthread.php?t=591503").  The bulk of the thread relates to the previous iteration of Ubuntu, but the last several pages deal with the new, 8.04 release.

What are the specs on your computer (just the manufacturer and model number will do if you can't find anything else on it)?

---

### Post by spiderbatdad on 2008-05-14
Updated previous post: 24 in 15 minutes: machine idle.

---

### Post by Dynaflow on 2008-05-14
> **Kestol said:**
> Well thx everybody...:)
But to put my mind to peace... Would some of u people that use the OS try the test i posted? 

My Compaq laptop's hard-drive load cycle count increases by 0/15 minutes when on AC power and by something like 2/15 minutes when on battery because that's what I set it to do.  Immediately after its default installation with Ubuntu, and before I configured it properly, the hard drive was doing about 3/minute.  It's all a question of configuration.

[para deleted]

---

### Post by Kestol on 2008-05-14
@Dynaflow

Here are my accurate specs and everything else:
[http://support.packardbell.com/uk/item/?m=home&sn=103136450326](http://support.packardbell.com/uk/item/?m=home&sn=103136450326)

---

### Post by inportb on 2008-05-14
> **Kestol said:**
> But to put my mind to peace... Would some of u people that use the OS try the test i posted?

Kestol, the test you are suggesting is highly hardware-specific. For example, it reports relatively light usage on my harddrive while it reports heavy usage on a friend's. We both then booted into Windows and played around for an hour. When we booted back into Linux, we found that disk usage under Windows was similar.

Now here's a test you can try yourself, right?

---

### Post by Dynaflow on 2008-05-14
> **Kestol said:**
> @Dynaflow

Here are my accurate specs and everything else:
[http://support.packardbell.com/uk/item/?m=home&sn=103136450326](http://support.packardbell.com/uk/item/?m=home&sn=103136450326)

```
Seagate Momentus 5400.3 160 GB Hard Disk Drive
160 GB 2.5" (S-ATA)
```

This drive would probably see some degree of excessive load-cycle count increase if Ubuntu were to be left on its default settings.  Fortunately, there's a relatively easy way to fix it by changing the default power-management settings.

I would suggest installing Ubuntu to dual-boot with Windows -- just to make everything more easily undoable if you decide to turn back -- and then rerunning the smartctl test over a few days to confirm.  (Hearing frequent not-quite-pings coming from the hard drive would count as an immediate positive.)  If there does seem to be an untoward increase in the load cycle count, see the first post of thread I linked to previously, then either do [this]("http://ubuntuforums.org/showpost.php?p=4897802&postcount=842t") if your laptop is not typically subjected to rough handling while on, or read through the last few pages of that thread to understand how to implement a more robust, less quick-and-dirty solution.

---

### Post by Kestol on 2008-05-14
easy way to fix it sounds great... :)
HOw do i do it?

---

### Post by Dynaflow on 2008-05-14
> **Kestol said:**
> easy way to fix it sounds great... :)
HOw do i do it?

See my edit to my last post. ^

---

### Post by Kestol on 2008-05-14
Well...
I've read the topic...
And i'm not sure wich method u mean by the "last pages" of the given link...
But i'll test the first thing... But i only have to do that once?
Right?

And futhermore.. Is the first one ok? Or should i apply the one u speak of in the " last pages"?

---

### Post by Kestol on 2008-05-14
I was also told to do this in a other forum:

Make script:
> gksudo gedit 99-hdd-ugly-fix.sh

add this:
> #/bin/bash
if on_ac_power = 1 ; then
hdparm -B 254 -M 254 /dev/sda
else
# possibly on battery
hdparm -B 192 -M 128 /dev/sda
fi

Install script to 4 places
> sudo install 99-hdd-ugly-fix.sh /etc/acpi/resume.d/ && sudo install 99-hdd-ugly-fix.sh /etc/acpi/start.d/ && sudo install 99-hdd-ugly-fix.sh /etc/acpi/ac.d/ && sudo install 99-hdd-ugly-fix.sh /etc/acpi/battery.d/

Check it:
> sudo hdparm -I /dev/sda

Is that ok?

---

### Post by Dynaflow on 2008-05-14
> **Kestol said:**
> Well...
I've read the topic...
And i'm not sure wich method u mean by the "last pages" of the given link...
But i'll test the first thing... But i only have to do that once?
Right?

And futhermore.. Is the first one ok? Or should i apply the one u speak of in the " last pages"?

The first one works fine enough in a couple of office laptops I've converted.  The thing about the load-cycle count is, every time the hard drive parks its heads, it's trying to protect your data.  If you drop your laptop or give it a *severe* jolt (assuming it survives), your hard drive has better odds of coming through intact if its heads are parked, rather than hovering over the surface of the disk.  You often don't want to eliminate the behavior or get rid of it too much (which the first solution does), particularly if the computer is going to be in risky environments (say, plugged into an adapter and kept on in an off-roading truck).  

As of this morning, page 88 [here]("http://ubuntuforums.org/showthread.php?t=591503&page=88") is the latest on the load-cycle count issue.  Work backwards a few pages from there, and you will get a more nuanced idea of how to configure your laptop to work exactly how you want it, balancing your preferred, normal-usage life of the drive versus its susceptibility to damage from shocks and such.

For now, go ahead and do your install, make the change suggested by jakon (the first suggestion -- but only if you determine the problem does indeed affect your drive), and then, once you become comfortable enough that you know what you're doing, use jakon's instructions to undo the change (also in the same post), and configure laptop_mode however you think best.  There's more about that in the late-80s pages in that thread.

---

### Post by Kestol on 2008-05-14
ok thx... Would u comment on the accidental dobbelt post i made too?

---

### Post by GordHatt on 2008-05-14
that's Rickie, 
the actor who plays Lahey lives just down the road from me

Gord

---

### Post by Dynaflow on 2008-05-14
> **Kestol said:**
> I was also told to do this in a other forum:

...

Is that ok?

That is the famous "ugly fix" that worked extremely well in the previous version (Gutsy Gibbon), but, due to changes in how Ubuntu handles certain low-level things, it doesn't really work for 8.04 Hardy Heron.  jakon's post is what I personally consider the closest current equivalent, but progress on this issue is evolving and ongoing, and a better quick-and-dirty solution (a la the original "ugly fix") will probably develop soon.  

For now, jakon's fix should be fine enough to use, and it is easily removable when a better drop-in solution comes down the pike.

---

### Post by Kestol on 2008-05-14
Ok great:)

But i can c some difference in the codes...
Jakons fix doesnt actually change any behavior in AC or Battery mode...
So do they run at the same settings?
Doesnt this do something?

---

### Post by Dynaflow on 2008-05-14
> **Kestol said:**
> Ok great:)

But i can c some difference in the codes...
Jakons fix doesnt actually change any behavior in AC or Battery mode...
So do they run at the same settings?
Doesnt this do something?

Rather, it changes the behavior in *both* battery mode and AC mode in the same way because it doesn't seem to discriminate between them.  That's why I'd consider the better option to be reading through at least the first post and the last several pages of the central load cycle count thread and figuring out how best to configure laptop_mode for your particular machine and the particular way you intend to use it, e.g., if you want the hard drive more protected from bumps -- even if it causes it to age faster -- when you're off the power cord and presumably mobile.  

For the time being, if you determine that you have the problem, jakon's solution is a perfectly acceptable stopgap for all but the most abusive and/or accident-prone laptop users.

---

### Post by Dynaflow on 2008-05-14
Come to think of it, if you are a beginner and less comfortable on the "bleeding edge," you may want to consider installing the previous, 7.10 Gutsy Gibbon version and applying ubuntu-demon's original "ugly fix:" [http://ubuntuforums.org/showpost.php?p=3675960&postcount=26]("http://ubuntuforums.org/showpost.php?p=3675960&postcount=26")

Fully updated, Gutsy should be just about as functional for you as 8.10 Hardy Heron, and it's had more time to have its kinks worked out and ready-made solutions developed for them.

---

### Post by t0p on 2008-05-14
> **billgoldberg said:**
> If you use your computer your hard drive will slowly start to die, that's normal.

*Nooo!!* *turns off computer... for ever*

---

### Post by Kestol on 2008-05-14
Going to try the jakon fix for now...
Since my test did 50 parkings in 30 minutes:confused:

But well... I entered the command
> sudo gedit /etc/hdparm.conf

and added to the end of the line
> /dev/sda {
apm = 254
}

So i got this at the ending: (copied the thing before with in the quote)
> #command_line {
#       hdparm -q -m16 -q -W0 -q -d1 /dev/hda
#}

/dev/sda {
apm = 254
}

But how do i do this?
> 2. Save [http://launchpadlibrarian.net/14195287/30hdparm](http://launchpadlibrarian.net/14195287/30hdparm) to /tmp/30hdparm . Then,

I cant rightclick and save it... It wants to save it as html...
So how do i do that...???

---

### Post by shifty_powers on 2008-05-14
click on the link then copy and paste ;)

---

### Post by Kestol on 2008-05-14
copy and paste were?
It has to be in a seperate thing if i understand the guide right...:(

---

### Post by shifty_powers on 2008-05-14
heh sorry, kind of jumped into the middle of this thread.

which guide? could you post a link?

---

### Post by Dynaflow on 2008-05-14
> **Kestol said:**
> ...


But how do i do this?
...
I cant rightclick and save it... It wants to save it as html...
So how do i do that...???

```
gksudo gedit /tmp/30hdparm
```

Copy the text from the page the link takes you to.  Paste it into the text editor that pops up when you do the above command.  Save.  Voila.

---

### Post by shifty_powers on 2008-05-14
heh thats what i assumed, but without knowing anything of the rest of thread and what guide he was using, was a little apprenhesive ;)

---

### Post by louieb on 2008-05-14
> **alienexplorers said:**
> Since using Ubuntu in 2006 I have gone through 4 hard drives.  Explain that!

Unlucky? ](*,) Been using Ubuntu about as long. Had a few drives die since I started using a PC back in 1986. But none have died on a computer running Ubuntu yet.  

I've seen articles about Linux and Ubuntu in particular being hard on hard drives. But so is heat, moisture, and dropping the laptop.

---

### Post by candive on 2008-05-14
I was looking into that on Major Geeks, Linux forum.
My hard drive was overheating due to the head parking and unparking non stop.
But since the updates that problem has stopped.

---

### Post by Kestol on 2008-05-14
Yay... This fixed the problem fully:):):)

Thx alot...

Only thing left is this:

> That's it. You can undo it by deleting /usr/lib/pm-utils/sleep.d/30hdparm . Don't forget that this makes your hd more vulnerable to bumps.

What are bumps?
And where do they come from?

---

### Post by Dynaflow on 2008-05-14
Bumps: accelerations followed by rapid deceleration or vice versa, e.g., dropping your laptop onto a cement floor or hitting it with a hammer.

---

### Post by Kestol on 2008-05-14
Aaah ok... 
Really thx for helping me out...

Ok everything is running ok now...
But well... Now it's making 0 in 30 minutes-_-

And the deleting of Jakons method:
> That's it. You can undo it by deleting /usr/lib/pm-utils/sleep.d/30hdparm .

I browsed to the folder where 30hdparm is supposed to be.. But it isnt there:confused:

---

### Post by Dynaflow on 2008-05-14
Bring up the omnipotent version of the file browser by typing:

```
sudo nautilus
```

In its toolbar, click View -> Show hidden files

That should allow you to see and modify any file in the filesystem (careful!).

---

### Post by nicedude on 2008-05-14
My first script posted here earlier didn't cover this fully for everyone so I have made 2 versions for everyone in case your drive is sda or hda in fdisk references. Below I give command to test which your is addressed as. So figure out which your drive is called and then download the script that applies to it. Once downloaded to your desktop right click on the script and go to properties -> in the permission tab select to make the file executable ( this must be done with any script you download or make yourself ). Once you have it set as executable and its on your desktop ( Assumes your desktop is called desktop ) just run each of the four commands below to copy the script to each location it is needed so that it will fix this problem.

At first I had the hdparm parameters backwards and had the script set to -B 254 which is almost APM off for your disk, I have since found that a setting of -B 200 works just fine here and my cycle count hasn't gone up any in 40 minutes so I am happy as a pig in slop.

Your drive could be addressed as hda or sda - To check run "sudo fdisk -l" without quotes then look and see if it says /dev/hda or /dev/sda 

DOWNLOAD SCRIPT "99-hda-load-count-fix.sh" IF YOUR DRIVE IS CALLED HDA BY FDISK AND THEN USE THESE COMMANDS
* make sure to set script as executable before copying or it wont work

sudo cp ~/Desktop/99-hda-load-count-fix.sh /etc/acpi
sudo cp ~/Desktop/99-hda-load-count-fix.sh /etc/acpi/start.d
sudo cp ~/Desktop/99-hda-load-count-fix.sh /etc/acpi/suspend.d
sudo cp ~/Desktop/99-hda-load-count-fix.sh /etc/acpi/resume.d

DOWNLOAD SCRIPT "99-sda-load-count-fix.sh" IF YOUR DRIVE IS CALLED SDA BY FDISK AND THEN USE THESE COMMANDS
* make sure to set script as executable before copying or it wont work

sudo cp ~/Desktop/99-sda-load-count-fix.sh /etc/acpi
sudo cp ~/Desktop/99-sda-load-count-fix.sh /etc/acpi/start.d
sudo cp ~/Desktop/99-sda-load-count-fix.sh /etc/acpi/suspend.d
sudo cp ~/Desktop/99-sda-load-count-fix.sh /etc/acpi/resume.d

This will stop all the load cycles we are worried about.

After you use these commands to copy it where it needs to go just reboot for changes to take effect :-)

My first script sets it to almost no power management which I figured out is too much and not necessary, so this one sets APM for your disk at hdparm -B 200 which is sufficient to stop all my extra cycles here anyway and should fix yours as long as you figure out what your disk device is called and get the appropriate script from the 2 below. Sorry for the hasty script earlier but I was in a hurry to figure this out and it took a minute to figure out some peoples drives would be referenced as sda not hda, so sorry and this post is my ammends.

Note: Some disks are unresponsive to having their APM changed by hdparm, and therefore the workaround doesn't work. It would be a good idea, in such cases, to disable APM in the BIOS if possible


MORE INFO ON PROBLEM IN GENERAL

This problem is only present due to the existence of *all three* of the following factors:
* Hardware is set (default or otherwise) to aggressive power management, causing heads to park. (default behaviour of many drives and often the only user available type of power management)
* Disk is touched often, causing heads to unpark. (default behavior of many distributions)
* Drives are spec'd to a limited number of these cycles. (600,000 is the most common, although some may be spec'd higher or lower).

Reasonable Limits / Criteria for a fix:
* There should be fewer than ~15 load cycles per hour, except during heavy usage while on battery.
* This provides a life expectancy of over four years, which is reasonable for a hard disk.

If no other fix works for you then you will need to look in your system bios and disable APM ( Power Management ) 
this shouldn't be a problem for a desktop system - but would affect laptop battery life :-(

HOPE THIS HELPS YOU OUT EVERYONE :-)

---

### Post by nicedude on 2008-05-14
I am on Hardy 8.04 fully updated and I can confirm the high disk load cycle count was affecting me as well. 

This is not a problem that effects everyone as it is aparently hard drive brand specific - Particularly WD ( Western Digital ) and they have clearly stated they don't support linux end users and don't care to fix this ( Wow never heard that form a manufacturer ) but there are work arounds if this is affecting your system such as the one I propose utilizing hdparm to control the behavior.

Once again this is not a Ubuntu problem alone as it affects all linux systems unless they have a workaround in place. And second this may not be affecting your system you will have to use Kestrels suggestion to test for yourself if you are affected. I can report that some calculations show that this bug could reduce your PC's hard drive life ( if on 24hrs a day ) to 1 yr. If you only use your computer a few hours a day then do the math and your hdd should live longer than you will want to use it.

---

### Post by Afkpuz on 2008-05-14
I bet that your hard drive failing on its own, not due to software.  And in regards to ubuntu destroying your hard drive, my experience was the exact opposite.  Right before I switched to linux, my hard drive crashed.  I was using windows xp and it simply refused to boot.  I then tried installing ubuntu dapper drake and to my surpirse, it installed and was able to boot!  Granted, every boot up, ubuntu would say that it found errors and would fix them.  They just kept coming back though.  So linux breathed new life into my hard drive where windows just quit.  I eventually replaced the drive and have been using ubuntu since jan 2006.  I've also done alot of reinstalls too with no ill effects.

---

### Post by nicedude on 2008-05-14
to Afkpuz and others who doubt Kestrel I doubted this at first as well and then I just Googled it and also tested my own load cycle counts in Hardy 8.04 (fully updated) and he is correct that the load cycles for certain hard drives in LINUX in general ( Not just Ubuntu ) are above recommended specifications ( mine was going up 20 counts every 10minutes - thats 120 counts a hour so 600,000 cycles /120 = 5000 hours 5000/24=208 Days | which means in less than 1 year my hdd would surpass the manufacturers life for load cycling if used 24/7 - This is unacceptable and so I will remedy it instead of crossing my fingers or pointing them for that matter) 


THIS ONLY AFFECTS CERTAIN BRANDS OF HARD DRIVES primarily WD ( and they have said they will not patch the drive firmware to fix it for linux ) 

THERE IS MUCH MORE INFORMATION ABOUT THIS SITUATION NOT ON UBUNTU FORUMS BUT OTHER LINUX FORUMS SO GOOGLE IT PEOPLE AND SEE FOR YOURSELF THAT THIS IS A REAL SITUATION

If you want a fix then try the one I proposed above as it is a simple script that needs only to be marked as executable and then copied to 4 locations and it should calm down your load cycle counts. If not then modify it to a lower number in the script ( ie. script line reads hdparm -B 254 change that to a lower number till as low as 200 and keep retrying till your counts go down to a safe level your comfortable with )

While no one has said anywhere that this will absolutely kill your hdd if you don't fix it theoretically it could drastically reduce its lifespan as some manufacturers only rate their drives for 600,000 cycles and so even if yours has 1,000,000 plus currently , so what maybe 1,100,000 and it goes poof. its best to err on the side of caution.

Over the next few days I will monitor my cycles and adjust my hdparm script parameters until I achieve a load cycle count that will last 4+ years of operation. When I figure out what the -B figure is for my laptop I will report it back here for my model laptop ( ACER 5520-5716 160GB )

If you think I am wrong or that this isn't a potentially real problem then you are free to believe whatever you want. I personally want to thank kestrel for bringing this to my attention though as no one else seemed to figure out that this is a problem to begin with and I think I will try to protect my laptop rather than just roll the dice with my hardware.

---

### Post by stalkier on 2008-05-14
I have been running Ubunu on this laptop for quite a while and I have gone through 2 hard drives. One was a Toshiba (which are a POS drive anyways) and the other was not faulty it was upgraded from 60GB to 120GB. If it was true that a OS kills a HDD then people using Vista should be warned. I am not bashing MS or their OS I am simply saying that Windows reads and writes to the disc far more than Linux. Most hdd failure in laptops is due to the constant moving around of the system. I take mine all kinds of places and I am sure my new hdd will fail at some point in time. It happens with any system that get moved. Move your desktop around from place to place banging it along the way and see it it works well after a while. This is just my opinion though.

---

### Post by dtrot55 on 2008-05-14
Well HD's are unpredictable anyways..theres no real way to say a OS will cause your hard drive to die quicker....but there are ways you can take off the load..like not running Anti Virus software all the time...turing off the screen saver and just turning on the "Turn off monitor after a certain amount of time" setting.  I have went through 8 Hard drives, and im was a Solo Windows user until this year...so like i said...HD's are unpredictable...you can pretty much just assume they will last 2years or less...and if they last more..then you have gotten lucky.

---

### Post by stalkier on 2008-05-14
Thanks for the script Nicedude. I decided to err on the preventive side just in case. Can't hurt.

---

### Post by theZoid on 2008-05-19
> **Kestol said:**
> Well thx everybody...:)
But to put my mind to peace... Would some of u people that use the OS try the test i posted? 
On a [COLOR="Red"]LAPTOP [/COLOR]:D

I mean the one in the first post...

If u dont want to browse here is what to do:

Install:


Start command:


You will get something like:


Remember the red number... 
Wait 15 minutes and do the command again...

Post the increase here for me:)

Hope some people will try it:)

108100

15 min later:

108104

Well?  Asus with 250gb WD Scorpio

---

### Post by zoiks on 2008-05-19
Thanks Nicedude for your help in post #56. I've implemented it and it works great.

I was getting seriously annoyed with the "greedle-greedle-greedle-globbidy-GLOOP" constantly which was the HD parking itself (increasing Load_Cycle_Count). For some reason my drive was doing it several times a minute and the hair on the back of my neck was beginning to stand up. I'm already up to 9783 Load Cycle Counts, and I've barely had this laptop a week!

I had read somewhere else that putting noatime (instead of relatime) in the options in /etc/fstab would do the trick, but I tried that and it didn't do spit. (That means it did nothing for you For-ners.)

I'm running 8.04 Hardy. FWIW, my disk is

```
~$ sudo lshw
[...]
           *-disk
                description: ATA Disk
                product: Hitachi HTS54252
                vendor: Hitachi

```

Before codifying your solution into /etc/acpi/ I spent a little time seeing how far down I could go with the -B parameter. It turns out for my HD, the magic number is 192. That number or higher and the constant load cycles stop. At 191 or lower, it's constantly "globbidy-GLOOP"-ing. But I put it at 200 anyway, because, well, "Everybody's doing it." After putting your solution to work my computer goes at least several minutes before each increment in the Load_Cycle_Count.

**Cheers, and I hope this issue makes a bigger stink on these forums and elsewhere, as I suspect the vast majority of people are happily murdering their laptop hard drives without knowing it.** I don't consider it an Ubuntu or Linux problem per se, as by default they are just leaving the power management values at the defaults set by the HD manufactures. I do have to wonder if the HD manufacturers set the default behavior so aggresively so they can claim lower average power consumption or something. Green is keen, you know.

I've been through 3 laptop hard drives and one 40G drive just failed spectacularly on me. As it turns out, its Load_Cycle_Count was about 210,000 when it failed. Was it *because* of the Load_Cycle_Count? I dunno. But it's a data point.

---

### Post by Dynaflow on 2008-05-20
There's a new, unofficial ugly fix, and it seems to be working.  See:  [http://ubuntuforums.org/showpost.php?p=4965173&postcount=873]("http://ubuntuforums.org/showpost.php?p=4965173&postcount=873")

---

