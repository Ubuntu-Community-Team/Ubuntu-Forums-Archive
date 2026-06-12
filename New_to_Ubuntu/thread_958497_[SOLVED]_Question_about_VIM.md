---
title: "[SOLVED] Question about VIM"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by drakeman007 on 2008-10-25
Hello, im newbie in the linux world like everybody knows, im actually learning with a pdf book called "A practical guide to ubuntu linux" is really clear and easy to understand, right know im practicing with vim, but the book doesnt explain me this, 
if i open a terminal console, and put
```
vim practice
```
a new file comes and i write anything if i want to close the vim file in this case "practice" i put ```
:q!
``` this command is to save i guess, but if i want to open the file again where i can search for it? what is the default location of saved files in vim?

Thanks!

---

### Post by john.hall on 2008-10-25
:q! doesn't write the file, it exits without saving your changes.

If you want to exit and save your changes, use :wq instead.

If the filename you give is in the current directory, it will create the file in the current directory.  For example,

```

vim practice
# add something to the file and exit with :wq
vim practice

```

The second vim practice will open the file that you created with the first vim.

---

### Post by twisted_steel on 2008-10-25
The
```
:q!
```command actually discards changes to the file.  This tells vim that you want to quit and ignore any prompts to save the file.  If you want to save the file, you should instead enter
```
:wq
```This writes the file to disk and then quits.

If a full path is not given to the file you are editing, it will be in the current directory.  So to test things out, you can do ```
vim practice
``` and enter some text.  Then do a ```
:wq
``` to save the file.  To re-open the file in vim, just do ```
vim practice
``` again.

---

### Post by twisted_steel on 2008-10-25
I guess I was too slow :p

---

### Post by john.hall on 2008-10-25
> **twisted_steel said:**
> I guess I was too slow :p

We said the exact same thing!  Except yours was formatted better.

---

### Post by drakeman007 on 2008-10-25
Jejeje thanks guys for helping me! now i know why i cant find the file hehehe, shame on me askin this questions, but now i know where was my error...
Thanks....:popcorn:

---

### Post by Dr Small on 2008-10-25
```
:w = save
:w newname = save file as "newname"
:wq = save and quit
:q = quit
:q! = quit and ignore warning (of changed file)
:e filename = edit "filename"
i = insert after cursor [insert mode]
a = append before cursor
esc = enter [command mode]
/text = search document for "text"
n = go to next search result
N = go to previous search result
gg = go to top of document
G = go to bottom of document
yy = yank line
5yy = yank the next 5 lines
p = paste
dd = cut line (to buffer)
5dd = cut the next 5 lines (to buffer)
u = undo to last change
```

Also, vimtutor is excellent for a beginner.

---

### Post by drakeman007 on 2008-10-25
> **Dr Small said:**
> ```
:w = save
:w newname = save file as "newname"
:wq = save and quit
:q = quit
:q! = quit and ignore warning (of changed file)
:e filename = edit "filename"
i = insert after cursor [insert mode]
a = append before cursor
esc = enter [command mode]
/text = search document for "text"
n = go to next search result
N = go to previous search result
gg = go to top of document
G = go to bottom of document
yy = yank line
5yy = yank the next 5 lines
p = paste
dd = cut line (to buffer)
5dd = cut the next 5 lines (to buffer)
u = undo to last change
```

Also, vimtutor is excellent for a beginner.

Thanks Dr. Small, really appreciatte.

---

