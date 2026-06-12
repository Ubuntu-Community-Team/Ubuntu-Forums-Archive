---
title: "changing column width in Nautilus when &quot;view as list&quot;"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by gerben1 on 2008-05-25
When I set Nautilus to view the folder contents as a list, changing the column widths is very difficult. I hope this is just some setting.

My columns are:

Name | Size | Type | Date Modified

and this is how it resizing the widths works for me at the moment:
- trying to move the "|" between Name and Size, does not work, won't move
- trying to move the "|" between Size and Type, adjusts the position of the "|" between Name and Size
- trying to move the "|" between Type and Date modified, adjusts the position of the "|" between Name and Size and the "|" between Size and Type

Here is a screenshot showing what happens:
[[IMG]http://img93.imageshack.us/img93/1752/columnwidthchangelm1.th.jpg[/IMG]](http://img93.imageshack.us/my.php?image=columnwidthchangelm1.jpg)

---

### Post by paul.matthijsse on 2008-05-26
Hello, I just noticed this same behavior as of today, apparantly something wrong somewhere. Can't figure out what though...

---

### Post by gerben1 on 2008-05-26
I wonder if everybody has this, or whether it is just some people

---

### Post by paul.matthijsse on 2008-05-26
> **gerben1 said:**
> I wonder if everybody has this, or whether it is just some peopleApparently only the two of us! 

I noticed another thing as well since yesterday morning, perhaps related. When I transfer files from my photo card (sd), Nautilus changes the date of the photo (the moment of creation) to the date of transferring the photo to the pc. In exif viewers the original date is still shown, but not in Nautilus. 

As an amateur photographer this disturbs me, because I can't see any more in Nautilus if the photos were taken a month ago or three days ago... Never saw this behavior before, so I guess it's a bug (but a nasty one for me). 

I tried changing date settings in Nautilus (gconf-edit) to date_accessed, date_modified and another one, but something like date_creation is not available. Changing settings doesn't work. I am a bit lost here, as I really need to see the creation date...

Edit. This date problem exists on a French and a Dutch Ubuntu with Hardy Heron with all the updates.

---

### Post by gerben1 on 2008-05-27
Hmm, I do not have that problem, "Date modified" works fine here, it show the date that the picture was taken, exactly the same as in the exif data.

---

### Post by philinux on 2008-05-27
I gave up with nautilus to copy files from my old pc to new ans the timestamp of my pics were all lost. 

I used this instead.

cp -R --preserve=timestamp folder1 folder2

I haven't tried gthumb yet.

---

### Post by nick_h on 2008-05-27
I can reproduce this problem.

You should report it as a bug - [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

---

### Post by philinux on 2008-05-27
Done

---

### Post by paul.matthijsse on 2008-05-27
> **philinux said:**
> cp -R --preserve=timestamp folder1 folder2Works! Thank you very much because I really need to see the correct timestamps (that is: creation time) of my photos, as I have over 20.000 of them! 

Cheers, Paul.

---

### Post by philinux on 2008-05-27
Bug 215499 was already there.

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/215499](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/215499)

Install gnome-commander for now for a gui. It appears in accessories menu.

---

### Post by nick_h on 2008-05-27
> Bug 215499 was already there.

I can't find any bug relating to the problem that the OP posted about though.

---

### Post by philinux on 2008-05-27
> **gerben1 said:**
> When I set Nautilus to view the folder contents as a list, changing the column widths is very difficult. I hope this is just some setting.

My columns are:

Name | Size | Type | Date Modified

and this is how it resizing the widths works for me at the moment:
- trying to move the "|" between Name and Size, does not work, won't move
- trying to move the "|" between Size and Type, adjusts the position of the "|" between Name and Size
- trying to move the "|" between Type and Date modified, adjusts the position of the "|" between Name and Size and the "|" between Size and Type

Here is a screenshot showing what happens:
[[IMG]http://img93.imageshack.us/img93/1752/columnwidthchangelm1.th.jpg[/IMG]](http://img93.imageshack.us/my.php?image=columnwidthchangelm1.jpg)

You have to mouse the mouse the opposite way to what comes natural. Very odd.

---

### Post by gerben1 on 2008-05-28
> **nick_h said:**
> I can't find any bug relating to the problem that the OP posted about though.

I just reported it:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/235449](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/235449)

> **philinux said:**
> You have to mouse the mouse the opposite way to what comes natural. Very odd.

Yes, and it also does not move the "divider" that you grab but the ones to the left of it.

With these columns:

Name | Size | Type | Date Modified

if you grab the divider between Type and Date and move the mouse, that divider will not move, but the other two dividers (i.e. the one between Name and Size and the one between Size and Type) will move, but opposite to the direction in which you move your mouse.

---

### Post by gerben1 on 2008-05-28
Apparently this bug was already reported in 2005:
[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/25940](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/25940)

---

### Post by philinux on 2008-05-28
They fixed it in Feisty but now it's back.

New users coming from windows hate this kind of niggle.

---

### Post by nick_h on 2008-05-28
Although it is a GTK bug other applications such as Rhythmbox seem to use better settings.  It is a pity that someone couldn't have a look at improving it in nautilus.

I expect they class this sort of bug as low priority.

---

### Post by gerben1 on 2008-05-28
Yes, from reading the responses in that long thread, it looks like they see this as something which is just not working "ideal" but does the job so it's not that bad. Apparently this behavior is natural seen from the way they coded it, but seriously the "normal users" will not find this reasonable. 

To the user it will probably seem very obvious that you should be able to drag the borders between columns to adjust the size of the neighbouring columns. I cannot understand that this is seen as a low priority issue. People new to ubuntu that notice this will immediately think that something is broken, and won't trust their system to be a good, proper, stable install...

---

### Post by paul.matthijsse on 2008-05-28
> **philinux said:**
> Bug 215499 was already there.

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/215499](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/215499)

Install gnome-commander for now for a gui. It appears in accessories menu.Thanks again philinux, gnome-commander indeed preserves the timestamps while copying files from a sd-card to the pc. 

Side note. I copied the photos that were transferred to my pc with gnome-commander (so with the correct timestamps) via a sftp connection to another pc on my lan, as a backup. Same problem appeared; timestamps on the remote pc were those of the moment of copying. 

Then I tried Krusader (that has a nice option 'sync dirs') -- same wrong story... 

Only rsync did the job as expected. 

Perhaps you say; use gnome-commander also for synching dirs to a remote machine, but it always says something like "ftp service not available". Apparently some port is not open (ftp is #21 isn't it? Have to take a closer look at that...).

Thanks anyway for your time.

Cheers, Paul.

---

### Post by Pipps on 2008-07-07
> **gerben1 said:**
> Yes, from reading the responses in that long thread, it looks like they see this as something which is just not working "ideal" but does the job so it's not that bad. Apparently this behavior is natural seen from the way they coded it, but seriously the "normal users" will not find this reasonable. 

To the user it will probably seem very obvious that you should be able to drag the borders between columns to adjust the size of the neighbouring columns. I cannot understand that this is seen as a low priority issue. People new to ubuntu that notice this will immediately think that something is broken, and won't trust their system to be a good, proper, stable install...
I am also finding this to be a really irritating niggle.

Is there any way to resolve this yet?

---

### Post by gerben1 on 2008-07-07
someone is looking at it again, hopefully he'll be able to solve it, see the last post here:
[http://bugzilla.gnome.org/show_bug.cgi?id=316087](http://bugzilla.gnome.org/show_bug.cgi?id=316087)

---

