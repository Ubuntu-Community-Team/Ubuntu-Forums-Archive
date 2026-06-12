---
title: "making text in terminal more colorful?"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by bluepowder7 on 2008-06-24
is there a way of configuring the terminal (in xubuntu) to use other colors than white for my commands and what it is saying to me?  for example, if i run "sudo aptitude install package", it would be nice if the prompt and what i write are a different color than the slew of "reading package, unpacking, checkind dep..." it spits out.  and maybe if there's an error line, have it show in red.  have package changes shown in blue.  that kind of stuff.  having it ALL in white makes it hard to quickly look through what's been done.

now, if i do "ls", then yeah the colors get used to differentiate between file, link, and directory.  but that's the ONLY place they get used as far as i can tell.

---

### Post by fahadsadah on 2008-06-24
You can make the prompt (the bit that looks like "user@host:/directory$") a different colour.
Please post the foreground and background colour you want, and whether you want bold text or not, so I can tell you a code to add into the systemwide bashrc.

The aptitude colouring is a good idea - will look into that.

---

### Post by phidia on 2008-06-24
There is a bash reference [here]("http://www.delorie.com/gnu/docs/bash/bashref_toc.html") and it seems like the section that deals with that is [here]("http://www.delorie.com/gnu/docs/bash/bashref_69.html").

---

### Post by bluepowder7 on 2008-06-24
i'm currently running a black background / wallpaper, so black background and various colors for the text (i suppose green for prompt lines, white for generic info it tells me, red for errors, blue for new packages it's going to install / upgrade / remove).  no need for bolding anything.  though, in a few days, i may need to change my background depending on how hard it is on my eyes, so i'd like to learn how to set all the properties.

i'll look into those linked threads / articles and see what that gains me, too.

---

