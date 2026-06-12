---
title: "Deleting &quot;ghost files&quot; from a usb flash drive?"
date: 2012-03-06
forum: New to Ubuntu
---

### Post by nullified_nostalgia on 2012-03-06
I cut/pasted some files from my linux environment onto a usb flash drive.  I then cut/pasted them from the flash drive into a windows environment on another machine.  The windows machine shows that the flash drive is completely empty, but when I plug it back into the linux machine it shows that all of the files are still on the flash drive.  When I try to delete them it gives me an error and says the files do not exist.  How do I get rid of these "ghost files"?

Any help is appreciated!  :)

---

### Post by critin on 2012-03-06
I don't believe Windows will see linux formatted drives.

---

### Post by critin on 2012-03-06
Have you tried to setup a lan network so the machines can share files?

---

### Post by nullified_nostalgia on 2012-03-07
> **critin said:**
> Have you tried to setup a lan network so the machines can share files?
Nope, the windows machine in question is one I keep completely isolated from the internet / networks so it stays in pristine condition.  That also means I don't have to update anything on it so it runs as fast as it did when it was new.  Windows has a tendency to get slower as it accumulates more updates, at least from my experience.

I've transferred files back and forth before using a flash drive like this and never had this problem before.  For example I was doing the same thing two days ago and it worked fine, then I reinstalled lubuntu and started noticing this ghost file problem with the flash drive.  I figure a format of the flash drive would probably take care of the problem but I'd rather not have to do that on the regular, kind of a hassle.  Just wondered if there's any particular reason linux would see ghosts of files that have been deleted using a windows machine.

Oh and just for the record the flash drive is formatted in fat32.

---

### Post by morhin on 2012-04-17
I could be wrong but what I have found is this.

If I delete from my flash drive thingee it removes the info but leaves the space in case you want to restore the files. Remember, in ubuntu the files are not deleted but only moved to trash.

With the thingee (thumb/flash drive) still in place I go to trash and now I delete the files. This empties the drive. 

Otherwise I had to take the drive to my windows machine (yes, business dictates that I keep one) and delete them there. 

Let me know if that works

Morhin

;)

---

### Post by Ghost_Mazal on 2012-04-17
BE VERY CAREFUL WITH THE FOLLOWING COMMAND. USE AT OWN RISK. !!!

You can try this in the terminal.
First cd to the usb drive. (that will depend where yours are mounted)

When you are absolutely 100% sure you are standing in the root of your USB drive:

<snip>

This will FORCEFULLY delete EVERYTHING in the current folder WITHOUT confirmation , INCLUDING folders and sub folders. So also do not use if you only want to remove certain stuff , but only if you want to completely wipe everything on the USB stick.

BE VERY CAREFULL !!!

---

### Post by nullified_nostalgia on 2012-05-16
At long last I've finally figured this one out.  What was happening is every mounted drive has it's own trash directory, and deleting (or cutting) files via windows doesn't delete the index of the files from the drive - so linux can still see them.  I couldn't get a lot of files to empty from my trash so I googled that problem and came up with this solution, which works for usb flash drives as well.  Personally I find it much quicker to just format the flash drive, but a script to run these commands would probably be a lot quicker.  (Or Ghost_Mazal's solution which I still haven't tried.)

[http://www.zimbio.com/Ubuntu+Linux/articles/615/Ubuntu+Won+t+Empty+Trash](http://www.zimbio.com/Ubuntu+Linux/articles/615/Ubuntu+Won+t+Empty+Trash)

Extraction of the useful info from that link:

Here's what you have to do. Open a new terminal session and:
[CENTER]**sudo find / -type d -name *Trash***[/CENTER]
This goes and finds all of the Trash folders your computer sees. On my server, this brought up the following:
[CENTER]**/media/backupdrive/.Trash-1000**
**/home/username/.local/share/.Trash**[/CENTER]
[LEFT]Of  course, replace "username" with the username specific to your computer.  These are both of the Trash bins on my computer. In order to delete  them, type in:[/LEFT]
[CENTER]**rm -rf /media/backupdrive/.Trash-1000**
and then
**rm -rf /home/username/.local/share/Trash**[/CENTER]
Voila! This will effectively force-delete both Trash bins.

---

### Post by jtarin on 2012-05-16
I just delete them when I open them up on the drive that exposes them.....or quick format in Win.

---

