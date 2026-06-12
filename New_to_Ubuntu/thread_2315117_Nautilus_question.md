---
title: "Nautilus question"
date: 2016-02-26
forum: New to Ubuntu
---

### Post by dona-pietro on 2016-02-26
Sorry if this is the wrong place where to post the question. 

Can I open a nautilus window with custom content? e.g. I have a list of files with different paths 

```

/place1/file1.pdf
/place2/file2.txt
/place3/file3.avi

```

And I would like to open a new nautilus windows with those three files as content!

Thank you 

Pietro

---

### Post by Bucky Ball on 2016-02-26
Welcome. I can't see how you'd do that unless you put all those files in the same folder. But then they wouldn't be in different places. ;)

What you're wanting to do is not really the way things work with Nautilus (or any file browser I know of). You could, though, open a folder in Nautilus, hit control+t to open a new tab and go to the location of your second file, open a third tab and go to the third file ... etc.

About the best I can offer. Curious to see what others throw in ... :-k

---

### Post by mc4man on 2016-02-26
Taking "content" literally, no. Nautilus is a file manager not a pdf or text reader or media player. The 'canvas' that it uses to display icons in is set in the source & marginally affected by theme.

---

### Post by howefield on 2016-02-26
Not sure if you could script something that opened one window with 3 tabs., each tab opening the folder containing the relevant file(s). Too much work for dubious results for me though :)

What about creating symlinks to the files ?

---

### Post by Bucky Ball on 2016-02-26
> **howefield said:**
> What about creating symlinks to the files ?

Nicely. Yea, that could work ...

```
ln -s 'location to link to' 'name of symlink'
```

Create a folder, say called /home/folder. Then, replacing your files, do:

```
ln -s /path/to/file1 /home/folder/file1
```

Replace '/path/to/file1' with you real details and path to the file (and same for second path to symlink folder). The command above won't move file1 to folder but it will put a link to file1 in folder which, when you click it, opens file1. Repeat for any other files you want in that folder.

---

