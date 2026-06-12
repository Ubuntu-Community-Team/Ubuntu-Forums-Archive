---
title: "find all gedit files?"
date: 2016-11-03
forum: New to Ubuntu
---

### Post by jxk2 on 2016-11-03
hej there,

I apologize in advance if that might be a poor question. I went through the forum used the search engine but can't figure it out proberly.

basically I made a backup some time ago. I have that backup now in one folder on a freshly installed ubuntu machine.

back then I made some notes and saved it just as a plain/text gedit file. now I am looking for a way to search for all plain/text gedit files.

when I use the search option in files I might filter my results to only plain/text results. It appears that while scanning it crashes quite often.

so what I am looking for is a command or a tool I could find all gedit files in one particular folder. I would then go through them and try to 

find my notes. I also tried the find command, but that was overwhelming. 

any help is greatly appreciated and sorry again if that might have been answered in the past at some thread

cheers

jxk

---

### Post by howefield on 2016-11-03
You could try the grep command if you can recall some strings of text that you are looking for..

```
grep -irl "string_to_search_for" ~/path_to_files/
``` 

eg, grepping for the word *grep* in my ~/Documents folder results in...

```
grep -irl "grep" ~/Documents/
/home/hugh/Documents/Handy Commands
/home/hugh/Documents/Manually install ttf-mscorefonts-installer
```

If that isn't enough then a find command would probably be best and someone can give you an example.

---

### Post by CantankRus on 2016-11-03
Edit: grep shown above by howefield is just as good...I just like the output of ack-grep better and the defaults it uses.

ack-grep is a fast search tool.
If you remember some word or phrase that is fairly unique to your saved notes,
open a terminal and cd to the folder and run...
```
ack-grep -i "[COLOR="#808080"]*uniqueword or phrase*[/COLOR]"
```
Will recurse through directories and not be case sensitive.
Need to install ack-grep.

---

### Post by steeldriver on 2016-11-03
Unfortunately there really is no such thing as a "gedit file" - gedit is just a text editor, so (AFAIK) it doesn't insert anything into files that you edit with it that would identify them directly

If gedit is the only Linux-ish text editor that you have used, then one way you might be able to narrow the search down might be to search for its autosave files - these are characterized by a tilde suffix i.e. if you edited `somefile` using gedit, then you will likely find a `somefile~`in the same directory

So you could try

```

find path/to/backup/dir -name '*~' -type f

```

Alternatively, you could identify *any *plain text files using something like

```

find path/to/backup/dir -type f -exec file {} + | awk -F: '$2 ~ /ASCII text/'

```

(this will also find things like shell scripts and so on - it can be made more specific if that's a problem).

---

### Post by howefield on 2016-11-03
> **CantankRus said:**
> ...I just like the output of ack-grep better and the defaults it uses.

Seems quite a cool tool which I hadn't used before, though worth mentioning that it isn't installed by default.

> **steeldriver said:**
> If gedit is the only Linux-ish text editor that you have used, then one way you might be able to narrow the search down might be to search for its autosave files - these are characterized by a tilde suffix i.e. if you edited `somefile` using gedit, then you will likely find a `somefile~`in the same directory


Don't think that autosave is the default behaviour any more but not sure which release it stopped being so.

---

### Post by Bucky Ball on 2016-11-03
I use Catfish. Simple app in the repositories.

---

