---
title: "Emacs in the terminal"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by poosenki on 2008-05-30
Hi, I recently installed emacs and I'd like it to run through the terminal like usual, but it always pops up a new window with more of a GUI interface. There's nothing terribly wrong with that, but I'd prefer if it just worked as usual.

Does anyone know how to do that? I'm just typing the usual $ emacs file_name.

Thanks a lot!

---

### Post by badperson on 2008-05-30
I don't use emacs a lot, but I usually type
sudo emacs filename

---

### Post by poosenki on 2008-05-30
> **badperson said:**
> I don't use emacs a lot, but I usually type
sudo emacs filename
Thank you for the response, but it's still the same behavior whether or sudo or not. I appreciate it the thought though :)

---

### Post by ukripper on 2008-05-30
> **poosenki said:**
> Hi, I recently installed emacs and I'd like it to run through the terminal like usual, but it always pops up a new window with more of a GUI interface. There's nothing terribly wrong with that, but I'd prefer if it just worked as usual.

Does anyone know how to do that? I'm just typing the usual $ emacs file_name.

Thanks a lot!

try this in terminal 

```
 emacs -nw
```

---

### Post by poosenki on 2008-05-30
> **ukripper said:**
> try this in terminal 

```
 emacs -nw
```
Great, that works, thanks! I'll figure out how to set that and no splash to default and then I'm all set.

---

### Post by george9233 on 2008-05-30
If you want that to be persistent, adding an alias to your ~/.bashrc might be a good idea. Open ~/.bashrc with a text editor and add this line:
```

alias emacs='emacs -nw --no-splash'

```
Close the text editor and type in terminal:
```

source ~/.bashrc

```
And it's done.

---

### Post by HeWhoE on 2010-05-24
I make it systemwide like so...

Call emacs23-x with the -nw option, make a file with the following shell script in it, name it emacs and make it executable.

1. Create a shell script with the following two lines. Name the file emacs.
```
#!/usr/sh
/usr/bin/emacs23-x -nw
```

2. Make the script file executable.
[INDENT][FONT="Courier New"]chmod +x emacs[/FONT][/INDENT]

3. Move the file to your /usr/bin directory and overwrite the existing symbolic link.
[INDENT][FONT="Courier New"]sudo mv emacs /usr/bin/[/FONT][/INDENT]

**[SIZE="3"]La Fin[/SIZE]**
(until the package gets updated and your shell script gets overwritten).

---

