---
title: "using a .run file"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by jacobroecker on 2008-09-25
I need to get my video driver working and the manufacturer has created a .run file that I need to execute in terminal. 

What is the command to execute this file type?  I thought it would run automatically when I typed in the name under a privledged account--I was wrong.

-Jacob
[http://trailbrain.com/wiki]("http://trailbrain.com/wiki")

---

### Post by kpkeerthi on 2008-09-25
First, set the 'execute' permission on the file:

```
chmod u+x <file-name>.run
```

Now run the file:
```
./<file-name>.run
```

---

### Post by jacobroecker on 2008-09-25
Awesome!!


Thanks

---

### Post by Sparkypine on 2008-11-02
It took me several days to finally find this post on how to execute a .run file.  I installed Ubuntu "i" in Virtualbox and needed to install the add on tools...which a shortcut to a cdrom drive was "conveniently" placed on my desktop.  The problem wasn't getting to the cdrom in the gui, but what to do with the enclosed .run command.  Double clicking seemed to invoke something to happen but it stopped short because I was not "God."  Fine, I embarked on a long journey trying to find where, in the terminal, I was supposed to navigate to find this cdrom drive in order to sudo the file.  This proved to be equally frustrating.  So, either I spend a lot of time trying to find where cdrom mounts are located in the file system, or I enable the gui root and just double click.  I enabled gui root.  Sure, "...all you needed to do was a simple search to find the answer on the abundant Ubuntu forums.." but why should I have to spend SO much time to do what should be simple analogs to what I do in Windows.  I WANT Ubuntu to be a contender/replacement for Windows but it's these small nuances that need worked out.  I know it's hard to see through the eyes of a noob when developing software but these simple operations should be taken for granted.  Maybe there is/was an altogether simpler way to do this and, once told, I would/will face palm the obviousness of it...but again, that's my point!

---

