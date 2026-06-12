---
title: "upgrade to 14.04"
date: 2014-08-11
forum: New to Ubuntu
---

### Post by fotoflex on 2014-08-11
I was invited today to upgrade to 14.04.
As I'm only starting to understand how Xubuntu works, I'm not sure how to proceed.
And having searched this forum about any problems, I saw 'no desktop', 'won't boot', etc, etc.
All things I wouldn't be able to solve, not even with instructions.
I'm also afraid all settings and files I have on my desktop and not on my external HDD will disappear.
Can't I just continue using my 'old' Xubuntu?

---

### Post by Dennis N on 2014-08-12
> Can't I just continue using my 'old' Xubuntu? 
Yes, if it's 12.04:
> Xubuntu 12.04 is a Long Term Support release and will be supported for three years. This contrasts with Edubuntu, Kubuntu and Ubuntu 12.04 which, while also LTS releases, will all be supported for five years.
--Wikipedia.
After that three years, Xubuntu 12.04 would still receive any updates to packages in common with Ubuntu. That would likely include most if not all security updates.

---

### Post by amanchesterman on 2014-08-12
It rather depends on how old your 'old' Xubuntu is. The 12.04 release has LTS (= Long Term Support) and is maintained with updates etc. for three years, i.e. until 2015. The 14.04 release also has LTS and will therefore be maintained until 2017. Those are the only two versions currently supported, so far as I'm aware. If you are using an unsupported version, then you are not receiving security fixes and operational improvements, and that is not recommended.
Whether you are intending to upgrade or not, you should have all your files etc. backed up on separate media.
Personally I have my computer set up with a separate /home partition (which I also keep backed up). That way, it's a relatively simple job to upgrade the OS itself while keeping all my files and settings intact.
Also, as a personal preference, I don't use the 'upgrade' option: I tried it once, years ago, and got into difficulties. Instead I do a fresh install, which I have read is more reliable. The last time it took me about half an hour, plus a bit more time to customise the new version to my liking, so it's not a big job.

---

### Post by fotoflex on 2014-08-12
Thanks very much!
Yes, I'm using 12.04, (I choose that because of the LTS) for about a year now.
My laptop's harddisk gave up the ghost and I could not re-install Vista,
so I had no choice, really, but to install Ubuntu.
All files were on external HHD's, but the new disk for the laptop was much bigger than the old one,
and with the new OS I had to get used to, a lot of what I installed and saved went straight to desktop, so I could see what happened.
But now I see it's time to clean up the system, save what must be saved, and after that do the upgrade, no pressure. :)
I will look into that Home partition, is it possible to move that to the new OS, and would that keep the settings?

---

### Post by mörgæs on 2014-08-12
You can install a separate /home in the present system but if you are new to Xubuntu I suggest that you wait until you some day install 14.04 (as opposed to upgrade).

---

### Post by 3rdalbum on 2014-08-12
> **fotoflex said:**
> I was invited today to upgrade to 14.04.
As I'm only starting to understand how Xubuntu works, I'm not sure how to proceed.
And having searched this forum about any problems, I saw 'no desktop', 'won't boot', etc, etc.
All things I wouldn't be able to solve, not even with instructions.
I'm also afraid all settings and files I have on my desktop and not on my external HDD will disappear.
Can't I just continue using my 'old' Xubuntu?

You can continue to use 12.04 if you want, but Xubuntu 12.04 is only supported until April 2015 so you would need to upgrade before then.

Don't worry about the threads you have seen with problems. Nobody posts to a support forum saying that they have no problems! They just enjoy their trouble free system :-)

There have been SIGNIFICANTLY fewer reports of problems with 14.04 than with earlier versions. Even 12.04 was regarded as a buggier release than 14.04. So don't worry too much.

If you do the upgrade offered to you, your files and settings will be saved. The operating system is upgraded "around" your files and you won't lose data. However there is a bit more risk associated with this sort of upgrade depending on what modifications you have made to your 12.04.

I recommend instead burning a 14.04 DVD and booting it. Run the installer and choose "Something Else" from the screen that asks how you want to install. Click your current Ubuntu partition and click "Edit Partition". From the mount-point menu, choose "/". Click OK. If you have a /home partition, click it and do the same except set the mount point to "/home". Do not format any partitions. Click Forward and answer " continue" to the next question that appears on screen.

This will preserve your home folder, settings and files, and reinstall mostly the same programs you had before. The new version of Ubuntu will be a fresh install and less risky than doing the upgrade method you were offered.

---

### Post by fotoflex on 2014-08-12
Thanks.
I think I'll continue saving everything to the external HD, and after that try to upgrade the way 3rdalbum suggests.
If that does not save my settings the way I expected, I can still choose for an entirely fresh install of 14.04.
I remember the 12.04 install taking hardly any time, especially because I was used to Vista-install,
 which was akin to copying the telephone book on stone tablets.
Whit a dull chisel. 
I may need some help, though. I do understand some English, but I don't speak Computer at all.
"[COLOR=#000000]the mount-point menu"? :confused:
Okay if I post here again when the time comes?[/COLOR]

---

### Post by amanchesterman on 2014-08-12
When I started with Xubuntu a few years back I didn't have a separate /home partition, the whole installation was in one partition on the disk.
Then I found and followed the tutorial [here]("http://psychocats.net/ubuntu/separatehome"). It's written for Ubuntu but it seemed to apply to Xubuntu without any problem. It made it much easier, I found, to re-install Xubuntu, and to try out other distros as well, while keeping all my documents etc. intact in /home.
There's still a need of course to keep backup copies of your files, and I'd certainly advise backing up everything before you try changing or creating partitions.
If you do it, then remember **not** to reformat your /home partition when you install new versions in future, otherwise you will lose everything of course.
And yes of course you can come back here for more advice at any time.

---

### Post by fotoflex on 2015-01-07
Well, two days ago I finally tried to use the upgrade-button.
Sadly that did not work. At all.
System collaps.
So I ran Xubuntu 12.04 from the live CD.
Normally, I could have downloaded 14.04 and burned a new start-up CD,
but as I was using the player to run my laptop on, that was not an option.
The only other option was to re-install 12.04 and try to upgrade again.
Took me most of the day and lots and lots of things couldn be installed.
I started writing it down, but had to give up.
Anyway, the system ran and I used Update Manager and that seemed to install these things,
so everything was fine.
Yesterday I installed some of the programs I had used earlier and did indeed rip a DVD and converted it.
Later in the evening the laptop became unresponsive.
Did not react on double-clicking, but on some occasions it did when I pressed Ctrl OR the right-click button with it at the same time.
Sometimes I had to navigate with the arrow buttons.
All very confusing, to say the least.
Navigation in the browser seems normal.
I tried several re-boots that didn't change anything and there were pop-ups telling me that Ubuntuhad had an internal error, would I like to send a report?
The (lack of) navigation made that impossible, really, neither could I copy what was written in the Details.
I had copied the Home file to an external HDD before, making sure that all important files were in there and safe.
Concluding: as the system is brand new and I have done little moderation, this is a good time to decide to re-install 4.04, 12.04 or fix the system.
Any suggestions, questions or advice?

Thanks in advance

---

### Post by mörgæs on 2015-01-08
Yes, a clean install of 14.04.1 is the way to go.

---

### Post by fotoflex on 2015-01-08
Thank you.
I realized I could now burn a 14.04 live cd.
Not all that easy, though, without a right-click menu!
But I managed it and now 14.04 is running.
Just hope it keeps on running this time.

---

### Post by fotoflex on 2015-01-08
Thank you.
Once I realised I could now burn a CD, things went quite well.
Well, that is considering the fact I had no right-click menu.
That took some working round and didn´t exactly speed up the process.
The system is now running and I hope it will continue to do so.

---

### Post by mörgæs on 2015-01-09
Good, please mark the thread 'solved'.

---

