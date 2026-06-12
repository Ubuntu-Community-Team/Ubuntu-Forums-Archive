---
title: "Can I make default &quot;Documents&quot; etc. go to an external HD."
date: 2012-04-10
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-04-10
My concept is to use the 8 GB USB flash drive for programs and my 500 GB USB drive for all data, media,etc.

Is it possible to switch the default location of these to the HD?

---

### Post by Daveth on 2012-04-10
probably on a case my case basis- so you can select a new path in Writer to move from home/user to your usb path, and so on for other programs you would run. Not sure if you can do that globally, though it is quite possible to set up the usb as an effective "partition".
Unless someone else here knows more of the subject.

---

### Post by jerome1232 on 2012-04-10
I use symlinks to link all my personal data to my Windows drive, you could do similar.


make sure there's no data in the folder you wish to link, then delete the folder. Browse into your usb drive and middle click drag the folder you want your documents to go into to your home folder, drop it and select "link here", click the folder once, hit "f2", and rename it to "Documents" repeat for each folder you want linked in this way, ie for Videos, Music, etc...


The cli way

```

rmdir ~/Documents
ln -s /media/path/to/new/Documents ~/Documents
```

---

### Post by daslinkard on 2012-04-11
I know in Libre Office you can go into the Tools-- Options-- Path and edit your desired path.  As far as your other items linked up, from the research that I have seen, I believe Jerome has hit the nail on the head in writing about symlinks.

---

### Post by Boyntonstu on 2012-04-11
If I punch places "documents"  I see:

open'/home/BoyntonStu/Documents'

How/where do I change that default location to:

open'/Stu EXT HD/Data/Documents'  ?

---

### Post by Boyntonstu on 2012-04-11
> **jerome1232 said:**
> I use symlinks to link all my personal data to my Windows drive, you could do similar.


make sure there's no data in the folder you wish to link, then delete the folder. Browse into your usb drive and middle click drag the folder you want your documents to go into to your home folder, drop it and select "link here", click the folder once, hit "f2", and rename it to "Documents" repeat for each folder you want linked in this way, ie for Videos, Music, etc...


The cli way

```

rmdir ~/Documents
ln -s /media/path/to/new/Documents ~/Documents
```

If I punch places "documents" I see:

open'/home/BoyntonStu/Documents'

How/where do I change that default location to:

open'/Stu EXT HD/Data/Documents' ?

---

### Post by jerome1232 on 2012-04-11
Copy anything you have out of your Documents folder. Delete the Documents folder. Middle button drag HD/Data/Documents to your home folder. Rename the new symlink so it just says "Documents".

---

### Post by bogan on 2012-04-11
> **Boyntonstu said:**
> If I punch places "documents"  I see:

open'/home/BoyntonStu/Documents'

How/where do I change that default location to:

open'/Stu EXT HD/Data/Documents'  ?Unfortunately,you cannott edit the 'Places' menu in 'Main Menu, so I do not have an answer to your question either, but an easy way round is to open a new folder in the Desktop, set it to display your path, and rename it "StuDocs", or somesuch.

In Unity2D OR 3d, in gnome Classic, or with a Gnome2 Panel or a Dock, you could then drag it to such a position as suits you best.

Chao!. **bogan**.

---

### Post by haqking on 2012-04-11
go to home folder

show hidden files

goto .config

open users-dirs.dirs

change the default locations for whatever folder you like

logout and back in and done

Peace

---

### Post by Mark Phelps on 2012-04-11
Actually, that open can not work -- because you have embedded blanks in the directory name.

If you try it as it, it will try to open "/Stu" and fail.

Linux doesn't like blanks in directory names or file names.  So, you would do better choosing another name, or replacing the blanks with dashes.

---

### Post by haqking on 2012-04-11
answered in your other thread [http://ubuntuforums.org/showthread.php?t=1956046](http://ubuntuforums.org/showthread.php?t=1956046)

You edit the user-dirs.dirs file in home/.config folder.

Peace

---

### Post by sffvba[e0rt on 2012-04-11
*Threads **merged*** (asking the same question in multiple threads waters down support efforts.)


404

---

