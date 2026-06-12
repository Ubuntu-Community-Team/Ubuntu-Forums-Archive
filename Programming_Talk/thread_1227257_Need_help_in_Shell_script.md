---
title: "Need help in Shell script"
date: 2009-07-30
forum: Programming Talk
---

### Post by oakdeveloper on 2009-07-30
Hi,

I am a newbie to shell scripting. Recently I downloaded a programming tutorial from the internet as an ISO image and when I mounted it I found that all the files had their extensions suffixed with ";1" because of which the programs to run them couldn't recognize it. For example, index.htm was named as INDEX.HTM;1 and index.pdf was named as INDEX.PDF;1 and so on...

Now I need a Shell script to rename the extensions and also change the file names from upper case to lower case. I found this command
```
rename 's/\.HTM\;1/\.html/' *.HTM\;1
``` to rename extensions which works fine. But I want to make it work recursively. Please help me..

Thanks,
Babu

---

### Post by Dill on 2009-07-30
Try combining **find** with **xargs**:

```
find -name '*.HTML\;1' | xargs rename 's/\.HTML\;1/\.html/'
```

That should work recursively and rename each file that matches the specified name pattern.

Cheers,
Dill

---

### Post by oakdeveloper on 2009-07-30
> **Dill said:**
> Try combining **find** with **xargs**:

```
find -name '*.HTML\;1' | xargs rename 's/\.HTML\;1/\.html/'
```That should work recursively and rename each file that matches the specified name pattern.

Cheers,
Dill

Thanks Dill. It didn't work for me. But I have figured out myself to do it recursively. Here is the code:

```
find . -name '*.HTM\;1' -exec rename 's/\.HTM\;1/\.html/' *.HTM\;1 {} \;
```

I have a problem now. I want to change the filenames from uppercase to lowercase. There are several hundreds of files. Can someone let me know how to change the case of the filename with a command or a script ?

---

### Post by Dill on 2009-07-30
Check out the **tr** man page. If you wanted to change "HELLO" to lowercase, for instance, you'd want:

> echo "HELLO" | tr "[:upper:]" "[:lower:]"

Also, just out of curiosity, what about the xargs script didn't work for you? I'm a bit new to xargs myself and I'm trying to figure out where I might have gone wrong : ).

Cheers,
Dill

---

### Post by stroyan on 2009-07-30
xargs would fail as used if there were spaces in file names.
That can be handled using options to delimit file names with null characters.
```
find -name '*.HTML\;1' -print0 | xargs -0 rename 's/\.HTML\;1/\.html/'
```

The default mount options for an iso9660 on ubuntu should map ";1" to "" and uppercase to lowercase.  I don't know why you are seeing the raw names.
The default should use the "map=normal" option that does the mapping.
That is document in the "Mount options for iso9660" part of "man mount".
Here is an example that sets those explicitly, although that shouldn't be needed.
```

mkdir example_dir
sudo mount -o loop -t iso9660 -o map=normal example.iso example_dir

```

---

### Post by oakdeveloper on 2009-07-31
> **stroyan said:**
> xargs would fail as used if there were spaces in file names.
That can be handled using options to delimit file names with null characters.
```
find -name '*.HTML\;1' -print0 | xargs -0 rename 's/\.HTML\;1/\.html/'
```The default mount options for an iso9660 on ubuntu should map ";1" to "" and uppercase to lowercase.  I don't know why you are seeing the raw names.
The default should use the "map=normal" option that does the mapping.
That is document in the "Mount options for iso9660" part of "man mount".
Here is an example that sets those explicitly, although that shouldn't be needed.
```

mkdir example_dir
sudo mount -o loop -t iso9660 -o map=normal example.iso example_dir

```
Thanks so much stroyan!!! Even after renaming files and extensions, I found many broken links. But after mounting the iso manually with your command, all things fell in place perfectly.
Thanks again! 

Regards,
Babu

---

### Post by immeëmosol on 2009-07-31
It says on [http://mamchenkov.net/wordpress/2005/09/26/recursively-renaming-files-in-linux/](http://mamchenkov.net/wordpress/2005/09/26/recursively-renaming-files-in-linux/) to do something like this :
rename 's/\.HTM\;1/\.html/' `find . -name *.HTM\;1`

In order to rename al files ending with .HTM;1 into files ending with .html .
So that's about the same as with xargs (or find with -exec) only a bit shorter perhaps .

---

