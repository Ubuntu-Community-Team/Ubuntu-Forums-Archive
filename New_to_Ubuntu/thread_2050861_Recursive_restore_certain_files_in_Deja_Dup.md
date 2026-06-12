---
title: "Recursive restore certain files in Deja Dup"
date: 2012-08-31
forum: New to Ubuntu
---

### Post by duncan12 on 2012-08-31
I noticed that most of my photos are missing.... :mad:

So I went into my home folder and clicked File -> Restore Missing Files (I had kept a Deja Dup backup). It came up with a few files, but only ones from the Home directory itself, not the folders inside it. If I open Pictures -> Photos and click Restore Missing Files I get a file (actually a folder) called "2011". Yes please!

But I obviously can't enter every folder and run this - I need to run it on the entire /home/duncan directory. I do want the interface where you tick the files you want restored. I do not want to restore my entire home directory to the way it was a while ago (I think I know what happened - an embarrassing mistake with rm - a while ago) - I have made new files since then I obviously need to keep.

How can I scan for missing files recursively in my home directory, and bring up the interface where you tick the files to restore?

---

### Post by duncan12 on 2012-08-31
And by the way that embarrassing mistake with rm was **(DO NOT RUN)**:
```
rm -r ~
```

That deletes your home directory recursively. I thought it deleted the current directory at the time :lolflag:

I Ctrl+C'd it after about 2 seconds so didn't think anything of it until now - rm too fast for me..

Anyway this is slightly urgent so help would be appreciated.

---

### Post by duncan12 on 2012-08-31
Sorry to bump in 3 hours not 24 but this is getting urgent. I've looked through the duplicity manual but not sure if by "Restore" it means "change back to how it was" or "add files to folder that are in backup but not folder, leave files alone that are in folder but not backup"

I want to do the latter, and I want to get to choose which files to restore (some I may have deliberately deleted). Will doing a restore in duplicity help me?

---

### Post by duncan12 on 2012-09-01
bump

---

### Post by duncan12 on 2012-09-01
bump

If I really need to I can put the entire backup on my external hard drive and use some program to find out what files exist on the drive but not the computer, and copy the ones I choose. Can someone suggest a program?

---

### Post by jerome1232 on 2012-09-01
I Just realized you already tried what I was suggesting, [COLOR=#3C3C3C][FONT=sans-serif]somehow I "didn't see that post" while I was reading. I apologize.





[/FONT][/COLOR]

---

### Post by amac777 on 2012-09-01
I would suggest you first make a separate backup of your home folder right now. Just copy the whole thing to an external drive like this:

```
cp -a ~ /mnt/external_drive
```

Then you can restore your home directory from your original backup. If you find that some of the newer files are now gone, you can go get them from your newer backup you just made with the above command.

---

### Post by duncan12 on 2012-09-01
> **jerome1232 said:**
> I got this from the built in help (accessed by click the help button in deja-dup or by pressing F1 while in deja-dup) Does this sound like the information you were looking for? (these instruction are carried out in nautilus in case that isn't clear)

[COLOR=#6C6C6C][FONT=sans-serif]**Restoring a Lost File**

[/FONT][/COLOR]
[COLOR=#3C3C3C][FONT=sans-serif]
[LIST]
[*]Browse to the folder containing the file you lost.
[*]Click [COLOR=#6C6C6C][COLOR=#6C6C6C]File[/COLOR] &#9656; [COLOR=#6C6C6C]Restore Missing Files&#8230;[/COLOR][/COLOR].
[*]When the [COLOR=#6C6C6C]Restore[/COLOR] dialog appears, it will scan for files that are in the backup but no longer in the folder.
[*]When you see the file you want to restore appear, select it and click[COLOR=#6C6C6C]Forward[/COLOR].
[*]Review your selections and click [COLOR=#6C6C6C]Restore[/COLOR].
[/LIST]
[/FONT][/COLOR]

Thanks. I've done that, but the problem is this:

Say this is /home/duncan currently:

[LIST]
[*]dir1
[LIST][*]sub1[/LIST]
[*]dir2
[/LIST]

And previously:
[LIST]
[*]dir1
[LIST][*]sub1
[*]gone2.txt[/LIST]
[*]dir2
[*]gone.txt
[/LIST]


And I click File -> Restore Missing Files while it /home/duncan. It only searches in that folder, not in subfolders. So it only comes up with gone.txt but not gone2.txt. What I want is for it to search recursively so it gets gone1.txt and gone2.txt. Obviously my home directory is a lot larger than that so I can't go in to every directory and click Restore Missing Files...

Hopefully I've been a little clearer this time :p

---

### Post by duncan12 on 2012-09-01
> **amac777 said:**
> I would suggest you first make a separate backup of your home folder right now. Just copy the whole thing to an external drive like this:

```
cp -a ~ /mnt/external_drive
```

Then you can restore your home directory from your original backup. If you find that some of the newer files are now gone, you can go get them from your newer backup you just made with the above command.

The backup's about a month old due to my negligence. So I'd need some kind of program to help me compare the two folders and copy what's missing.

---

### Post by duncan12 on 2012-09-01
The reason I found files missing in the first place was that I was backing up /home/duncan/ to do a clean install.

So here's what I'll do:

a) c = create, v = verbose (tell me what's happening), p = preserve permissions, f = to file
```
tar cvpf /media/FreeAgent\ GoFlex\ Drive/backup/current.tar /home/duncan/
```

That way I've got a tar of all my actual files.

b) Restore the month-old Deja Dup backup to ```
/media/FreeAgent\ GoFlex\ Drive/backup/old/
```

c) Wipe, reinstall, sort out merging the folders later.

---

### Post by duncan12 on 2012-09-01
Edit: disregard this post, read below post

So I tarred my home directory with the command in my post above:
```
tar cvpf /media/FreeAgent\ GoFlex\ Drive/backup/current.tar /home/duncan/
```

When it finished (2 hours later!) I opened the tar with Archive Manager. It seemed OK. I tried to rename a file in the tar and it came up with "Adding files to Archive" for a long time. Eventually I clicked cancel and it wouldn't cancel. In the end I had to killall file-roller (which is archive manager) and killall tar to be able to eject the drive.

I mounted the tar, out of curiosity, with Archive Mounter (appears on right-click menu).


The attached image compares the tar (right), and my real home directory (left). The tar has a few thousand more files in it. Why? I'm not sure whether this was caused by Archive Manager's behaviour or not.

---

### Post by duncan12 on 2012-09-02
OK don't worry about the above question. I've put off reinstalling to next weekend, and I will simply copy my files onto the drive. No TARs to worry about.

But I'll only do that once I've got my missing files back, and since no answer for how to do this came from Ubuntu Forums I've put a question on launchpad [here]("https://answers.launchpad.net/deja-dup/+question/207477").

What I've learnt (apart from keeping backups - if I didn't all my photos would be gone):

Stick this at the end of ~/.bashrc
```

#safe rm mode
alias rm='rm -i'

```

It'll prompt you before each file rm deletes.

Marking this thread as solved since I'll pursue this issue on Launchpad instead.

---

