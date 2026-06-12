---
title: "is this kosher: rm -rf ~/.Trash/*"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by adamogardner on 2008-09-17
For gnome trash removal from the command line.  Please do not post your lectures on the dangers of using commands that start with the letter "r."  I already got it and thats why I am asking, ok? sorry to spoil any opportunities.  is this command kosher before I run it?  rm -rf ~/.Trash/*    What exactly is that "*" mean? or /* rather?

for one thing doesn't the -r portion remove the whole directory?  meaning I won't have a trashcan (or whatever it's called)?

---

### Post by anotherdisciple on 2008-09-17
It would be fine for version before Hardy...

Hardy locates the trash in a different spot... and it has information about those files in another folder... deleting just the files and not the info would likely cause issues.

---

### Post by egwest on 2008-09-17
Right click on Trash Can, click empty, that simple.

do not want it to go to the trash but remove right away?

Highlight file/folder, whatever you want to delete, and use <shift><delete> keys, a warning will pop up asking if you are sure you want to permanently delete the item. select delete.

---

### Post by adamogardner on 2008-09-17
> **anotherdisciple said:**
> It would be fine for version before Hardy...

Hardy locates the trash in a different spot... and it has information about those files in another folder... deleting just the files and not the info would likely cause issues.

I'm a little confused.  What would the command be?

---

### Post by adamogardner on 2008-09-17
> **egwest said:**
> Right click on Trash Can, click empty, that simple.

do not want it to go to the trash but remove right away?

Highlight file/folder, whatever you want to delete, and use <shift><delete> keys, a warning will pop up asking if you are sure you want to permanently delete the item. select delete.

If I wanted simple, I would watch tv

---

### Post by Sub101 on 2008-09-17
> **egwest said:**
> Right click on Trash Can, click empty, that simple.

do not want it to go to the trash but remove right away?

Highlight file/folder, whatever you want to delete, and use <shift><delete> keys, a warning will pop up asking if you are sure you want to permanently delete the item. select delete.

One issue you can get is deleting things you don't have permissions to delete. I've downloaded things before which i have then deleted, it send to the trash then on empty trash i get permission denied. I then locate trash file address and rm that.

---

### Post by karlr42 on 2008-09-17
> **egwest said:**
> Right click on Trash Can, click empty, that simple.
Great, but what if you need to do that in a script?

---

### Post by -Zeus- on 2008-09-17
This will empty all trash in hardy/intrepid (root and whatever user you're logged in as)

```
sudo rm -rf ~/.local/share/Trash/*;sudo rm -rf ~root/.local/share/Trash/*
```

If you want to empty the trash of ALL users, try this:

```
sudo rm -rf /home/*/.local/share/Trash/*;sudo rm -rf ~root/.local/share/Trash/*
```

---

### Post by anotherdisciple on 2008-09-17
well... in hardy it would look like this

```
rm -rf /home/user/.local/share/Trash/files/* && rm -rf /home/user/.local/share/Trash/info/* 
```

---

### Post by anotherdisciple on 2008-09-17
> **-Zeus- said:**
> This will empty all trash in hardy/intrepid

```
sudo rm -rf ~/.local/share/Trash/*;sudo rm -rf ~root/.local/share/Trash/*
```


YIKES!... I think this will delete your trash bin... I would delete the stuff inside the 2 folders that are in the Trash

---

### Post by aysiu on 2008-09-17
If you don't mind the danger, the proper command to *paste* (I would never retype this) would be ```
sudo rm -rf ~/.local/share/Trash/files/*
``` The safer way, if you happened to get root-owned files into your user trash would be ```
sudo chown -R *username*:*username* ~/.local/share/Trash
``` and then right-click the trash to empty it.

Really, there should never be items in the trash that you can't empty graphically, though. If there are, you're doing something wrong, and [this](http://www.psychocats.net/ubuntu/graphicalsudo) may help you avoid the situation in the future.

---

### Post by -Zeus- on 2008-09-17
> **anotherdisciple said:**
> YIKES!... I think this will delete your trash bin... I would delete the stuff inside the 2 folders that are in the Trash

What are you talking about?  that would be fine

---

### Post by anotherdisciple on 2008-09-17
> **aysiu said:**
> If you don't mind the danger, the proper command to *paste* (I would never retype this) would be ```
sudo rm -rf ~/.local/share/Trash/files/*
``` The safer way, if you happened to get root-owned files into your user trash would be ```
sudo chown -R *username*:*username* ~/.local/share/Trash
``` and then right-click the trash to empty it.

Really, there should never be items in the trash that you can't empty graphically, though. If there are, you're doing something wrong, and [this](http://www.psychocats.net/ubuntu/graphicalsudo) may help you avoid the situation in the future.

But aysiu, won't that leave the info files?

---

### Post by sisco311 on 2008-09-17
> **adamogardner said:**
> For gnome trash removal from the command line.  Please do not post your lectures on the dangers of using commands that start with the letter "r."  I already got it and thats why I am asking, ok? sorry to spoil any opportunities.  is this command kosher before I run it?  rm -rf ~/.Trash/*    What exactly is that "*" mean? or /* rather?

for one thing doesn't the -r portion remove the whole directory?  meaning I won't have a trashcan (or whatever it's called)?

rm = remove 
-r = recursively (remove files/folders/sub-folders)
-f = force (never prompt)
~ = your home folder
* = any files and folders  

the trash in hardy is in *~/.local/share/Trash/*

---

### Post by aysiu on 2008-09-17
> **anotherdisciple said:**
> But aysiu, won't that leave the info files?
Yeah. It's okay, though.

In my experience, the *info* files dynamically adjust based on what files are in *files*.

---

### Post by anotherdisciple on 2008-09-17
> **-Zeus- said:**
> What are you talking about?  that would be fine

Here is what I am talking about.... Gnome 2.22+ has the trash in this location 

```
~/.local/share/Trash/
```

Open the trash and it organizes everything into two folders...

```
~/.local/share/Trash/files
~/.local/share/Trash/info
```

If you did your command... it wouldn't just delete the files... it would delete the whole way it organizes trash...

What I am suggesting you do is delete the files in both of those folders, but leave the folders... know what I mean?

---

### Post by -Zeus- on 2008-09-17
oh, I had no idea that's how it worked.  I think it will still be ok...

---

### Post by anotherdisciple on 2008-09-17
> **aysiu said:**
> Yeah. It's okay, though.

In my experience, the *info* files dynamically adjust based on what files are in *files*.

hmmm... do they dynamically adjust after a reboot though? Seems like I don't remember them ever going away after I deleted things from the ./files

Edit: I should say... Do you have to reboot for them to dynamically adjust?

---

### Post by aysiu on 2008-09-17
> **anotherdisciple said:**
> hmmm... do they dynamically adjust after a reboot though? Seems like I don't remember them ever going away after I deleted things from the ./files

Edit: I should say... Do you have to reboot for them to dynamically adjust?
Actually, I just did a test. Turns out it's not dynamic (either before or after a reboot), but it also doesn't affect performance. You can still move items to the trash and empty the trash. The references in the *info* files to the no-longer-existing files has no impact on trash functionality.

---

### Post by anotherdisciple on 2008-09-17
> **aysiu said:**
> Actually, I just did a test. Turns out it's not dynamic (either before or after a reboot), but it also doesn't affect performance. You can still move items to the trash and empty the trash. The references in the *info* files to the no-longer-existing files has no impact on trash functionality.

It wouldn't hurt to delete the info files though, right? So you might as well do it.

---

### Post by sisco311 on 2008-09-17
never mind

---

### Post by egwest on 2008-09-17
> **Sub101 said:**
> One issue you can get is deleting things you don't have permissions to delete. I've downloaded things before which i have then deleted, it send to the trash then on empty trash i get permission denied. I then locate trash file address and rm that.

Really? Strange, I have never had any problem deleting anything. From the trash or by using the <shift><delete> key combo.
Guess I have been lucky.

---

### Post by jack frost on 2008-09-27
> **-Zeus- said:**
> This will empty all trash in hardy/intrepid (root and whatever user you're logged in as)

```
sudo rm -rf ~/.local/share/Trash/*;sudo rm -rf ~root/.local/share/Trash/*
```

If you want to empty the trash of ALL users, try this:

```
sudo rm -rf /home/*/.local/share/Trash/*;sudo rm -rf ~root/.local/share/Trash/*
```
thanks.. I know it was an old post but I had a bunch of files from a samba share that made the owner as nobody.. I got it to the permissions back to me; but it did not delete until I used your commands.. thanks again.

---

### Post by bumanie on 2008-09-27
Should be used as a last resort, but if all else fails, that does work!

---

