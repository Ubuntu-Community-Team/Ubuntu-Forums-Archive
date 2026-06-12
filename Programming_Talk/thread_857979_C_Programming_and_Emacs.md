---
title: "C Programming and Emacs"
date: 2008-07-13
forum: Programming Talk
---

### Post by elgoog on 2008-07-13
Hi, How can I use C Programming with Emacs. I just installed Emacs for the first time and one problem with using it is tabs and indentation. 
Does someone have a link to any tutorial that help me regarding this.

---

### Post by LaRoza on 2008-07-13
> **elgoog said:**
> Hi, How can I use C Programming with Emacs. I just installed Emacs for the first time and one problem with using it is tabs and indentation. 
Does someone have a link to any tutorial that help me regarding this.

Emacs is highly customizable (it is just a REPL). 

Google "emacs with C" gets me: [http://www.bloomington.in.us/~brutt/emacs-c-dev.html](http://www.bloomington.in.us/~brutt/emacs-c-dev.html)

(Note, Emacs is evil and Vim is the best editor)

---

### Post by Canis familiaris on 2008-07-13
> **LaRoza said:**
> (Note, Emacs is evil and Vim is the best editor)
Why so?

---

### Post by LaRoza on 2008-07-13
> **Anurag_panda said:**
> Why so?

I don't want to get into it on this thread, but I couldn't give advise for emacs (or say anything about it) without stating my views. Must represent my side of the flame.

---

### Post by Canis familiaris on 2008-07-13
> **LaRoza said:**
> I don't want to get into it on this thread, but I couldn't give advise for emacs (or say anything about it) without stating my views. Must represent my side of the flame.
Yeah but the word EVIL is tad too strong.

---

### Post by LaRoza on 2008-07-13
> **Anurag_panda said:**
> Yeah but the word EVIL is tad too strong.

No, it is too weak, but I have to keep in mind the CoC when responding. The Church of Emacs with its godless high priest are the bane of text editing. (If you think I am joking, try [http://www.dina.kvl.dk/~abraham/religion/](http://www.dina.kvl.dk/~abraham/religion/))

---

### Post by schauerlich on 2008-07-13
> **LaRoza said:**
> No, it is too weak, but I have to keep in mind the CoC when responding. The Church of Emacs with its godless high priest are the bane of text editing. (If you think I am joking, try [http://www.dina.kvl.dk/~abraham/religion/]("http://www.dina.kvl.dk/%7Eabraham/religion/"))

LaRoza, this is why we keep you around. :D

---

### Post by -grubby on 2008-07-13
> **EDavidBurg said:**
> LaRoza, this is why we keep you around. :D

How could we get rid of our favorite bot? They're integrated right into Vbulletin. Almost makes me wish I had $160 just so I could have a LaRoza of my own

---

### Post by Canis familiaris on 2008-07-13
> **nathangrubb said:**
> How could we get rid of our favorite bot? They're integrated right into Vbulletin. Almost makes me wish I had $160 just so I could have a LaRoza of my own
So LaRoza is a bot! :lolflag:
Yeah I was wondering how could a human make a post while being offline.

---

### Post by Ruhe on 2008-07-13
> **LaRoza said:**
> 
Google "emacs with C" gets me: [http://www.bloomington.in.us/~brutt/emacs-c-dev.html](http://www.bloomington.in.us/~brutt/emacs-c-dev.html)


I also use these two hoocks:

```

;; here you can apply any C style which you like, I choosed K&R
(add-hook 'c-mode-hook        
	  '(lambda ( ) 
	     (c-set-style "k&r")))

;; auto new line
;; indents cursor when you press ENTER
(add-hook 'c-mode-hook
	  '(lambda ( )
	     (c-toggle-auto-state)))

```


Maybe anybody can tell me, how to make ecb outline all the functions in opened file. "Methods" window shows only includes.
"Rebuild methods buffer" doesn't help.

---

### Post by CptPicard on 2008-07-13
I do believe that it is the other side around -- LaRoza has assimilated this instance of VBulletin and added its distinctiveness to her own. Now, the bulletin exists in a sort of Matrix-like state she is able to enter and exit at will...

But anyway OP has chosen well regarding his text-editing salvation. Thrice vi is the number of the beast, and even the Collective is just a REPL (apparently on a completely open port too -- after all Data was able to run (sleep) on it), so one day we may be able to port Emacs to run on it and use the whole thing for our own purposes ... try that with vi.

---

### Post by nvteighen on 2008-07-13
Use MS Notepad! (Or better, QBASIC \editor, to launch MS-DOS Editor)

(If you're a beginner, gedit may be all you need)

---

### Post by LaRoza on 2008-07-13
> **nvteighen said:**
> (If you're a beginner, gedit may be all you need)

Even for advanced programmers, gedit has enough useful features to be the editor used. Its plugins are really good.

---

### Post by johnl on 2008-07-13
There are a lot of nifty emacs modules out there that you can use: xcscope.el for cscope integration, the cdet package for general development features, p4.el (if you're using perforce; there are other modules out there for svn, cvs, etc...), flymake.el for on-the-fly syntax checking.

Here are some of the things that I run in the c-mode-hook:
```

(c-set-style "k&r")         ;; Kernihan & Richie's style
(setq tab-width 8)          ;; tab is 8 spaces
(setq c-basic-offset 4)     ;; indent is 4 spaces
(c-set-offset 'substatement-open 0) ;; No indent for open bracket
(show-paren-mode 1)         ;; Highlight matching parens
(turn-on-font-lock)         ;; Turn on font lock mode
(setq indent-tabs-mode nil) ;; only use spaces for indenting.

```

---

