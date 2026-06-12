---
title: "grsync- recover backed up files"
date: 2012-01-03
forum: New to Ubuntu
---

### Post by Ms. Daisy on 2012-01-03
Hello,

I dutifully backed up my home folder in Ubuntu onto a pen drive using grsync.  Now I'd like to recover it.  I choose the source as the pen drive. I choose the destination as my home folder.  And I end up with a folder full of useless executables & text files added to my home folder. 

So obviously it's not intuitive like that.  Being the dork that I am, I looked for grsync manuals on line.  Found lots of manuals that pretty much say you do exactly what I did.

Um... so can someone help a moron out?  How do I get the executable & text files to turn into useful data back in my home folder?

Here's a screen shot of the files in my pen drive backup:
[IMG]http://1.bp.blogspot.com/-ME-AK5kUDOg/TwPbdstbTZI/AAAAAAAAACI/s6mRPPb4azE/s320/grsync.png[/IMG]

---

### Post by Ms. Daisy on 2012-01-05
This wouldn't indicate that my home folder was encrypted, would it? I've installed & reinstalled Ubuntu so many times I can't remember if I encrypted the home folder or not.

---

### Post by QLee on 2012-01-05
> **Ms. Daisy said:**
> ...
Um... so can someone help a moron out?

Well, I'll try to help you but I don't think you are a moron. Actually it seems that your intuition is correct. And it appears that you do understand how to restore with grsync.

It seems to me that where you went wrong is the backup, not the restore. What you showed looks more like the /bin folder (at least part of it)  rather than /home.

Edit: I suppose I should add, you don't need to go to the 'Net for manuals for software that you have installed. Open a terminal and type, man grsync, to see the manual page for grsync.

---

### Post by Ms. Daisy on 2012-01-05
Thanks QLee! So I backed up by /bin folder... oops!  Good thing I didn't have anything of real value in the home folder.  Now I just need to figure out WHY it backed up the /bin folder when I specifically pointed grsync to the /home folder.  And I did it several times all with the same result.
 
If I understand the architecture of Ubuntu folders, /bin and /home are totally different locations (i.e. one is not inside of the other).  Is that correct?

---

### Post by QLee on 2012-01-05
> **Ms. Daisy said:**
> ...
If I understand the architecture of Ubuntu folders, /bin and /home are totally different locations (i.e. one is not inside of the other).  Is that correct?

Yes.

They are both under (meaning subfolders of) what is usually referred to as "/", the root of your filesystem.

---

### Post by QLee on 2012-01-05
I wanted to let you work things out for yourself because that is the best way to have a chance of remembering it and you seem like a thoughtful user (at least one who does try to think things through). However, I'm leaving now so I just want to leave you with a hint that might help if you get stuck.

I don't know how you chose the /bin folder for your backup, however, if I assume correctly from what you wrote above you want the contents of your /home folder (in this case I mean the /home that has the separate folders for each user's separate ~home - e.g. /home/daisy; /home/<username>) to be copied to the pendrive. 

In that case the source directory (folder) that you want to use in grsync is probably, /home/, to rsync the contents of the folder /home to the pendrive. Test your backup and restore options on a folder that doesn't have anything important in it (e.g. one that you create just to test with, you can delete it when you finish testing) and pay particular attention to the different result when the trailing / is used with a folder path as in /home/.

Good luck, but I expect you will make your own luck through appropriate effort.

---

