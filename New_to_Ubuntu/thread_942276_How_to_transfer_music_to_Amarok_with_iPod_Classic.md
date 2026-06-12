---
title: "How to transfer music to Amarok with iPod Classic"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by Acoshi on 2008-10-09
I have an iPod Classic (160gb) and I have been trying to follow the instructions on how to allow Amarok to transfer my music, but I keep getting the exact same error.

Media Device: failed to create lockfile on iPod mounted at /media/disk: Read-only file system

I have Hardy Heron install on my MacBook and don't have access to Windows or Mac.

Any suggestions out there?

---

### Post by Acoshi on 2008-11-22
bump

---

### Post by Toshibawarrior on 2008-11-22
If you're in Ubuntu (with Gnome of course) you can install **gtkpod-aac** (Found in Synaptic)...Much better iPod management. Personally gtkpod is the only program that works for me on my iPod Classic (160GB same as yours).

Check out [this post]("http://ubuntu-dawn.blogspot.com/2008/09/ipod-ubuntu-love.html") I made on my blog about this subject. You can transfer your music collection to gtkpod. I'm really not sure if gtkpod will work under other desktop environment like KDE of xfce...Anyways check my post out and you'll definitely get it working. If not just give me a holler and I'll be happy to help! :popcorn:

Happy iPodding!

EDIT: After re-reading your post I understood that you wanted to move your music from the iPod to Amarok...well you can do that too. Just copy your music collection (with gtkpod) and then add the folder with your music to Amarok's collection. Make sure to let me know how it goes for ya!

---

### Post by Acoshi on 2008-11-22
Cool, thanks for the post!

---

### Post by johnnylavah on 2008-11-22
> **Toshibawarrior said:**
> If you're in Ubuntu (with Gnome of course) you can install **gtkpod-aac** (Found in Synaptic)...Much better iPod management. Personally gtkpod is the only program that works for me on my iPod Classic (160GB same as yours).

Check out [this post]("http://ubuntu-dawn.blogspot.com/2008/09/ipod-ubuntu-love.html") I made on my blog about this subject. You can transfer your music collection to gtkpod. I'm really not sure if gtkpod will work under other desktop environment like KDE of xfce...Anyways check my post out and you'll definitely get it working. If not just give me a holler and I'll be happy to help! :popcorn:

Happy iPodding!

EDIT: After re-reading your post I understood that you wanted to move your music from the iPod to Amarok...well you can do that too. Just copy your music collection (with gtkpod) and then add the folder with your music to Amarok's collection. Make sure to let me know how it goes for ya!

great blog! gtkpod is much nicer than rhythembox. i am syncing with an old school 20gb ipod and it is working great.

since my ipod is not capable of displaying images, i receive the following message when opening gtk...

"Error reading iPod photo database (Photos directory not found: '/media/MYPOD/iPod_Control/Photos' (or similar).)"

i created a Photos directory on my ipod, but still receive this message when opening gtkpod.  

any ideas?

thanks!

---

### Post by johnnylavah on 2008-11-23
> **johnnylavah said:**
> great blog! gtkpod is much nicer than rhythembox. i am syncing with an old school 20gb ipod and it is working great.

since my ipod is not capable of displaying images, i receive the following message when opening gtk...

"Error reading iPod photo database (Photos directory not found: '/media/MYPOD/iPod_Control/Photos' (or similar).)"

i created a Photos directory on my ipod, but still receive this message when opening gtkpod.  

any ideas?

thanks!

I fixed this by creating the Photos folder in the main ipod directory instead of iPod_Control directory.

---

### Post by Toshibawarrior on 2008-11-23
Sorry for my lateness....That was exatly the way to fix it. Somehow gtkpod doesn't find picture databases anywhere in the iPod directory except for the root of the drive. I usually just ignore this error ('cause I have a Nano 1st gen too) but creating the folder is much cleaner! :)

Glad to know you liked my blog! And that your iPod is working under Linux! If you have any more questions just post a comment on the blog, a post here , or on a PM:)!

See ya around!

---

### Post by johnnylavah on 2008-11-23
> **Toshibawarrior said:**
> Sorry for my lateness....That was exatly the way to fix it. Somehow gtkpod doesn't find picture databases anywhere in the iPod directory except for the root of the drive. I usually just ignore this error ('cause I have a Nano 1st gen too) but creating the folder is much cleaner! :)

Glad to know you liked my blog! And that your iPod is working under Linux! If you have any more questions just post a comment on the blog, a post here , or on a PM:)!

See ya around!

iPod is working great!  gtkpod truly makes my iPod/linux experience much more enjoyable! keep up the good work on your blog...

---

### Post by Toshibawarrior on 2008-11-23
> **johnnylavah said:**
> iPod is working great!  gtkpod truly makes my iPod/linux experience much more enjoyable! keep up the good work on your blog...

Thanks a lot! Glad to know your iPod is working in Ubuntu! I'll make some updates to my blog tomorrow. If you need any more help, just ask :)!

---

### Post by catatonicprime on 2008-11-24
> **johnnylavah said:**
> I fixed this by creating the Photos folder in the main ipod directory instead of iPod_Control directory.

Same, Thanks Johnny.

---

### Post by Predatorian on 2008-11-25
when ever i try adding music to my ipod 160gb, it tells me i dont have permission to add or remove any thing from it. what should i do?

---

### Post by Toshibawarrior on 2008-11-25
How are you adding music to it?...By Nautilus?...

Just follow my instructions on my blog (I posted the link above) and make sure you follow all the steps. You shouldn't have any problems!

---

### Post by williamson389 on 2008-11-25
I am having toruble with a 1st Gen Nano.  I recently reinstalled to 64bit hardy and therefore my ipod has music on it.   I used to use amarok, but it says there is a Itunes lock on it, which keeps reappearing even after i delete it manually.  

I tried Gtkpod and it seemed to be working great until i hit save changes.  Error messages flew up everywhere saying the files were not copied to my computer,  or files were not transferred to the Ipod or Files cant transfer because it is read-only.

Any ideas would be appreciated especially because i had it working fine with linux before.  I guess it serves as lesson to not rock the boat. ;)

---

### Post by Toshibawarrior on 2008-11-25
Good point...never rock the boat especially when it's sailing smoothly.

Anyways, I also have a 4GB 1st gen nano and it's working just fine here in gtkpod on Ubuntu 32-bit (Never tried it on 64bit). You can check if you have **gtkpod-aac** or **gtkpod**...In my opinion **gtkpod-aac** works *better and has support for .aac and .mp4 files*.

Check that out for now...and reboot the machine, just to make sure that the computer and the nano are working side-by-side. Let me know what happens.

---

### Post by williamson389 on 2008-11-25
I have actually tried Gtkpod-aac and Gtkpod but neither worked.  After restart, i tried again with amarok, but to no avail.  It came up with the familiar "iPod mounted at /media/IPOD already locked" which then ends with unknown error when i press to remove.   With Gtkpod,  the following error pops up when the IPOD is connected.  
Error opening /media/IPOD/iPod_Control/Artwork/F1031_1.ithmb: Read-only file system
Error opening /media/IPOD/iPod_Control/Artwork/F1027_1.ithmb: Read-only file system
Opening of '/media/IPOD/iPod_Control/iTunes/iTunesDB' for writing failed (Read-only file system)
Seems like i have to remove this lock.  i have seen walkthroughs and forums that say to remove itunes_lock manually from the ipod, but i have tried and it will not delete.

---

### Post by Toshibawarrior on 2008-11-26
Go to a terminal and type:

```
gksudo nautilus
```

And now search for your iPod's mountpoint and try deleting the lock there. When you use the above command you become root and are able to delete everything...just be careful with that kind of power.

Try it and post back the result.

Also, have you ever formatted the iPod using MAC?......The filesystem that MAC puts into the iPod is not compatible with most applications.

Let me know what happens.

---

