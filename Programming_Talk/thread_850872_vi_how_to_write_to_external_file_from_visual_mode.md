---
title: "vi how to write to external file from visual mode"
date: 2008-07-06
forum: Programming Talk
---

### Post by DBQ on 2008-07-06
Hi everybody.  I was wondering if there is a way in vi (or vim) to do something like this: switch to visual by pressing v, select the code I am interested in, and then do something like :w external_file or :w >> extenrnal_file (ie write the visually selected code to the external file).  I need to do this a lot during my programming.  I tried doing this before, but it does not work.

I find it a nuisance to have to find the first, and the last line of the code every time.  Is there a way to do it visually (in vi/vim sense)?

Thank you guys (and gals).

---

### Post by ghostdog74 on 2008-07-06
just one way:
after you select the lines in visual mode, yank it by pressing "y". Then :e newfile, paste the lines, and :w it.

---

### Post by DBQ on 2008-07-06
> **ghostdog74 said:**
> just one way:
after you select the lines in visual mode, yank it by pressing "y". Then :e newfile, paste the lines, and :w it.

What a pity there is no better way...

---

### Post by stylishpants on 2008-07-06
> **DBQ said:**
> Hi everybody.  I was wondering if there is a way in vi (or vim) to do something like this: switch to visual by pressing v, select the code I am interested in, and then do something like :w external_file or :w >> extenrnal_file (ie write the visually selected code to the external file).  I need to do this a lot during my programming.  I tried doing this before, but it does not work.

I find it a nuisance to have to find the first, and the last line of the code every time.  Is there a way to do it visually (in vi/vim sense)?

Thank you guys (and gals).

This works fine in vim.  I do it all the time.

Select something in linewise visual mode, then do :w filename 
(shows up as :'<,'>w  filename, of course.)

If you try to use visual mode per-character instead of linewise (using v instead of V,) you will still get the linewise behaviour.

Are you sure you have vim-full installed?

Of course, this only works for writing a new file (or overwriting an existing one, with :w!).  If you want to append, that's different.

---

### Post by DBQ on 2008-07-06
Thank You! It works!

Is there a better way of doing append somehow?

---

### Post by stylishpants on 2008-07-06
I am not aware of a simple way.

It is certainly possible to add a bit of code to your ~/.vimrc which defines a function you can call that does the job.

Probably beyond my own meager vim scripting abilities though.

---

### Post by odyniec on 2008-07-06
This works for appending:
```
:'<,'>w >> filename
```

---

### Post by DBQ on 2008-07-06
Thank you all.  I will try the suggestion for appending.

---

### Post by DBQ on 2008-07-06
I think I have this one solved.  However, I have another question regarding the visual mode.  I started a new thread for it.  Thank you all:

[http://ubuntuforums.org/showthread.php?p=5333642#post5333642](http://ubuntuforums.org/showthread.php?p=5333642#post5333642)

---

