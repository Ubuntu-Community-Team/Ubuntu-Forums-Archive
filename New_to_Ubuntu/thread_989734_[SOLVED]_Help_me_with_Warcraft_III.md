---
title: "[SOLVED] Help me with Warcraft III"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by Samerious on 2008-11-21
Alright so I can't get this bad boy to work. The first problem I'm having is the fact the graphics are really messed up and the second is there is a lot of lag. 
my specs are:

Intel(R) Pentium(R) 4 CPU 2.40GHz
             total       used       free     shared    buffers     cached
Mem:           867        624        242          0          7        299
-/+ buffers/cache:        317        549
Swap:         1655        134       1520
Intel Corporation 82865G Integrated Graphics 
There is a screen shot of what it looks like when i open it up.

---

### Post by Crafty Kisses on 2008-11-21
Do you have desktop effects enabled?

---

### Post by Wisp558 on 2008-11-21
Have you tried making a launcher (or running it from the terminal as something like...

wine /Anydirectory/andsoon/war3.exe **[B]-opengl**[/B]

Because without OpenGL... it will be screwy.

---

### Post by Samerious on 2008-11-21
I didn't I disabled those bad boys in hope it would up the speed a bit... (Is it normal for me to be useing so much RAM when i only have firefox up? )

---

### Post by Wisp558 on 2008-11-21
Hmmm... I know firefox uses a lot of RAM on MS OSes, but it's on MS.

My Ubuntu FF eats up about 40 megs...

---

### Post by Samerious on 2008-11-21
I don't know for some reason when I try to run
/home/samerious/.wine/drive_c/Program Files/Warcraft III/war3.exe -opengl
in the terminal it says 
/home/samerious/.wine/drive_c/Program Files/Warcraft III
No such file or directory

---

### Post by Wisp558 on 2008-11-21
As this is the Beginner forums...

Have you tried 

"~/.wine/drive_c/Program Files/Warcraft III/war3.exe" -opengl

Note the quotations, as Linux doesn't like spaces...

Or you could make a symlink and follow that to cut the Directory name...

---

### Post by Samerious on 2008-11-21
Should I put my name somewhere in that command?
Symlink , I have no idea what or how.

---

### Post by Wisp558 on 2008-11-21
Oh, sorry.

~/ is short for your home directory, which is /home/samerious

You can make a symlink by using the command ln -s [source] [destination]


BUT I have WC3 working without any linking, and I wouldn't really advise it.

You could read the wikipedia article on symlinks, I don't think I'd be great at explaining it in simple terms....



The exact command I use to run WC3 is

wine "/media/Arnesthas/Program Files/Warcraft III/Warcraft III.exe" -opengl

---

### Post by Samerious on 2008-11-21
is media a folder you have WC III installed under?

---

### Post by Wisp558 on 2008-11-21
sorry, I didn't mean to confuse you. No, it's where my WC3 is installed. /media/Arnesthas is my mounted XP partition.

So Instead of /media/Arnesthas, you would be under ~/.wine/drive_c and so on.

---

### Post by Samerious on 2008-11-21
Ok for some reason it doesn't want to register my Program Files Folder... I ran different commands up until so ~/.wine/drive_c told me it was a valid directory but
 ~/.wine/drive_c/Program_Files/ says its not a directory ... I also tried "~/.wine/drive_c/Program Files" same result Not a file or directory...

---

### Post by Wisp558 on 2008-11-21
First... underscores are NOT spaces.
My favorite method for doing spaces would be...

```
/drive_c/Program\ Files/etc...
```

The backslash forces Linux to interpret the space literally.

so run 

```
 cd ~/.wine/drive_c/Program\ Files/ 
```


After that... I don't know.

---

### Post by Samerious on 2008-11-21
Awesome that totally worked now we got the route files finally fixed lets see if the open GL does the trick! AWESOME! It did... Much Appreciated...

---

### Post by Samerious on 2008-11-21
Rofl onto the next problem! Connecting to Battle net.

---

### Post by Wisp558 on 2008-11-21
Oh dear...

I haven't done that yet, but WC3x is supposedly a platinum under wine, so it SHOULD work, in theory...

...wait... just did it, but it kicks me off, 'cause I have a no-cd patch in. Just make sure to choose the right region and so on.


Have fun ;P


Oh, if you haven't already, you can make a launcher for it. If you don't know how, I'll tell you. I'm feeling philanthropic.

---

### Post by Samerious on 2008-11-22
Alright thanks! Appralently i just had to chose a server should have chcecked those few things first before i freaked out XD...

---

