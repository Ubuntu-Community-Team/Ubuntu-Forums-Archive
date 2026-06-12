---
title: "Error during CD and DVD playback"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by wandman on 2008-05-10
Hi,

I am trying to play audio cd's and DVD's using xubuntu 8.04. When I put a disc in Totem opens up but I get an error message saying "location not found".

Any help would be appreciated.

---

### Post by wandman on 2008-05-13
bump

---

### Post by wargodsown on 2008-05-15
yea i hhear you i got the same problem my bro who got me into ubuntu was fixen it for me but he wound up haveing to go back to work so i been tinkering myself its the fact that the players don't have all the codecs to play the encrypted info on the disks that i think is the problem  but hey i could be wrong well i'll check in and see if anybody knows how to fix it later hope u have more luck than i do lol

---

### Post by fred.warren on 2008-08-02
Hi I just solved this problem myself and will be filing a bug report.

Thunar has the association for audio cds cdda:/ instead of the proper cdda:// and for dvds as dvd:/ instead of dvd://

To correct this do the following
[LIST=1]
[*]Open Thunar (Can be found on the Menu under Accessories)
[*]From the menu at the top of Thunar select **_E_dit**
[*]From the **_E_dit** menu select **Pr_e_ferences**
[*]From the **File Manager Preferences** dialog, click on the tab labeled **Advanced**
[*]From the **Advanced** tab click on the blue linked word **Configure**
[*]From the **Removable Drives and Media** dialog, click on the tab labeled **Multimedia**
[*]From the **Multimedia** tab for the **Audio CDs _C_ommand** locate the entry **totem cdda:/**
[*]Change that to **totem cdda://**
[*]From the **Multimedia** tab for the **Video CDs/DVDs C_o_mmand** locate the entry **totem dvd:/**
[*]Change that to **totem dvd://**
[*]Close all dialogs and exit Thunar
[*]Insert your CD or DVD and enjoy
[/LIST]

---

### Post by wandman on 2008-10-30
Thanks for that Fred,

I tried it but still no joy for me. Totem automatically closes after attempting to play the dvd.

I can now play audio cds but totem only recognises the first track. It plays that then stops.

---

### Post by splitime on 2008-12-17
> **wandman said:**
> Thanks for that Fred,

I tried it but still no joy for me. Totem automatically closes after attempting to play the dvd.

I can now play audio cds but totem only recognises the first track. It plays that then stops.

I've added a bunch of different things and am to the point where Totem closes itself when I try to play a DVD. 

Unsure what to try next.

---

