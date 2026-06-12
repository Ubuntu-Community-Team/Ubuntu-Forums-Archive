---
title: "Copy file with rename in Nautilus?"
date: 2011-12-05
forum: New to Ubuntu
---

### Post by Laobi on 2011-12-05
Is there a way to copy a file in Nautilus which would allow to rename the file while copying?  Something like "Copy as..." or like in GnomeCommander's copy dialog box?

---

### Post by mapes12 on 2011-12-06
With the file open you should be able to go File>Save as...

---

### Post by pierreyy on 2011-12-06
hey this is what ur lookin for:

**cp**: The **cp** command will make a copy of a file for you.  Example:  **"cp file foo"**   will make an exact copy of "file" and name it "foo", but the file   "file" will still be there. If you are copying a directory, you must use   **"cp -r directory foo"** (copy recursively). (To  understand what  "recursively" means, think of it this way: to copy the  directory and  all its files and subdirectories and all their files and  subdirectories  of the subdirectories and all their files, and on and on,   "recursively")

the link is:
```
https://help.ubuntu.com/community/UsingTheTerminal
```check it out.

ps this is done using  the terminal.

---

### Post by Laobi on 2011-12-07
Thanks for replaying.  I know for the **cp** command, it does exactly what I need, but I was hoping for a quick method in Nautilus.

Nautilus gives a dialog to change the name of the file while copying to another directory only if a file with the same name already exists in the destination directory.  I was hoping there was a way to get this dialog regardles of the file with the same name already existing in the destination directory or not (ex. with some qualifier key like ctrl, alt or something during drag&drop action).

I guess I'll just have to use the two step process of copying and then renaming.  It's not that much trouble after all. :)

---

### Post by enjoijesus94 on 2011-12-07
In Terminal
gksudo nautilus

> Remember Running As Root Is Dangerous

Then Find The Selected File And Rename It

:popcorn:

---

### Post by Bodsda on 2011-12-07
You could write a nautilus script to offer this functionality, but im wondering if its really worth it

Scenario 1 - A 'Copy as command'
1) Right click
2) Click 'Copy As'
3) Enter new name into dialog
4) Press ok

Scenario 2
1) Highlight
2) CTRL+C
3) CTRL+v
4) F2
5) Type new name

Scenario 2 has 1 extra step, but as you dont need the mouse it will be a lot faster, and you dont need any custom scripts.

Bodsda

---

### Post by tuddy666 on 2011-12-07
> **enjoijesus94 said:**
> In Terminal
gksudo nautilus



Then Find The Selected File And Rename It

:popcorn:

But that just renames the file. It doesn't copy -and- rename, which is what OP was asking for. Oh, and you're telling them to run Nautilus as a superuser, which is bad practice (unless you really, really need to run a graphical file manager as root for whatever reason).

Honestly, OP, your best bets are to either use cp from a terminal, as explained above, or to copy and manually rename. It's a step backwards, yes, but it works.

---

### Post by enjoijesus94 on 2011-12-07
Got A Point Tuddy666

Thanks For The Heads Up:lolflag:

---

### Post by Laobi on 2011-12-07
> **Bodsda said:**
> You could write a nautilus script to offer this functionality, but im wondering if its really worth it

Scenario 1 - A 'Copy as command'
1) Right click
2) Click 'Copy As'
3) Enter new name into dialog
4) Press ok

Bodsda

Bodsda, thanks for the tip!

I've managed to quickly cobble up a Nautilus script.  Not really drag&drop, but this will do fine! :)

Here it is:
```

#!/bin/sh
# Nautilus "Copy as..." script

sfl=$@
spth=$(zenity --file-selection --filename="$sfl" --save --confirm-overwrite)
cp "$sfl" "$spth"

```

---

### Post by Bodsda on 2011-12-07
> **Laobi said:**
> Bodsda, thanks for the tip!

I've managed to quickly cobble up a Nautilus script.  Not really drag&drop, but this will do fine! :)

Here it is:
```

#!/bin/sh
# Nautilus "Copy as..." script

sfl=$@
spth=$(zenity --file-selection --filename="$sfl" --save --confirm-overwrite)
cp "$sfl" "$spth"

```

Good work!

Bodsda

---

