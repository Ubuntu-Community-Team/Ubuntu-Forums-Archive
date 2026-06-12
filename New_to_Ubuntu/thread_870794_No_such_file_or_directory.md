---
title: "No such file or directory"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by anlaoch on 2008-07-26
Hi.

I've tried using Terminal (as root) to access a folder *I* set up, so I can configure Transmission's latest release.  I don't know what's up, but when I navigate into my home folder, Terminal denies access, indeed the existence, of any of my folders including "Desktop", "Videos", "Music", "Documents" etc.

I even experimented with ~/ , but still the same "no such..." messages.

Any suggestions what I'm doing wrong?

Thanks in advance.

---

### Post by Bachstelze on 2008-07-26
Could you please explain precisely what you're doing?

---

### Post by Growbag on 2008-07-26
Can you post here the exact commands you typed?  That would be helpful.

You can see what you previously typed by opening a terminal again, and pressing the up arrow.

It saves all the commands for each user, so if you were running the commands as root (ie you did a sudo su first), then you will have to get to root first to see the previous commands you typed as root.

Does that make sense?  Sorry if that is confusing.

When making a new folder, always make sure you are in the place you need to be first by changing to that folder, ie: **cd /**  will get you to the root folder, **cd ~** will take you to your home folder (if you are root at the time, it will send you to **/root/**).

And of course the usual lecture:  Be careful what you do as root, nasty things can be done without realising it! :).

---

### Post by eightmillion on 2008-07-26
I suspect that you're going to ~/. You have to remember that this points to the root user's home directory when you are root which is /root. To navigate to your own home directory you'll have to enter the full path.

---

### Post by anlaoch on 2008-07-26
I've downloaded the following file in order to get the latest version of Transmissionbt:

transmission-1.22.tar.bz2

I've extracted it to a folder called transmission-1.22 in the following directory:

filesystem/home/anlaoch/software

According to the instructions, I have to cd to the directory transmission-1.22 folder and do a ./configure, and then some other stuff.  So, I open Terminal, do a "dir" and get the following results:

Desktop    Examples  PDF       Public	 Templates
Documents  Music     Pictures  Software  Videos

Makes sense to me then to do a "cd software", but then I get the error messages mentioned earlier.  The commands I've tried include:

cd software
cd /software
cd ~/software

I've done the same with the other folders, and desktop, but get the same message each time.

Hope that clarifies.

---

### Post by anlaoch on 2008-07-26
The commands I entered as root (after sudo su) are the same commands I entered as myself, i.e. cd software, cd ~/software, cd /software, cd /anlaoch/software etc.

Any suggestions?

Thanks,

---

### Post by eightmillion on 2008-07-26
Try 'cd /home/anlaoch/software'. If that doesn't work post the output of 'pwd' please. When you are root, *~/software* points to */root/software* instead of */home/anlaoch/software*.

---

### Post by CatKiller on 2008-07-26
> **anlaoch said:**
> I've downloaded the following file in order to get the latest version of Transmissionbt:

transmission-1.22.tar.bz2

I've extracted it to a folder called transmission-1.22 in the following directory:

filesystem/home/anlaoch/software

According to the instructions, I have to cd to the directory transmission-1.22 folder and do a ./configure, and then some other stuff.  So, I open Terminal, do a "dir" and get the following results:

Desktop    Examples  PDF       Public	 Templates
Documents  Music     Pictures  **Software**  Videos

Makes sense to me then to do a "cd **software**", but then I get the error messages mentioned earlier.

Case is important. *cd software* is not the same as *cd Software*.

---

### Post by Growbag on 2008-07-26
Linux is always **case sensitive**, the folder *software* is NOT the same as folder *Software*!

And **dir** is an msdos command, how are you doing that under Linux?

Open a terminal again, and this time type:

```
cd S
```

Type that EXACTLY as you see it, and after you type the capital "S", press the TAB key twice quickly.

It will give you a list of everything in the current folder starting with a capital S.

Then type the next letter that corresponds to the file/folder you want, in this case the letter "o", and press TAB once to autocomplete the pathname.

Cool eh?

Or simply type:

```
cd ~/Software
```

Using TAB autocompletion is the best way though, it makes it so much easier, especially when you get nasty filenames like file.1.6.889776-34-5.sh etc', which would be a pain in the rear to type in full!

---

### Post by CatKiller on 2008-07-26
> **Growbag said:**
> And **dir** is an msdos command, how are you doing that under Linux?

For ease-of-use, **dir** is defined as an alias of **ls** that returns results that look like the results from dir. I can't remember exactly what the ls options are.

---

### Post by stevoo on 2008-07-26
dir ? i have not used that in  a long time.

Rememeber in linux everything is case sensitive. 
So software is not the same like Software

You should be trying 
cd filesystem/home/anlaoch/Software
of cd ~/Software

if you are still having problems 

go into anlaoch dir
and  type cd S
press tab once. It will normally fill the next on it own if there is nothing else starting with S. If there is nothing will happen. 
That will get you in there

---

### Post by anlaoch on 2008-07-26
Thanks to all who helped.  It was as simple as using using the correct case in moving from folder to folder.

I'll know better now :-)

---

