---
title: "No boot, no mouse, no keyboard. No hair."
date: 2012-12-03
forum: New to Ubuntu
---

### Post by Greenstar110 on 2012-12-03
Hi, sorry if this is basic, but am a computer dyslexic, which is why I use Ubuntu :)
This has occurred before, and my fix was a total reinstall, which took a couple of days with reinstalling software. That was a couple of months and a lot of configuring ago.
Now it has occurred again. 
I have 12.04, updated, with Gnome destop as cannot get on with Unity.. When I booted this morning the system went into GNU GRUB version 1.99-21ubuntu3.4 and continues to do so after several restarts.
I cannot interact with it as in that state I have no keyboard or mouse response.
I have tried  starting with the 12.04 CD, all starts up fine, and can look at the files. With the live CD I do have mouse and keyboard, but I can't find a rescue facility.
Please, how do i get my sytem back? That is, without this reccurring glitch.
Fortunately all my files are backed up on my Mac, which i am using now, and has worked without glitches for several years during which several linux versions have died.
Why don't I stay with Macs? Linux has fantastic opensource software, when it works, and a helpful community, which it needs.
Thanks folks.

---

### Post by oldfred on 2012-12-03
When I had mouse & keyboard issues several years ago with my new system it was a setting in BIOS. And if you happened to refresh BIOS it resets to defaults. My default setting is USB mouse & keyboard is off and only the ps/2 ports work.

You can also export a list of all installed applications to make it easier to reinstall next time.

       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

---

### Post by audiomick on 2012-12-03
> **Greenstar110 said:**
> ... the system went into GNU GRUB version 1.99-21ubuntu3.4 and continues to do so after several restarts.
I cannot interact with it as in that state I have no keyboard or mouse response....

So your problem is actually that your system is not booting correctly, right? And this is compounded by your keyboard and mouse not working until that system is up?

As far as the mouse goes, I had the same thought that oldfred has already mentioned: look in your BIOS for settings relevant to USB support during boot. On mine, I think it is called "usb legacy support" or something similar. Alternatly, if you have a ps2 keyboard and mouse, they should always work. I have one of each that I am keeping for now for exactly that reason.

As far as your boot goes, you might like to look at this
[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")
At the very least, run the boot info script as descibed there and post the link to where it lands here. That will help people analyse your boot problem.

As far as the lack of hair goes, I don't think there are any genuine cures for that at all, but I can sell you a really expensive lotion if you like... ;)

---

### Post by squakie on 2012-12-03
> **audiomick said:**
> ....
As far as the lack of hair goes, I don't think there are any genuine cures for that at all, but I can sell you a really expensive lotion if you like... ;)

I like that!  I thought that it was great to see someone open a thread with a title that at least shows they have some humor in the situation, instead of the typical "I need help", "my wireless doesn't work" or even better "why won't my Windows program run?".

And +1 on the legacy USB support - that was the first thing that went through my mind.

---

### Post by Greenstar110 on 2012-12-04
Thanks folks. Yes, humour is required. Still some hair loss, but what's gone is gone.
I booted just now and found 'disc boot failure', no grub, and with the live CD the HD wasn't found. I guess that's it, a flakey hard drive. Thanks for the info re re-installation. It's a rainy day, but the DWP are onto me and I must do my job search - and this old mac is slow now. Could a failing HD prevent boot up? I am wondering why I even got grub to boot. OR, could something have knackered my instalation?
Biggest loss are all my bookmarks on Firefox, many, many hours of browsing. I am wondering if there is some way of archiving them. I used to just copy into a text file, but have been lazy, and have used FEBE, but had trouble getting it to run in 12.04.
Thanks helpful people.
ps, am downloading boot repair (CD). For some reason, it's a 4hr download (339Mb/!) I can't tell if it's on the 12.04 CD I have - be a valuable addition.

---

### Post by Greenstar110 on 2012-12-04
Download for Boot repair ran at second attempt. Ran this on my Ub PC. Fixed it! Fortunately it activated the standard first menu item after a short delay, so my mouse/keyboard issue was sidestepped. My system boots up now, nothing lost. 

I am both impressed and unimpressed. Firstly, thanks for the help, without which I would have probably scrapped the hard drive. The rescue CD worked well. Magic. 

Ok, so why was it necessary? What broke? It's  a pretty serious flaw,  if your whole ship goes down every few months!  I wouldn't trust any files to it. I do back up, but there are problems with bookmarks, for example. I have Dropbox and ALL my current files go there, and hence to my Mac and it's external drive. That doesn't go down every few months. Sorry, but Linux has it's glitches.

I  have [http://paste2.org/p/2560803](http://paste2.org/p/2560803) if this helps. How can I avoid it breaking again? 
It would be great if this rescue disc was part of the Ubuntu release. Maybe it is now.   

Thanks again,
Tony, slightly less hairy.

---

### Post by oldfred on 2012-12-04
You can easily add the PPA for Boot-Repair and run the two update commands to add it to any liveCD or USB. Of course with  a CD or DVD it is not saved.

Quick review of BootInfo report does not show any major issues.

I prefer to separate data from system. Will not make it any more reliable and if hard drive fails it still fails then backups are the only recourse. But then I can reinstall and still have my data. You can either have a separate /home or a bit more advanced separate data partition. I move some of the hidden  folders like Thunderbird & Firefox into my data partitions so they also are separate. Not sure if the links I use to make system think folders are still in /home would work with dropbox.

---

### Post by Greenstar110 on 2012-12-04
Thanks Fred ... you must be on night shift in Chicago? :KS
Is it possible to set up a separate data partition now I have it all installed?  All the Firefox stuff gets lost each time I have to reinstall, and I have many many bookmarks. I am a bit wobbley with partitioning ... I've screwed everything up in the past, not the last time I expect!

---

### Post by DuckHook on 2012-12-04
Listen to wise *oldfred*. You won't go wrong. I used to set up a separate /home partition until he recently set me on the right path with the separate /data partition. This allows you to truly multiboot and attach only the generic data, without inheriting inappropriate config files that aren't appropriate across different distros. Very smart, very neat, very tidy.

The first rule to monkeying around with partitions is *back up*. If something then goes wrong, you are merely inconvenienced. Might even solve some system problems with a clean virgin install.

In your case, I'm just picking up some bad warning signs: "old Mac", history of disappearing apps and functions, numerous lost boots, etc. It could be that your HDD is reaching end-of-life. My advice would be to replace it and use this opportunity to partition exactly the way you want before installing a new system. You would still have the old HDD to fall back on plus your backup. Since HDDs are so absurdly cheap these days, this would seem to be your best course right now.

---

### Post by audiomick on 2012-12-04
> **DuckHook said:**
> Listen to wise *oldfred*...In your case, I'm just picking up some bad warning signs: "old Mac", history of disappearing apps and functions, numerous lost boots, etc. It could be that your HDD is reaching end-of-life. My advice would be to replace it and use this opportunity ...


That sounds like solid advice to me. If you can't replace it, you might consider an external drive for backing up to, although from one of your posts it seems you have a pretty good backup strategy already. 

As far as your bookmarks go, you could save the hidden folder .mozilla out of you /home/user folder. I think someone mentioned that already, didn't they? If you put that in the /home/user folder of a new install, firefox should come up the way you had it set up in the install it was saved from.

 Also, in my firefox in the bookmarks menu there is an entry "show all bookmarks" that opens a library of the bookmarks where you can fool around with the menus and whatnot. The key combination ctrl+shift+O opens it as well. In there, there is a menu that is called "import and save", or maybe "import and backup". In mine, it is "importieren und sichern". ;) Anyway, in there, there is an option to backup your bookmarks. I haven't tried this, but I expect it works.

---

### Post by oldfred on 2012-12-04
I got started on a separate data partition with my first install and trying to learn Ubuntu. We were XP. So I am learning how to do things in Ubuntu and my lovely spouse wanted to check email or go on Internet which was XP. So reboot and XP boot is slow and fustrating.
So I found you can move Firefox & Thunderbird into a shared NTFS data partition and then we had the same bookmarks and emails in both systems. Much less booting into Windows. One application kept me from shutting it down until this year.
I now have all new data going into a Linux formatted partition, but have not converted from my older NTFS shared partition yet. 
I also copy my entire FF & TB profiles to my laptop when travelling and back them up after housecleaning.

 I jsut saw audiomick's post. Firefox used have a file with book marks in HTML or text that you could easily save and use. But now for last several years it is in sqlite and you do have to separately save bookmarks to extract from the db. I prefer to save entire profile, but that is a lot larger.

---

### Post by Greenstar110 on 2012-12-31
There is still a problem with my installation. I need still to explore the options suggested here, for FF and TB back up, but meanwhile I have had the same problem booting up. various things happen. Firstly, I had two gersions of grub appear, one text only. Then I would find that nothing booted, initially the HD was detected but no boot, so ran disc rescue again. [http://paste2.org/p/2651121](http://paste2.org/p/2651121). All seemed ok again. A few days later, similar behavour, this time with no HD detected.  I thought my disc must have failed, but no, ran rescue again, and [http://paste2.org/p/2674601](http://paste2.org/p/2674601), and now has booted without any problem.

I need obviously to fix this: might there be a hardware problem, or is there just something going on with my install that makes it better to start again? Between failures I have run Bleachbit. Given Ubuntu has misbehaved in successive installs, I am wondering whether to change versions. Again. Days of configuration and intalling. Again.

---

### Post by audiomick on 2012-12-31
> **Greenstar110 said:**
> ...I need obviously to fix this: might there be a hardware problem,...

It is starting to sound a bit like a hardware problem. The possibility of a flaky HDD has already been mentioned, I think. Have you already had the suggestion to look at the SMART values of the drive? They are values that the drive stores about itself that can indicate problems. 

Open the diskdrive administration utility in Ubuntu and look for a button to the right if the window after you have selected the drive. Here, I'll put on a screenshot. It is in German, but you can see where the mouse is pointing. Have a look at what that says about your drive.

I also had another thing on this machine. About every couple of months, it would start having trouble finding the drive at boot. I "fixed" it a number of times by unplugging and re-plugging the SATA cable to the drive, and the problem went away completely when I finally just change the cable for a new one. Don't forget about those sort of possibilities...

---

### Post by Greenstar110 on 2013-01-03
Hi Michael, thanks, had to scratch to find 'disc administration tool', turned out to be 'Disc Utility' :p Sorry, have to work things out each time. It says ...

Spin up Good, Start/Stop n/a, reallocated sector Good, Read Channel Good, Error rate, n/a, Timer Good, a long list of things either good or n/a. Overall, 'Passed' and 'Disc is Healthy'. 

So looks ok. Of course this is when it HAS booted. This happens 50% of the time. :icon_frown: At the moment. 
All thoughts very welcome!

---

### Post by audiomick on 2013-01-03
> **Greenstar110 said:**
> Hi Michael, thanks, had to scratch to find 'disc administration tool', turned out to be 'Disc Utility' :p

My fault. My machines speak German, and I don't know what half of the stuff is called exactly in English... ;)

> 
Spin up Good, Start/Stop n/a, reallocated sector Good, Read Channel Good, Error rate, n/a, Timer Good, a long list of things either good or n/a. Overall, 'Passed' and 'Disc is Healthy'. 

So looks ok. Of course this is when it HAS booted.

This looks good. Those are values that the Drive registers about itself. There is an option there somewhere to make it have a fresh look at itself. Did you do that, to make sure the values are current? Assuming that, good news. Your drive is probably not failing. 

The next thing I would do is physically disconnect the drive and reconnect it. I think I already mentioned I had problems where the physical connection was at fault, and the behaviour was similar to what you describe, Pulling the plug and putting it back might clean contacts, should reseat the connection (even if only temporarily) or perhaps, if a connector is about to fail, break the connection altogether. 

If nothing changes, that possibility can be ticked off. If things stop altogether, change the cable for a start. If you're really lucky, things might improve.

---

