---
title: "How do I assign a command to act on a specific file type?"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by bobsmith2 on 2008-10-25
I'm trying to find an easier way to extract partial RAR archives. Here's how I do it now... If I have just the first file in the archive (let's say it's "filename.rar"), I open the terminal and type in this command:

```
unrar e -kb filename.rar
```

That extracts the first portion of the archive, but I'd much prefer to simply double click on an rar file in Nautilus and have that command applied to any rar I click on. Is that doable? How do I set it up? I tried assigning the command by right-clicking an rar file in Nautilus > Open with other application > Use custom cammand, but that doesn't work. Nothing happens. Is there a way? Thanks?

---

### Post by Victormd on 2008-10-25
You can right click the file, go to properties, then go to the "Open With" tab. There you will be able to add a custom command to open the file.

Or, right click, go to "Open with Other Application" and click on the "Use a custom command" to add a new command to open the file.

Edit: Just saw that you did the second one... hehe

---

### Post by Victormd on 2008-10-25
The problem might be on how you enter the command. What are you using as the command?
```
unrar e -kb
```
or something like:
```
unrar e -kb $file
```
??

I did something similar to [make MS Word my default editor]("http://ubuntuforums.org/showthread.php?t=915526") and ended up having to create a script, and link the file to the script.

Doesn't the "right-click > Extract Here" work on partial RAR files? I know it works on RAR files...

---

### Post by bobsmith2 on 2008-10-26
Thanks Victormd. I finally figured out the problem... it was dumping the output into the home directory - not the directory the rar file was in. So now, whenever I right click on any rar file and select "Open with "unrar"", it extracts the partial (or complete archive) file and dumps it into the home directory. I used this command:

```
unrar e -kb
```

Is there some code I can add to the above command that will force the output to whatever directory the rar file happens to be in? If I can do that, I'll be set.

---

### Post by Victormd on 2008-10-26
I don't have RAR installed, I'll install it and play around with it to see what I can come up with...

---

### Post by Victormd on 2008-10-28
> **bobsmith2 said:**
> Is there some code I can add to the above command that will force the output to whatever directory the rar file happens to be in? If I can do that, I'll be set.

Just out of curiosity, why don't you use the native RAR support through the right click>extract function?

---

