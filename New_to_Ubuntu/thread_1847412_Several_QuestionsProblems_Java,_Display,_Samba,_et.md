---
title: "Several Questions/Problems: Java, Display, Samba, etc"
date: 2011-09-20
forum: New to Ubuntu
---

### Post by Birchle on 2011-09-20
I'm a brand new, first-time Ubuntu user, so any suggestions or info requests will need to be very specific and step-by-step.  I'm not afraid of the terminal or anything else; I just don't usually know what to do without being explicitly told.

I have the 64-bit version of 11.04, from the alternate installer, and am dual-booting with Windows 7.  I'm using the 'Ubuntu Classic (no effects)' desktop option.

I've tried looking up each of these questions myself, though it's possible some weren't as thoroughly searched, given how many unposted questions I've already answered.  I tried to break each question into a section, but it's still a lengthy post.  If it would be better to put each of these in separate threads, I can do so, but it seemed like it would be spammy to create a dozen newbie-question threads all by myself.


_[SIZE=2]**Internet-Related Problems**[/SIZE]_

**Java Plugin**

I have two browsers installed -- the default Firefox, and SeaMonkey.  I have installed the Sun Java plugin through Synaptic, and it works perfectly in Firefox.  After a friend suggested creating a symbolic link from the SeaMonkey plugins folder to the java plugin (sudo ln -s /usr/lib/mozilla/plugins/libjavaplugin.so), java worked in SeaMonkey, too.

Then I discovered the Synaptic-supplied SeaMonkey is buggy, uninstalled it, and downloaded/installed the tar.bz2 for a newer version (2.1, intentionally not the current version).  Now, java no longer works in SeaMonkey.  The previously-created link was still there, but not recognized.  To try and fix the problem, I have since tried:

[LIST]
[*]Linking to all of these, one at a time:
[LIST]
[*]/etc/alternatives/mozilla-javaplugin.so
[*]/etc/alternatives/xulrunner-1.9-javaplugin.so
[*]/usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/amd64/libjavaplugin_jni.so
[*]/usr/lib/mozilla/plugins/libjavaplugin.so
[*]/usr/lib/ure/lib/sunjavaplugin.so
[*]/usr/lib/xulrunner-addons/plugins/libjavaplugin.so
[*]/var/lib/dpkg/alternatives/mozilla-javaplugin.so
[*]/var/lib/dpkg/alternatives/xulrunner-1.9-javaplugin.so
[/LIST]
 
[*]Installing IcedTea (icedtea-netx_1.1.1-0ubuntu1~11.04.1_amd64.deb) and linking to these:
[LIST]
[*]/usr/share/app-install/desktop/icedtea-plugin.desktop
[*]/usr/share/app-install/desktop/icedtea-netx-javaws.desktop (just on the off-chance it might somehow work, since I was out of ideas)
[/LIST]
 
[*]Extracting/Installing the Linux x86 - Compressed Binary (jdk-7-linux-i586.tar.gz) from [here]("http://www.oracle.com/technetwork/java/javase/downloads/java-se-jdk-7-download-432154.html%5BURL=%22http://www.oracle.com/technetwork/java/javase/downloads/java-se-jdk-7-download-432154.html") and linking to:
[LIST]
[*]/opt/jdk1.7.0/jre/plugin/i386/ns7/libjavaplugin_oji.so
[/LIST]
 
[*]Pulling my hair out
[/LIST]
I have not tried linking to these, though I probably will after I post this update:
[LIST]
[*]/opt/jdk1.7.0/jre/lib/i386/libjavaplugin_jni.so
[*]/opt/jdk1.7.0/jre/lib/i386/libjavaplugin_nscp.so
[*]/opt/jdk1.7.0/jre/lib/i386/libjavaplugin_nscp_gcc29.so
[*]/opt/jdk1.7.0/jre/lib/i386/libjavaplugin_oji.so
[*]/opt/jdk1.7.0/lib/i386/libjavaplugin_jni.so
[*]/opt/jdk1.7.0/lib/i386/libjavaplugin_nscp.so
[*]/opt/jdk1.7.0/lib/i386/libjavaplugin_nscp_gcc29.so
[*]/opt/jdk1.7.0/lib/i386/libjavaplugin_oji.so
[/LIST]
Previous links were deleted before new links were tried, to make sure they didn't conflict.  I'm back to the original link right now, but nothing I know to try seems to be working, and googling is only suggesting there might need to be a symbolic link -- which I've clearly already tried.


**Image Links and Disabled CSS**

When I disable CSS, I expect image links to have a 1px blue/purple border to indicate the link.  However, it looks like there is still a "border: 0" (or equivalent) somewhere, because the border doesn't show.  This seems to be a cross-browser quirk specific to Ubuntu, but I'm not sure where or why such a setting would be configured.  Any suggestions or hints of how to change it?


_[SIZE=2]**Miscellaneous Problems**[/SIZE]_

**Program Icons in the Title Bar and Task Bar**

Either manually installed (from tar.bz2) programs, or manually installed Mozilla programs, don't seem to display the program icons.  Currently, I'm having problems with SeaMonkey and Thunderbird.

[LIST]
[*]SeaMonkey was originally installed through Synaptic (I can't remember if the icon showed then, but I don't believe it did.), then later uninstalled so I could manually install a different version.
[*]Thunderbird was manually installed from the start, first the most recent version, then later downgraded to an older version.  In neither case did the icon show, however, so it's not a version issue.
[/LIST]
After some time spent with Google, I found /chrome/icons/default in each program's folder, and all the necessary window icons seem to be there, but it doesn't look like the programs can find them.  Why not?  How can I fix this?


**Touchpad Driver**

I have a Synaptics touchpad, and a Synaptics driver is installed.  I would like to change some settings for my touchpad, and various searches have suggested that I can make the changes in SHMConfig and/or xorg.config, but SHMConfig doesn't exist, and xorg.config seems too generic and doesn't even mention the existence of Synaptics like it's apparently supposed to.  As such, I'm not convinced the driver is actually being used.  How can I confirm if it is or isn't?  And if it isn't, how do I force it to be used instead of whatever is currently being used?


**Standby -- Unreliable**

It's not constant, but it's happened several times now.  Whether the computer goes into standby itself, or I tell it to go into standby, sometimes (maybe half the time?) when I push the power button to wake it up again, nothing happens.  The power light turns solid instead of the standby fade in/out, but the hard drive doesn't spin up and the screen stays black/off.  Has anyone else noticed this problem?  Is there any known fix?


**Weird Full-Screen Border**

When I open a program by clicking its icon on the panel, a yellow 1px or 2px border flashes around the top/left edges of the screen.  It only happens the first time I open a program -- if I just booted the computer, and click the icon, there's a border.  If I close the program and open it via the icon again, no border.  Restart the computer and open the program, border.  Open a second program via its icon, border.  The border goes away right after shows up, so it's not really a problem, but it doesn't seem like the intended behavior.  Any insight into what might be causing it or why?


_[SIZE=2]**Solved Problems**[/SIZE]_ (just for reference)
  
  ***Solved!* [s]Icon to Indicate New Mail[/s]**
  
 [s]I have used Thunderbird for years, in Windows.  When I have new  mail, an envelope icon pops up in the system tray to notify me.  In  Ubuntu, I see options for noises and popups, but nothing as simple as  the system tray icon.  Displaying the envelope icon in the default panel  info applet (with the bluetooth, wireless, volume, battery, date, etc  indicators) would be ideal, though having it as its own separate  indicator would be ok too, if that's the only way.  Is this possible?[/s]
 
 
 ***Solved!* ****[s]Scroll Bars[/s]**
 
 [s]Some programs have a normal-width scroll bar.  Others have a 2px  scroll indicator, and if you hover over it, a rectangle with up/down  arrows pops up.  The indicator is nice about not taking up screen space,  but it is extraordinarily impractical for long files, since you can't  click the indicator to drag it to the target section of the file.  You  can only move line-by-line clicking the arrows, or screen-by-screen  holding page up/page down.  These are both fine for short files, but  much too slow otherwise.  Is there a way to force all programs to use  the normal-width clickable scroll bars?  Or to make the skinny scroll  indicators clickable?[/s]
 
 
 ***Not Possible* [s]Title Bars[/s]**
 
 [s]Some programs (Firefox, gedit, etc) show the program name at the end  of the text in the title bar.  Others (File Manager, etc) don't show the  program name at all.  Is there a way to force the program name to be  shown at the end in all cases?[/s]


***Solved!* [s]Auto-Mount Samba(?) Partitions[/s]**

[s]Right now, if I go to Places > [partition], it mounts the  partition for me.  How do I make it mount the partition automatically,  without having to open it in the file manager?  I've found a few  websites that I think are trying to explain that, but they've left me  more confused than anything else.  Is there a good, clear, detailed,  step-by-step guide out there somewhere?[/s]

---

### Post by Lisiano on 2011-09-20
_[SIZE=2]**Internet-Related Problems**[/SIZE]_

**Java Plugin**

I don't know but maybe purging and installing SeaMonkey again might solve this? 
```
sudo apt-get purge seamonkey
sudo apt-get install seamonkey
```
Purging clears configuration files in addition to removing a program.


**Icon to Indicate New Mail**

By default, you  get notified with all 3. A envelope is located (By default) in the upper right to the left (I think) of the clock. You can open various messaging related programs from it, also it acts as a unified location for your messaging notifications, whenever you get a message it get's highlighted and a notification bubble on the top right corner appears. It dissapears after a while, the envelope stays highlighted.

**Image Links and Disabled CSS**

I just took a look. Note: My HTML skills are awfull. Nesting a [PHP]<a href="Some_url"><img src="Some_Image"></a>[/PHP] didn't give me a border. (I use Chrome if this makes a difference)


_[SIZE=2]**Miscellaneous Problems**[/SIZE]_

**Program Icons in the Title Bar and Task Bar**

Look at "Icon to indicate New Mail", all messaging apps are in it, except for Skype AFAIK.


**Scroll Bars**

They are clickable. Instead of clicking the "2px scroll indicator", click the "rectangle with up/down arrows", personally I don't really like them on a 1920x1080 screen but they are quite useful on my netbook with a 1024x600 screen.


**Title Bars**

Please define what do you mean by "end of text in the title bar", do you mean near a button?


**Touchpad Driver**

Trying going to System -> Preference -> Mouse. You can configure the touchpad there.

**Auto-Mount Samba Partitions**

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
Also, are the Samba shares always online?


**Standby -- Unreliable**

Some people experience this. I think this is cause by the GPU not waking up and locking up the system.


**Weird Full-Screen Border**

A picture tells a million words. Mind attaching a screenshot?[/QUOTE]

---

### Post by MashedUp on 2011-09-20
**Icon to Indicate New Mail**

Right click a panel (hmm, you're using Unity - does it still have panels???), Add To Panel, and either the Indicator App or the Notification area will give you what you want (I forget which).


**Scroll Bars**

They are clickable...?


**Title Bars**

Title bar behaviour is determined by the window theme (metacity?).  I think default is not to show the program name (?) so programs that are showing them have taken it on themselves to do that.  You can find metacity themes at gnome-look.org that may do what you want.


**Auto-Mount Samba Partitions**

Auto-mounting is done by adding an entry to /etc/fstab, but I've never tried it for samba, I just bookmark samba partitions in the file manager and access them when I need them.

---

### Post by Birchle on 2011-09-20
_[SIZE=2]**Internet-Related Problems**[/SIZE]_

> **Lisiano said:**
> **Java Plugin**

I don't know but maybe purging and installing SeaMonkey again might solve this? 
```
sudo apt-get purge seamonkey
sudo apt-get install seamonkey
```Purging clears configuration files in addition to removing a program.
When I removed it via Synaptic, I chose the "Mark for Complete Removal" option, which gave a warning that it removes user preferences, not just the program -- is that equivalent to purging?
Installing again is a non-issue, though, since I'm not using the apt-get version anymore.  I downloaded the tar.bz2 from [http://www.seamonkey-project.org/start/](http://www.seamonkey-project.org/start/) and extracted it.

> **Lisiano said:**
> **Icon to Indicate New Mail**

By default, you  get notified with all 3. A envelope is located (By default) in the upper right to the left (I think) of the clock. You can open various messaging related programs from it, also it acts as a unified location for your messaging notifications, whenever you get a message it get's highlighted and a notification bubble on the top right corner appears. It dissapears after a while, the envelope stays highlighted.
> **MashedUp said:**
> **Icon to Indicate New Mail**
 
 Right click a panel (hmm, you're using Unity - does it still have  panels???), Add To Panel, and either the Indicator App or the  Notification area will give you what you want (I forget which).
**@Lisiano:** There is an envelope there, yes.  But it seems to be hard-coded to Empathy and Evolution, and I'm not using either of those.  Is there a way to attach Thunderbird instead of Evolution?
**@MashedUp:** Actually, I think the Classic desktop is Gnome again.  In any case, I do have panels.  The Indicator Applet is what I already have, with Bluetooth, Wireless, Volume, Evolution-envelope.  Adding a Notification Area didn't seem to do anything.  Does it only show that it exists when there's a notification pending, and since I have no new e-mail, there's nothing to notify about?

> **Lisiano said:**
> **Image Links and Disabled CSS**

I just took a look. Note: My HTML skills are awfull. Nesting a [PHP]<a href="Some_url"><img src="Some_Image"></a>[/PHP] didn't give me a border. (I use Chrome if this makes a difference)
Well, assuming you're also on Ubuntu, it makes it sound even more like it's the OS hiding the border.  Without any CSS, that code snippet should show a border, as far as I've always understood.

[U][SIZE=2][B]Miscellaneous Problems

[/B][/SIZE][/U]  > **Lisiano said:**
> **Scroll Bars**

They are clickable. Instead of clicking the "2px scroll indicator", click the "rectangle with up/down arrows", personally I don't really like them on a 1920x1080 screen but they are quite useful on my netbook with a 1024x600 screen.
Hmm.  I'm not sure if the question or the answer was the misunderstood part, but the answer at least caused me to try click-and-holding the rectangle, rather than just clicking the arrows.  It's certainly not intuitive, but it accomplishes what I want, so I guess that works.  Thanks!

 > **Lisiano said:**
> **Touchpad Driver**

Trying going to System -> Preference -> Mouse. You can configure the touchpad there.
Only to a very limited extent.  And, in fact, there are several things missing in there which contribute to my wondering if the right driver is being used -- most notably a "touchpad" tab which it sounds like I should have.

 > **Lisiano said:**
> **Auto-Mount Samba Partitions**

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
Also, are the Samba shares always online?
I did find that page before, but it confused me to no end.  I'll have another look and see if I can pull out specific questions, though.
They are partitions on the same hard drive as Ubuntu itself, so I'm guessing that means they're always online.  Right?

 > **Lisiano said:**
> **Standby -- Unreliable**

Some people experience this. I think this is cause by the GPU not waking up and locking up the system.
GPU?  Is there a way to make sure it wakes up like it's supposed to?

 > **Lisiano said:**
> **Weird Full-Screen Border**

A picture tells a million words. Mind attaching a screenshot?
I'm not honestly sure if I can.  It flashes that fast.  But I'll try, next time I restart (probably several times tomorrow).


> **MashedUp said:**
> **Title Bars**

Title bar behaviour is determined by the window theme (metacity?).  I  think default is not to show the program name (?) so programs that are  showing them have taken it on themselves to do that.  You can find  metacity themes at gnome-look.org that may do what you want.
Will do, thanks!

> **MashedUp said:**
> **Auto-Mount Samba Partitions**

Auto-mounting is done by adding an entry to /etc/fstab, but I've never  tried it for samba, I just bookmark samba partitions in the file manager  and access them when I need them.
Yeah, this is what I've been doing, but I would prefer to avoid it if possible.  I'll drop the topic for now, until I've had a chance to look through Lisiano's link again and ask some more specific questions.

---

### Post by Krytarik on 2011-09-21
> **Birchle said:**
> **Icon to Indicate New Mail**

I have used Thunderbird for years, in Windows.  When I have new mail, an envelope icon pops up in the system tray to notify me.  In Ubuntu, I see options for noises and popups, but nothing as simple as the system tray icon.  Displaying the envelope icon in the default panel info applet (with the bluetooth, wireless, volume, battery, date, etc indicators) would be ideal, though having it as its own separate indicator would be ok too, if that's the only way.  Is this possible?
Please see this guide:

[http://www.tuxgarage.com/2011/06/replace-evolution-with-thunderbird.html](http://www.tuxgarage.com/2011/06/replace-evolution-with-thunderbird.html)

> **Birchle said:**
> **Scroll Bars**

Hmm.  I'm not sure if the question or the answer was the misunderstood  part, but the answer at least caused me to try click-and-holding the  rectangle, rather than just clicking the arrows.  It's certainly not  intuitive, but it accomplishes what I want, so I guess that works.   Thanks! 
If you prefer to disable the Overlay Scrollbars completely instead, see here:

[http://www.tuxgarage.com/2011/04/disable-overlay-scrollbars-in-ubuntu.html](http://www.tuxgarage.com/2011/04/disable-overlay-scrollbars-in-ubuntu.html)

> **Birchle said:**
> **Title Bars**

Some programs (Firefox, gedit, etc) show the program name at the end of the text in the title bar.  Others (File Manager, etc) don't.  Is there a way to force the program name to be shown at the end in all cases?
It seems like you are *not* meaning the positioning of the window titles, but the content, in this case the name of the respective applications, right?

If so, then no setting of Metacity will change that reg. the concerning applications.

Greetings.

---

### Post by sandyd on 2011-09-21
Use gpointingdevicesettings for your touchpad? [http://live.gnome.org/GPointingDeviceSettings](http://live.gnome.org/GPointingDeviceSettings) or gsynaptics

---

### Post by Lisiano on 2011-09-21
> **Birchle said:**
> 
When I removed it via Synaptic, I chose the "Mark for Complete Removal" option, which gave a warning that it removes user preferences, not just the program -- is that equivalent to purging?
Installing again is a non-issue, though, since I'm not using the apt-get version anymore.  I downloaded the tar.bz2 from [http://www.seamonkey-project.org/start/](http://www.seamonkey-project.org/start/) and extracted it.

Yes, it's the Synaptic equivalent of apt-get purge.
> **Birchle said:**
> 
Well, assuming you're also on Ubuntu, it makes it sound even more like it's the OS hiding the border.  Without any CSS, that code snippet should show a border, as far as I've always understood.
 Technically I'm on Kubuntu but that does not make a difference in this area. The kernel is the same, drivers the same, Chrome from google repos.
> **Birchle said:**
> 
Only to a very limited extent.  And, in fact, there are several things missing in there which contribute to my wondering if the right driver is being used -- most notably a "touchpad" tab which it sounds like I should have.
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)
Or maybe what sandyd posted.
> **Birchle said:**
> 
I did find that page before, but it confused me to no end.  I'll have another look and see if I can pull out specific questions, though.
They are partitions on the same hard drive as Ubuntu itself, so I'm guessing that means they're always online.  Right?
I think you are confusing something (Or did at least).
Samba is a network share, as when you go to Network Places (I think) and look around at the PCs on the network and do stuff on their filesystems.
Now since we got the thing about Samba away, adding the NTFS partitions should be easy (I'm assuming you are talking about NTFS in any case the procedure is the same for any partition), just tell us where you want the partition to be mounted and it's name```
sudo fdisk -l
```, if in doubt, post the whole output of fdisk here.
> **Birchle said:**
> 
I'm not honestly sure if I can.  It flashes that fast.  But I'll try, next time I restart (probably several times tomorrow).
You could try recording a video at 60fps.

> **Krytarik said:**
> 
If you prefer to disable the Overlay Scrollbars completely instead, see here:

[http://www.tuxgarage.com/2011/04/disable-overlay-scrollbars-in-ubuntu.html](http://www.tuxgarage.com/2011/04/disable-overlay-scrollbars-in-ubuntu.html)


+1

---

### Post by Morbius1 on 2011-09-21
> **Auto-Mount Samba Partitions**

Right now, if I go to Places > [partition], it mounts the partition  for me.  How do I make it mount the partition automatically, without  having to open it in the file manager?  I've found a few websites that I  think are trying to explain that, but they've left me more confused  than anything else.  Is there a good, clear, detailed, step-by-step  guide out there somewhere?Easy way?

Use Gigolo: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

There are a number of advantages ( besides ease of use ) to the gvfs method used by Gigolo to the traditional fstab method.

**[COLOR=Blue]EDIT: After reading though the posts here I'm not really sure I've offered the correct solution to your question.[/COLOR]**

You used the word Samba which corresponds to shares on other machines in your network - that's why I suggested Gigolo.

But your description looks like you're talking about auto-mounting partitions installed on your local system. The easiest way for that is to use the "template" approach as used by the Ubuntu installer itself. When you get ready to discuss this post the output of each of the following commands and we can talk:
```
sudo blkid -c /dev/null
cat /etc/fstab
mount
```

---

### Post by Birchle on 2011-09-21
**@Krytarik:**
For the first two: Thanks!  Now I'm curious, though.  I recognize the apt-get commands in the first link.  Both links have others I don't recognize, though.  From the second, what does
```
echo "export LIBOVERLAY_SCROLLBAR=0" | sudo tee /etc/X11/Xsession.d/80overlayscrollbars> /dev/null
```actually do/mean?  What are | and tee?
For title bars, yes, that is what I meant.  I had a feeling the content was set, but it never hurts to check!


**Touchpad**
> **sandyd said:**
> Use gpointingdevicesettings for your touchpad? [http://live.gnome.org/GPointingDeviceSettings](http://live.gnome.org/GPointingDeviceSettings) or gsynaptics
If it comes to it, I will, but having the synaptics driver installed should already include some sort of config GUI, shouldn't it?  Hence why I'm wondering if the driver is even active and how to check for that, before worrying about anything else.

> **Lisiano said:**
> [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)
Or maybe what sandyd posted.
From that page: "Ubuntu provides configuration of the most common touchpad options in System > Preferences > Mouse, under the Touchpad tab. If you cannot find this tab, see the Troubleshooting section at the end of this page."

I cannot find the tab, so off to Troubleshooting: "To check if a touchpad has been detected open a terminal and check the input device list given by this command:
```
xinput list
```If one of the lines mentions a touchpad or glidepoint (perhaps also "Synaptics" or "ALPS", your touchpad has been detected."

Which gives me this result (ignoring the keyboard parts):
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              id=4    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 ALPS GlidePoint                  id=11   [slave  pointer  (2)]
```So my touchpad is detected.  But still no indication of whether the proper driver is being used.
(Side note, somewhere over in Windows, it said I have a Synaptics touchpad.  Why does Ubuntu say it's an ALPS touchpad?  Or does that line not mean it's an ALPS touchpad?  For that matter, where/how do I even find hardware specs in Ubuntu?)


**Mounting**
> **Lisiano said:**
> I think you are confusing something (Or did at least).
Samba is a network share, as when you go to Network Places (I think) and look around at the PCs on the network and do stuff on their filesystems.
Now since we got the thing about Samba away, adding the NTFS partitions should be easy (I'm assuming you are talking about NTFS in any case the procedure is the same for any partition), just tell us where you want the partition to be mounted and it's name```
sudo fdisk -l
```, if in doubt, post the whole output of fdisk here.
**Also in response to Morbius1:**
It's probably my confusion.  I have one hard drive, with multiple partitions.  No network involved.  I was previously told that to mount Windows-format partitions (NTFS, FAT32), you need to use Samba and smbmount, rather than the normal mount.  Additionally, when I tried normal mount just to see what happened, it did mount the drive -- but everything on it was inaccessible.  I could navigate through the directories, but I couldn't open any files.  So I assumed that was the difference between mount and smbmount.  Am I misunderstanding parts?

As for specifically what I want to do...

When I boot the laptop, I can click the Places menu, and it lists all the partitions on this hard drive.  I can then click one of those partitions to open it in file manager, and it shows up on my desktop then, too.  I'm assuming this is when the partition is actually mounted.  Right?  What command does the OS generate when I click the partition from Places?

What I would like is to have that Places > [partition] step happen automatically when I turn on the computer.  The partitions hold some data shared between Ubuntu and Windows (most notably, my Thunderbird profile), and no programs in Ubuntu can access that data until the Places > [partition] step happens.  I can work around it by doing that step manually every time, but it's a bit annoying.

```
sudo blkid -c /dev/null:
/dev/sda1: SEC_TYPE="msdos" LABEL="DELLDIAG" UUID="60FF-BBEF" TYPE="vfat" 
/dev/sda2: LABEL="Recovery" UUID="3C5636005635BC08" TYPE="ntfs" 
/dev/sda3: LABEL="OS" UUID="F67044247043E9C7" TYPE="ntfs" 
/dev/sda5: UUID="19cf2707-7392-4284-a985-bf65637f4db5" TYPE="swap" 
/dev/sda6: LABEL="MEDIA" UUID="1673-EE49" TYPE="vfat" 
/dev/sda7: LABEL="Ubuntu11" UUID="a772f8ec-8aeb-4b45-9e28-fc6bdaf2d69e" TYPE="ext4" 
/dev/sda8: LABEL="DATA" UUID="334A-CBA8" TYPE="vfat"

cat /etc/fstab:
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=a772f8ec-8aeb-4b45-9e28-fc6bdaf2d69e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=19cf2707-7392-4284-a985-bf65637f4db5 none            swap    sw              0       0

mount:
/dev/sda7 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/*****/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=*****)
/dev/sda8 on /media/DATA type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)

sudo fdisk -l:
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa9dee2f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      102400   de  Dell Utility
Partition 1 does not end on cylinder boundary.
/dev/sda2   *          13         666     5242880    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3             666        9021    67108864    7  HPFS/NTFS
/dev/sda4            9021       38914   240114689    5  Extended
/dev/sda5           25169       26142     7811072   82  Linux swap / Solaris
/dev/sda6           26142       38914   102590464    b  W95 FAT32
/dev/sda7           20070       25169    40958976   83  Linux
/dev/sda8            9021       20070    88751104    b  W95 FAT32

Partition table entries are not in disk order
```Now, what does all that mean (commands and output both)?
/dev/sda8 and /dev/sda6 are the partitions I want to auto-mount.


**Border Flicker**
> **Lisiano said:**
> You could try recording a video at 60fps.
That might work.  I failed at getting screenshots fast enough several times already.  Is there anything pre-installed that can record video?  Or if not, what do you suggest?  I've only ever played them, never made them.

---

### Post by Morbius1 on 2011-09-21
Samba has nothing to do with mounting internal drives.

For the mount part:

[1] Unmount the partition you have mounted though Nautilus:
```
sudo umount /media/Data
```[2] Create permanent homes for the partitions to live in:
```
sudo mkdir /media/Data
``````
sudo mkdir /media/Media
```[3] Edit fstab as root:
```
gksu gedit /etc/fstab
```[4] Add the following lines to the end of fstab:
```
UUID=1673-EE49 /media/Media vfat utf8,umask=007,uid=1000,gid=46 0 2
UUID=334A-CBA8 /media/Data vfat utf8,umask=007,uid=1000,gid=46 0 2
```[5] Save fstab, exit gedit, and back in the terminal run the following command which will test for errors and if there are none will mount the partitions without a reboot:
```
sudo mount -a
```

---

### Post by Birchle on 2011-09-21
Quick question before I go off and try that:
What is the difference between sudo and gksu?  Google seems to be mixed on whether they're the same, just graphical vs not, or whether they actually work differently/access files differently.  Since you used sudo for three commands, and gksu for a fourth, does that mean they do in fact work differently and are not interchangeable?

---

### Post by Morbius1 on 2011-09-21
sudo is for the terminal

gksu is for any graphical ( gui ) application. If you run a gui with sudo you will eventually corrupt your system.

---

### Post by Birchle on 2011-09-21
Worked, yay!  Thanks!

> **Morbius1 said:**
> If you run a gui with sudo you will eventually corrupt your system.
Why/How?  And maybe more importantly, why does sudo work with guis, if it's dangerous?

---

### Post by Lisiano on 2011-09-21
+1 for above. Do exactly as he said, then everything will be mounted on boot. Edit: Wow I took a long time to write this post....

[QUOTE=Birchle]
So my touchpad is detected. But still no indication of whether the proper driver is being used.[/QUOTE]
That is the indication it is loaded correctly, else it will be something like "AT Translated Set Mouse" or something. Also it says ALPS probably because the touchpad identifies itself as it, Linux unlike Windows reads the identification codes on the devices and asks the device for it's name, while Windows just tells you what the device probably is (If no driver installed) like a camera, mouse, mass storage. Nothing else. But if you install the driver, the driver then gives the device a name.
[QUOTE=Birchle]For that matter, where/how do I even find hardware specs in Ubuntu?[/QUOTE]
Depends on what you want.
```
cat /proc/cpuinfo
sudo fdisk -l
uname -a
ifconfig -a
iwconfig -a
lspci
lsusb
sudo lshw
...
```
There are many commands and many ways to find information, for example I said "fdisk -l", depending on what is needed it might be "sudo blkid", "mount", etc. Don't worry, if we ever need to know something from you or anyone, we always tell what to type in the terminal to get it. If you want to know what a certain command does, just type ```
man bash
``` Replace bash with any program you want to read more about.
[QUOTE=Birchle]
Is there anything pre-installed that can record video? Or if not, what do you suggest? I've only ever played them, never made them.[/QUOTE]
Pre-installed = Yes. GUI = No.
```
 ffmpeg -f x11grab -r 60 -s 1280x720 -i :0.0 -vcodec libx264 -vpre lossless_ultrafast -threads 0 video.mkv
```
Replace -r 60 with whatever Hz your monitor is running at. No real advantage recording faster, it will have duplicate frames (Instead of 60 DIFFERENT frames, on a 50Hz it will only be 50 Different frames with 10 being repeated. So a extra frame that just increases the size every 5 frames.) Also it mostly acts as a limiter since you will probably record slower.
Replace -s 1280x720 with your desktop resolution.
Check both using ```
xrandr
```
The line with a * is what you want.
```
1920x1080      50.0*    52.0     53.0     54.0     55.0     56.0     57.0     58.0
```
This means my screen is running at 1920x1080 at 50Hz. So put in my case I'd put -r 50 -s 1920x1080
When done, just press Ctrl+C on the terminal and you will find  the screencapture with the name video.mkv, upload it to some host like MediaFire, anywhere is fine really.

There is also a program gRecordMyDesktop (I think), quite nice if you don't want to do it in a terminal. Also let's you specify a region to grab so you can just grab that exact part where it happens. Do leave some space around it so we know where it is though.

---

### Post by capscrew on 2011-09-21
> **Birchle said:**
> Worked, yay!  Thanks!


Why/How?  And maybe more importantly, why does sudo work with guis, if it's dangerous?

The reason has to do with which environment variables you use (e.g bash shell vs nautilus).  The danger is relative.  Permissions can be applied incorrectly and (depending on the users expertise) hard to correct.

Google "sudo vs gksudo" for more info.

---

### Post by doppel.ganger on 2011-09-21
Internet: Use Google Chrome. THE fastest. THE most secure. THE most shiny web browser.

[http://chrome.google.com/](http://chrome.google.com/)

-DG

---

### Post by Birchle on 2011-09-21
> **doppel.ganger said:**
> Internet: Use Google Chrome. THE fastest. THE most secure. THE most shiny web browser.

[http://chrome.google.com/](http://chrome.google.com/)

-DG
What does this have to do with anything?  I don't need a new browser, and even if I do install Chrome (which I was planning to do eventually anyhow), the questions in my first post still apply.

**@Everyone else:**
I'll respond to the other posts when I get back home, but I just noticed that plain text files (aka notes for school or other similarly mundane things) in the now-auto-mounted partitions are suddenly being reported as executable.  This did not happen prior to following the auto-mount instructions.  I have changed nothing else, and in fact done nothing else -- I turned off the computer after confirming the auto-mounting seemed to work, and only just turned it back on.
> Do you want to run "<filename>.txt", or display its contents?
"<filename>.txt" is an executable text file.
[Run in Terminal]  [Display]  [Cancel]  [Run]Clicking display allows me to edit as desired, but why on earth are these files suddenly claiming they're executable?

---

### Post by Krytarik on 2011-09-21
> **Birchle said:**
> **@Krytarik:**
From the second, what does
```
echo "export LIBOVERLAY_SCROLLBAR=0" | sudo tee /etc/X11/Xsession.d/80overlayscrollbars > /dev/null
```actually do/mean?  What are | and tee?

1. "[echo]("http://manpages.ubuntu.com/manpages/natty/en/man1/echo.1.html")" sends "export LIBOVERLAY_SCROLLBAR=0" to standard output (stdout).

2. The "|" '[pipes]("http://www.tuxfiles.org/linuxhelp/iodirection.html")' stdout to the command that is right beneath it.

3. "sudo [tee]("http://manpages.ubuntu.com/manpages/natty/en/man1/tee.1.html")", eventually, takes the piped stdout as input, and writes it into "/etc/X11/Xsession.d/80overlayscrollbars".

4. And "> /dev/null", finally, '[redirects]("http://www.tuxfiles.org/linuxhelp/iodirection.html")' the stdout that is produced by "tee" - besides the file - to "[/dev/null]("http://en.wikipedia.org/wiki//dev/null")", so that it's not printed on the screen.

Detailed enough!? :D

---

### Post by Birchle on 2011-09-22
> **Krytarik said:**
> Detailed enough!? :D
Wonderfully!  It seems I even managed to guess mostly correctly.  Thanks!

> **Lisiano said:**
> There is also a program gRecordMyDesktop (I  think), quite nice if you don't want to do it in a terminal. Also let's  you specify a region to grab so you can just grab that exact part where  it happens. Do leave some space around it so we know where it is  though.
Specifying a region was appealing, so I tried that.  Even it didn't catch the yellow border-flash, though.  Either that, or it got cut off, but it certainly looks like the capture goes all the way to the edge of the screen, so cutting off shouldn't be the problem.  I'll fuss around some more tomorrow, and see if I can get a full-screen capture (either with recordMyDekstop or terminal) to catch the flash.

Just to be clear, though -- I paste the ffmpeg (with edits) line to terminal, and hit enter.  It then immediately starts recording?  Or do I need to do something to start it, before Ctrl+C to stop it?


**As for all the touchpad questions...**
It started when I realized there was no (graphical) option to adjust the base pointer speed.  There was a slider for the acceleration, but not for the base speed.  So, I found [http://manpages.ubuntu.com/manpages/intrepid/man1/xset.1.html](http://manpages.ubuntu.com/manpages/intrepid/man1/xset.1.html) and used "xset m <fraction> 0" to up the speed and smooth the acceleration.

While searching, I also stumbled across [http://manpages.ubuntu.com/manpages/natty/en/man4/synaptics.4.html](http://manpages.ubuntu.com/manpages/natty/en/man4/synaptics.4.html) which says, among other things, "A good way to  find  appropriate  edge  parameters  is  to  enable  the        SHMConfig  option  and  run "synclient -m 1" to see the x/y coordinates        corresponding to different positions on the touchpad."

However, "synclient -m 1" tells me:
```
Can't access shared memory area. SHMConfig disabled?
Couldn't find synaptics properties. No synaptics driver loaded?
```And from there, I got lost.  Some places say to type something in the terminal to enable SHMConfig.  Others say to edit xorg.conf (but unclear which one, since there are several similarly-named files, and varying websites say to edit or create various of those files in various locations).  Others say to do something with HAL (which is...?).  Others say that HAL is outdated.  Others say to install xserver-xorg-input-synaptics -- but it already is installed.  They all seem to hint that synclient, syndaemon, and a Touchpad tab in System > Preferences > Mouse should be available, but none of them seem to be.  Hence my question about if the Synaptics driver is even running.

If anyone else can make more sense of that conflicting info than I can, these are the end goals:

[LIST]
[*]Force the vertical scroll bar to work all the way to the right edge, rather than with a gap between the scroll bar's right edge and the touchpad's right edge
[*]Disable the obnoxious scroll bar tap-to-right-click (but leave tap-to-left-click intact)
[*]Perhaps shift the touchpad's top edge down, so I don't keep bumping it when I use the top set of buttons
[*]Figure out why the touchpad doesn't auto-temporarily-disable while typing, like it is supposed to
[*]Probably more fussing that I've forgotten because it isn't currently being a nuisance
[/LIST]
Can anyone figure out what and/or where I should be asking to fix those problems, since my current "is the driver even working?" doesn't seem to be the appropriate question?

---

### Post by Morbius1 on 2011-09-22
> I just noticed that plain text files (aka notes for school or other similarly mundane things) in the now-auto-mounted partitions are suddenly being reported as executable. This did not happen prior to following the auto-mount instructions. I have changed nothing else, and in fact done nothing else -- I turned off the computer after confirming the auto-mounting seemed to work, and only just turned it back on.
Quote:
Do you want to run "<filename>.txt", or display its contents?
"<filename>.txt" is an executable text file.
[Run in Terminal] [Display] [Cancel] [Run]
Clicking display allows me to edit as desired, but why on earth are these files suddenly claiming they're executable?You've got 2 choices:

**[1] Disable the prompt asking you if you want to Display or Run**

Nautilus > Edit > Preferences > Behavior > Executable Text Files > View executable text files when they are opened.

**[2] Change the fstab entries to make all files not executable:**

Change these:
> UUID=1673-EE49 /media/Media vfat utf8,umask=007,uid=1000,gid=46 0 2
UUID=334A-CBA8 /media/Data vfat utf8,umask=007,uid=1000,gid=46 0 2To these:
> UUID=1673-EE49 /media/Media vfat utf8,[COLOR=Blue]dmask=007,fmask=117[/COLOR],uid=1000,gid=46 0 2
UUID=334A-CBA8 /media/Data vfat utf8,[COLOR=Blue]dmask=007,fmask=117[/COLOR],uid=1000,gid=46 0 2All Windows filesystem files start off in life as being read/write/executable to everyone. Umask is used to remove permissions depending on what your requirements are but umask works on both files and folders and folders have to be set as executable. The dmask ( for directories ) and fmask ( for files ) are the components that make up umask and the fmask settings here will disable [COLOR=Blue]**all**[/COLOR] files from being executable. When mounting any windows filesystem the permissions settings in fstab apply to all files. This is just the opposite of how a Linux filesystem works.

If you go with option 2 remember to unmount the currently mounted fat32 partitions, change fstab, and run "sudo mount -a" to remount.

---

### Post by Birchle on 2011-09-22
First, a (quick?) question.  A friend told me to find files/paths with "locate" and now I'm seeing other posts instructing people to find them with "which".  What's the difference?


> **Morbius1 said:**
> You've got 2 choices:

**[1] Disable the prompt asking you if you want to Display or Run**

**[2] Change the fstab entries to make all files not executable:**
The second sounds like it is just asking for future trouble, if I wind up with an executable in one of those partitions and forget that I set everything to be not executable.  But, if nothing within the folders is executable, why do the folders themselves still need to be executable?  And, if folders always have to be executable, why is there even an fmask, when it has only one valid value?

The first sounds more viable.  Presumably I could still run truly executable files through the context menu if/when necessary, if I disable the prompt?

Why isn't there a way to say only text files aren't executable? (Though I'm still not sure that's ideal, for the same reason.)  And, while files may all start off as executable in Windows, it doesn't seem logical that they necessarily *remain* executable.  But it sounds like that must be what happens, based on your explanation.  How does Windows not try to execute them as well, if it still says they're executable?

And, if auto-mounting is translating "plain text" into "executable", why did that not happen with manual Places > [partition] mounting?  What is done differently in the manual version?  Why can't that same thing be done for the automatic version?

Edit:  Just found this: [http://manpages.ubuntu.com/manpages/natty/en/man8/automount.8.html](http://manpages.ubuntu.com/manpages/natty/en/man8/automount.8.html)
It sounds like that might be what is used for the Places > [partition] mounting?  If so, could I toss that command with appropriate arguments into a file somewhere (rc.local?) to have it run at boot, just as if I immediately opened the partitions via Places, and have the executable settings work correctly that way?

---

### Post by Lisiano on 2011-09-22
> **Birchle said:**
> First, a (quick?) question.  A friend told me to find files/paths with "locate" and now I'm seeing other posts instructing people to find them with "which".  What's the difference?
Which - find a command executable (which bash)
locate - find a file (locate bash)

> **Birchle said:**
> 
The second sounds like it is just asking for future trouble, if I wind up with an executable in one of those partitions and forget that I set everything to be not executable.  But, if nothing within the folders is executable, why do the folders themselves still need to be executable?  And, if folders always have to be executable, why is there even an fmask, when it has only one valid value?
Windows uses ACL, Linux doesn't use the NTFS ACL. So there is no danger in setting it that way. Also folders need to be executable or else you can't see what is inside them, while you can still access stuff you need to know the exact filename.
> **Birchle said:**
> 
The first sounds more viable.  Presumably I could still run truly executable files through the context menu if/when necessary, if I disable the prompt?
Bingo. But if you wish to run a Windows file you need a program called Wine.
```
sudo apt-get install wine
```
Windows programs don't need the executable bit set to run it via Wine (Wine reads it , translate it and runs the translated code, it doesn't execute it directly).

> **Birchle said:**
> Why isn't there a way to say only text files aren't executable? (Though I'm still not sure that's ideal, for the same reason.)  And, while files may all start off as executable in Windows, it doesn't seem logical that they necessarily *remain* executable.  But it sounds like that must be what happens, based on your explanation.  How does Windows not try to execute them as well, if it still says they're executable?
As I already said. Linux doesn't use the NTFS ACL by default so it never writes new permissions for the files. If you want to see for yourself, try looking something in C:\Documents and Settings\Username (C:\Users\Username) and notice how the files (In Linux) have you as the owner, now take a look at C:\Windows, you are also the owner, while if you look in Windows, you will notice that in C:\Windows they still belong to System.
> **Birchle said:**
> 
And, if auto-mounting is translating "plain text" into "executable", why did that not happen with manual Places > [partition] mounting?  What is done differently in the manual version?  Why can't that same thing be done for the automatic version?
The way with fstab does it a bit differently than how the Places > Partition works. That uses gvfs-mount instead.

---

### Post by Morbius1 on 2011-09-22
Lisiano, I think you and I are saying the same thing but ...
> The second sounds like it is just asking for future trouble.The second is how you were running it before you decided to automount but with more access. The way Places > Partition mounts a fat32 partition is this way:
> UUID=1673-EE49 /media/"LABEL of partition" vfat utf8,uid=1000,dmask=077,fmask=133 0 2The partition is mounted with access only to you and with all files marked as not executable. 
> But, if nothing within the folders is executable, why do the folders themselves still need to be executable?Because the definition of executable changes when referencing a directory ( folder ). If a directory is not set as executable then you won't be able to open it to see what's inside.
> Why isn't there a way to say only text files aren't executable?Because Linux doesn't determine the executability of a given file by extension the way Windows does. It does it by the state of the Linux execute bit and windows doesn't have a Linux executable bit. The umask/dmask/fmask parameter gives Linux a "view" so that it treats it as though it has that bit but it's an all or nothing proposition.
> And, while files may all start off as executable in Windows, it doesn't seem logical that they necessarily remain executable. But it sounds like that must be what happens, based on your explanation. How does Windows not try to execute them as well, if it still says they're executable?All Windows files start off as executable from Linux's perspective based on the Linux driver that's being used to mount it not from Windows's perspective. 
> And, if auto-mounting is translating "plain text" into "executable", why did that not happen with manual Places > [partition] mounting?See above

As for autofs, I've only ever tried it when attempting to mount a remote share and I couldn't get it to work. Never really understood the need to use it on internal partition so I can't really help you with that. If you can get it to work you can tell us how to do it. ;)

---

### Post by Birchle on 2011-09-22
> **Morbius1 said:**
> Lisiano, I think you and I are saying the same thing but ...
Between the two of you, I think I'm starting to understand this, so I'm glad you both answered. :)  Responses to each of your posts are all mixed up this time, too, just fyi.

> The second is how you were running it before you decided to automount but with more access.Ah.  I didn't realize that.  In that case, the second option probably is the better one, since things were working as expected with the Places > [partition] method.

One small (and only vaguely relevant) question, though...  If I were to set automount access only to me, as happens with Places, and then another user logs in to the computer, would the automounted drives show on their desktop, but be unviewable?  Or would they not even show/mount (as in, does access only to me also mean automounts only for me?), but still be mountable/viewable via Places?  Or would they not be mountable at all to another user?

> Also folders need to be executable or else you can't see what is inside  them, while you can still access stuff you need to know the exact  filename.> Because the definition of executable changes when referencing a directory ( folder ). If a directory is not set as executable then you won't be able to open it to see what's inside.I definitely had not realized that would be considered execution.  With that definition, it makes a lot more sense.

> Windows programs don't need the executable bit set to run it via Wine  (Wine reads it , translate it and runs the translated code, it doesn't  execute it directly).That was another question I meant to ask.  Thanks for answering even though I forgot to ask!  This also means Morbius' second option remains viable, which is good to know.

> Because Linux doesn't determine the executability of a given file by extension the way Windows does. ...I (sort of) get the executable bit stuff, and that extensions are optional, but even with/without that, Linux does seem able to identify files -- the Type column in the File Manger.  If it can do that, and can thereby identify files as "plain text documents", it seems like there should be a way to have it treat "plain text document" types as non-executable.  That was more what I meant by "Why isn't there a way to say only text files aren't executable?"

Though, since it's now clarified that all files being non-executable is the manual-mount default, that's more of a curiosity question than a true concern.

> All Windows files start off as executable from Linux's perspective based on the Linux driver that's being used to mount it not from Windows's perspective.So to rephrase, Windows files are deemed executable in Linux when Linux first sees them.  They are not actually *created* as executables when Windows first brings them into existence, they are only treated as such when Linux finds them.  Right?  If so, that makes much more sense than how I first understood the explanation.

> The way with fstab does it a bit differently than how the Places > Partition works. That uses gvfs-mount instead.> As for autofs, I've only ever tried it when attempting to mount a remote share and I couldn't get it to work. Never really understood the need to use it on internal partition so I can't really help you with that. If you can get it to work you can tell us how to do it. ;)Hmm.  I found mount, and that didn't work.  Morbius posted directions for fstab which, aside from this executable stuff, does work.  I found a link about automount, and now there is also mention of gvfs-mount and autofs.  It sounds like the last three are unnecessary at this point, but nonetheless, what are they?  Why/How does mention of one translate into mention of two others?  Or are they all the same thing, just aliases?


And to toss in more links, I also stumbled on [http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
If the final two columns are supposed to be "0 0", why are mine "0 2"?  What do the numbers mean and what do they do differently?


> Which - find a command executable (which bash)
locate - find a file (locate bash)So which is only for executables, while locate works for any file at all?  Why does which exist, in that case, since locate already does the same thing (and more)?


And a new question!  Browser URL bars.  In Windows, the default is for single click to highlight everything.  In Linux, single click highlights nothing.  Windows, you can click again to unhighlight everything, or double click to highlight the word/phrase under the cursor, as delimited by slashes, dots, spaces, etc.  Linux, you can double click to highlight everything.  Is there also a way to highlight only the word/phrase under the cursor?  I can only seem to make it switch between everything and nothing, with no in between.

---

### Post by Morbius1 on 2011-09-22
> I (sort of) get the executable bit stuff, and that extensions are optional, but even with/without that, Linux does seem able to identify files -- the Type column in the File Manger. If it can do that, and can thereby identify files as "plain text documents", it seems like there should be a way to have it treat "plain text document" types as non-executable. That was more what I meant by "Why isn't there a way to say only text files aren't executable?"There is simply no way to differentiate files at least in terms of permissions and ownership when Linux looks at a Windows filesystem. Linux is looking for Linux bits set at the file level itself. There are no Linux bits within a given file in a windows filesystem. You can't do a chmod or a chown on a windows file.
> And to toss in more links, I also stumbled on [http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
If the final two columns are supposed to be "0 0", why are mine "0 2"? What do the numbers mean and what do they do differently?The last digit tells the system to do a filesystem check every so often at boot. The how to you referenced is about ntfs not fat32. Fat32 is older and a filesystem check makes more sense. A "0" turns it off a "1" or a "2" determines the relative order of that check in relation to the other partitions being mounted.
> One small (and only vaguely relevant) question, though... If I were to set automount access only to me .........You are not setting access only to you. This line:
> UUID=1673-EE49 /media/Media vfat utf8,dmask=007,fmask=117,uid=1000,gid=46 0 2Will make you the owner of the mounted partition (uid=1000) but you have granted access to all other local users (gid=46). gid is the group id and "46" represents the group "plugdev". All new users created from Admin > Users and Groups are members of the plugdev group by default.
> Windows programs don't need the executable bit set to run it via Wine   (Wine reads it , translate it and runs the translated code, it doesn't   execute it directly).                      While that statement is 100% absolutely correct, in practice if you double click an exe file you will get an error message that it is not executable. The error message isn't coming from Wine it's coming from something called cautious-launcher ( it also happens with a jar file BTW ). To fix that: [http://ubuntuforums.org/showthread.php?t=1747138](http://ubuntuforums.org/showthread.php?t=1747138)

EDIT: You've worn me out - I'm shutting down for the day ;)

---

### Post by Birchle on 2011-09-23
> **Morbius1 said:**
> You've worn me out - I'm shutting down for the day ;)
Slow response this time, sorry.  But, I do appreciate all the lengthy responses, from you and the others.  They have been very informative.

I haven't had any trouble with .exe's the couple times I have tested them, but I bookmarked that link in case I need it in the future.  Thanks. :)

Any ideas on the Java or title bar program icon problems?

---

### Post by Birchle on 2011-09-23
I'm not sure what the policy on double posting is here, but I want to make sure this gets seen, so...

**A little more touchpad info:**
I've decided to work on the assumption that my Synaptics driver is working, and it's just the config stuff (specifically SHMConfig) that isn't working.  To test that theory, I tried temporarily enabling SHMConfig, as suggested by this thread: [http://askubuntu.com/questions/50201/how-to-enable-shmconfig](http://askubuntu.com/questions/50201/how-to-enable-shmconfig)
```
$ synclient SHMConfig=1
Couldn't find synaptics properties. No synaptics driver loaded?
```Ok, let's make sure synclient is even there, since I'm not sure what else to make of that error message:
```
$ locate synclient
/usr/bin/synclient
/usr/share/man/man1/synclient.1.gz
```And for good measure...
```
$ locate syndaemon
/usr/bin/syndaemon
/usr/share/man/man1/syndaemon.1.gz

$ locate SHMConfig
# nothing returned

$ locate shmconfig
# nothing returned
```So, Synaptics touchpad driver is installed, including synclient and syndaemon.  But it can't find the config file/setting/whatever-it-is that it's supposed to have.  Or something.  Why not?  How do I fix it?


I'm just glad I've been using a touchpad almost exclusively for the past 8 years, or this one would be so much more annoying than it already is...



Edit:
As one example of the many xorg.conf edit instructions I've seen, here ([https://bugs.launchpad.net/ubuntu/+source/gsynaptics/+bug/132627](https://bugs.launchpad.net/ubuntu/+source/gsynaptics/+bug/132627)) it says to add this to /etc/X11/xorg.conf
```
Section "InputDevice"
        Identifier "Synaptics Touchpad"
        Driver "synaptics"
        Option "SendCoreEvents" "true"
        Option "Device" "/dev/psaux"
        Option "Protocol" "auto-dev"
        Option "HorizScrollDelta" "0"
        Option "SHMConfig" "true" # <-- and add this line to it
EndSection
```
However, that was posted several years ago, so before I try it, is it still current?  Or have parts been changed since then, such that copying that exactly won't work/will break something else?

There is also mention in a few places (including earlier in this thread) of installing gsynaptics, or now, gpointing-device-settings, since that is apparently the newer version.  Which of the two (the xorg.conf edit or gsynaptics/gpointing) is the better route?  And, if the driver is supposed to have the options and configurations already available, why is *either* needed?  Why do I need to install something extra to access what is supposed to already be available?

---

### Post by MashedUp on 2011-09-23
> **Birchle said:**
> I (sort of) get the executable bit stuff, and that extensions are optional, but even with/without that, Linux does seem able to identify files -- the Type column in the File Manger.  If it can do that, and can thereby identify files as "plain text documents", it seems like there should be a way to have it treat "plain text document" types as non-executable.  That was more what I meant by "Why isn't there a way to say only text files aren't executable?"

In Nautilus (the file manager) go Edit > Preferences > Behaviour, and you can set this there.

---

### Post by Lisiano on 2011-09-24
I would say to first try gsynaptics or gpointing-device-settings first. Then go the xorg.conf route. Just in case it does break something and you can't see anything (Which shouldn't happen).
Before doing the edit do a backup of xorg.cofg
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bk
```
Now do your edit and reboot/restart X.
If it fails then either reboot into recovery mode or switch to a TTY (Ctrl+Atl+F1-F6)
Omit the sudo if you use Recovery with Root shell.
```
sudo rm /etc/X11/xorg.conf
sudo cp /etc/X11/xorg.conf.bk /etc/X11/xorg.conf
```
Now reboot again (If in recovery)
```
reboot
```
or start X (If in a TTY)
```
sudo /etc/init.d/gdm start
```

[quote=Birchle]I (sort of) get the executable bit stuff, and that extensions are optional, but even with/without that, Linux does seem able to identify files -- the Type column in the File Manger. If it can do that, and can thereby identify files as "plain text documents", it seems like there should be a way to have it treat "plain text document" types as non-executable. That was more what I meant by "Why isn't there a way to say only text files aren't executable?"[/quote]
Nautilus and every other GUI file manager looks at the file extension or at the file itself if there is no extension and tries to identify what it is, Linux itself doesn't do anything. Usually we (Linux users) use extensions purely to identify stuff for ourselves. For example, usually a file with no extension is a directory or executable, .sh Shell script, .png/.jpg/etc are images, .img are disk images, .bk/.backup are backup files... Etc.
While it is possible to live with no extensions, the user will hate himself for not using them (Especially console users)

[quote=Birchle]So which is only for executables, while locate works for any file at all? Why does which exist, in that case, since locate already does the same thing (and more)?[/quote]
which finds the executable you would be using when you type the command (In the example I posted before -> bash).
I guess I should have explained that a executable in Linux, is any file you set the exucatable bit on, so Linux ELF (sorta like .exe files) files and scripts. For example pm-hibernate. Let's say I want to modify it but I don't know where it is.
locate pm-hibernate
```
/home/alecive/.icons/AwOken/clear/128x128/apps/gpm-hibernate.png
/home/alecive/.icons/AwOken/clear/24x24/apps/gpm-hibernate.png
/usr/sbin/pm-hibernate
/usr/share/gnome-power-manager/icons/hicolor/16x16/actions/gpm-hibernate.png
/usr/share/gnome-power-manager/icons/hicolor/22x22/actions/gpm-hibernate.png
/usr/share/gnome-power-manager/icons/hicolor/24x24/actions/gpm-hibernate.png
/usr/share/gnome-power-manager/icons/hicolor/32x32/actions/gpm-hibernate.png
/usr/share/gnome-power-manager/icons/hicolor/48x48/actions/gpm-hibernate.png
/usr/share/gnome-power-manager/icons/hicolor/scalable/actions/gpm-hibernate.svg
/usr/share/icons/GartoonRedux/16x16/actions/gpm-hibernate.png
/usr/share/icons/GartoonRedux/22x22/actions/gpm-hibernate.png
/usr/share/icons/GartoonRedux/24x24/actions/gpm-hibernate.png
/usr/share/icons/GartoonRedux/32x32/actions/gpm-hibernate.png
/usr/share/icons/GartoonRedux/scalable/actions/gpm-hibernate.svg
/usr/share/icons/Humanity/apps/16/gpm-hibernate.svg
/usr/share/icons/Humanity/apps/22/gpm-hibernate.svg
/usr/share/icons/Humanity/apps/48/gpm-hibernate.svg
/usr/share/man/man8/pm-hibernate.8.gz
```
Not good, sometimes you can get a lot more stuff than above... Let's try which instead
```
/usr/sbin/pm-hibernate
```
A lot cleaner.

Also from a scripters perspective, you can check if a person has something installed using which without actually executing the file, hard-coding the location (BAD) or depending on a package manager

---

### Post by Birchle on 2011-09-26
> **Lisiano said:**
> I would say to first try gsynaptics or gpointing-device-settings first. Then go the xorg.conf route. Just in case it does break something and you can't see anything (Which shouldn't happen).
Well, I ended up trying xorg.conf anyhow, before you responded...  It did absolutely nothing.  Didn't fix anything, break anything, or even seem to change anything.  The various touchpad commands I tried/posted earlier still complained that SHMConfig was disabled, or that the commands didn't exist, just like before editting xorg.conf.  So I'll move on to trying gpointing-device-settings and hope for a better outcome.

> locate pm-hibernate
```
-snip-
```Not good, sometimes you can get a lot more stuff than above... Let's try which instead
```
/usr/sbin/pm-hibernate
```A lot cleaner.

Also from a scripters perspective, you can check if a person has something installed using which without actually executing the file, hard-coding the location (BAD) or depending on a package managerAh!  Now I understand why there's a difference.  That makes a lot more sense.  Thanks. :)

---

### Post by Birchle on 2011-09-28
> **Birchle said:**
> I'll move on to trying gpointing-device-settings and hope for a better outcome.
Installing gpointing-device-settings adds "Pointing Devices" to System > Preferences.  And Pointing Devices is all of [this]("http://i54.tinypic.com/149u2h.png") -- aka, nothing I can't already do through either the main Mouse settings, or with xset in the terminal.

Trying synclient SHMConfig=1 with gpointing installed doesn't accomplish anything, either.  Everything seems to react exactly how it did before -- suggesting that the Synaptics driver isn't loaded.  I don't know what else there is to try, at this point.

---

