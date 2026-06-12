---
title: "Change from swap partition to swap file?"
date: 2013-05-30
forum: New to Ubuntu
---

### Post by AnnB on 2013-05-30
Hello!

My daughter has a newer PC which came with Windows 8.  I installed Ubuntu 12.10, so her 1TB HD now has its limit of 4 partitions: 2 for Windows and 2 for Ubuntu.  Windows recently stopped allowing her to install anything - even Windows updates from Microsoft, so after numerous virus scans and other tweaks, we gave up and reinstalled Windows from the copy on the second partition.  This is going to happen again, probably more than once, so I would like to eliminate the need to back up and restore all her music, pictures, movies and documents by creating a partition exclusively for them.  But that would be 5 partitions, and I'm limited to 4.

So I'm wondering about eliminating the linux-swap partition and replacing it with a swap file in the Ubuntu partition, freeing up the linux-swap partition so I can create an NTFS partition to share between the two operating systems.  The [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) document explains how to create and format a swap file and add it to the running system.  Presumably, this will switch it from using the linux-swap partition to the newly created swap file so the swap partition can be removed.  So, my questions are:

1. Is this even a reasonable solution?  It's a desktop gaming rig with decent performance and 8GB of memory so I'm thinking that any performance hit won't be all that noticeable.  Are there other possible issues I should consider before doing this?  Could it affect stability?

2. The [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) doesn't have directions specifically for switching from a swap partition to a swap file.  Is this even possible and if so, should I create a swap file and switch to it according to the directions first and then remove the linux-swap partition using Gparted?

3. When I installed Ubuntu 12.10, I stupidly used a 32-bit live USB that I had created for an old IBM laptop - I guess I was so worried about even being able to install it at all on a machine with "secure boot" that I didn't pay attention to what I was actually installing.  I really need to do a reinstall using my 64-bit live USB.  Will the installer let me choose between a swap file and swap partition?  If it's possible to do this way, I would prefer it since it would solve both issues at once and we already have all her user files backed up.

Sorry to be so verbose and thank you for any help and advice you can give me.

AnnB

---

### Post by mcduck on 2013-05-30
What I'd recommend is delete the swap partition, then create a new extended partition in it's place, and then create new swap & the storage partition you want as logical partitions inside the extended one.

The limit of four partitions only applies to primary ones, but you can have three primary partitions + one extended partition and as many logical ones as you want...

---

### Post by AnnB on 2013-05-30
Thank you, mcduck!

I just looked at the partition info and my info in my original question is wrong - Win 8 created *three* partitions which forced Ubuntu to install itself in an extended partition.  The extended partition is tiny - only about 20G - and it is has two (logical?) partitions.

I have just under 200G of unallocated space between two of the Win 8 partitions and the Ubuntu extended partition:

/dev/sda1 - NTFS - "system" - 350m
/dev/sda2 - NTFS - Windows - 700g
Unalloc (around 200g)
/dev/sda4 - extended - 20g
     - /dev/sda5 - EXT4 - 12g
     - /dev/sda6 - linux-swap - 8g
dev/sda3 - NTFS - Windows recovery
Unalloc - 2m

I want some of that 200g of unallocated space for the storage partition and possibly to give Ubuntu more space but I really don't feel competent to resize the /dev/sda4 extended partition backward.  I mean, doesn't that involve mucking around with locations?  Where if you mess up you have a real headache?

Thanks again!

AnnB

---

### Post by Impavidus on 2013-05-31
With gparted you can just grow the extended partition (/dev/sda4) into the unallocated space. It's quite straight-forward, not much that can go wrong. You may have to disable swap before doing this. Then create a new shared partition and make the ubuntu partition a bit larger. It may be quickest if you just delete your /dev/sda5 and create a new one. You were going to reinstall Ubuntu anyway. When reinstalling make sure you pick "something else" and point it to the ext4 partition you made ready for it.

You can create a shared ntfs partition using gparted, but make sure you don't touch the existing windows partitions. This may break windows. Also, don't create new partitions from windows. This may convert to dynamic partitions, making it impossible to install Ubuntu.

I'm a bit surprised you have MBR partitioning. I thought most pre-installed win8 boxes had GPT partitioning, but so be it.

---

### Post by AnnB on 2013-05-31
Thank you, Impavidus!

So deleting the /dev/sda5 partition will allow me to move the whole /dev/sda4 extended partition "backwards" when reinstalling?  Do you think I should remove the /dev/sda5 (linux-swap) also?  Then I want to make a third logical partition within /dev/sda4 for my data, correct?

I'm as surprised as you about the MBR partitioning, but I didn't have a choice, so I'm pretty much stuck with it if I need Windoze.  Maybe someday game developers will include Linux in their supported platforms, but currently, if one wants to play Skyrim, one has to put up with Microsoft (ick).

Thanks again!

AnnB

---

### Post by newb85 on 2013-05-31
Perhaps I'm missing something here, but I thought Windows 8 machines always came with EFI partitioning.  And I thought EFI partitioning didn't have the 4-partition limit that MBR has.

---

### Post by AnnB on 2013-05-31
Hi, newb85!

Mine definitely has Windows 8 (the "Metro" ugliness and counter-intuitiveness is unmistakeable) and it's definitely got a 4-partition limit - I get an error message when I try to create a new primary partition.  I wish I could have ordered it a few weeks earlier when they were still shipping with Win 7 (and a CD), but alas....

AnnB

---

### Post by Impavidus on 2013-05-31
There's no need to delete /dev/sda6 (swap). In fact, keeping it mounted whenever possible may make the other operations faster. There isn't really a need to delete /dev/sda5 (ext4) either, but doing so and then making a larger new one may be somewhat faster. It will delete all data on it, but you wanted to reinstall anyway. And of course make your shared ntfs partition. Expanding a partition into unallocated space shouldn't take much time.

The best way is to run a live ubuntu session, run gparted from there and modify the partitions before installing. Then you don't have to change your partitions using the installer any more.

---

### Post by AnnB on 2013-05-31
Thanks, Impavidus!  I think that sounds like the way to go - boot from the live USB and use Gparted to remove/change the partitions and do a full reinstall.  Thanks *very much *for the tip about doing the partitioning ahead of time from a live USB session - I'm way more comfortable with Gparted than I am with the installer's partitioning tools.  Oh.  I should probably start off by rubbing the belly of my toy Tux for good luck, right?

Now all I need to do is pry the teenager loose from the computer long enough to do it!

I will post back results and update to "resolved" when I'm done - probably tomorrow sometime.

I really appreciate everyone sharing their knowledge and experience.  This is a big reason why I love using Ubuntu - Information is always available and when I'm unsure about something, the community is so willing to help.

AnnB

---

### Post by AnnB on 2013-08-08
This worked perfectly!  Thanks, everyone, for your help and advice.

---

