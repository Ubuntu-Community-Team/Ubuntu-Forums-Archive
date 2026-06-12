---
title: "taking space from ubuntu"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by mr-Kirch on 2008-06-07
you might have seen my post about stealing space from vista to give to ubuntu. now i want to take space back from ubuntu because ubuntu has 527 gigs and my vista only has 9 left and i am moving into gaming and i just got the half life series. and i am sick of booting from ubuntu to vista..so can somebody plz tell me how to take memory from ubuntu i only want about 15 gigs to ubuntu and the rest to vista

---

### Post by omi291 on 2008-06-07
You can just edit the partitions..I've heard gParted works really well

---

### Post by mr-Kirch on 2008-06-07
thats the thing when i try to edit partions my explorer.exe turns off its like everytime i go into control panel or my computer explorer.exe goes away so i have to task manager then new task then explorer.exe and retry everything

---

### Post by Paqman on 2008-06-07
First, back up all your data.
Second, defrag Windows a couple of times. Auslogic's Disk Defragger is loads better than the default Windows one
Third, boot into your LiveCD and open up the Partition Editor (Gparted)

You should have no problem resizing from there. It might take a while though...

---

### Post by housam on 2008-06-07
> **Paqman said:**
> First, back up all your data.
Second, defrag Windows a couple of times. Auslogic's Disk Defragger is loads better than the default Windows one
Third, boot into your LiveCD and open up the Partition Editor (Gparted)

You should have no problem resizing from there. It might take a while though...

Using Gparted from the live cd will not let hem resizing ubuntu partition unless it is unmounted.
better to do it by using [[COLOR="Red"]_Gparted live cd_[/COLOR]]("http://gparted.sourceforge.net/livecd.php")

---

### Post by Paqman on 2008-06-07
> **housam said:**
> Using Gparted from the live cd will not let hem resizing ubuntu partition unless it is unmounted.
better to do it by using [[COLOR="Red"]_Gparted live cd_[/COLOR]]("http://gparted.sourceforge.net/livecd.php")

The Ubuntu partition won't be mounted by the LiveCD though. It doesn't mount anything unless you tell it to.

---

