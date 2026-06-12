---
title: "can't delete finder.dat files on master hard drive"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by bth73 on 2008-05-29
I've got a lot of finder.dat files in my media folders I want to delete.
I do a search in the browser and they all come up but are undeletable.
THIS IS THE MOST FRUSTRATING THING ABOUT ALL THESE LINUX OS'S. PERMISSIONS, READ ONLY FILES, ECT.
IS THERE ANY WAY TO TURN OFF ALL THESE PROTECTIONS?
I WANT TO BE ABLE TO DELETE ANYTHING TO THE POINT OF SCREWING UP THE WHOLE SYSTEM AT ANY TIME OR PLACE.
THANKS, bt

---

### Post by kwacka on 2008-05-29
> **bth73 said:**
> THIS IS THE MOST FRUSTRATING THING ABOUT ALL THESE LINUX OS'S. PERMISSIONS, READ ONLY FILES, ECT.
IS THERE ANY WAY TO TURN OFF ALL THESE PROTECTIONS?
I WANT TO BE ABLE TO DELETE ANYTHING TO THE POINT OF SCREWING UP THE WHOLE SYSTEM AT ANY TIME OR PLACE.
THANKS, bt

Sure, that's the Microsoft way.

Then you have to install anti-virus, Spybot, Ad-Aware, etc.

They've even cottoned on to it for Visa - but the dumb sods have made it easy to turn that protection off.

Using a terminal, type in ```
gksudo nautilus
```

WARNING: youcan now delete any file on your computer (whether you want to or not).

Select files you want to delete, and delete.

Close nautilus and you are in control once more.

---

### Post by unutbu on 2008-05-29
For the sake of clarity, suppose all the finder.dat files you want to delete are in a directory called (or subdirectories of) /media/apple. 

Open a terminal. Type 

```

cd /media/apple
sudo find . -name finder.dat -exec rm -i '{}' \;

```

This will find every file called finder.dat in /media/apple, and it will ask you if you want to delete it. 

If you are absolutely sure you want all such files deleted and don't want to be questioned about each one, remove the '-i' from the command above.

---

### Post by bth73 on 2008-05-31
OK,I'm ignorant. How do I state the path to my home music folder?
Also, this seems to be some programming errors:
I turn on View Hidden files and no finder.dat files are shown.
I load all my mp3's into movie player and they not only show up but they also error out the player.
I do the search in nautilus for finder.dat and there they are but I can't delete from there.
The finder.dat files are microsoft bread crumbs right?
The first fix didn't work.
The primary purpose of a computer is to manipulate files. Why is it so difficult to delete files in linux? Please give me full access. Any file, any hard drive, any time, all the time.
Is it possible to be root all the time?
Thanks, bt

---

