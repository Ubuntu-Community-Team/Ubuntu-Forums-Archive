---
title: "[SOLVED] force copy or delete files locked in .trash on flash drive"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by LTFC2020 on 2008-09-05
hi
I have a flash drive that although is virtually empty, only has 15mb of storage left
ctrl H reveals a .trash folder that has lots of files in it (some I want to keep and some I want to delete)
I am unable to do this as I do not have permission
I have tried sudo nautilus but the disk does not show up when I do this
How do I force permission to delete and copy these files?
Thanks

---

### Post by iaculallad on 2008-09-05
What about using the terminal. Change directory to your mounted Flash Drive's location and try issuing the command below:

```
sudo rm -rf /mountpoint/Flashname/.Trash-your_username/*
```

---

### Post by Elfy on 2008-09-05
> **iaculallad said:**
> What about using the terminal. Change directory to your mounted Flash Drive's location and try issuing the command below:

```
sudo rm -rf /mountpoint/Flashname/.Trash-your_username/*
```

That would delete them all :)

(some I want to keep and some I want to delete)

Why doesn't it show in gksudo nautilus?

Look in /media for the flash drive

---

### Post by LTFC2020 on 2008-09-05
I don't want to rm - rf the whole .trash folder as I wish to keep some of the files

---

### Post by Elfy on 2008-09-05
If you can't do it in nautilus then use the terminal but chnage to the directory and do it there for each you want to delete.

IF the disk is mounted as disk for instance

```
cd /media/disk/.Trash
``` - or whatever the folder is called and then use ```
sudo rm nameoffile
```

---

### Post by iaculallad on 2008-09-05
> **forestpixie said:**
> That would delete them all :)

(some I want to keep and some I want to delete)

Why doesn't it show in gksudo nautilus?

Look in /media for the flash drive

Aaayyyy.... The OP wanted to keep some files. That command would be dangerous for you to use. Try other alternative ways. I mislooked that part :)

---

### Post by LTFC2020 on 2008-09-05
iaculallad
no worries
luckily I've seen enough of those posters with the **don't use rm - rf warning** at the bottom :)

---

### Post by LTFC2020 on 2008-09-05
I tried /media/disk/.Trash-richard

and got this reply

bash: /media/disk/.Trash-richard: is a directory

what is the next step?

---

### Post by aomlives on 2008-09-05
I think you forgot the cd command. It should be like this:

```
cd /media/disk/.Trash-richard
```cheers

---

### Post by iaculallad on 2008-09-05
> **LTFC2020 said:**
> I tried /media/disk/.Trash-richard

and got this reply

bash: /media/disk/.Trash-richard: is a directory

what is the next step?

On your terminal:

```
cd /media/disk/.Trash-richard
```

and while inside that directory, it's time for you to delete the files you want removed with:

```
sudo rm filenames_you_want_deleted
```

---

### Post by LTFC2020 on 2008-09-05
does that mean I can safely use:
sudo rm nameoffile

and keep files with the same name on my hard disk?

i.e. am I just deleting the flash drive files with that name?

or will any file in my home directory be deleted too?:confused:

---

### Post by Elfy on 2008-09-05
Then use dir or ls to get names of files then delete the ones you want. Or if it's quicker might be worth making a folder and moving files you want ot keep so you can empty the trash.

---

### Post by LTFC2020 on 2008-09-05
sorry people
I assumed the cd then space was a typo
this terminal can be :confused: to me sometimes

richard@richard-laptop:~$ cd /media/disk/.Trash-richard
[email]richard@richard-laptop:/media/disk/.Tras[/email]h-richard$ 

ready to go

thanks

---

### Post by Elfy on 2008-09-05
> i.e. am I just deleting the flash drive files with that name?
or will any file in my home directory be deleted too?

You will only be deleting files in the folder you are currently in unless you specify a path to your /home

---

### Post by LTFC2020 on 2008-09-05
oh... I spoke too soon

[email]richard@richard-laptop:/media/disk/.Tras[/email]h-richard$ sudo rm IPCC2007
rm: cannot remove `IPCC2007': Is a directory
[email]richard@richard-laptop:/media/disk/.Tras[/email]h-richard$ 

incidently what is the difference between a file and a directory?

---

### Post by Elfy on 2008-09-05
A directory could contain files - but a file is a ... file :) - unless of course the file is an archive

You need to use -r 

```
sudo rm -r directoryname
```

---

### Post by aomlives on 2008-09-05
> **LTFC2020 said:**
> incidently what is the difference between a file and a directory?

A directory is a way to contain and group other files

I think that sort of explains it :)

You might want to take a look at the [Wikipedia]("http://en.wikipedia.org/wiki/Directory_%28file_systems%29") page though.

---

