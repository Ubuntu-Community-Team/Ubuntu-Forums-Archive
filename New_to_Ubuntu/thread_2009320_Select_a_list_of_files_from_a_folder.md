---
title: "Select a list of files from a folder"
date: 2012-06-24
forum: New to Ubuntu
---

### Post by koosfoto.hu on 2012-06-24
Greetings,

I have a folder (with subfolders) with some thousands of photos. 
And there is a list of several hundred filenames (without the .jpg extension).

I would like to copy the photos identified in the list into another (empty) folder. 

How may I issue a command to **select ALL the files** in the list from within the folder and to **copy** them into another (empty) folder?

What program and which command to use?

Thanks,

Tamas

---

### Post by steeldriver on 2012-06-24
are there other jpg files in the directories that you *don't* want to copy? or can you just ignore the list and copy *all* jpg files?

what is the format of the list (plain text? one file per line?)

does the list include the directory path to each file or just the filename?

Try to be as specific as possible about what you want to do - with examples if possible

---

### Post by sudodus on 2012-06-24
I suggest that you use [FONT="Courier New"]rsync[/FONT] with the option [FONT="Courier New"]--files-from[/FONT]. Read ```
man rsync
``` particularly the text about 'files-from'

Typically something like ```
rsync --files-from=/tmp/foo /usr remote:/backup
```

---

### Post by koosfoto.hu on 2012-06-24
> **steeldriver said:**
> are there other jpg files in the directories that you *don't* want to copy? or can you just ignore the list and copy *all* jpg files?

what is the format of the list (plain text? one file per line?)

does the list include the directory path to each file or just the filename?

Try to be as specific as possible about what you want to do - with examples if possible


Thanks steeldriver,

Obviously the folder contains much more files, than the list. (Copy a folder is easy...)
The file-list can be in a plain text file, one fer line. (Now it is in a calc file, however, it is easy to make a simple text file from it...)

The list itself contains only the filenames (without extention, what is always .jpg. However, if it is needed, I can add the extention, as well easiyl in Calc)


Thanks,

Tamas

---

### Post by sudodus on 2012-06-24
> **koosfoto.hu said:**
> Thanks steeldriver,

Obviously the folder contains much more files, than the list. (Copy a folder is easy...)
The file-list can be in a plain text file, one fer line. (Now it is in a calc file, however, it is easy to make a simple text file from it...)

The list itself contains only the filenames (without extention, what is always .jpg. However, if it is needed, I can add the extention, as well easiyl in Calc)


Thanks,

Tamas
With [FONT="Courier New"]rsync --file-list[/FONT] you need the full file-names including the extension, and it should be a simple text file.

---

### Post by koosfoto.hu on 2012-06-24
> **sudodus said:**
> I suggest that you use [FONT="Courier New"]rsync[/FONT] with the option [FONT="Courier New"]--files-from[/FONT]. Read ```
man rsync
``` particularly the text about 'files-from'

Typically something like ```
rsync --files-from=/tmp/foo /usr remote:/backup
```

Hi sudodus!

Thanks for the command line.

Just for my understanding:

--files-from= here comes a simple text file with one file-name (complete with extention) per line

Then I put the folder from where I want to copy and the folder (can be local, I guess) to where I am to copy. 

Is it so?

Thanks,

Tamas

---

### Post by sudodus on 2012-06-24
> **koosfoto.hu said:**
> Hi sudodus!

Thanks for the command line.

Just for my understanding:

--files-from= here comes a simple text file with one file-name (complete with extention) per line

Then I put the folder from where I want to copy and the folder (can be local, I guess) to where I am to copy. 

Is it so?

Thanks,

Tamas
Yes

from [FONT="Courier New"]man rsync[/FONT]:
> Local:  rsync [OPTION...] SRC... [DEST]

---

### Post by koosfoto.hu on 2012-06-24
Thanks sudodus!

It worked. :)

Tamas

---

### Post by sudodus on 2012-06-25
I'm glad it worked :KS

Please click **Thread Tools** at the top of this page and mark this thread as SOLVED

---

### Post by koosfoto.hu on 2012-06-25
Thanks, again!

I marked it as SOLVED, as it is really solved. :)

---

