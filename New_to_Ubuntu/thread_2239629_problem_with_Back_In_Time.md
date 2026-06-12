---
title: "problem with Back In Time"
date: 2014-08-14
forum: New to Ubuntu
---

### Post by Saffo on 2014-08-14
So, I am new to Ubuntu.

I just downloaded Back In Time and I set it up (I think!) to back up my Home folder on an external hard drive.
(In case it is relevant, the external hard drive has multiple partitions, most of what are HFS+ because I used it to back up my old Macbook, but the partition I am using is ext4)

Back In Time seemed to work fine, except for one problem--- it didn't actually back anything up at all. It created an empty snapshot and I cant seem to figure out what I am doing wrong.

Here's a screenshot



[ATTACH=CONFIG]255494[/ATTACH]

As you can see, the "home" folder in the snapshot is completely empty. And if I click "take snapshot" it says there is nothing to back up. 


Finally, please respond in plain English. I am trying to learn Ubuntu/Linux but there is a steep learning curve and I am still just a beginner.

Thanks!

~S

---

### Post by whitesmith on 2014-08-15
Welcome to the forum! I note that you are attempting a root backup. This is sketchy since you have highly limited (read almost nonexistent) p ermissions outside of $HOME. You should have a special version [**Back in Time (root)**] that allows these kinds of backups. The $HOME backup probably fails because BIT encounters a fatal error backing up root. Cheers!

---

### Post by Saffo on 2014-08-15
Hi, thank you!

I'm not sure I follow..... (Sorry, I am still new to Ubuntu; trying to learn all these terms.) I am not backing up the root directory. Only the home directory. But it seems that it shows "Root" on there because that is the parent directory? Maybe?

I noticed there are three different versions of back in time on the software center: "(backintime-gnome)" "(root)" and "(backintime-kde)"
I wasn't sure which one to download, so I downloaded gnome because it had the most reviews........
I only set my home folder as the folder to backup. I don't know why the root shows up in the screenshot.

---

### Post by newb85 on 2014-08-15
Is there a reason you want to use Back in Time?  Deja Dup has a much simpler interface.  Of course, it's your choice.

I don't have experience with Back in Time, but it looks to me like you haven't gone through all the steps to actually back up your /home directory.  But then, your screenshot doesn't tell us a lot about the settings you've adjusted.

---

### Post by Saffo on 2014-08-15
I couldn't figure out how to use Deja Dup... and then I saw better reviews of Back In Time. I'm really not sure what the difference is. 

What are the steps I need to go through?

---

### Post by whitesmith on 2014-08-15
@Saffo: I tried Deja Dup (which is called Backups by Ubuntu). It attempts to mimic Mac's backup tool by being simplistic. Unfortunately it fails because, like the Mac thingie, is assumes users are a little soft upstairs, if not commitably stupid. If you're running Unity, use the top button to find and run it. If you are running the Gnome DE (as I am), take it for a drive by going to Applications->Accessories->Backups. Either way, go to Scheduling. Note that you're limited to a minimum of 6 months of stored backups. Now have a peek at my configuration file for Back in Time in the attachment. See the difference? 'Nuff said. Stick with BIT.

[edit] Which Ubuntu desktop are you on? Unity (the one with the fancy dock along the left side of the screen) or Gnome (Applications and Places are at the top of the screen, which is free of launchers [icons in Winspeak] until you put them there? I ask because having the wrong version of BIT could be part of your problem.

[edit2] Screenshots of all configuration panels are now part of this post, but bear in mind that I'm backing up to an external 2 TB SATA 3 device. You'll need a fair amount of storage--about 180 G--if you want to go as far back as I.

---

### Post by Paulgirardin on 2014-08-15
Back in Time Root should be on your system.It is installed along with Back in Time.Having said that you probably don't need it.
Click on the log view icon in the BIT window and see what kind of errors are reported.In Log view you can select All,Errors,Informations or changes.This will inform you about what actually was performed during the snapshot.Below is what a normal BIT window looks like.The errors are just referring to permissions for a Trash folder on one of my drives

---

### Post by Saffo on 2014-08-24
hey everyone, thanks for the suggestions. i wanted to say, this issue is still unresolved but i have been too busy to deal with it this past week. i will post again when i get the chance to look into it more.

thanks again!

---

