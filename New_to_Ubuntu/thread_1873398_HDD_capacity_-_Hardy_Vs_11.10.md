---
title: "HDD capacity - Hardy Vs 11.10"
date: 2011-11-01
forum: New to Ubuntu
---

### Post by oxmanik on 2011-11-01
Hi i recently bought a new hard disk (500Gb), as my previous one was too small (60Gb).
I was using Hardy  before and after receiving the new hard drive i installed the 11.10 version on it.
It's been just a few hours, the new version looks quiet nice, but I’m disappointed with one thing.
Maybe it's just ignorance, or a naive expectation... anyway here it goes.

On my previous OS, Hardy, i had a 60Gb HDD, and a filesystem capacity of 106GB.

This was really nice as 60Gb is not much at all.
I have to say that i never understood how it was possible, How can you write 106Gb on a 60Gb HDD.

I presumed it had something to do with the way Linux manages the filesystem.

So when i bought the new HDD 500GB, i was Quite excited and curious to know what the filesystem capacity would be.

After installing and exploring the new 11.10 version, i found out that the filesystem capacity was within the HDD capacity (496Gb), i was expecting the filesystem would have a bigger capacity as it was before with Hardy.

Can anyone explain me Why?
How was Hardy able to extend the HDD capacity to nearly twice it's size and the new 11.10 version can't?

Thanks in advance, waiting for some light on the matter.

---

### Post by mcduck on 2011-11-01
Hardy definitely wasn't able to extend your filesystem capability anywhere beyond the real capacity.

I'd assume that either you actually had some other drives connected (depending on the tool you use to check this, the filesystem capacity might either mean the whole filesystem, including all mounted drives, or just a single partition's capacity) or the false capacity you saw was a result from some bug causing the program you used to miscalculate the value.

Trying to actually write 106GB worth of data into your 60GB hard drive would definitely have resulted in either error report or loss of the exceeding data.

---

### Post by oxmanik on 2011-11-01
> **mcduck said:**
> Hardy definitely wasn't able to extend your filesystem capability anywhere beyond the real capacity.

I'd assume that either you actually had some other drives connected (depending on the tool you use to check this, the filesystem capacity might either mean the whole filesystem, including all mounted drives, or just a single partition's capacity) or the false capacity you saw was a result from some bug causing the program you used to miscalculate the value.

Trying to actually write 106GB worth of data into your 60GB hard drive would definitely have resulted in either error report or loss of the exceeding data.


No other drives connected, the disk usage analyzer gave me that info.
Plus it was like that all the time, i had at least two hardy installations and on bought it was like that.
I'll reconet my hard drive and will provide some screen shots.

---

### Post by mcduck on 2011-11-01
> **oxmanik said:**
> No other drives connected, the disk usage analyzer gave me that info.
Plus it was like that all the time, i had at least two hardy installations and on bought it was like that.
I'll reconet my hard drive and will provide some screen shots.

If you reconnect it, you could at the same time provide output from running "sudo fdisk -l" and "df -h" in a terminal, just to see what those tools report as the size.

Anyway, the disc usage analyzer is only really useful for checking *where* disc space is being used, not for how much space you have or how much of it is in use.

It will, by default, scan all filesystems instead of a single drive, and also has some known bugs related for things like gvfs which might make it count the space twice for things like encrypted directories network locations etc.

I can assure you that there is no tool in Hardy that would magically allow you to write more data to a drive. Would be pretty nice if such thing existed, though... :)

---

### Post by oxmanik on 2011-11-01
> **mcduck said:**
> If you reconnect it, you could at the same time provide output from running "sudo fdisk -l" and "df -h" in a terminal, just to see what those tools report as the size.

Anyway, the disc usage analyser is only really useful for checking *where* disc space is being used, not for how much space you have or how much of it is in use.

It will, by default, scan all filesystems instead of a single drive, and also has some known bugs related for things like gvfs which might make it count the space twice for things like encrypted directories network locations etc.

I can assure you that there is no tool in Hardy that would magically allow you to write more data to a drive. Would be pretty nice if such thing existed, though... :)


I think you're write, check the screen shot.
There was a bug on the disc usage analyzer, for shure.
Disc size 54Gb used 50Gb. Why i haven't check this? :-\"

---

### Post by oxmanik on 2011-11-01
Moral of the story, there's no such thing as magic...:oops:

I'll just have to get used to ubuntu's new look and tune it as i go along.

Thanks [mcduck ]("http://ubuntuforums.org/member.php?u=17309"):wink: and if you have any usefull tips for starting with 11.10 feel free to share.

---

### Post by arpanaut on 2011-11-01
For tips and getting started with using Unity try:

[http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity](http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity)

Lots of useful links and info there.

---

### Post by mcduck on 2011-11-01
> **oxmanik said:**
> Moral of the story, there's no such thing as magic...:oops:

I'll just have to get used to ubuntu's new look and tune it as i go along.

Thanks [mcduck ]("http://ubuntuforums.org/member.php?u=17309"):wink: and if you have any usefull tips for starting with 11.10 feel free to share.

Yeah, it seems it was indeed counting the virtual filesystem in ~/.gvfs into your disc size.

Useful tips for 11.10? That's quite open-ended question. :D
Anyway, install [gnome-tweak-tool]("apt:gnome-tweak-tool") to be able to change your themes, fonts and some other settings missing by default from Gnome 3, and learn to use the Super button with Unity (super+number to quickly open programs from the launcher, super+s for workspaces, and f course super+any words to search for your applications and files in Dash).

---

