---
title: "Following up on ubiquity bugs"
date: 2011-08-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2011-08-15
I have some history with this and some here will remember that. But I started into the Lubuntu bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/819538](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/819538)

And I still had some old stuff to follow up on which is getting me OT on my Lubuntu thread so I'm posting the bug report links here, in large part just for my own benefit while I'm iso-testing.

**Ubiquity proceeds to use free space without warning** (Still mentioned in release notes)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265)

**Ubiquity should have a command line option to override the free space check ** (Lubuntu now requires only 3.9GB for install, no change in Ubuntu, but the alternate images are a handy work-around)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/775124](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/775124)

**Installation creates a new swap partition** (Triaged, presumably very hard to fix)

[https://bugs.launchpad.net/ubuntu/+source/partman-auto/+bug/782507](https://bugs.launchpad.net/ubuntu/+source/partman-auto/+bug/782507)

Actually they're all related and I've fought with the devs before on fixing some of this stuff so i need to get organized. This is step #1 in that direction.

Adding:

**Install alongside option displays incorrect device designations ** (Milestone Beta 2)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397)

**Ubiquity installer is difficult to read on "Allocate Drive Space"** (this was fixed in ubiquity 2.7.15)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/743238](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/743238)

This one needs a rename, something like "**apt-clone fails ...........**" (Triaged)

[https://bugs.launchpad.net/ubuntu/+source/apt-clone/+bug/758013](https://bugs.launchpad.net/ubuntu/+source/apt-clone/+bug/758013)

Any help will be appreciated.

---

### Post by kansasnoob on 2011-08-16
AFAIK this is the latest dev spec on ubiquity:

[https://docs.google.com/View?id=dfkkjjcj_101gnkrpg5v#2.7.14](https://docs.google.com/View?id=dfkkjjcj_101gnkrpg5v#2.7.14)

I find this interesting:

> [http://seogadget.co.uk/wp-content/uploads/2008/06/diskpartition4.gif](http://seogadget.co.uk/wp-content/uploads/2008/06/diskpartition4.gif) - 'largest continuous free space' here really means 'largest unpartitioned space'.
What's our story on the 'use largest unpartitioned space' option?  I'm not overly concerned if we drop it, as I don't think it's a common use case and users can always resort to the advanced partitioner. -Evan Dandrea **[COLOR="Red"]6/3/10[/COLOR]** 11:16 AM

But you can't just use the manual partitioner if the installer finds enough "free space". It just begins the installation w/o ever presenting any other options :(

---

### Post by kansasnoob on 2011-08-16
Well, stirring things up does at least let me know that the devs are paying attention:

[https://bugs.launchpad.net/ubuntu/+source/partman-auto/+bug/782507/comments/7](https://bugs.launchpad.net/ubuntu/+source/partman-auto/+bug/782507/comments/7)

I'll bet the ubiquity devs have a dartboard devoted just to me :)

---

### Post by dino99 on 2011-08-16
wow the boss himself ;)

---

### Post by kansasnoob on 2011-08-21
I see there are some changes so I better have a look:

[https://launchpad.net/ubuntu/oneiric/+source/ubiquity/+changelog](https://launchpad.net/ubuntu/oneiric/+source/ubiquity/+changelog)

> ubiquity (2.7.15) oneiric; urgency=low

  [ Colin Watson ]
  * Remove dead code from debian/oem-config.oem-config.upstart.
  * Prefer recent versions of ntfs-3g to ntfsprogs, as ntfsresize has moved
    to ntfs-3g.

  [ Evan Dandrea ]
  * Change the first partitioning page title to 'Installation Type.'
    Thanks Matthew Paul Thomas.
  * Merge PyGI branch. Ubiquity now uses PyGI and GTK+3.
  * Feature Freeze exception (LP: #825274).
  * Automatic update of included source packages: base-installer
    1.119ubuntu4, console-setup 1.57ubuntu23, flash-kernel 2.28ubuntu28,
    netcfg 1.68ubuntu1, partman-auto-loop 0ubuntu20, partman-
    basicfilesystems 71ubuntu1, partman-efi 24ubuntu2, partman-
    partitioning 81ubuntu2, tzsetup 1:0.26ubuntu10, user-setup
    1.28ubuntu18.

  [ Brian Murray ]
  * Instead of sending people to +filebug recommend using apport

  [ Luke Yelavich ]
  * Add support for launching high contrast, screen reader, keyboard modifiers,
    and onscreen keyboard accessibility profiles in maybe-ubiquity mode, high
    contrast and screen reader profiles being launcheable either from an
    indicator, or via keyboard shortcut, the rest of the profiles available
    via the indicator only
  * bin/ubiquity-dm:
    - Start at-spi either when an appropriate accessibility profile is enabled,
      or when maybe-ubiquity mode is enabled
    - Remove references to orbit, as the a11y stack now uses dbus
  * debian/control: Add python-appindicator as a dependency of
    ubiquity-frontend-gtk
  * Play the system-ready sound once accessibility profile support code has
    been run to signal the user that a profile shortcut key can be pressed
  * Enable caret browsing/text cursor movement in the slideshow if the screen
    reader accessibility profile is enabled

  [ Mario Limonciello ]
  * Fix calls to get_size() in ubiquity-dm from pygi transition.
 -- Evan Dandrea <email address hidden>   Thu, 18 Aug 2011 17:56:46 +0100

Nothing about the aforementioned bugs but it's always worth a look ;)

---

### Post by kansasnoob on 2011-08-21
I think something may have changed, but it'll require more testing to be sure. I started with this:

[ATTACH]200534[/ATTACH]

[ATTACH]200535[/ATTACH]

And this is what I was presented with:

[ATTACH]200536[/ATTACH]

It's somewhat difficult now to test every conceivable installation scenario. 

I need to disconnect a drive and try again :)

---

### Post by kansasnoob on 2011-08-22
Less hurried this AM and I can actually see that this is fixed:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/743238](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/743238)

Definitely easier to read (old on the left, new on the right):

[ATTACH]200569[/ATTACH]

Still waking up but I'll get a testing plan down here shortly :D

---

### Post by cariboo on 2011-08-22
I assume if you only have Windows installed, or a blank hard drive, it will give you a choice, as to where to install it.

---

### Post by kansasnoob on 2011-08-22
> **cariboo907 said:**
> I assume if you only have Windows installed, or a blank hard drive, it will give you a choice, as to where to install it.

I've tried a couple of scenarios with Windows, one with Windows using 2 NTFS primary partitions and adequate free space, and it looked fine:

[ATTACH]200580[/ATTACH]

And another with Windows using 4 primary partitions which also looked fine:

[ATTACH]200583[/ATTACH]

I haven't yet had time to try any different sized blank drives. This is why I say it takes a long time now to test all the different scenarios :)

Testing is time consuming and after the first dozen tests a certain amount of confusion sets in, but I've also completed some tests where either just one, or multiple Linux Os's exist - with or without free space - and I'm about 95% sure that this bug is fixed now:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265)

But 95% isn't good enough, I need to double check some things ;)

---

### Post by kansasnoob on 2011-08-22
This is just a note to myself.

I need to reproduce this exactly with the newest ubiquity:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265/comments/21](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265/comments/21)

After a long break. About 6 hours of doing nothing but ubiquity testing has me drained.

---

### Post by dino99 on 2011-08-22
> **kansasnoob said:**
> Less hurried this AM and I can actually see that this is fixed:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/743238](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/743238)

Definitely easier to read (old on the left, new on the right):

[ATTACH]200569[/ATTACH]

Still waking up but I'll get a testing plan down here shortly :D

into Installation type: the first proposition is still scary. Does that mean Ubiquity does not create by default a /home partition ?
At least the last proposition "something else" is clear, but nothing tell to use an Alternate iso :(

---

### Post by kansasnoob on 2011-08-22
There may also be a regression in the automated locale thingy, I must now manually choose my locale when the map shows up.

And also the "import settings" thing seems borked ATM.

These are just notes to myself to follow up on :)

---

### Post by kansasnoob on 2011-08-22
> **dino99 said:**
> into Installation type: the first proposition is still scary. Does that mean Ubiquity does not create by default a /home partition ?
At least the last proposition "something else" is clear, but nothing tell to use an Alternate iso :(

**[COLOR="Red"]Does that mean Ubiquity does not create by default a /home partition ?[/COLOR]**

Correct, still no separate /home. IMHO that's OK, in fact that change scares the hell out of me from a testing perspective :(

**[COLOR="Red"]At least the last proposition "something else" is clear, but nothing tell to use an Alternate iso[/COLOR]**

Must it also remind us to tie our shoes so we don't trip over our own shoelaces :lolflag:

I actually hated the new ubiquity when it began in Maverick but I've come to appreciate many of it's new features and I think we're really gaining now. I hope they don't make any more major changes until after 12.04 :)

OT but even Unity is improving :D

---

### Post by kansasnoob on 2011-08-22
Why spend so much time testing :rolleyes:

This is why! I decided to start a new test using the manual/advanced/something-else method and ran up against a wall:

[ATTACH]200595[/ATTACH]

It appears that manual partitioning may be totally borked :P

That's why I test :)

My bug/FFE response:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/825274/comments/10](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/825274/comments/10)

---

### Post by kansasnoob on 2011-08-22
I'd ask this favor of anyone and everyone interested, please use a Live CD/DVD/USB dated August 21 or later and check to be sure you're using ubiquity version 2.7.15 or later.

Next be sure to use the manual/advanced partitioning tool (now called "something else") and see if it's possible to proceed at all. I seem to only get "blacked out" options.

---

### Post by mc4man on 2011-08-22
will have to try todays - on sat.'s build saw the same thing with manual but was able to make the appropriate choices even though blacked out.

---

### Post by arpanaut on 2011-08-22
Seeing the same thing on 8/22 daily/live.
affirmed your comment on bug report above.

---

### Post by fjgaude on 2011-08-22
Okay, the same from this morning's daily build. On x64, three drive, main box.

The guys have lots of work to finish on this version.

---

### Post by kansasnoob on 2011-08-22
> **arpanaut said:**
> Seeing the same thing on 8/22 daily/live.
affirmed your comment on bug report above.

Filed a new report:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/831649](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/831649)

Wiped out ATM though :)

---

### Post by fjgaude on 2011-08-22
Will receive all reports... I'll need it fixed before I can install 11.10 on my main box.

Thanks for keeping up with this bug, kansas.

---

### Post by kansasnoob on 2011-08-22
> **mc4man said:**
> will have to try todays - on sat.'s build saw the same thing with manual but was able to make the appropriate choices even though blacked out.

I think I could proceed if my partitions were created using gparted prior to beginning, which is what I'd normally do in the real world, but one should be able to resize, reformat, etc from the manual installer itself.

Having dealt with Evan Dandrea and Colin Watson in the past this will be an easy one for them ;)

They're kind of caught between a rock and a hard place, where the design team is the rock and we end users are the hard place.

I seriously respect these devs, they work very hard, I've seen them do so right at the last minute with some of my bugs :D

And they've always been respectful of me even when I'm clueless.

---

### Post by arpanaut on 2011-08-22
> **kansasnoob said:**
> Filed a new report:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/831649](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/831649)

Wiped out ATM though :)
Added my "Me Too"
My thanks for your persistence on these issues Erick

---

### Post by kansasnoob on 2011-08-23
Jean-Baptiste Lallement discovered another bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/831431](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/831431)

Not an actual duplicate because one effects setting the mount point whereas the other effects selecting the partition type (use as).

Turns out he was also ahead of me on that other bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/830923](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/830923)

It turns out to actually be a legibility problem, grey text on a nearly black background is not such a good idea.

---

### Post by kansasnoob on 2011-08-23
I ran a couple more tests this AM specifically looking for changes that effect how and when free-space is used and there's no real fix going on there.

In some cases the explanatory text seems sufficient, but in others it can still be a bit of a shocker. I need to try a couple of blank drive installs :)

---

### Post by cariboo on 2011-08-25
I just finished doing a fresh install, and ran into a couple of things that I haven't seen you mention:

[LIST=1]
[*]When two monitors are connected, the Live CD won't boot to a desktop, using nomodeset, disables the second monitor, allowing it to boot to a desktop.

[*]When both wireless and wired connections are available, the network selection screen is a bit confusing, there isn't a choice to use wired only, although it does connect to download the updates and language packs.

[*]On first restart both monitors are in mirror mode
[/LIST]

All the above problems are easy enough to get around, but for a first time user, it might be enough to put them off the whole process.

---

### Post by kansasnoob on 2011-08-26
> **cariboo907 said:**
> I just finished doing a fresh install, and ran into a couple of things that I haven't seen you mention:

[LIST=1]
[*]When two monitors are connected, the Live CD won't boot to a desktop, using nomodeset, disables the second monitor, allowing it to boot to a desktop.

[*]When both wireless and wired connections are available, the network selection screen is a bit confusing, there isn't a choice to use wired only, although it does connect to download the updates and language packs.

[*]On first restart both monitors are in mirror mode
[/LIST]

All the above problems are easy enough to get around, but for a first time user, it might be enough to put them off the whole process.

I have neither wireless or a computer with dual monitor capabilities ATM so I have no way of testing either of those. Have you reported them as bugs?

---

### Post by mc4man on 2011-08-27
Still seeing the blacked out dropdowns on 08/26, though the manual partitioning went fine.
With a nvidia 8400m am also still needing to set nomodeset to get the daily to boot (have bug on that
Couldn't however get past the 'take picture/choose picture section', the continue button remained unresponsive ('ready when you are'

---

### Post by cariboo on 2011-08-27
> **kansasnoob said:**
> I have neither wireless or a computer with dual monitor capabilities ATM so I have no way of testing either of those. Have you reported them as bugs?

No yet, but I should get to it in the next day or two.

---

### Post by RJ12 on 2011-08-27
> **mc4man said:**
> Still seeing the blacked out dropdowns on 08/26, though the manual partitioning went fine.
With a nvidia 8400m am also still needing to set nomodeset to get the daily to boot (have bug on that
Couldn't however get past the 'take picture/choose picture section', the continue button remained unresponsive ('ready when you are'

Same thing is happening here :(

---

### Post by kansasnoob on 2011-09-21
I'm too tired and burned out ATM to report this as a new bug, but with two existing *ubuntu installs I get offered this:

[ATTACH]202669[/ATTACH]

This was the existing partitioning from previous tests:

[ATTACH]202670[/ATTACH]

And after quitting the installation - because I couldn't write a new partition table using the installer - and wiping the drive I still get this:

[ATTACH]202671[/ATTACH]

I just want to ](*,)

Actually should be hitting head against desk or keyboard.

I won't get any more meaningful testing done before Beta 2, that's just the way it is.

And I won't have much time between now and final so ..................... I don't know what'll happen.

IMHO they just keep making the live installer worse and worse.

---

### Post by kansasnoob on 2011-09-22
Well, it turns out 90% of that was a stupid rant :redface:

One of the previous installations was "aborted" so ubiquity was seeing things properly.

But OTOH it is wrong, but not really harmful, to have the installer say "erase disc" when it's a blank disc to begin with :)

Regardless, that was rather a pointless rant.

Thanks for putting up with me.

---

### Post by ronacc on 2011-09-22
you said you were tired and burned out right at the start , it happens to all of us so we made allowances ):P When I looked at your screenshots I thought it was just a poor choice of words in ubiquity ( no surprise ) except for that wouldn't write a new partition table part . On a serious note I became so disgusted and disillusioned with ubiquity's handling of partitions many cycles ago , I don't even bother anymore , I just use gparted
to prepare my partitions and choose "custom " when I get to that part and pray it doesn't do something disastrous anyway .

---

### Post by dino99 on 2011-09-22
> **ronacc said:**
> you said you were tired and burned out right at the start , it happens to all of us so we made allowances ):P When I looked at your screenshots I thought it was just a poor choice of words in ubiquity ( no surprise ) except for that wouldn't write a new partition table part . On a serious note I became so disgusted and disillusioned with ubiquity's handling of partitions many cycles ago , I don't even bother anymore , I just use gparted
to prepare my partitions and choose "custom " when I get to that part and pray it doesn't do something disastrous anyway .

you are not alone :)
searching about ubiquity pending bugs: the list is so long with "critical" & others "high" still not fixed since ages. If Canonical care about its famous distro, it need too to seriously fix the installer first.

---

### Post by kansasnoob on 2011-09-22
> **ronacc said:**
> you said you were tired and burned out right at the start , it happens to all of us so we made allowances ):P When I looked at your screenshots I thought it was just a poor choice of words in ubiquity ( no surprise ) except for that wouldn't write a new partition table part . On a serious note I became so disgusted and disillusioned with ubiquity's handling of partitions many cycles ago , I don't even bother anymore , I just use gparted
to prepare my partitions and choose "custom " when I get to that part and pray it doesn't do something disastrous anyway .

In the "real world" I also lay out my partitions with gparted prior to installation. Anything else just gets sloppy, what with the installer creating a new swap with each installation.

But when I'm iso-testing I try to wear my noob shoes and test every imaginable combination in hopes of finding any absolutely critical bugs.

During the last two rounds I've been doing some Ubuntu and Lubuntu testing, and also the Lubuntu alternate since she's the new kid on the block. So after the second day I'm always starting to get pretty fried. Note taking is an absolute must :)

---

