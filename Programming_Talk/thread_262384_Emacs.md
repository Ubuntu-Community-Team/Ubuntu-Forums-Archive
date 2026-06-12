---
title: "Emacs"
date: 2006-09-21
forum: Programming Talk
---

### Post by Skardal on 2006-09-21
I've heard a lot talk about Emacs, and I'm just wondering...is it worth learning? :-k 
What benefits does it have? Why use Emacs instead of using
ie gedit, or an IDE like Eclipse?

Thank you!

---

### Post by Tomosaur on 2006-09-21
Emacs is a pretty powerful text editor, and is 'easier' than vi/vim. However, neither is particularly easy to learn, and I would recommend that if you want to learn either, learn vi. 

For the most part, I'd say just stick with gedit, it does everything I currently need it to.

---

### Post by vialick on 2006-09-21
> **Tomosaur said:**
> Emacs is a pretty powerful text editor, and is 'easier' than vi/vim. However, neither is particularly easy to learn, and I would recommend that if you want to learn either, learn vi. 

For the most part, I'd say just stick with gedit, it does everything I currently need it to.
I found I picked up vim quite quickly, but I'm still confused a lot with Emacs (even the emacs styled keystrokes in info) and wouldn't be able to use it for anything.

---

### Post by coder_ on 2006-09-21
I find I'm more productive in vim, but you should try out a number of editors for a while such as emacs, nano, pico, vi/vim, or your GUI using one, and see which one you like the best or are more productive in.

I find I am more productive with my keyboard than with my mouse, so I prefer screen editors more than ones with full GUIs.

---

### Post by X.Cyclop on 2006-09-21
I prefer nano.:)

---

### Post by amo-ej1 on 2006-09-22
emacs is extremely keyboard centric and you will be able to do basicly anything without lifting your hand from your keyboard. Which allows you to edit extremely fast. BUT you should know which keys to press. Without lifting your hand also includes not even touching the arrow keys which can be quite annoying to pick up in the beginning.

The big advantage of an editor is that is universal, the big disadvantage is that it isn't strongly linked with other tools (like code completion, debuger integration etc). Personally I don't need any debugging interface and such when I want to debug something I'll open it in gdb myself.

But in the end it's only a matter of what you like the only thing that i would suggest is choose one thing, learn it extremely well and use it all the time. For me that one thing is emacs ;)

---

### Post by billyfoxtrot on 2006-09-22
If you're interested in learning Emacs, you should check out O'Reilly's "Learning GNU Emacs."  I found it to be a very good tutorial and reference, although you could probably find a lot of the same information in the Emacs help pages.  I just prefer to have a book in my hands.

---

### Post by toojays on 2006-09-23
> **amo-ej1 said:**
> The big advantage of an editor is that is universal, the big disadvantage is that it isn't strongly linked with other tools (like code completion, debuger integration etc). Personally I don't need any debugging interface and such when I want to debug something I'll open it in gdb myself.

Actually, emacs does have debugger integration. For more information see [Running Debuggers Under Emacs](http://www.gnu.org/software/emacs/manual/html_node/Debuggers.html). I haven't used this much myself, but I've heard that the debugger integration is much improved in Emacs 22.

There are also various modes for code completion. I tend to use the basic dabbrev-expand function myself, which is bound to M-/ by default. More sophisticated, language aware completion functions are provided by language-specific major modes, for example SLIME for Common Lisp, and guile-debugging for Guile Scheme.

---

### Post by empcrono on 2006-09-23
> **toojays said:**
> Actually, emacs does have debugger integration. For more information see [Running Debuggers Under Emacs](http://www.gnu.org/software/emacs/manual/html_node/Debuggers.html). I haven't used this much myself, but I've heard that the debugger integration is much improved in Emacs 22.

There are also various modes for code completion. I tend to use the basic dabbrev-expand function myself, which is bound to M-/ by default. More sophisticated, language aware completion functions are provided by language-specific major modes, for example SLIME for Common Lisp, and guile-debugging for Guile Scheme.

so let me get this strait ive never used emac or vi. but i think the purpose is to let u programe / i.e edit programs. so is there a advantage to say use emac over pythons idle? to program for say python?

---

### Post by toojays on 2006-09-23
I've not used idle, so I don't know how it compares to Emacs with python-mode. Perhaps it is better. But I suspect that idle is not so good at editing LaTeX documents. Or C code. As an Emacs user, I can write/compile/debug all these types of things within the same editor, which makes me more productive.

Specifically I use:

  * Emacs with cc-mode for editing C and C++ programs, and M-x compile for compiling them. I use this for both PC programs and embedded microcontroller software.

  * Emacs+AuCTeX for editing and compiling LaTeX documents.

  * Emacs+python-mode for editing and executing Python code.

  * Emacs+nxml-mode for editing DocBook documents. Again I use M-x compile to compile the DocBook into HTML.

  * Emacs+guile-debugging mode for editing and debugging Guile code.

Sometimes I do more than one of the above at once. For instance, if I'm interfacing Guile with a C library, I will be switching between C and Guile regularly.

I should also point out that I use revision control with all these kind of things. Some projects use SVN and some use CVS, but I don't need to worry about it with Emacs, I use C-x v = and C-x v v and C-x v d and they work they same whether it's CVS or SVN. Oh, and also C-x 4 a is a good one for making ChangeLog entries.

Just a few reasons why I like Emacs . . . :)

---

### Post by empcrono on 2006-09-23
> **toojays said:**
> I've not used idle, so I don't know how it compares to Emacs with python-mode. Perhaps it is better. But I suspect that idle is not so good at editing LaTeX documents. Or C code. As an Emacs user, I can write/compile/debug all these types of things within the same editor, which makes me more productive.

Specifically I use:

  * Emacs with cc-mode for editing C and C++ programs, and M-x compile for compiling them. I use this for both PC programs and embedded microcontroller software.

  * Emacs+AuCTeX for editing and compiling LaTeX documents.

  * Emacs+python-mode for editing and executing Python code.

  * Emacs+nxml-mode for editing DocBook documents. Again I use M-x compile to compile the DocBook into HTML.

  * Emacs+guile-debugging mode for editing and debugging Guile code.

Sometimes I do more than one of the above at once. For instance, if I'm interfacing Guile with a C library, I will be switching between C and Guile regularly.

I should also point out that I use revision control with all these kind of things. Some projects use SVN and some use CVS, but I don't need to worry about it with Emacs, I use C-x v = and C-x v v and C-x v d and they work they same whether it's CVS or SVN. Oh, and also C-x 4 a is a good one for making ChangeLog entries.

Just a few reasons why I like Emacs . . . :)


does it work well with bash scripting?

---

### Post by toojays on 2006-09-23
I've not used it much for this, but I just loaded up a bash script to have a look. It has a shell-script mode with highlighting, indentation and keystrokes for inserting shell contructs like loops and case statements. Looks good to me.

---

### Post by empcrono on 2006-09-23
> **toojays said:**
> I've not used it much for this, but I just loaded up a bash script to have a look. It has a shell-script mode with highlighting, indentation and keystrokes for inserting shell contructs like loops and case statements. Looks good to me.

sweet i installed it but all the text in it is boxes.. dang something good didnt happen in the install

---

### Post by toojays on 2006-09-23
Which package did you install? I suggest you install emacs-snapshot-gtk from Synaptic and use that, it is a bit nicer than emacs21.

If you are in a non-English locale, you may need to add some font packages, for example xfonts-intl-chinese. Search in Synaptic for xfonts and choose some which look appropriate.

---

### Post by empcrono on 2006-09-23
> **toojays said:**
> Which package did you install? I suggest you install emacs-snapshot-gtk from Synaptic and use that, it is a bit nicer than emacs21.

If you are in a non-English locale, you may need to add some font packages, for example xfonts-intl-chinese. Search in Synaptic for xfonts and choose some which look appropriate.

ok it is nicer and it was emacs21 i installed i can tell im going to have to do some research to learn how to use it effcientyl but none the less it looks promising. it still gives me a much of boxes when say i put my mouse over some of the options in the tool bar type thing but thats fine. also im a english user

---

### Post by roboa1983 on 2006-09-28
Hi
I've been program for more than eight months now. It's not much, but I decided to use emacs over vi. 
I believe it's just a question of getting used to things. Now, I've personalized the emacs interface and it's more helpful, but if you don't want to spend the memory on the interface, then I guess the others help just as well.

---

### Post by RockinRob2258 on 2007-05-17
> **billyfoxtrot said:**
> If you're interested in learning Emacs, you should check out O'Reilly's "Learning GNU Emacs."  I found it to be a very good tutorial and reference, although you could probably find a lot of the same information in the Emacs help pages.  I just prefer to have a book in my hands.


I'll second that!  The book was excellent and helped me learn what I needed in emacs very quickly.  I kinda "had" to use emacs since I had discovered the handy Emacs VHDL mode and was writing a lot of VHDL code that semester.  The book is still a useful reference, and I probably need to dig it out again :D

---

