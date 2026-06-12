---
title: "Gnome drag &amp; drop"
date: 2007-02-22
forum: Programming Talk
---

### Post by floberg on 2007-02-22
Hi,

I have searched the net to find something about this, but nothing... Must be easy...

I wanna write an application. Put a link to it on my desktop. Drag & drop file/dir etc on it and then fetch what was dropped on it in my application.

Im gonna write this in Python, but... if you know anything about how its done in any other language/script etc... I would just love to know!

Thanks,

F

---

### Post by louis_nichols on 2007-02-22
Actually, that is the normal functionality of all links on the desktop.

So for example, let's say you make a program called *fetch* that would work in the command line like:

```
fetch *filename*
``` and perform some operation on the file.

Then, if you make a new launcher on the desktop and the command for that launcher is *fetch*, you will be able to drag and drop files on the icon of the launcher and that will be exactly equivalent to the command above. So all you have to do is design the application to take the path to a filename as input and you're set. I'm not sure whether it will recurse in directories, but I think that can be manipulated in your application, by making it take both filenames and folders as input and, in the case of folders, recurse into them.

Hope you understood my explanation.

---

### Post by floberg on 2007-02-22
Thanks for the answer,

I tried that with a small shellscript before I asked:
#!/bin/bash
echo $? > testoutput

And when dropped a file on it, the testoutput stated 0 ???

Now, when I have read your reply... I tried this instead (dunno why I used $? before, but... well) :
#!/bin/bash
echo $* > testoutput

And... There we go! :D Yes, I got it... The rest I will fix with my application.

Thanks a lot!

/F

---

### Post by dlublink on 2008-02-20
Hey!

I tried what was suggested, but when I drag files to drop on the script the script doesn't "light up" blue and I can't drag and drop it.

Any ideas why?

Thanks,

David

---

