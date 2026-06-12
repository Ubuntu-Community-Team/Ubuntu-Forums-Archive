---
title: "listing files in terminal"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by ians1 on 2008-06-20
Hi

Maybe a simple thing for some but I need to change some permissions on a folder I created on another volume (not the boot volume).

How do I change volumes so that I can list/change files etc in that volume?

ian

---

### Post by Dynaflow on 2008-06-20
Simplest way:

```
sudo nautilus
```

Browse for what you're looking for, right click it, go to Properties, and then change permissions from the Permissions tab.

If you *really* want to do it through the command line, this takes you to a directory:
```
cd /PATHTODIRECTORY
```
And this takes you up a level:
```
cd ..
```
To list files in a directory, use:
```
ls -a
```

---

### Post by wormser on 2008-06-20
> **Dynaflow said:**
> Simplest way:
```
sudo nautilus
```

When using root privileges with graphical applications it is recommend to use gksudo instead of sudo.

More [here]("http://www.psychocats.net/ubuntu/graphicalsudo").  So, this would be the command.

```
gksudo nautilus
```

---

### Post by Dynaflow on 2008-06-20
> **wormser said:**
> When using root privileges with graphical applications it is recommend to use gksudo instead of sudo.

More [here]("http://www.psychocats.net/ubuntu/graphicalsudo").  So, this would be the command.

```
gksudo nautilus
```

So *that's* why.  Interesting.

---

### Post by ians1 on 2008-06-20
The nautilus line runs a gui with a file browser.  Opening the volume with the folder in that I created and right clicking I get an option Properties, selecting that opens a dialogue with various tabs atop, including Permissions.  Selecting Permissions tab displays three areas, Owner Group and Others with Folder and File options for each respectively.

Owner says ians (my login)
Folder Access: Create and Delete Files
File Access: ----

Group says root
Folder Acess: none
File Access: ----

Others says <blank>
Folder Access: ----
File Access: ----

Trying to change any of them does nothing, they just flick back to what they say above, clicking the button at the foot of that dialogue "Apply Permissions to Enclosed Files" just clears any choices I make above.

Its all a bit strange I think as when I created the share on this folder I ticked the box that said "Guest Access" so I would have thought the "Others" would include read/write access for anyone.

I may be barking up the wrong tree (or just plain barking, lol) being a beginner, but isn't there a command line thingy like chmod to change permissions I could use?

I just dont know how to specify the volume name at the command prompt because it does not seem to recognise the "xxGb Media" label the GUI displays.

I am probably asking the wrong questions, help!

ian

ps the object of the exercise was to make the folder read/write accessible to everyone on  the local network.

---

### Post by GaryUK on 2008-06-20
> **ians1 said:**
> The nautilus line runs a gui with a file browser.  Opening the volume with the folder in that I created and right clicking I get an option Properties, selecting that opens a dialogue with various tabs atop, including Permissions.  Selecting Permissions tab displays three areas, Owner Group and Others with Folder and File options for each respectively.

Owner says ians (my login)
Folder Access: Create and Delete Files
File Access: ----

Group says root
Folder Acess: none
File Access: ----

Others says <blank>
Folder Access: ----
File Access: ----

Trying to change any of them does nothing, they just flick back to what they say above, clicking the button at the foot of that dialogue "Apply Permissions to Enclosed Files" just clears any choices I make above.

Its all a bit strange I think as when I created the share on this folder I ticked the box that said "Guest Access" so I would have thought the "Others" would include read/write access for anyone.

I may be barking up the wrong tree (or just plain barking, lol) being a beginner, but isn't there a command line thingy like chmod to change permissions I could use?

I just dont know how to specify the volume name at the command prompt because it does not seem to recognise the "xxGb Media" label the GUI displays.

I am probably asking the wrong questions, help!

ian

ps the object of the exercise was to make the folder read/write accessible to everyone on  the local network.

Ian,

There is indeed a chmod command and it works by using three digits to represent the permissions. You can only chmod without using sudo when you are the owner (eg you are in your own home folder). The digits in order are for owner, group and everybody. The numbers are 4 for read, 2 for write and 1 for execute. Like this:

Owner - Group - Everybody
R-W-X - R-W-X - R-W-X
4-2-1 - 4-2-1 - 4-2-1

so, if you want to give RWX permissions to owner and Group and RW permissions to Everybody it would be:

Owner - 4+2+1 = 7
Group - 4+2+1 = 7
Everybody - 4+2 = 6

Therefore command would be "chmod 776 <path then filename>"

Hope this helps....

Gary.

---

### Post by ians1 on 2008-06-20
How do I specify the path to another volume, like another disk as this is?

ian

---

### Post by Dedoimedo on 2008-06-20
Hello,

In Linux, there's only one root. There are no separate volumes like in Windows C:, D: etc.

Thus, you merely need to change to the desired directory:

cd "dir-name"

Cheers,
Dedoimedo

---

### Post by ians1 on 2008-06-20
Still can't do it, just says 

```
ians@ians-unix:/$ cd D_arc
bash: cd: D_arc: No such file or directory

```

but I can see it in the file browser

ian

---

### Post by ians1 on 2008-06-20
Its OK

I found it

```
ians@ians-unix:/media/disk$ dir
D_arc

```

Its just a bit obscure because the file browser thingy lists volumes by name eg "100Gb Media" or "New Volume" which don't corespond to the /media/disk as above.

ian

---

