---
title: "I can't delete these files from Trash"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by KevNice on 2008-06-04
I sent a bunch of torrent-related files into my trashbin. They are some kind of "padding file" related to a TV show I downloaded.

Anyway it won't let me empty my trash bin. When I try to delete a file individually from trash, I get this message:
[I]
There was an error getting information about "storage_.Trash-1000<name of file>"[/I]

further details say:

*Error stating file '/storage/.Trash-1000_____/files<name of file>": No such file or directory*

anyone know what's going on here, or if there is some sort of force-delete command?

Thanks

---

### Post by Bubba64 on 2008-06-04
> **KevNice said:**
> I sent a bunch of torrent-related files into my trashbin. They are some kind of "padding file" related to a TV show I downloaded.

Anyway it won't let me empty my trash bin. When I try to delete a file individually from trash, I get this message:
[I]
There was an error getting information about "storage_.Trash-1000<name of file>"[/I]

further details say:

*Error stating file '/storage/.Trash-1000_____/files<name of file>": No such file or directory*

anyone know what's going on here, or if there is some sort of force-delete command?

Thanks

There are a lot of threads on this issue I know they can be hard to find, here is one.
[http://ubuntuforums.org/showthread.php?t=817075&highlight=delete](http://ubuntuforums.org/showthread.php?t=817075&highlight=delete)

---

### Post by KevNice on 2008-06-04
Thanks for that link, but that addresses a permissions problem.

My problem doesnt seem to be with permissions; rather, it is as if the files didn't exist at all.

I tried the ```
sudo rm -rf ~/.local/share/Trash/*
```

command but it didn't do anything

---

### Post by Bubba64 on 2008-06-04
Try highlighting them then hold down shift and hit delete on the keyboard. I also have put files that wouldn't delete into a new folder by dragging them to the desktop and new folder put them in then try the highlight shift delete or in trash to see if that works.

---

### Post by KevNice on 2008-06-04
the shift-delete move didn't work.

Also now it won't let me move the folders in Trash. If I try to move them I get the same message, saying that the files don't exist.

And now I have a new problem.

Now when I try to move things to trash, I get a message saying that the item cannot be moved to trash, and if I want to delete it permanently now.

I think it may have happened when I tried to remove the files-- it seems I had deleted the Trash folder by accident, because I went into /.local/share and the Trash folder was gone.

I have since tried to fix it by using mkdir and making a "Trash" folder, and then a "files" folder within the new Trash folder; however, I still can't move things to Trash. I'm guessing it's a problem with paths?

---

### Post by cariboo on 2008-06-04
Try this. in a terminal:

```
cd .local/share/Trash/file
```

then

```
sudo chmod -R 777 *
```

this changes the file permissions to world readable (you're going to delete them so who cares). Once you've done this, close the terminal and you should be able to get rid of the files you don't want.

Jim

---

### Post by Bubba64 on 2008-06-04
Have you done restart I have also had this remove files like this.

---

### Post by cariboo on 2008-06-04
You posted before I finished my last post. Have a look at this link it may solve your problem:

[http://ubuntuforums.org/showthread.php?t=799950&highlight=trash+icon+missing](http://ubuntuforums.org/showthread.php?t=799950&highlight=trash+icon+missing)

Jim

---

### Post by Daveg4otu on 2008-06-04
FWIW Had a similar problem  with torrent  odds'n sods....I could shift them to the trash -  and delete - but within a few minutes they would reappear on the desktop.

After several attempts  , I finally  created New folder on Desktop....put the files in it ...moved it to trash and deleted  OK.

---

### Post by Bubba64 on 2008-06-04
> **Daveg4otu said:**
> FWIW Had a similar problem  with torrent  odds'n sods....I could shift them to the trash -  and delete - but within a few minutes they would reappear on the desktop.

After several attempts  , I finally  created New folder on Desktop....put the files in it ...moved it to trash and deleted  OK.

If you can't move your files out of trash make a folder on the desktop put it in the trash and put the files into it and see if that deletes.

---

### Post by KevNice on 2008-06-05
> **Bubba64 said:**
> If you can't move your files out of trash make a folder on the desktop put it in the trash and put the files into it and see if that deletes.

This doesn't work for me, because as I said I think I mistakenly deleted the Trash folder at one point in Terminal, and now the path of files to trash seems disrupted. When I try to delete a file off of the desktop, it says it "cannot be moved to Trash, want to delete immediately?" 

Anyone know what's going on with that? Or can help me restore the original Trash settings? I created a new Trash directory but I may have done it wrong.

Still can't move any of those files though.

---

### Post by bumanie on 2008-06-05
That sounds as though the trash bin is now on a different partition (or something like that). You could try > gksudo nautilus and then go to places and double click the filesystem icon. You should then be able to navigate via gui to all areas of the file system. gksudo is basiacally the gui form of super user, therefore you should be able to delete the files in this mode.

---

### Post by ChameleonDave on 2008-06-05
> **KevNice said:**
> Thanks for that link, but that addresses a permissions problem.

My problem doesnt seem to be with permissions; rather, it is as if the files didn't exist at all.

I tried the ```
sudo rm -rf ~/.local/share/Trash/*
```

command but it didn't do anything
That's because you have an extra partition which you have decided to mount at the "/storage/" location.  Such partitions have their own recycling bin.  Do this:

```
sudo rm -fr /storage/.Trash*
```

---

### Post by KevNice on 2008-06-05
> **ChameleonDave said:**
> That's because you have an extra partition which you have decided to mount at the "/storage/" location.  Such partitions have their own recycling bin.  Do this:

```
sudo rm -fr /storage/.Trash*
```

Hey that worked!!! Thank you!! Those pesky files are gone.

However, I still can't move files to trash anymore. There appears to still be a problem with the paths. Any ideas?

---

