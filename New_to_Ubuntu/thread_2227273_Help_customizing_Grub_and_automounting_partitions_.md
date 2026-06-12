---
title: "Help customizing Grub and automounting partitions on boot"
date: 2014-05-31
forum: New to Ubuntu
---

### Post by NA3OH on 2014-05-31
So now that I've been using Ubuntu for a month or so now, I've decided to update my boring Grub menu.

However, I've been running into some issues customizing it using the program Grub Customizer.


This picture is what I've been trying to change it to
[ATTACH=CONFIG]253634[/ATTACH]

But after hitting save and restarting my pc, I just get this boot screen.
[ATTACH=CONFIG]253636[/ATTACH]
It seems to have completely disregarded the options I had chosen for  the background image and the color option. It does look like it has  saved my font choice though.

So I boot up and see that the partition that I have the background image saved on is not mounted and when I boot up the grub customizer program, the background image shows "none" until I mount the partition and refresh the program. You can see it in the image below.
[ATTACH=CONFIG]253637[/ATTACH]

So I tried looking into how to autmount partitions on boot and I've been having mixed results. After searching for information about this, I was told to use this line in the Startup Applications using the uuid of each partition I wanted to mount. I'm mounting two partitions here, the second one is the partition with the picture I want as my background. The second partition is just another partition I want to mount on boot. 

```
 /usr/bin/udisks --mount /dev/disk/by-uuid/01CF5610152D4EB0 ; /usr/bin/udisks --mount /dev/disk/by-uuid/01CF48949CE3FAE0
```

The uuids are correct, I've probably triple checked them. But what happens is that only one ends up being mounted. 

I'll keep messing with it and hopefully I'll get it solved. But if anyone could help me out that'd be great

EDIT: I don't know how to delete that failed thumbnail down there. Just ignore it

---

### Post by LastDino on 2014-05-31
Wouldn't it be more efficient to just move that source picture to the drive which is getting mounted automatically? For example; your picture folder in home directory?

As for mounting on boot, see this thread.
[http://ubuntuforums.org/showthread.php?t=2227168](http://ubuntuforums.org/showthread.php?t=2227168)

---

### Post by NA3OH on 2014-05-31
Probably. I'll try it right now but how would I solve it the way I've been going about it?

Also, how do I get to my pictures folder starting from the beginning? All that shows up when I go to my home directory from here is my desktop
[ATTACH=CONFIG]253638[/ATTACH]

---

### Post by LastDino on 2014-05-31
Click on home and then click on folder named same as your user name, then select picture folder.

You can go to any path you desire by directly typing it as well, for that you need to click on that pencil icon on left top corner.

---

### Post by NA3OH on 2014-05-31
Pardon my ignorance here, but I don't see a picture folder when I try to select it from the windows that pops up from Grub Customizer. Just doing it from the regular file manager works though
[ATTACH=CONFIG]253639[/ATTACH]

---

### Post by LastDino on 2014-05-31
That's because you're clicking on wrong folder, you were suppose to click on the home displayed in your last screen shot in list shown in right panel just below the etc folder.

---

### Post by NA3OH on 2014-05-31
Ohhhhhhhhhhhhh. I feel dumb. It's late in my defense#-o

---

### Post by NA3OH on 2014-06-01
Okay it works. One thing that I want to change though is that the border is made up of question marks within squares which you can see in my screenshot in my original post. Doesn't look the greatest. Also is there a way to remove the instructions on the bottom of the grub menu? Looks kinda ugly and I already know it.

How do I get rid of this/change it?

Also thanks for helping me thus far.

---

### Post by oldfred on 2014-06-01
Did you change to an unusual font? So it cannot find correct characters?

Does not use Grub Customizer, just manually update grub.
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

---

