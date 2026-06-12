---
title: "The thread for Karmic Krashers"
date: 2010-01-21
forum: Recurring Discussions
---

### Post by k64 on 2010-01-21
If there's anything you hate about Ubuntu 9.10 Karmic Koala, here's the thread to talk about it. Say anything you want. Personally, I would say "If you have Karmic, upgrade to Lucid Alpha 2".

---

### Post by Icehuck on 2010-01-21
> **k64 said:**
> If there's anything you hate about Ubuntu 9.10 Karmic Koala, here's the thread to talk about it. Say anything you want. Personally, I would say "If you have Karmic, upgrade to Lucid Alpha 2".

Why would you recommend anyone upgrade to alpha software? There are people who don't know any better, and here you are trying to tell them to do something dumb.

---

### Post by XubuRoxMySox on 2010-01-21
Well, I might get called a troll for this, but...

**[COLOR="Navy"]There is no excuse IMO for putting experimental or Beta software by default in a brand-new release of any Linux distro that bills itself as "beginner friendly," as Ubuntu did in Karmic.[/COLOR]** PulseAudio for a glaring example. It's fine for "high risk" distros like Sidux where that bleeding edge stuff belongs and users *knowingly expect and accept* the risk (and the fun) of using untested stuff. Ubuntu is billed as being suitable for Linux beginners and "ordinary users." 

But the good news is that Ubuntu has a younger sibling, **[COLOR="Blue"]_X_ubuntu[/COLOR]**, which is developed separately and independently. Karmic Xubuntu does not ship with PulseAudio (nor with Mono, if that matters to you) nor other un-proven experimental stuff. **[COLOR="Navy"]Xubuntu is a very well-kept secret![/COLOR]** As beginner-friendly as Ubuntu is supposed to be, but flawless, fast, trouble free, and up-to-date.

My advice to "vanilla Ubuntu" users who are frustrated with Karmic and who feel left out or out of touch using an "older version:" Have a look at Ubuntu's little sister! It's delightfully simple, fast, and trouble-free.

-Robin

---

### Post by Techsnap on 2010-01-21
GRUB 2 was a huge mistake because for a lot of people it simply doesn't work. Fancy putting in a beta bootloader for a distro which is marketed as a "Beginner Friendly" one, do the devs who make these decisions have no sense!?

---

### Post by gradinaruvasile on 2010-01-21
> **dixiedancer said:**
> Well, I might get called a troll for this, but...

**[COLOR="Navy"]There is no excuse IMO for putting experimental or Beta software by default in a brand-new release of any Linux distro that bills itself as "beginner friendly," as Ubuntu did in Karmic.[/COLOR]** PulseAudio for a glaring example. It's fine for "high risk" distros like Sidux where that bleeding edge stuff belongs and users *knowingly expect and accept* the risk (and the fun) of using untested stuff. Ubuntu is billed as being suitable for Linux beginners and "ordinary users." 

But the good news is that Ubuntu has a younger sibling, **[COLOR="Blue"]_X_ubuntu[/COLOR]**, which is developed separately and independently. Karmic Xubuntu does not ship with PulseAudio (nor with Mono, if that matters to you) nor other un-proven experimental stuff. **[COLOR="Navy"]Xubuntu is a very well-kept secret![/COLOR]** As beginner-friendly as Ubuntu is supposed to be, but flawless, fast, trouble free, and up-to-date.

My advice to "vanilla Ubuntu" users who are frustrated with Karmic and who feel left out or out of touch using an "older version:" Have a look at Ubuntu's little sister! It's delightfully simple, fast, and trouble-free.

-Robin

Well Xubuntu is fast and stable. But the beginners out there will have some problems with it:

- Some programs dont show up in menus because of different menu structure - that, for a Windows backgrounded user is very bad. If you dont know about terminal'n'stuff youre toasted.
- It lacks some of Gnome's integrated features like click-on file  sharing, addressbar samba/ftp/whatever addressing etc.
- No working menu editor yet. 
- Share mounting/opening (via gvfs) did not work OOTB. i had to install a few packages to make it work.

These being said use Xubuntu 9.10 on a laptop and its way faster than Gnome. I had to create my own custom launchers for some programs and i had to install some packages to make share mounting work. I like its lower profile (and proven) default programs (Pidgin, Thunderbird etc) that are not integrated in the DE's core. 
But thats me, ive been using/messing with Ubuntu for 2 years - most people might find it lacking in features.

I also had to install PulseAudio because i use bluetooth handsfree - i had absolutely no sound problems in playing movies or listening music, flash sound playback.

---

### Post by ~sHyLoCk~ on 2010-01-21
Releasing karmic was a huge mistake. But oh well

---

### Post by Techsnap on 2010-01-21
This is my favorite on the Overview  :

> 
**ext4 by default**

  The new "ext4" filesystem is used by default for new installations with Ubuntu 9.10 RC; of course, other filesystems are still available via the manual partitioner. Existing filesystems will not be upgraded.   
  If you have full backups and are confident, you can upgrade an existing ext3 filesystem to ext4 by following directions in the [Ext4 Howto]("http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4"). (Note that the comments on that page at the time of writing about Ubuntu's use of vol_id vs. blkid are out of date and are not applicable to Ubuntu 9.10 RC.) Maximum performance will typically only be achieved on new filesystems, not on filesystems that have been upgraded from ext3. Then on the Release notes:

> **Possible corruption of large files with ext4 filesystem**

    
 There have been some reports of data corruption with fresh (not upgraded) ext4 file systems using the Ubuntu 9.10 kernel when writing to large files (over 512MB). The issue is under investigation, and if confirmed will be resolved in a post-release update. Users who routinely manipulate large files may want to consider using ext3 file systems until this issue is resolved. ([453579]("https://bugs.launchpad.net/bugs/453579"))  
So they switch the default FS to ext4 then counter argue doing that on the release notes because of the bug. Now a bug like that should have warranted them NOT switching to EXT4. But no that would be logical thinking. So the new user who doesn't have a clue what EXT is, will just use the defaults and be happy until their files could get corrupted. 

Then what? Do people explain to them "Well it's a new FS it has bugs". I'll tell you what they'll do, they'll go back to Windows because they never had this issue before and with something as serious as filesystem corruption I think that the decision to include by default was absolutely stupid and thoughtless.

---

### Post by Ylon on 2010-01-21
Differently from the common usage/release of new OS's product. Which each product is a separate entity (even if share the same kernel like in many Windows versions), Ubuntu born as a "unique flow" of the same product.

Innovation lead to instability.. but Ubuntu offer the option of "fully supported" previous stable version; _different_ stable version.

You can still install the 8.04LTS and have the last software, security update and even import some new shiny features from the next version.

You can choice between 8.10, 9.04 and 9.10.... is a pure and completly free choice: if your hardware manufacturer (providing with good linux driver) had allowed you to!

---

### Post by Techsnap on 2010-01-21
> You can still install the 8.04LTS and have the last software, security update and even import some new shiny features from the next version.

Oh I'm going to have fun explaining to my customers that they're going to have to use Backports to get their latest software or upgrade to the latest version of the OS. It's just not realistic.

---

### Post by Brandel Valico on 2010-01-21
I don't get the logic of threads like this. I was always told that the short term releases are testing releases. While the long term releases are meant to be the actual releases or Stable releases. 

It seems that more and more people are treating the short term releases like full and complete releases. Is this an actual change made by Ubuntu or is it simply that the users have gotten so used to the 6 month release cycle that they consider them full releases?

Don't misunderstand me I wait for that 6 month release also and love upgrading to the newest release usually around alpha 4 or 5 and messing with it. But I always keep in mind that only the long term releases should be considered full releases or Stable. So my server only upgrades between LTS releases. 

Karmic is not a LTS release it's a development release to test new features and get them settled before the next LTS incorporates them. 

Am I way off on this view of the releases?

---

### Post by Techsnap on 2010-01-21
> I was always told that the short term releases are testing releases.

No that's not true.

---

### Post by Zoot7 on 2010-01-21
> **dixiedancer said:**
> **[COLOR="Navy"]There is no excuse IMO for putting experimental or Beta software by default in a brand-new release of any Linux distro that bills itself as "beginner friendly," as Ubuntu did in Karmic.[/COLOR]** PulseAudio for a glaring example. It's fine for "high risk" distros like Sidux where that bleeding edge stuff belongs and users *knowingly expect and accept* the risk (and the fun) of using untested stuff. Ubuntu is billed as being suitable for Linux beginners and "ordinary users." 
This.

Karmic was the release that made me give up on Ubuntu totally.
One could overlook the forced inclusion of elements such as Pulseaudio were it a less popular distro with different goals, but the fact Ubuntu is touted as a replacement to Mac and Windows really makes it look laughable IMO.

---

### Post by tuddy666 on 2010-01-21
I like Karmic so far, but Pulseaudio and Grub 2 were pretty dumb moves. Both are in beta and both have problems on lots of computers.
Now, I like new, bleeding-edge technology as much as the next person, but I think that including a new, shiny thing just because it's new and shiny is pretty shoddy on Canonical's part. Now, I'm lucky enough to have both Pulse and Grub2 work just fine on all of my computers, but I've heard enough stories of people having one or the other not work "out of the box" to know that, for a "beginner's" distro that claims to work on a wide range of hardware, Karmic is doing just the opposite.

But, as I say, Karmic is brilliant -if- it works on your system.

---

