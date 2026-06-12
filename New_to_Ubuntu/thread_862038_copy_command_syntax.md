---
title: "copy command syntax"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by expatCM on 2008-07-17
I have a directory with multiple sub-directories.  Each sub-directory has .wav, .mps and in the structure m3u files.

I want to copy this directory and its structure to another location. 

In doing so I do not want to copy the .wav file but I would like to copy everything else.

Since the source and destination are on my server I need to try and work out the correct command to do this.

I think this is the cp -R command (or is it cp -a?) but how do I filter out the .wav files?   I took a look at man cp and since I cannot find the answer there I guess I may not be approaching this in the right way.

Any suggestions please.

---

### Post by dominiquec on 2008-07-17
The simplest way I can think of is to delete the wav files after you've copied them.  You can do this using the find command.  

On the parent directory this is what you would run:

```
find . -name "*.wav" -exec rm {} \;
```

---

### Post by sdennie on 2008-07-17
From the base of the directory try:

```

tar cvf files.tar `find . -type f ! -name "*.wav"`

```

That will create a tar file called files.tar without an .wav files that you can untar anywhere you want.

---

### Post by expatCM on 2008-07-17
Now that I can see the way I just looked up your command syntax and understand the approach ... thanks for that.

I wonder, is there another way.... ?   There is a reason - Space is a bit of an issue on the destination (it ran out a few days ago and made everything stop) and so copying over and then deleting may but a bit of a challenge.  I would prefer to copy over the net result.

I guess a workaround would be to copy the directory structure to another location, run the command and then move the resulting directory structure.

---

### Post by expatCM on 2008-07-17
I never for a moment considered using the tar command.  That is creative thinking :)

I need to look this up and understand what all the switches do ....  I will post back shortly ....

---

### Post by The Cog on 2008-07-17
If space is an issue, you could pipe the output from the tar command to a "tar -x"  process, never actually generating the intermediate tar file as an entity on disk.

---

### Post by hyper_ch on 2008-07-17
you could first create a text files with all the files in there and sort the .wavs out and then you use a bash script that just runs down the list and copies each file (and make necessary dirs)

---

### Post by Dedoimedo on 2008-07-17
Hi,

You can do this:

```
cp -R *?[^.wav] /destination
```

This will copy all files except (^) those with .wav ...
See if this works out.

Or try this:

```
ls -1 | grep -v "^.wav$" > list
cp -R /destination <list
```

The first command will remove all .wav at the end of the string ($) and save them to a list, then you will use the list as input to copy ...

Not near a Ubuntu machine now (working in evil Win corpo), so cannot verify the minutes of the commands, but they should work.

Furthermore, you can also use xargs to combine the two commands into a single line.

Dedoimedo

---

