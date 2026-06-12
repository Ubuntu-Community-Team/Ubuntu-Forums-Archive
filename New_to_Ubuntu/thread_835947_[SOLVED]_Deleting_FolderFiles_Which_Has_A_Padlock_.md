---
title: "[SOLVED] Deleting Folder/Files Which Has A Padlock Icon Above It"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by lhb1142 on 2008-06-21
I recently transferred some documents and folders from my wife's old Windows XP computer to her new Ubuntu Linux computer.

One of the folders was the "My Music" folder. I wanted to place its contents into the "Music" folder on the Ubuntu machine. I tried "cutting" the contents of the "My Music" folder but "cut" was grayed out. I noticed a Padlock icon above the "My Music" folder. I was able to "copy" the included files to the "Music" folder on the Ubuntu computer, but I cannot delete nor move to trash the original "My Music" folder in the Documents section which still has that Padlock icon and still contains all the original files. I am unable to delete any of the files individually.

How do I get rid of that "Padlock" and delete completely that folder?

I hope that whomever answers my question will explain in detail exactly what I have to do. Thank you.

I thank anyone who will answer me.

---

### Post by perlluver on 2008-06-21
> **lhb1142 said:**
> I recently transferred some documents and folders from my wife's old Windows XP computer to her new Ubuntu Linux computer.

One of the folders was the "My Music" folder. I wanted to place its contents into the "Music" folder on the Ubuntu machine. I tried "cutting" the contents of the "My Music" folder but "cut" was grayed out. I noticed a Padlock icon above the "My Music" folder. I was able to "copy" the included files to the "Music" folder on the Ubuntu computer, but I cannot delete nor move to trash the original "My Music" folder in the Documents section which still has that Padlock icon and still contains all the original files. I am unable to delete any of the files individually.

How do I get rid of that "Padlock" and delete completely that folder?

I hope that whomever answers my question will explain in detail exactly what I have to do. Thank you.

I thank anyone who will answer me.

Go to that folder and right click on it, select properties, go to the permissions tab, under file access, and select create and delete files instead of just read.  Or you can delete it, with a command I am afraid of giving...

---

### Post by AndThenWhat on 2008-06-21
1.) Right-click the file
2.) Click Properties
3.) Go to the "Permissions" tab
4.) For all of the drop downs change them to "Read And Write"

You can also do ALT+F2 and enter **gksu nautilus** and put in your password (WARNING: This will give you root access so anything that you try to delete has no choice but to be deleted. Basically, be extremely cautious.)

Once nautilus opens, navigate to your home folder or wherever the "My Music" folder resides that you want to delete and try deleting it.

---

### Post by lhb1142 on 2008-06-21
Thanks to all. I was able to get rid of that padlocked folder. Unfortunately, somehow, the Ubuntu "Music" folder in "Places" also went with it! How can I get that back? (The music is still all backed up on my wife's external hard drive so nothing is lost.)

I would like to put all of her music in the "Music" folder if I can reestablish it.

Thanks to all who replied previously and to all who will help me with this latest problem.

---

### Post by perlluver on 2008-06-21
> **lhb1142 said:**
> Thanks to all. I was able to get rid of that padlocked folder. Unfortunately, somehow, the Ubuntu "Music" folder in "Places" also went with it! How can I get that back? (The music is still all backed up on my wife's external hard drive so nothing is lost.)

I would like to put all of her music in the "Music" folder if I can reestablish it.

Thanks to all who replied previously and to all who will help me with this latest problem.

Just go to her Home folder and right click, add folder, and name it Music.

---

### Post by lhb1142 on 2008-06-21
Beautiful! It worked. But this "Music" folder does not show up under "Places." Is there a way to get it to show there as well?

Thanks VERY MUCH for your help!

---

### Post by AndThenWhat on 2008-06-21
> **perlluver said:**
> Just go to her Home folder and right click, add folder, and name it Music.

And then go into the newly created Music folder and go to the **Bookmarks** menu and click **Add Bookmark** and that's it.

After that, the Music folder should be under the Places menu.

---

### Post by lhb1142 on 2008-06-21
Perfect Again! I won't ask you how you got your knowledge - but I WILL tell you that I am full of admiration for it and also for your willingness to help me.

Thank YOU - and I also thank everyone else here who has helped me.

I am used to hobby-type newsgroups where people like me get "flamed" for asking what the "veterans" consider basic questions.

That has NOT happened to me here nor have I seen such behavior anywhere on this site.

It makes me glad that I tried Ubuntu Linux (I am going to install it on my own computer, an Acer TravelMate 8104, tomorrow) and this site restores my faith in the basic goodness of people.

Thank you again!

---

