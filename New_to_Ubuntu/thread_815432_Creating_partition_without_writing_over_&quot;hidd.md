---
title: "Creating partition without writing over &quot;hidden&quot; recovery partition"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by archer6 on 2008-06-01
I'm about to install Ubuntu 8.04 as dual boot on the same drive as XP Pro is on, along with a "hidden" recovery partition on my ThinkPad. The recovery partition is there to restore windows, instead of having to use recovery discs. I want to retain that partition and not overwrite it while partitioning the HD.

My question is when I get to the screen shown below, which presently only shows 2 partitions (as an example), will it also show the "hidden" partition when I use it, so I can keep it and not overwrite it while partitioning the HD?  Thanks!
[IMG]http://www.psychocats.net/ubuntu/images/installinghardyplus10.png[/IMG]

---

### Post by ibuclaw on 2008-06-01
[EDIT]
Oops. that above picture is an example. :)

If you fear that your Windows XP restore partition may be lost, you may have to go and manually partition the drive.

Although, in the minor circumstances that things may go wrong. I will suggest that you may want to install ubuntu on a separate drive, if at all possible.

Regards
Iain

---

### Post by quelx on 2008-06-01
Yes, it may show up as **Hidden W95 FAT16** or some such, just don't delete the last partition, that is generaly the recovery partition on thinkpads.

if nothing else READ THIS :)
[http://www.thinkwiki.org/wiki/Hidden_Protected_Area](http://www.thinkwiki.org/wiki/Hidden_Protected_Area)

[http://forums.lenovo.com/lnv/board/message?board.id=T_Series_Thinkpads&thread.id=306](http://forums.lenovo.com/lnv/board/message?board.id=T_Series_Thinkpads&thread.id=306)

---

### Post by archer6 on 2008-06-01
> **tinivole said:**
> What does option 3 (use largest continuous space) present you with?

If you fear that your Windows XP restore partition may be lost, you may have to go and manually partition the drive.

Although, with the little amount of harddisk space that you have. I will suggest that you may want to install ubuntu on a separate drive, if at all possible.

Thanks for your fast response. That picture above is not mine, I grabbed it off the web. I have a 100GB drive. I'm preparing in advance to do this, and learning all I can beforehand. 

My Ubuntu 8.04 live CD will not be here until Tuesday, therefore I don't know what it will look like. So I'm asking the question, as I was wondering if the partition tool on the disc would show my rescue partition (about 5GB). I just did not want to get to that point, and not know what to do. 

Ideas?

---

### Post by sayakb on 2008-06-01
If you use Guided partitioning + Resize, you will not lose any partition. The largest partition shall be resized and Ubuntu will be installed in the free space so created.

---

### Post by archer6 on 2008-06-01
> **LinuxIsInnovation said:**
> If you use Guided partitioning + Resize, you will not lose any partition. The largest partition shall be resized and Ubuntu will be installed in the free space so created.

Terrific! 

Then to answer the question you may be asking yourself, didn't I just help this guy with a dual boot question for two drives?

Yes, you were kind enough to help me earlier with a question regarding setting up _another one_ of the four ThinkPads in my family as a dual boot, but with two hard drives.....:)

So my point is: 

#1) Thanks very much for the help. 

#2) Yes, I'm diving in and converting all of our computers to Ubuntu in the next few days, and thankfully they are all similar ThinkPads......;)

Cheers!

---

### Post by sayakb on 2008-06-01
Make sure you remove Windows only when you don't need it anymore :)
Now, since a year, I myself don't seem to need Windows at all. Maybe because my laptops and desktops are perfectly supported by Hardy :D

---

### Post by archer6 on 2008-06-01
> **quelx said:**
> Yes, it may show up as **Hidden W95 FAT16** or some such, just don't delete the last partition, that is generaly the recovery partition on thinkpads.

if nothing else READ THIS :)
[http://www.thinkwiki.org/wiki/Hidden_Protected_Area](http://www.thinkwiki.org/wiki/Hidden_Protected_Area)

[http://forums.lenovo.com/lnv/board/message?board.id=T_Series_Thinkpads&thread.id=306](http://forums.lenovo.com/lnv/board/message?board.id=T_Series_Thinkpads&thread.id=306)

Thanks for the links, I'm a voracious reader and I'm very thirsty for all the knowledge I can acquire about Ubuntu. My goal is to progress from my present level, ground zero - total dummy, to whoot.... I found the keyboard....:)

Cheers!

---

### Post by archer6 on 2008-06-01
> **LinuxIsInnovation said:**
> Make sure you remove Windows only when you don't need it anymore :)
Now, since a year, I myself don't seem to need Windows at all. Maybe because my laptops and desktops are perfectly supported by Hardy :D

Wow.... your a mind reader too!

Yes, I'm very eager to reach that point. I haven't been this exited  in a long time. I've been entertaining Linux for a few months, but had no time to deal with it. Now I do, did some more reading, found Ubuntu and I'm enjoying every minute of it. 

And it just keeps getting better, as I found this great forum and then this morning a member here pointed out that my main program I use every day for work _ Maya _ is available in a Linux version, something that I didn't expect, therefore I didn't know about it. 

Cheers!

---

### Post by sayakb on 2008-06-01
Well, then just four words for you: Get rid of Windows :lolflag:

---

### Post by archer6 on 2008-06-01
> **LinuxIsInnovation said:**
> Well, then just four words for you: Get rid of Windows :lolflag:

Heh! The best laugh I've enjoyed all day! :lolflag:

---

