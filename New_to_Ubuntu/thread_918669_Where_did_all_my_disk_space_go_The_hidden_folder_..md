---
title: "Where did all my disk space go? The hidden folder .root/.local/share/Trash [Solved]"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by love2share on 2008-09-13
I could not explain that my hard disk was so full considering the files I had on it. Trashcan was emptied ten times. Did all the cleaning I could think of ([http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html]("http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html")) but still found it unexplainable where the space went to. The Gnome Disk manager didn't provide the right answer. I installed the program **xdiskusage**. First I ran it and discovered some ten gig in the root but access denied; so I could not find out what it was. So ran it in the terminal: [COLOR="SeaGreen"]sudo xdiskusage[/COLOR] . Then I discovered that these 10 gig where in the folder root/.local/share/Trash. Went there in Nautilus as root and unhid the local folder with Ctrl+H.
Tried to delete the files but after a short disappearance the files were recovered.These were mostly large incremental backup files that I had decided I wanted on an external hard drive and had deleted. Made with **sbackup**.
Anyway looked in the forums and found this suggestion:

In Hardy, the location of the trash has changed to
Code:

```
~/.local/share/Trash/files
```

To empty the trash this command should do it:
Hardy Heron:
Code:

```
sudo rm -fr ~/.local/share/Trash/files/*
```

Tried this but it didn't work out as it should. The files were still there.
Elswhere I found this:

Since it is a directory, you cannot just
rm /root/.local/share/Trash/files


You need to [COLOR="Green"]```
rm -rf /root/.local/share/Trash/files
```[/COLOR]

I tried and finally I had ten more gig at my disposal.
But this raises some questions... how is it possible that there are two Trash 'locations' (maybe virtual)and that one is hardly accessible and noticeable for the common user? And how should he discover there are two trash locations? 
Or is it just that what is done in the Admin mode isn't visible for the user. But as everybody, well mostly anybody, sometimes is active in the admin mode it's probable that this should happen. A solution would be to make an option: See the trashcan as root.
This is very confusing and this matter should be addressed in some way or the other. As many people use Ubuntu as a dual boot and may have limited space to run the OS.

---

