---
title: "HOWTO: Decrease disk activity"
date: 2008-06-25
forum: Outdated Tutorials &amp; Tips
---

### Post by sdennie on 2008-06-25
**Overview**
This guide is aimed at people who wish to reduce the frequency at which their disks are written to.  Reasons to do that may include:

- The noise or sight of the disk constantly writing every few seconds is annoying.
- To reduce heat.
- To reduce Load_Cycle_Count problems as described [here]("http://ubuntuforums.org/showthread.php?t=805570").

By default, Ubuntu (actually, Linux in general), has two important features that cause the disk to write every few seconds.  The first is the default journal commit time of the [ext3]("http://en.wikipedia.org/wiki/Ext3") filesystem and the second is the [rate at which the kernel wakes up to write dirty pages to disk]("http://www.westnet.com/~gsmith/content/linux-pdflush.htm").

By default, both of these settings are set to 5 seconds which is one of the primary reasons that Ubuntu systems seem to never have idle disks.  This guide will show you how to raise those settings to a higher value in order to reduce disk activity.

**Disclaimer**
This guide shows you how to change default Ubuntu settings that are specifically in place to reduce the amount of work lost in the case of unexpected system shutdown.  [COLOR="Red"]If you don't feel your system is 100% stable, do not use this guide.  If you live in an area with frequent power outages, do not use this guide.
[/COLOR]
**Implementation**
We are going to change the default 5 second settings to [COLOR="Blue"]60[/COLOR] seconds.  Anywhere were we are using the [COLOR="Blue"]60[/COLOR] seconds number, I will highlight in blue so that if you wish to adjust this value, you know exactly what to change.  I'm using 60 seconds because it means that in the event of an unexpected power outage, you will lose at most around 60 seconds of work.  If you are using a laptop or have an UPS for your machine, you can set this number higher if you wish.

To do this, we will backup 2 files, change the settings and then reboot to test.  All these commands should be run from a new terminal where the current directory is your home directory.

The first file we will change is /etc/fstab so that it only commits the journal every 60 seconds.  First, backup /etc/fstab (dda stands for Decrease Disk Activity):

```

sudo cp /etc/fstab /etc/fstab.dda.bak

```

Then, [tinivole]("http://ubuntuforums.org/member.php?u=490875") was nice enough to provide an awk command to automatically change all the ext3 partitions to have a commit time of 60 seconds.  We will run the command and output to a temporary file so that we can verify that the output is correct:

```

awk '{if ($3 == "ext3") print $1" "$2"\t"$3"\t"$4",commit=[COLOR="Blue"]60[/COLOR] "$5"\t"$6; else print}' /etc/fstab > fstab.tmp

```

Now, we will verify that the changes are correct:

```

diff /etc/fstab fstab.tmp

```

You should see output that looks similar to this:

```

6c6
< UUID=d12eeb71-f5a8-4062-95da-d0513c37ced2 /               ext3    defaults,errors=remount-ro 0       1
---
> UUID=d12eeb71-f5a8-4062-95da-d0513c37ced2 /	ext3	defaults,errors=remount-ro**,commit=**[COLOR="Blue"]60[/COLOR] 0	1

```

Notice the **,commit=**[COLOR="Blue"]60[/COLOR].  You may have more output than that but, any line in the output that begins with ">" should have it and it's very important that it looks like this.  If you have any doubt whatsoever, post the output of that command in this thread and wait until myself or someone else says that the output is ok before proceeding.

If the output looks ok, then we can replace /etc/fstab with our temporary file and then remove it:

```

sudo cp fstab.tmp /etc/fstab
rm fstab.tmp

```

That's it for ext3 changes and we will move on to kernel tunable changes.  First we will make a backup of /etc/sysctl.conf and create a file for editing:

```

sudo cp /etc/sysctl.conf /etc/sysctl.conf.dda.bak
cp /etc/sysctl.conf sysctl.tmp

```

Now open sysctl.tmp with your editor of choice and, at the bottom of the file, add:

```

vm.dirty_ratio = 40
vm.dirty_background_ratio = 1
vm.dirty_writeback_centisecs = [COLOR="Blue"]6000[/COLOR]

```

In this case, we are specifying centiseconds so, rather than 60 seconds, we use [COLOR="Blue"]6000[/COLOR] centiseconds here.  The top two options simply wait slightly longer to request disk writes and then write as much as possible.

Once those changes have been made, we can copy our temporary file back and remove it:

```

sudo cp sysctl.tmp /etc/sysctl.conf
rm sysctl.tmp

```

Update:
For Hardy, the final step is to disable the part of pm-utils that will reset our values.  To do this we simply make the script that resets these values not executable:

```

sudo chmod -x /usr/lib/pm-utils/power.d/laptop-tools

```

This final step is not needed for versions of Ubuntu before Hardy.

That's it for system changes.

**Testing**
The easiest way to test is to simply reboot your system and, once you have logged in and the system is fully up, watch your hard drive lights.  You should notice them flickering far less often.  As a more thorough test, you can run the following commands:

```

cat /proc/mounts | grep commit

```

You should see your commit=[COLOR="Blue"]60[/COLOR] changes with that command.  To test the other file we changed, issue the following three commands:

```

cat /proc/sys/vm/dirty_ratio
cat /proc/sys/vm/dirty_background_ratio
cat /proc/sys/vm/dirty_writeback_centisecs

```

The output should be, "40", "1" and "[COLOR="Blue"]6000[/COLOR]" respectively (it may actually be 5999 and not 6000.  This is normal).

Questions/Comments/Suggestions welcome.

---

### Post by logos34 on 2008-06-25
Interesting.  Will this cure the problem so many people complain about (myself included as recently as Feisty)--viz. constant disk accessing/flickering hard drive light even when idle?  

Also, what about using this:

> ... / ext3 [COLOR=Red]noatime[/COLOR],errors=remount-ro 0 1
?

---

### Post by sdennie on 2008-06-25
> **logos34 said:**
> Interesting.  Will this cure the problem so many people complain about (myself included as recently as Feisty)--viz. constant disk accessing/flickering hard drive light even when idle?  

Also, what about using this:


?

This will drastically reduce the frequency in which the disk is written so, yes.  If you are using Hardy, noatime shouldn't be needed.  I have a clean virtual machine that is upgraded from Gutsy to Hardy and:

```

cat /etc/fstab | grep ext3

```

Says:

```

UUID=d12eeb71-f5a8-4062-95da-d0513c37ced2 /               ext3    defaults,errors=remount-ro 0       1

```

(Notice, no noatime, no relatime, etc)

However, when I look at how the disk is actually mounted with:

```

cat /proc/mounts | grep ext3

```

I get (among other things):

```

/dev/disk/by-uuid/d12eeb71-f5a8-4062-95da-d0513c37ced2 / ext3 rw,**relatime**,errors=remount-ro,data=ordered 0 0

```

Notice that it added relatime without any intervention on my part.  So, explicitly stating noatime or relatime in /etc/fstab probably isn't needed in Hardy.

---

### Post by logos34 on 2008-06-25
> **vor said:**
> This will drastically reduce the frequency in which the disk is written so, yes.  If you are using Hardy, noatime shouldn't be needed.  I have a clean virtual machine that is upgraded from Gutsy to Hardy and...
...So, explicitly stating noatime or relatime in /etc/fstab probably isn't needed in Hardy.

hmm, interesting.  maybe I'll try it like yours, without the noatime and relatime (my /home partition) options.

---

### Post by sdennie on 2008-06-25
Yes, you shouldn't need noatime or relatime explicitly in /etc/fstab for ext3 partitions (probably others as well but, I'm not positive) in Hardy.

---

### Post by shae on 2008-06-25
I followed your guide, but some of your settings in sysctl.conf seem to be ignored.  (Hardware is in my signature.)

```
shae@shae-laptop:~$ cat /proc/mounts | grep commit
/dev/disk/by-uuid/997a212b-d078-4b33-9a42-3e9cd62ebf23 / ext3 rw,relatime,errors=remount-ro,commit=60,data=ordered 0 0
/dev/disk/by-uuid/997a212b-d078-4b33-9a42-3e9cd62ebf23 /dev/.static/dev ext3 rw,relatime,errors=remount-ro,commit=60,data=ordered 0 0
shae@shae-laptop:~$ cat /proc/sys/vm/dirty_ratio
40
shae@shae-laptop:~$ cat /proc/sys/vm/dirty_background_ratio
10
shae@shae-laptop:~$ cat /proc/sys/vm/dirty_writeback_centisecs
500

```

---

### Post by Nullack on 2008-06-25
What I dont understand is why mounted drives with no activity from any processes will not sleep. My desktop has 1 physical drive that runs Linux and three other data drives running ntfs. Even when these three ntfs drives have no items running, they still wont sleep. There is no "dirty" journal data on these drives.

---

### Post by sdennie on 2008-06-25
> **shae said:**
> I followed your guide, but some of your settings in sysctl.conf seem to be ignored.  (Hardware is in my signature.)

```
shae@shae-laptop:~$ cat /proc/mounts | grep commit
/dev/disk/by-uuid/997a212b-d078-4b33-9a42-3e9cd62ebf23 / ext3 rw,relatime,errors=remount-ro,commit=60,data=ordered 0 0
/dev/disk/by-uuid/997a212b-d078-4b33-9a42-3e9cd62ebf23 /dev/.static/dev ext3 rw,relatime,errors=remount-ro,commit=60,data=ordered 0 0
shae@shae-laptop:~$ cat /proc/sys/vm/dirty_ratio
40
shae@shae-laptop:~$ cat /proc/sys/vm/dirty_background_ratio
10
shae@shae-laptop:~$ cat /proc/sys/vm/dirty_writeback_centisecs
500

```

What happens if you run:

```

sudo sysctl -p

```

That should reload /etc/sysctl.conf as well as print the values that it's reloading.  If you don't see your changes at the bottom, you may have made a mistake somewhere in the process.

---

### Post by sdennie on 2008-06-25
> **Nullack said:**
> What I dont understand is why mounted drives with no activity from any processes will not sleep. My desktop has 1 physical drive that runs Linux and three other data drives running ntfs. Even when these three ntfs drives have no items running, they still wont sleep. There is no "dirty" journal data on these drives.

By "sleep" do you mean go into suspend mode?  If so, have you used hdparm to set them to do so?  For example, to set /dev/sdb to suspend after 60 seconds of inactivity:

```

sudo hdparm -S12 /dev/sdb

```

For some reason the -S parameter is defined in increments of 5 seconds so, -S12 is 60 seconds.

---

### Post by shae on 2008-06-25
> **vor said:**
> What happens if you run:

```

sudo sysctl -p

```

That should reload /etc/sysctl.conf as well as print the values that it's reloading.  If you don't see your changes at the bottom, you may have made a mistake somewhere in the process.

After running that, the settings are properly set, but they do not survive a reboot.

---

### Post by sdennie on 2008-06-25
> **shae said:**
> After running that, the settings are properly set, but they do not survive a reboot.

How strange.  You're right in that this doesn't work in Hardy (but works in Gutsy).  I think something in Hardy is resetting these values but, I'll test it manually setting them with /etc/rc.local and update the HOWTO.  Thanks.

---

### Post by sdennie on 2008-06-25
I should have known that it is of course, pm-utils resetting these values.  I will update the HOWTO to disable the part of pm-utils that's setting these values and update the HOWTO.

---

### Post by nowshining on 2008-06-25
i got the same on gutsy - then again I have a custom kernel, etc...

n/m but 

cat /proc/sys/vm/dirty_writeback_centisecs
5999

other than that good.

---

### Post by sdennie on 2008-06-26
> **nowshining said:**
> i got the same on gutsy - then again I have a custom kernel, etc...

n/m but 

cat /proc/sys/vm/dirty_writeback_centisecs
5999

other than that good.

I'm not completely sure what you mean.  Setting dirty_writeback_centisecs to a value and having it show up close to that value is fine (It's often the case that it shows up as 1 centisecond less).  If you are having a problem with the HOWTO, I'm happy to help but, it sounds like it's working just fine for you.

---

### Post by nowshining on 2008-06-26
lol, it's working fine, I just didn't exactly understand what those things were for beforehand :) until u showed up with this thread.

---

### Post by Nullack on 2008-06-26
Thanks, Im trying:

 sudo hdparm -S24 /dev/sdd

Its activated and hopefully itll work well. :)

EDIT: Thanks very much!!! Its working. Ive moved it to 10minutes. This is great. Should be default, even if it was say 30 minutes or something.

Though question - man page isnt clear about how to query the parameter rather than change it?

---

### Post by sdennie on 2008-06-26
> **Nullack said:**
> 
Though question - man page isnt clear about how to query the parameter rather than change it?

I'm not sure either.  I just tried a bunch of things and nothing gave me the standby value.

---

### Post by Nullack on 2008-06-27
My setting for standby on HDDs isnt sticking following reboots. Do you know how to make it permanent please? Thanks, this has been a really great how to this should be default for desktop installs.

---

### Post by sdennie on 2008-06-27
> **Nullack said:**
> My setting for standby on HDDs isnt sticking following reboots. Do you know how to make it permanent please? Thanks, this has been a really great how to this should be default for desktop installs.

If you are using a desktop, the easiest way is to probably just add your hdparm settings to /etc/rc.local.  That should insure it runs whenever you start the machine.  It's slightly more complicated if you are using a laptop but, I can post those instructions too.

---

### Post by PeterBBB on 2008-06-28
> **vor said:**
>  .... probably just add your hdparm settings to /etc/rc.local.  That should insure it runs whenever you start the machine.  

It also works after reboot if the settings are placed in /etc/hdparm.conf , but the settings do not survive a resume.

Does anyone know how to get hdparm settings to survive a suspend/resume?


PB.

---

### Post by sdennie on 2008-06-28
> **PeterBBB said:**
> It also works after reboot if the settings are placed in /etc/hdparm.conf , but the settings do not survive a resume.

Does anyone know how to get hdparm settings to survive a suspend/resume?


PB.

Yes.  Something like this should work:

```

#!/bin/bash

. /usr/lib/pm-utils/functions

case "$1" in
    thaw|resume)
**    # Your hdparm settings here**
    ;;
esac

exit

```

Name the file like 99hdparm and install it with:

```

sudo install 99hdparm /etc/pm/sleep.d

```

That will run via pm-utils every time you resume.

Edit:
This is for Hardy only

---

### Post by PeterBBB on 2008-06-29
> **vor said:**
>  ... Something like this should work: 

It does. Thanks.

PB

---

### Post by socref on 2008-07-07
> **logos34 said:**
> Interesting.  Will this cure the problem so many people complain about (myself included as recently as Feisty)--viz. constant disk accessing/flickering hard drive light even when idle?  

I just spoke with Dell Ubuntu support regarding this problem of the constantly flickering H/D light (Ubuntu 7.10 on desktop). I was told that it is normal, and that I should worry only if the H/D light does NOT constantly flicker! 

When I asked if the constantly flickering H/D light meant extra wear-and-tear on the H/D disk and/or other H/D components I was told that the flickering light does not necessarily mean that the disk is spinning or being accessed.

Opinions?
socref

---

### Post by sdennie on 2008-07-07
> **socref said:**
> I just spoke with Dell Ubuntu support regarding this problem of the constantly flickering H/D light (Ubuntu 7.10 on desktop). I was told that it is normal, and that I should worry only if the H/D light does NOT constantly flicker! 

When I asked if the constantly flickering H/D light meant extra wear-and-tear on the H/D disk and/or other H/D components I was told that the flickering light does not necessarily mean that the disk is spinning or being accessed.

Opinions?
socref

I don't have a Dell desktop but, on my Dell laptop, after using something like this guide, the hard drive rarely blinks.  I can't imagine that Dell would release a product that would have a constantly flashing disk light for no apparent reason.

---

### Post by waapwoop1 on 2008-07-23
> **vor said:**
> How strange.  You're right in that this doesn't work in Hardy (but works in Gutsy).  I think something in Hardy is resetting these values but, I'll test it manually setting them with /etc/rc.local and update the HOWTO.  Thanks.

Hi, mine doesn't survive a reboot either. Can you help me. I'm not sure what to do with /etc/rc.local

I get centisecs as 500 on reboot, etc. Thanks in advance

---

### Post by sdennie on 2008-07-23
> **waapwoop1 said:**
> Hi, mine doesn't survive a reboot either. Can you help me. I'm not sure what to do with /etc/rc.local

I get centisecs as 500 on reboot, etc. Thanks in advance

If you are using Hardy, make sure you run this line or pm-utils will override your settings:

```

sudo chmod -x /usr/lib/pm-utils/power.d/laptop-tools

```

---

### Post by waapwoop1 on 2008-07-23
i ran that line, i've tried it a few times.

still the same thing after reboot.

---

### Post by waapwoop1 on 2008-07-24
can i somehow make sudo sysctl -p run at login? if so, how do i do that. Everytime i reboot and i type that i get the centisecs at what i said, not 500 as default

---

### Post by sdennie on 2008-07-26
> **waapwoop1 said:**
> can i somehow make sudo sysctl -p run at login? if so, how do i do that. Everytime i reboot and i type that i get the centisecs at what i said, not 500 as default

I'm not sure what would be causing the settings to reset.  pm-utils can cause them to reset but, if you are sure you've disabled the part of pm-utils that does this, I'm not sure what else would cause this problem unless you've installed some other piece of software that is doing it (or enabled laptop-mode?)

---

### Post by chavanak on 2008-07-30
Hi there I have applied the ugly fix for my hp laptop so that it does not spiup and down frequently. Now my problem is that the hdd temperature is clocking around 45 deg (max of 49 deg). Do you have any idea how i can reduce this heat? I don't want to remove the ugly fix as my hdd will behave in an insane manner. Btw am running hardy heron.

---

### Post by sdennie on 2008-07-30
> **chavanak said:**
> Hi there I have applied the ugly fix for my hp laptop so that it does not spiup and down frequently. Now my problem is that the hdd temperature is clocking around 45 deg (max of 49 deg). Do you have any idea how i can reduce this heat? I don't want to remove the ugly fix as my hdd will behave in an insane manner. Btw am running hardy heron.

Using this guide might help.  It by itself may keep the disks a bit cooler.  Once you've set this up, you may be able to turn the spinup/down behavior back on as, in theory, this should reduce Load_Cycle_Count by a factor of about 12 if it's setup correctly.

---

### Post by waapwoop1 on 2008-07-30
> **vor said:**
> I'm not sure what would be causing the settings to reset.  pm-utils can cause them to reset but, if you are sure you've disabled the part of pm-utils that does this, I'm not sure what else would cause this problem unless you've installed some other piece of software that is doing it (or enabled laptop-mode?)

If i add this to my startup scripts, i'm not sure it will work as i have to say sudo  sysctrl -p   and it will ask for a password.
Anyway to do this without having to ask for a password?

Everytime i log in i change this anyway

---

### Post by waapwoop1 on 2008-07-31
> **vor said:**
> Using this guide might help.  It by itself may keep the disks a bit cooler.  Once you've set this up, you may be able to turn the spinup/down behavior back on as, in theory, this should reduce Load_Cycle_Count by a factor of about 12 if it's setup correctly.


Setting the settings of this fix a bit more extreme cooled my HDD by about 3-4 degrees. That is why i run this every time i log on.

---

### Post by mikewhatever on 2008-08-01
> **chavanak said:**
> Hi there I have applied the ugly fix for my hp laptop so that it does not spiup and down frequently. Now my problem is that the hdd temperature is clocking around 45 deg (max of 49 deg). Do you have any idea how i can reduce this heat? I don't want to remove the ugly fix as my hdd will behave in an insane manner. Btw am running hardy heron.

The ugly fix, as proposed in the relevant thread, sets the hdparm value to 254 on ac, which imo is a little extreme. By experimenting with <hdparm -B XXX /dev/sda>, I found that aggressive spindowns start when the value is lower then 192. You may want to try the same, allowing the disk to spindown a little.

Edit: Vor, what does the commit=60 command do other then modifying fstab?
Can't I simply add commit=60 to ext3 line?

---

### Post by sdennie on 2008-08-02
> **mikewhatever said:**
> 
Edit: Vor, what does the commit=60 command do other then modifying fstab?
Can't I simply add commit=60 to ext3 line?

You can modify the fstab directly but, it's much easier to say, "run this command" than it is to explain how to modify every ext3 parition and add an option to it in a tutuorial.  :)

---

### Post by mikewhatever on 2008-08-02
> **vor said:**
> You can modify the fstab directly but, it's much easier to say, "run this command" than it is to explain how to modify every ext3 parition and add an option to it in a tutuorial.  :)

Right, thanks. :)

---

### Post by eldragon on 2008-09-01
vor, just a thought. this guide contradicts with what you are doing on the power-saving thread. this might be a reason why values are being reset.

---

### Post by AreonEpta on 2008-10-17
Here's my output. Is it okay?
```
diff /etc/fstab fstab.tmp
6c6
< UUID=44e56a43-78d2-4645-af89-397b0893bbf5 /               ext3    relatime,errors=remount-ro 0       1
---
> UUID=44e56a43-78d2-4645-af89-397b0893bbf5 /    ext3    relatime,errors=remount-ro,commit=300 0    1
areonepta@LimitlessLibrary:~$ 

```

---

### Post by ndennen on 2008-10-22
Hello!

I am running Hardy 8.04 and cannot get the settings from 

/etc/sysctl.conf

to stay in effect after a reboot.  I have used:

sudo chmod -x /usr/lib/pm-utils/power.d/laptop-tools

to disable the changes after startup, but it doesnt work.
I still have 40, 10, 500 for my settings after a reboot.

cat /proc/sys/vm/dirty_ratio
40
cat /proc/sys/vm/dirty_background_ratio
10
cat /proc/sys/vm/dirty_writeback_centisecs
500

I have double checked my settings.  if i use the following command

sudo sysctl -p

then my settings are corrected.  What am i doing wrong and why is it remaining disabled after reboot?  Thanks for your help.

-Nate

---

### Post by The Tronyx on 2009-01-07
Awesome information Vor.  Much appreciated!

---

### Post by zika on 2009-01-07
> **vor said:**
> Yes, you shouldn't need noatime or relatime explicitly in /etc/fstab for ext3 partitions (probably others as well but, I'm not positive) in Hardy.
what about Intrepid? if I delete relatime from /etc/fstab I get:```
/dev/disk/by-uuid/7e8ce743-2191-42ed-bfa1-ebb8298be377 / ext3 rw,errors=remount-ro,data=writeback 0 0
/dev/disk/by-uuid/7e8ce743-2191-42ed-bfa1-ebb8298be377 /dev/.static/dev ext3 ro,errors=remount-ro,data=writeback 0 0

```

whatsoever:does relatime (noatime, diratime, nodiratime) make any real difference?

---

### Post by oaxacamatt1 on 2009-01-07
Hey Sdennie,
I would like to try your little tutorial on 'quieting' the harddrive.  I looked over the subsequent posts and did not find any mention of people trying this technique with JFS file system, is that correct?  Do you know if anyone has tried this with JFS?  But if I do decide to try it with JFS can I change the AWK command near the begining.

For example,
awk '{if ($3 == "ext3") print $1" "$2"\t"$3"\t"$4",commit=60 "$5"\t"$6; else print}' /etc/fstab > fstab.tmp

Can I change the "ext3" to "jfs"??  Will that take care of the rest?  Do you know?

Cheers

---

### Post by Skip Da Shu on 2009-02-24
> **sdennie said:**
> **Overview**

Update:
For Hardy, the final step is to disable the part of pm-utils that will reset our values.  To do this we simply make the script that resets these values not executable:

```

sudo chmod -x /usr/lib/pm-utils/power.d/laptop-tools

```

This final step is not needed for versions of Ubuntu before Hardy.

I omitted this step when I followed your guide applying it to a headless number cruncher running Xubuntu v8.10, 64b.  While I do NOT know shell scripting, this script seems to test laptop mode being enabled.  It must be a global variable someplace, not sure how/what/when/where but I'm GUESSing that this must be set not true someplace. Might be due to some package I uninstalled in my post installation purge of 'packages I don't think this thing needs' or might just be Xubuntu. Dunno.
```
if [ x$ENABLE_LAPTOP_MODE = xtrue ]; then
	$LAPTOP_MODE auto
    fi
```


/etc/init.d/laptop-mode also has:
```
if [ x$ENABLE_LAPTOP_MODE = xfalse ]; then
	exit 0;
```


> **sdennie said:**
> **Overview**
The output should be, "40", "1" and "[COLOR="Blue"]6000[/COLOR]" respectively (it may actually be 5999 and not 6000.  This is normal).

Questions/Comments/Suggestions welcome.

After applying all the other changes and restarting it came up fine and reported the values shown above. 
 ***Thanx much for the excellent guide.***

---

### Post by Skip Da Shu on 2009-02-24
> **zika said:**
> what about Intrepid? if I delete relatime from /etc/fstab I get:```
/dev/disk/by-uuid/7e8ce743-2191-42ed-bfa1-ebb8298be377 / ext3 rw,errors=remount-ro,data=writeback 0 0
/dev/disk/by-uuid/7e8ce743-2191-42ed-bfa1-ebb8298be377 /dev/.static/dev ext3 ro,errors=remount-ro,data=writeback 0 0

```

whatsoever:does relatime (noatime, diratime, nodiratime) make any real difference?

I left relatime in my fstab.

From man mount:

atime - Update inode access time for each access. **This is the default**.

relatime - Update  inode  access  times  relative  to  modify or change time.  Access time is only updated if the previous access time was earlier than the current modify or change time. (Similar to noatime, but doesn't break mutt or other applications that need to know if a file has been read since the last time it was modified.)

noatime - Do not update inode access times on this file system (e.g, for  faster access on the news spool to speed up news servers).

---

### Post by LinasMikis on 2009-03-20
good guide, thanks :)
do it work for intrepid or jaunty?

---

### Post by Skip Da Shu on 2009-03-22
> **LinasMikis said:**
> good guide, thanks :)
do it work for intrepid or jaunty?

I pretty sure I tried it on v8.04LTS and v8.10.

---

### Post by esalnoj on 2009-03-25
I ran the checking code and this is my results:

Never mind. It worked.

---

### Post by chellrose on 2009-05-10
> **sdennie said:**
> 
```

diff /etc/fstab fstab.tmp

```You should see output that looks similar to this:

```

6c6
< UUID=d12eeb71-f5a8-4062-95da-d0513c37ced2 /               ext3    defaults,errors=remount-ro 0       1
---
> UUID=d12eeb71-f5a8-4062-95da-d0513c37ced2 /    ext3    defaults,errors=remount-ro**,commit=**[COLOR=Blue]60[/COLOR] 0    1

```


My output looks like yours except that where you have "defaults", I have "relatime".  Is that a problem?  I'm running Kubuntu 9.10, with Gnome at present (though I do also have the KDE that comes with Kubuntu).

Another question -- I rarely ever see the hard drive light lit up after I've booted and logged in.  Could this indicate that my system isn't doing the write-to-disk when it's supposed to?

Thanks.

---

### Post by Skip Da Shu on 2009-05-11
> **Sissy13 said:**
> My output looks like yours except that where you have "defaults", I have "relatime".  Is that a problem?  I'm running Kubuntu 9.10, with Gnome at present (though I do also have the KDE that comes with Kubuntu).

Another question -- I rarely ever see the hard drive light lit up after I've booted and logged in.  Could this indicate that my system isn't doing the write-to-disk when it's supposed to?

Thanks.relatime is a default since at least v8.10 and I think on v8.04... probably before.

I doubt it... This is a good thing.

---

### Post by chellrose on 2009-05-11
Skip,

Thanks.  I was able to follow the steps in the first post up to the chmod part.  I find that I don't have the laptop-tools file.  Is that a problem?

(This _is_ a laptop, so it would seem that the file should be there...)

Thanks again.

---

### Post by Skip Da Shu on 2009-05-12
> **Sissy13 said:**
> Skip,

Thanks.  I was able to follow the steps in the first post up to the chmod part.  I find that I don't have the laptop-tools file.  Is that a problem?

(This _is_ a laptop, so it would seem that the file should be there...)

Thanks again.

While I can't explain why you don't have it... my desktop has it... but it's just a little 6 line script and he's disabling it anyway so not having it shouldn't be a problem.

---

### Post by ProDigit on 2009-10-24
This is what I needed running the latest version of Xubuntu 9 from a USB stick!

Any guide will be appreciated!

I'm generally using an EXT2 partition with noatime enabled, and tried doing the kernel command mentioned above.
I think this is a vital mod for computers running from a USB stick.

Another guide would be awesome if it's written to start Xubuntu from 2 USB sticks or 2x SD cards in a raid config (if that ever will be possible) to improve IOPS (by using a different card/USB stick for reads and another one for writes to the other device).

---

### Post by Rebelli0us on 2009-11-05
Thank you, but that solution is much too technical for average users. I started reading this thread, really... even engineers get bored with too many command lines.

My hard disks run hotter in Ubuntu compared to Windows -- 34 C in XP, 41 C in Ubuntu. I don't know if it's the driver or excessive disk activity. my disks are WDC WD3200BEKT . Thanks, I'd be happy to help in any way I can.

---

### Post by nutznboltz on 2010-05-28
Read this

[http://wiki.debian.org/DebianEeePC/TipsAndTricks#Extendingflashmemorylife](http://wiki.debian.org/DebianEeePC/TipsAndTricks#Extendingflashmemorylife)

The RAMRUN and RAMLOCK parts are not needed for Ubuntu but the idea of using tmpfs in various places makes good sense.

After I added the journal_async_commit mount option my SLC SSD netbook stopped reporting SMART warnings that the drive was being improperly used.

---

### Post by c00kiemonster on 2010-10-16
Does anyone have a good idea of an ext4 (10.04.1) equivalent of this?

---

### Post by zika on 2010-10-16
> **nutznboltz said:**
> The RAMRUN and RAMLOCK parts are not needed for Ubuntu.Would You elaborate on this...

---

### Post by GoCool on 2011-03-04
> **c00kiemonster said:**
> Does anyone have a good idea of an ext4 (10.04.1) equivalent of this?

Yup...even i wanna know, is there an ext4 equivalent of this. Even I am using 10.04 netbook version.

---

