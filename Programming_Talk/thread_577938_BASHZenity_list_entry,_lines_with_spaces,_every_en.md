---
title: "BASH/Zenity: list entry, lines with spaces, every entry seperate"
date: 2007-10-16
forum: Programming Talk
---

### Post by ryanVickers on 2007-10-16
I'll elaborate on my title - as you can see this code below:

```
cd "$where"
list=$(ls -w 1)

folder=$(zenity --entry --title "Pick the File/Folder to Archive" --width 400 --text "What is the folder/file you wish to archive called?" --entry-text="$list");
```$where is just a place, no problems or complications there, but $list is a list of all the files/folders in $where, and I need some fine tuning...

I would like it to keep entries with a space on the same level, ex. a folder called "new folder" should show up as a single entry in the list as "new folder", but instead...

there are 2 ways - way one (with quotes) gets everything on one line and separates the names with one of those characters like a box with numbers in side (this one happens to mean "new line").

way two, without quotes or anything special lists everything in a nice list, but words with spaces, ex. a file fames new file, shows up as 2 entries "new" and "file".

Is there some way I can get the best of both worlds?  Single names, even with a space on their own line, and everything in a nice list!? :confused:

Edit: to clear things up, I've added screenshots ;)
How it *shoudl* be is like way two, but with new place as "new place", and **not** as "new" "place" :(

---

### Post by ryanVickers on 2007-10-16
what?  NO ONE has ***any*** idea of how I could do this!?!?! ](*,)

---

### Post by ryanVickers on 2007-10-16
[FONT=Fixedsys][COLOR=DarkRed][B][SIZE=4]Basically what I'm asking is "Is there a way to tell zenity to separate into new rows only on a certain character rather than just space?"

PLEASE HELP MEEE!!!! :cry:
[/SIZE][/B][/COLOR][/FONT]

---

### Post by cwaldbieser on 2007-10-17
> **ryanVickers said:**
> [FONT=Fixedsys][COLOR=DarkRed][B][SIZE=4]Basically what I'm asking is "Is there a way to tell zenity to separate into new rows only on a certain character rather than just space?"

PLEASE HELP MEEE!!!! :cry:
[/SIZE][/B][/COLOR][/FONT]

First, our post has not been up very long (only 6 hours).

You could try something like:
```

files=$(ls -Q)
eval zenity --list --column=caption $files

```
The first line gets a quoted list of files.
The second line tells your shell to re-parse, so the quotes are interpreted as part of the command.

I am not sure why you are using an entry in you example, a list dialog just made more sense to me.

---

### Post by Jacks0n on 2007-10-17
You need to set the variable "IFS", to whatever the separator character(s) are for the list. By default it's a single space, but in this case, it's a line. So...

```

cd "$where"
list=$(ls -w 1)

IFS="
"

folder=$(zenity --entry --title "Pick the File/Folder to Archive" --width 400 --text "What is the folder/file you wish to archive called?" --entry-text=$list);

```

should work.

But if you're selecting a directory, zenity's got

```

zenity --file-selection --directory

```

---

### Post by ryanVickers on 2007-10-17
Thanks a lot - I'll try both those options ASAP ;)

as to why I'm not using a list, don't worry, I have a very good reason :p (but don't think I haven't thought about it! :))

---

### Post by ryanVickers on 2007-10-17
**A few more questions:**[INDENT] 1. Can I set the file browser to accept file AND folders? 8-[
2. Can I set the file browser to show text? (probably not, right? ;))[/INDENT]

---

### Post by Jacks0n on 2007-10-23
1. Don't think so. If it's important you could always do a selection box, then an if statement whether it's a file or directory.

2. You can set the title with --title="Title goes here...", but otherwise not. I just do an info box before hand.

---

### Post by ryanVickers on 2007-10-23
ok, that's what I thought.  Even the idea about the selection box ;)

---

