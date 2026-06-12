---
title: "[SOLVED] Deleting windows partition (taking the dive!)"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by rabidninjawombat on 2008-05-18
Ok ive been running 8.04 for a little while now (and i previously had 6.04) and i am ready to take the dive. Ive been extremely satisfied and found that i can do everything i need to do without Windows.  Im currently duel booting with Linux and windows XP and would like to toss out the windows partition (mainly to free up the space for more room) And would just like a little advice on the best way to do so without screwing up anything on my current setup. 

Im currently have 2 hard drives. One 40 gig (master) which has the windows partition, and one 80 gig (slave) that has the Linux partition. Is it safe to just reformat the windows partition?  And what can i do about Grub? since i will no longer be needed it to duel boot. 

Thanks and any advice would be great for this noob :)

---

### Post by Xiong Chiamiov on 2008-05-18
You should be able to just launch GParted (make sure the windows drive is unmounted first) and reformat away to ext3.  I'm not sure where GRUB is currently located, but I suppose you could just change your bios to boot to the slave drive.  Still, I'd keep a copy of [SuperGrubDisk]("http://supergrubdisk.org") on hand, just in case.

---

### Post by HotShotDJ on 2008-05-18
> **rabidninjawombat said:**
> Is it safe to just reformat the windows partition?  And what can i do about Grub?Ok.  Yes, it is safe to just reformat the Windows partition as long as there is nothing on there that you want to save.

For grub, simply open a terminal and type:```
gksudo gedit /boot/grub/menu.lst
```Scroll to the very end of that file.  Look for the section that references windows... but ONLY the stuff that appears AFTER ## ## End Default Options ##  Change NOTHING above that line.  The section you want to delete will look something like this:```
title		Windows 95/98/NT/2000
root		(hd0,0)
chainloader	+1
```Now save and reboot.

Once that has been successfully done, come back into this thread and we can get it mounted where you want it. :)  (I have some suggestions for that)

---

### Post by rabidninjawombat on 2008-05-18
Thanks :) for the info. Was looking at Gparted as i was typing. Seems pretty strait forward. And thanks for the link.

---

### Post by rabidninjawombat on 2008-05-18
> **HotShotDJ said:**
> Ok.  Yes, it is safe to just reformat the Windows partition as long as there is nothing on there that you want to save.

For grub, simply open a terminal and type:```
gksudo gedit /boot/grub/menu.lst
```Scroll to the very end of that file.  Look for the section that references windows... but ONLY the stuff that appears AFTER ## ## End Default Options ##  Change NOTHING above that line.  The section you want to delete will look something like this:```
title		Windows 95/98/NT/2000
root		(hd0,0)
chainloader	+1
```Now save and reboot.

Once that has been successfully done, come back into this thread and we can get it mounted where you want it. :)  (I have some suggestions for that)

Ahh more info. thanks! Doing so right now.. the only thing i need to save that i havent already is my old firefox bookmarks. was trying to find location of the bookmarks with the disk mounted in ubuntu, but havent been able to locate it, I guess i could always boot back into windows (yech!) and export the bookmarks. 

I will follow you suggestions right away and follow up in this thread momentarily.

---

### Post by Xiong Chiamiov on 2008-05-18
[finding firefox bookmarks in xp]("http://clipmarks.com/clipmark/A019A4F0-F4D9-4A95-8F33-6CF2FE7556E7/")

---

### Post by rabidninjawombat on 2008-05-18
Heh... found it :) shoulda gave myself a couple more seconds

---

### Post by rabidninjawombat on 2008-05-18
Ok done and it all looks good. Windows is now gone from Grub, and the drive is currently mounted under /media/disk (im assuming) and yea i would probably like it mounted under the were it can be easily used for media storage (under the home folder im assuming)

---

### Post by Xiong Chiamiov on 2008-05-18
If you'd like to have it mounted in your home folder, we can do that, though it can be anywhere, really.

First we need to create a folder for it to be mounted to:
```

mkdir ~/storage

```
You can, of course, change storage to whatever else you like.  Just remember to change it as well in the later code.

We then need to find out where it is located.  Take a look at the contents of
```

sudo fdisk -l

```
and find which one used to be your Windows partition.  It'll probably be either sda1 or hda1.

So then, we just have to add it into your fstab, the file that controls automatic mounting:
```

gksudo gedit /etc/fstab

```
then add the line
```

/dev/sda1   /home/[username]/storage   ext3   defaults   0   0

```

We can check that things are ok with
```

sudo mount -a

```

---

### Post by HotShotDJ on 2008-05-18
Excellent!  it looks like  Xiong Chiamiov has the mounting part covered for you.  The only thing that I might do differently is to create the mount point as /mnt/Storage and then create a link to it in your home directory.  However, directly mounting it there as Xiong Chiamiov has instructed will certainly work.

---

### Post by Xiong Chiamiov on 2008-05-18
> **HotShotDJ said:**
> Excellent!  it looks like  Xiong Chiamiov has the mounting part covered for you.  The only thing that I might do differently is to create the mount point as /mnt/Storage and then create a link to it in your home directory.  However, directly mounting it there as Xiong Chiamiov has instructed will certainly work.
Hmm, I hadn't really thought of that.  In that case (HotShot double-check me), you would make the folder instead here:
```

sudo mkdir /mnt/storage

```
and also use that address in your fstab.  Then make a link to it in your home directory:
```

ln -s ~/storage /mnt/storage

```

EDIT and nothing to do with this: where the hell did I just get a 2nd thank on a post?

---

### Post by rabidninjawombat on 2008-05-18
Ok looks good,  the new drive is mounted in /home/[username]/multimedia, :) best part about that is all the commands and procedures mades sense,  im learning slowly but surely. 

Just one issue. Now that i have the folder mounted i dont have permission to access the folder (copy to) did i miss a step?

---

### Post by rabidninjawombat on 2008-05-18
Which method is more effecient?  Any diffrences in doing it directly to the home folder? or creating a mount point and creating a link to the home directly (and if so how would i do that?)

---

### Post by Xiong Chiamiov on 2008-05-18
Mm, I think just changing the permissions once should do it.
```

sudo chmod 777 ~/multimedia

```
I think will do it, but I always get screwed up with chmod, so I'd go through the GUI:
```

gksudo nautilus

```
Then right-click the folder, go to the permissions tab, and adjust appropriately.

We can check that by unmounting and remounting the drive.
```

sudo umount ~/multimedia
sudo mount ~/multimedia

```

---

### Post by Xiong Chiamiov on 2008-05-18
> **rabidninjawombat said:**
> Which method is more effecient?  Any diffrences in doing it directly to the home folder? or creating a mount point and creating a link to the home directly (and if so how would i do that?)
I don't believe there is any efficiency hit; it's just a matter of organization.  To do so, take a look at [my earlier post]("http://ubuntuforums.org/showpost.php?p=4984620&postcount=11").

---

### Post by rabidninjawombat on 2008-05-18
That worked fine thanks :)  I need to buff up on my chmod knowledge as well... its a bit confusing.  And always nervous about lauching nautlius under root. Dont wanna accidently delete /  :)

---

### Post by HotShotDJ on 2008-05-18
> **Xiong Chiamiov said:**
> (HotShot double-check me)Yes... those instructions look right to me.  I think we need to look at the permissions, though.


rabidninjawombat:  I need you to look at something.  Open up System--> Administration --> Users and Groups and unlock it.  CLick on "Manage Groups" and find the group named "users" and then click on "Properties"

Write down the Group ID, and be sure there is a check next to your name in the Group Members panel.

Now, in the fstab entry, change the part that says "default" to "default,devgid=###" (no spaces!)   Replace ### with the Group ID you just wrote down.

Reboot.  You should now have read write access to that drive.

---

### Post by HotShotDJ on 2008-05-18
Wow.. you guys had a whole conversation about that permissions issue while I was typing.  I've got to learn to think and type faster. :)

---

### Post by rabidninjawombat on 2008-05-18
I did it the above way mentioned by Xiong,  but i can edit fstab in the way you mentioned as we.. I think i will also go back in and change around the mount points just for organzations sake, might as well start myself off on the right foot :)  

Thread marked as solved! thanks guys!

---

### Post by HotShotDJ on 2008-05-18
> **Xiong Chiamiov said:**
> I don't believe there is any efficiency hit; it's just a matter of organization.Yes.  Exactly correct.  I like to do things according to the [Filesystem Hierarchy Standard]("http://www.pathname.com/fhs") as best as possible.  It just makes things easier in the long-run.

---

### Post by Xiong Chiamiov on 2008-05-18
> **HotShotDJ said:**
> Wow.. you guys had a whole conversation about that permissions issue while I was typing.  I've got to learn to think and type faster. :)

I got my typing speed upped dramatically when I first started IMing, and the incredibly high-traffic of this forum has helped that as well...

> **rabidninjawombat said:**
> 
Thread marked as solved! thanks guys!

Our pleasure.  It's always nice when things work like we think they do.

---

### Post by rabidninjawombat on 2008-05-18
Hrrmm sorry to bump the thread again , i switched around the mount points to /mnt/multimedia and im wondering if im doing the link wrong,  i did the command 

```
ln -s ~/multimedia /mnt/multimedia
``` from my /home directory,  

but i do not see the multimedia directory in the home folder.  I see it mounted in /mnt/multimeda and am able to access it just fine (after editing fstab with the proper group id)

i did the same command again and i get 

```
ln: creating symbolic link `/mnt/multimedia/multimedia': File exists
```

Just by looking at that it looks like i did something wrong but i cant figure out what. 

do i need to create a multimedia folder in the /home/[username] folder before creating the link?

Thanks again

---

### Post by Xiong Chiamiov on 2008-05-18
Oh sorry, that's what I get for my unfamiliarity with the ln command.

As you can see with the error that you get, not only did I add an extra part, but I got the order backwards.  I believe it should be 
```

ln -s /mnt/multimedia ~

```

I think.

---

### Post by HotShotDJ on 2008-05-18
> **rabidninjawombat said:**
> Just by looking at that it looks like i did something wrong but i cant figure out what. 
OOPS.. I should have noticed it before....
```
ln -s /mnt/multimedia /home/USER/multimedia
```Of course, replace USER with your user name.

---

### Post by rabidninjawombat on 2008-05-18
Awesome, that did it, and im all good to go.. now im only using one user ATM, but im assuming i will need to create the symbolic link for any other user i create using that same command?

And now we are really solved :)

Did i mention yet how awesome this forum is? :)

---

### Post by HotShotDJ on 2008-05-18
> **rabidninjawombat said:**
> but im assuming i will need to create the symbolic link for any other user i create using that same command?Yes.  And make sure you add the new user to the "users" group using the User & Groups Manager.

---

### Post by Xiong Chiamiov on 2008-05-18
> **rabidninjawombat said:**
> Awesome, that did it, and im all good to go.. now im only using one user ATM, but im assuming i will need to create the symbolic link for any other user i create using that same command?

And now we are really solved :)

Did i mention yet how awesome this forum is? :)
Well, they could still access it through its actual location, but if you want easy access, then yes, you'll have to make another link.  I'm not sure how the permissions will work, though, so you may have to adjust that a bit.  Permissions are obviously not my thing. EDIT: ...which is why I'll shut up and let you listen to HotShotDJ.

And yeah, these forums are pretty much why I'm using *buntu.

---

### Post by Xiong Chiamiov on 2008-05-18
Mm, btw, I just saw [this link]("http://ubuntuforums.org/showthread.php?t=425260") in someone's sig for a nice explanation of how permissions work.  I know I'll be giving it a good read.

---

