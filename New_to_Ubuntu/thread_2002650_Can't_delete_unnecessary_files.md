---
title: "Can't delete unnecessary files"
date: 2012-06-13
forum: New to Ubuntu
---

### Post by Airycat on 2012-06-13
I have a recup folder that is filled with 6gb of .dbf files. When I try to delete them the computer tells me I don't own them and have no permission to delete them. I just deleted a ton of other locked recup folders by running gksu nautilus, but when I run it now it simply opens a home folder that has  a desktop and a folder named GNUstep with an empty one named Library inside. This is not my normal Home folder. The unwanted folder is in my pictures folder which is in my normal Home folder. I have no idea how it got there and I can't move it.

How do I get rid of it? 

TIA
~Faith

---

### Post by idoitprone on 2012-06-13
> **Airycat said:**
> I have a recup folder that is filled with 6gb of .dbf files. When I try to delete them the computer tells me I don't own them and have no permission to delete them. I just deleted a ton of other locked recup folders by running gksu nautilus, but when I run it now it simply opens a home folder that has  a desktop and a folder named GNUstep with an empty one named Library inside. This is not my normal Home folder. The unwanted folder is in my pictures folder which is in my normal Home folder. I have no idea how it got there and I can't move it.

How do I get rid of it? 

TIA
~Faith

Do you know how to use commandline

cd to the dir that has the folder

post the output of these 2 commands
```

ls -l
whoami

```
I wonder who own those files in question

---

### Post by Airycat on 2012-06-13
Thank you.

I'd give a direct answer to your question if I understood it. (Punctuation?) I'm really a ***TOTAL N00B*** with Linux/Ubuntu.

commandline -- Is that opening a terminal to type in a command? ... I can do that. If that's not it, I have no idea what you mean.

Have no clue what you're asking/telling in the second line. I don't have a CD for this problem. Are you asking me to make one? Or does cd mean something else here?

Third line depends on first two.

The files are mine from when I did a search for lost files. I'm the only user on the computer and I'm the administrator. I don't know why it won't let me do things. *IF* this file were directly in the home folder, I could do it because it did let me remove all the other (200+) folders it came up with in my search. I think this was a false start (I'd forgotten to limit the parameters) and just went to the wrong folder. I'm just glad they all didn't go there!

---

### Post by Peripheral Visionary on 2012-06-13
I don't use Ubuntu, but if **Computer Janitor** is already installed, find it in the System menu and run it (you will need your root (Administrator) password. If it's not installed, open Synaptic Package Manager or Ubuntu Software Center and install it.

Another application that does a better job of cleaning up unnecessary files is called **Bleachbit**. Run "as root" (Administrator), it wipes away all the old unused stuff, cleans up cache, and deletes "orphaned" files that aren't used anymore.

---

### Post by drs305 on 2012-06-13
You can open nautilus as root - just be careful what you delete. Use SHIFT-DEL so the deleted folders/files are completely removed and not placed in root's Trash.

```
gksu nautilus ~/Pictures
```

---

### Post by Airycat on 2012-06-14
Thank you, drs305! That's what I needed.

---

