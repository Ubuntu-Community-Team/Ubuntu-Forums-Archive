---
title: "copy and pasting in vim"
date: 2010-08-18
forum: Programming Talk
---

### Post by qedprigmosynois on 2010-08-18
how do you copy and paste into vim from let's say a website. I know how to do it within files within vim, but otherwise at a complete loss.

---

### Post by DaithiF on 2010-08-18
```
"+gP
```

---

### Post by blur xc on 2010-08-18
ctrl-shift-c, ctrl-shift-v, just like in the terminal

I run into one hiccup- I've got it all set to auto indent when writing scripts or python code- so pasting in already indented code makes a mess- haven't figured out how to fix that yet...  but I haven't tried really hard yet either, so if someone knows how to turn it off temporarily, that'd be great.

BM

---

### Post by qedprigmosynois on 2010-08-18
> **blur xc said:**
> ctrl-shift-c, ctrl-shift-v, just like in the terminal

I run into one hiccup- I've got it all set to auto indent when writing scripts or python code- so pasting in already indented code makes a mess- haven't figured out how to fix that yet...  but I haven't tried really hard yet either, so if someone knows how to turn it off temporarily, that'd be great.

BM

i tried crtl shift v for pasting into vim however i get "visual block" in terminal mode and ^ in edit mode.
also can anyone explain what +gP is? 
is that the sequence i have to press?

---

### Post by MadCow108 on 2010-08-18
you paste as usual in insert mode but to fix indentation you have to turn on paste mode:
set paste

disable with
set nopaste

it is useful to set a shortcut for that, e.g.:
set pastetoggle=<F9>

in an other mode you have to use "+gP
this has the advantages that you don't need paste mode
this means:
" access following register
+ cut buffer
gP paste and put cursor after paste

"+p places cursor it in front

another useful buffer is the selection buffer *
you can see your registers with :register

---

### Post by qedprigmosynois on 2010-08-18
so the problem is that it only seems to work under gvim and i've tried the suggestions posted above, i thought i got it working, but then I realized i could only do it within certain applications. So now, i still have the problem of copying and pasting between applications without gvim.

---

### Post by jobix on 2010-08-19
Using the mouse to select the text and then clicking both the buttons on the mouse simultaneously while in your vi window (in edit mode) should work.

---

### Post by ssam on 2010-08-19
use
```

:set paste

```
to disable auto indent.

select the text with the mouse, and then middle click where you want it to go. this is the old fashioned method for copy and paste in X. once you get used to it is very handy.

```

:set nopaste

```
to turn auto indent back on.

---

### Post by qedprigmosynois on 2010-08-19
grr, still cant get it from a different apps. The mouse feature works, but it seems only for itself and other vim windows. It should work for anything right? Im using chrome right now.

---

### Post by Zorgoth on 2010-08-19
Just select the text with the moust and middle click and it is pasted at your cursor!  Works between any teo applications in X (and therefore between the console and any Window), and really fast once you get the basic idea.  I have to admit I even do it while editing code, horrible mouse user that I am :o

---

### Post by qedprigmosynois on 2010-08-20
what if you're using a laptop and the middle mouse option is unavailable?

---

### Post by redfox1160 on 2010-08-20
Here is a link from the Vim website on copy, cut, and paste: [http://vim.wikia.com/wiki/Copy,_cut_and_paste](http://vim.wikia.com/wiki/Copy,_cut_and_paste)

---

### Post by ssam on 2010-08-20
> **qedprigmosynois said:**
> what if you're using a laptop and the middle mouse option is unavailable?

often clicking the left and right mouse buttons at the same time counts as a middle click.

i think this is currently enabled by default, but will be disabled by default in a future ubuntu version.

---

### Post by Zorgoth on 2010-08-20
NO, NO, NO!  I like my (not) middle mouse button!

---

