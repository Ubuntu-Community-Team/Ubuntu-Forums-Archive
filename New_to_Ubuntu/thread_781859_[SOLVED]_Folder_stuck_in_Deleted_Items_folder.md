---
title: "[SOLVED] Folder stuck in Deleted Items folder"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by ubername on 2008-05-04
Hi

I have a folder stuck in the Deleted Items folder (i.e. the folder which is opened when I click on the trash can on the task bar). It has some sub-folders which are owned by root, so when I try and remove it from deleted items, I get an error regarding permissions. (I have no idea how I managed to delete it in the first place, but somehow I have!)

My problem is that I can't locate the actual folder on the disk where this is stored. I have tried searching for files called ./Trash, ./Trash-0, ./Trash-root, etc. and find entries for these but none of them has the contents of my 'Deleted Items folder'. I have also tried searching for the folder name, but it doesn't find it (I guess the search function doesn't search for things in folders it thinks are trash) FWIW the folder is called pan-0.132)

If I could find the folder on the disk I am confident I could mess with the permissions enough to allow me to delete it. Any Help?

TIA
Trash

---

### Post by starcannon on 2008-05-04
I'd try a quick search

```

cd /
sudo find . -name pan-0.132

# or even perhaps

sudo find . -name pan-0.132*

# or possibly

sudo find . -name *pan-0.132*

```

Thats how I find where things are "really" at when I'm stuck with an unresponsive link to a file.

---

### Post by TeoBigusGeekus on 2008-05-04
In Gutsy:
```
sudo rm /home/yourusername/.Trash/*
```

In Hardy:
```
sudo rm /home/yourusername/.local/share/Trash/files/*
```

---

### Post by Oldsoldier2003 on 2008-05-04
or if you are not comfortable with the command line

```
gksu nautilus
```
to start a root nautilus and then navigate to the folders specified above and remove the files. You may need to CTRL+H to show hidden files in Nautilus.

---

### Post by Fran89 on 2008-05-04
Thank you this also solved my problem, but i never recomend the rm command i'd rather sudo nautilus, that brings a root nautilus and navigate to the directory and delete... in my opinion its safer..

---

### Post by kwacka on 2008-05-04
Sorry, but I have to disagree.

'gksudo nautilus' gives you the same rights as a 'sudo rm' command.

Is it easier to click on a file/folder in error, or to type out its name by mistake?

---

### Post by ubername on 2008-05-04
> **starcannon said:**
> I'd try a quick search

```

cd /
sudo find . -name pan-0.132

# or even perhaps

sudo find . -name pan-0.132*

# or possibly

sudo find . -name *pan-0.132*

```

Thats how I find where things are "really" at when I'm stuck with an unresponsive link to a file.

Thanks very much. This has done the trick.

Mods: Please mark this thread as resolved.

---

### Post by Oldsoldier2003 on 2008-05-04
> **kwacka said:**
> Sorry, but I have to disagree.

'gksudo nautilus' gives you the same rights as a 'sudo rm' command.

Is it easier to click on a file/folder in error, or to type out its name by mistake?

Both methods have their pitfalls, bottom line is anytime you sudo whether it be in the terminal or in the GUI, you need to think twice and double check. :)

---

### Post by ubername on 2008-05-04
> **starcannon said:**
> I'd try a quick search

```

cd /
sudo find . -name pan-0.132

# or even perhaps

sudo find . -name pan-0.132*

# or possibly

sudo find . -name *pan-0.132*

```

Thats how I find where things are "really" at when I'm stuck with an unresponsive link to a file.

Hi Starcannon

You might want to check your links in your sig: I was so happy with your answer that I thought I would see what else you recommended, but your 'resolved link' is out of date, I think.

---

