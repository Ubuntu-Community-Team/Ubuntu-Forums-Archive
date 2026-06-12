---
title: "Can't read the floppy drive"
date: 2013-03-07
forum: New to Ubuntu
---

### Post by lwalper on 2013-03-07
Yeah, I know, who still even has a floppy drive in their machine?

Well, I've got a couple of 3.5" floppies formatted for Mac with data that I'd really like to get to. Of course, Win$$ doesn't read the disk and tells me it's not formatted (which it is, just with something it doesn't recognize).

1. Will Ubuntu read the disk?

2. If it will (and I've tried) why am I not able to access the floppy drive from the file manager? The drive appears in the list, but when I click the icon nothing happens. When I right-click the icon there's also an option to "Read the drive" (or some such thing -- I'm not at that terminal at the moment). When I do that, the drive light does come on, but the drive motor does not run and the the disk is not read.

3. Does the drive need to be mounted? When I roll over the icon the prompt says something like "Mount and read ...") --and if so, how do I go about mounting the drive?

---

### Post by ajgreeny on 2013-03-07
I think you now need to use udisks to mount and read/write to floppy disks, which does make life a bit difficult, as I have yet to find a simple way to mount them in my old desktop machine by simply using nautilus.

I have very little use for floppies now, but I did when I purchased my machine some while ago, and therefore if I need it now I use aliases of ```
alias fd+='udisks --mount /dev/fd0'
alias fd-='udisks --unmount /dev/fd0'
```in my hidden ~/.bash_aliases file to speed up the mount and unmount of the few floppies I have left with things on that I need.

Note that this is not a typo; the commands really are "mount", and in particular **"unmount**", as opposed to umount for the normal unmounting command.

I am not sure about the mac format situation, but I do know that mac filesystems can be read by Linux, though you may need some of the hfs packages installed.

---

### Post by mastablasta on 2013-03-07
have a look here: [URL="http://ubuntuforums.org/showthread.php?t=1772291"]http://ubuntuforums.org/showthread.php?t=1772291
[/URL]
and here: [http://askubuntu.com/questions/63142/how-do-i-get-a-floppy-drive-working](http://askubuntu.com/questions/63142/how-do-i-get-a-floppy-drive-working)

---

### Post by lwalper on 2013-03-07
Ok, thanks, I'll do some reading.

Have already tried a couple of these items -- no joy -- yet ...

---

### Post by schragge on 2013-03-07
Also, check if you are a member of the group *floppy* ```
groups
```
If not, then ```
sudo adduser $USER floppy
```

---

