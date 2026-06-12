---
title: "How many of you folks use Emacs?"
date: 2008-05-16
forum: Programming Talk
---

### Post by dempl_dempl on 2008-05-16
Hi,

 Ever since I've opened Emacs for the first time in my life, I couldn't figure it out why on earth anyone use that thing. 

 What can it do that other editors can't ? Many people seem to be praising it, but I don't see why. Can anybody help me in clarifying  that?

Thanks

---

### Post by Wybiral on 2008-05-16
You get used to the hotkeys and then it becomes way faster than using any GUI editor. It's also the best environment for Lisp, hands down (emacs+slime).

---

### Post by LaRoza on 2008-05-16
> **dempl_dempl said:**
> 
 What can it do that other editors can't ? 

Everything but text editing.

---

### Post by CptPicard on 2008-05-16
Emacs is essentially a lisp machine on its own right... completely programmable and customizable. As Wyb said Emacs+SLIME is a great combination, and all the other "modes" are great too -- there is one for pretty much every imaginable language, and stuff like smart indentation is still the best in Emacs for most languages than I've ever used elsewhere. Plus you get interfaces to debuggers and all kinds of other tools. It's a kind of "IDE swiss army knife" for everything and nothing in particular.. :)

---

### Post by Jessehk on 2008-05-16
I use it for all programming including C, C++, Python, and (very recently) LaTex. The indentation modes for Emacs are far more "intelligent" then they are for vi(m) and I find the interface more customizable and faster than Eclipse. 

I also like the integration with other tools: vc for excellent integration with SVN (a commit it just a C-x v v away), gdb (M-x gdb), and other tools (like dired, etc).

Emacs is excellent. Just make sure you get a modern version with better fonts, and a good colour scheme.

---

### Post by happyhamster on 2008-05-16
> **dempl_dempl said:**
>  What can it do that other editors can't ?
[http://xkcd.com/378/](http://xkcd.com/378/) :)

---

### Post by Verminox on 2008-05-17
I installed it yesterday and I didn't quite like the interface. For some reason, I prefer GEdit. Simple and straightforward. Sure it doesn't have many of the features Emacs has to speed up development but I'm in no hurry :p

---

### Post by btdown on 2008-05-17
VI....that is the only thing you need.

---

### Post by maximinus_uk on 2008-05-17
There's a VI mode out there as well....

But to be serious, I use EMACS+SLIME as a LISP development enviroment - it's the best I've met so far. To be fair, I wouldn't say EMACS is user friendly, but it is user-powerful.

---

### Post by MONODA on 2008-05-17
> Everything but text editing.
lol so true.

---

### Post by Wybiral on 2008-05-17
> **MONODA said:**
> lol so true.

If you put it in cua-mode, it becomes more text-editor-esque (it gives you the normal C&P keybindings and Ctrl+Z undo, etc). Just do M-x cua-mode

---

### Post by CptPicard on 2008-05-17
cua-mode is a must sort of, but I really have to some day properly learn to use mark, kill, yank and the kill ring. I mean... it is very powerful to be able to kill rows with C-k as many times as you like and then yank them all back with C-y.

Someone should understand how the more advanced manipulation of the kill ring works though, it never made sense for me. :)

---

### Post by johnl on 2008-05-17
Emacs is really counter-intuitive when you first start using it, but it's very powerful and neat when you start to get the hang of it.

The absolute first command I would teach someone looking to learn emacs is:

C-g  - the panic button.  Whenever emacs starts doing something that you didn't want it to do because you hit something accidentally, hit control+g a bunch of times until it stops :)


From there you can use M-x 'command' to try commands.  Emacs will show you the shortcut key bindings for whatever command you enter like this.  For example, If I do 'M-x next-buffer' emacs says 'You can run the command next-buffer with C-x <c-right>'

---

### Post by LaRoza on 2008-05-17
Thread Jailed and Emacs advocates banned.

---

### Post by dempl_dempl on 2008-05-18
He he... LaRoza = Judge Dred

---

### Post by NeonBible on 2008-05-18
How about Emacs vs Vi(m)? :popcorn:

---

### Post by LaRoza on 2008-05-18
> **NeonBible said:**
> How about Emacs vs Vi(m)? :popcorn:
See the sticky under "Holy Wars"

---

