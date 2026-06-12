---
title: "Script to combine files"
date: 2008-10-24
forum: Programming Talk
---

### Post by rye_ on 2008-10-24
Hi all,

A useful little utility I have written.
It automates the combining of split files (using cat), scanning the directory within which you use the script and combining each collection of split files into single files, named in accordance with the split files.

e.g. hello rye_.001, hello rye_.002, bye.001, bye.002 in a directory will results in the creation of files "hello rye" and "bye". 

The script moves the combined files to a sub-directory CURRENT_DIR/Combined files

To allow this to be run in the nautilus menu, add the script to
 ~/.gnome2/nautilus-scripts

P.S. its a ruby script (so install ruby, sudo apt-get install ruby)

Cheers,
Ryan

---

### Post by ghostdog74 on 2008-10-24
so your script basically does what split command does?

---

### Post by nvteighen on 2008-10-25
> **ghostdog74 said:**
> so your script basically does what split command does?
I believe it does the opposite... Then, it does the same as cat...

But, anyway, if it helped you to learn something or to do the time, there's nothing bad on reinventing the wheel!

EDIT: No, I notice that's a Nautilus script... Hey, that's a nice idea!!

---

### Post by rye_ on 2008-10-25
I just does what the cat command does, using cat.....

but what if I've got 10+ components of a split file, and can't be bothered to type them all in at the command line?
 or If I've got numerous files which have in-turn been split in a directory and I want them to be combined, should I have to enter each component file name into the terminal, for every file I wan't to combine.

I've always found it an unnecessary pain.  This removes the need to (open a terminal, or) think at all


Ryan

---

### Post by ghostdog74 on 2008-10-25
> **rye_ said:**
> 
but what if I've got 10+ components of a split file, and can't be bothered to type them all in at the command line?

by splitting your files up with a prefix , as in 
```

split -b 50m -d input.avi output

```
and then join them up using cat
```

cat output* > combined.avi

```
you are still able to get back the original. you don't have to type in 10+ components like you have said.

---

### Post by rye_ on 2008-10-25
EDIT: I'M THINKING ABOUT SELLING MY SCRIPT TO NASA, IT'S NOT INTENDED TO BE ANYTHING OTHER THAN A VERY EASY POINT AND CLICK AFFAIR.

how would you join the following split files, into there respective complete files? Also since things start to get messy, shift the split files into a new folder.

dog bowl.001
dog bowl.002
devil.001
devil.002
hippo hi 5 you obama or the other one.001
hippo hi 5 you obama or the other one.002
hippo hi 5 you obama or the other one.003
gig.001
gig.002
gig.003
gig.004
gig.005
gig.006
gig.007
gig.008
the theme tune from guys and dolls.001
the theme tune from guys and dolls.002
the theme tune from guys and dolls.003
Hell* &6%, 445.001
Hell* &6%, 446.002
Hell* &6%, 447.003

Imagine more of these file too.  I know I tend to accumulate all kinds of rubbish.

Of course you can go into the terminal, have to painstakingly look at the exact name of a potentially long and complicated file name....

or you can right-click in nautilus, click on my script and not have to do the above

---

