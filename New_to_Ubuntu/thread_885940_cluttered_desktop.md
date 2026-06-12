---
title: "cluttered desktop"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-08-10
my desktop looks pretty cluttered with the drive icons showing up.how can i free my desktop from these drive icons,without unmounting the drives?

---

### Post by coffeecat on 2008-08-10
From a terminal : 'gconf-editor'

Then - apps > nautilus > desktop. Untick volumes_visible.

---

### Post by adamogardner on 2008-08-10
I don't know  just asking here, but couldn't you just move those things to another folder?

---

### Post by coffeecat on 2008-08-10
> **adamogardner said:**
> couldn't you just move those things to another folder?

Interesting idea, but it doesn't work. I just tried it. :) You get an error. It's a nautilus desktop configuration issue. The fix I suggested will do it.

---

### Post by adamogardner on 2008-08-10
> **coffeecat said:**
> Interesting idea, but it doesn't work. I just tried it. :) You get an error. It's a nautilus desktop configuration issue. The fix I suggested will do it.

oh what is different inwhat your trying to move from a normal file?  I'm just asking because I'm learning.  I don't have drive icons on mine.

---

### Post by Shazaam on 2008-08-10
> **adamogardner said:**
> <snip> I'm just asking because I'm learning.  I don't have drive icons on mine.
From what I have seen the drive icons only show on the desktop with a default Hardy install when you go to Places>Removable Media and click on one of the drives. It puts an icon on the desktop then opens nautilus. When you close nautilus the desktop icon stays until you right-click the icon and choose "Unmount Volume".

---

### Post by coffeecat on 2008-08-10
> **adamogardner said:**
> oh what is different inwhat your trying to move from a normal file?  I'm just asking because I'm learning.  I don't have drive icons on mine.

Yes, the drive icons are different from a normal file. I find them useful, but the OP obviously doesn't want them. Which is fine - we all have different preferences.

You say you don't have drive icons on your desktop. Is that because you haven't any mounted drives? If you plug a USB drive in and a drive icon doesn't appear on the desktop and you would like one, just follow the steps in my first post, but tick volumes_visible instead of unticking it.

If you're still learning about Ubuntu and Linux and would like to experiment (safely :wink:), try starting gconf-editor the way I said and go to apps > nautilus > desktop. You'll also see boxes for the computer, home, network and trash icons. Try ticking and unticking them and see which you prefer. Ubuntu comes with the 'clean' uncluttered look, whereas if you try other gnome distros, you'll probably see the computer, home and trash icons on the desktop by default.

Enjoy! :)

---

### Post by coffeecat on 2008-08-10
> **Shazaam said:**
> From what I have seen the drive icons only show on the desktop with a default Hardy install when you go to Places>Removable Media and click on one of the drives.

I think it depends on that entry in gconf-editor, but I can't remember what a default install of Ubuntu is like - I tinker too much. :) And - if you have a partition (or partitions) on one of your internal drives, and entries in /etc/fstab to mount them at bootup, you'll get desktop icons for them as well. That's if the setting in gconf-editor is correct, of course.

---

### Post by Vivaldi Gloria on 2008-08-11
> **stonecoldjha said:**
> my desktop looks pretty cluttered with the drive icons showing up.how can i free my desktop from these drive icons,without unmounting the drives?

Better way to do it is to mount your filesystems (partitions) in /mnt/mountpoint using fstab. This will stop desktop icons. 

Then you can put symlinks to where ever you want. Also you can add it to places menu by opening a nautilus window and dragging the folder icon to the places pane on the left.

---

### Post by mcduck on 2008-08-11
> **coffeecat said:**
> I think it depends on that entry in gconf-editor, but I can't remember what a default install of Ubuntu is like - I tinker too much. :) And - if you have a partition (or partitions) on one of your internal drives, and entries in /etc/fstab to mount them at bootup, you'll get desktop icons for them as well. That's if the setting in gconf-editor is correct, of course.

Only if you configure fstab to mount those drives into /media. Mount theme anywhere else (like /mnt) and you won't get any icons.

---

### Post by coffeecat on 2008-08-11
> **mcduck said:**
> Only if you configure fstab to mount those drives into /media. Mount theme anywhere else (like /mnt) and you won't get any icons.

Yes, you're quite right. Thanks for clarifying.

---

