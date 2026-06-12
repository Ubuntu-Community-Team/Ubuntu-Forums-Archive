---
title: "Emacs - pasting from other applications"
date: 2008-07-11
forum: Programming Talk
---

### Post by DBQ on 2008-07-11
Hi everybody.  Question.  Say, I would like to paste into emacs something that I copied from firefox (assume text).  How would I go about that?  Thank You!

Did anybody else, when still being an emacs n00b, found the thing a pain to configure?  I have been a vi user for quite a while, but thought it would be wise to explore the "dark side" (at least thats how the vi people call it :)).  Would like to learn emacs as well.

---

### Post by HalPomeranz on 2008-07-11
> **DBQ said:**
> Hi everybody.  Question.  Say, I would like to paste into emacs something that I copied from firefox (assume text).  How would I go about that?

It's pretty easy.  Select the text you want in Firefox-- you just have to highlight the text, you don't actually need to select Copy or anything.  Then in the Emacs window, click the middle mouse button at the point where you want the text to be inserted.  That's it.

Emacs is a little daunting at first, but it's a very efficient text editor once you get the hang of it, and it's especially good if you're writing software.  You might find this link useful: [http://www.gnu.org/software/emacs/tour/](http://www.gnu.org/software/emacs/tour/)

---

### Post by badperson on 2008-07-11
by middle mouse button, do you mean the scroll wheel?
also, do you know how to do that with keystrokes?
bp

---

### Post by HalPomeranz on 2008-07-11
> **badperson said:**
> by middle mouse button, do you mean the scroll wheel?
also, do you know how to do that with keystrokes?


Yeah, on mice with a scroll wheel in the middle, the scroll wheel usually acts as the middle button if you press down.  Note that clicking the left and right buttons at the same time should also act like a middle-click (I know that some scroll wheel mice make it a pain to use the middle button).  You might want to invest in a three-button mouse with a thumb wheel-- it makes life much better (my personal favorite is [http://www.contourdesign.com/pmo/index.htm](http://www.contourdesign.com/pmo/index.htm), but they're a little spendy).

The keyboard binding for the paste operation is Ctrl-Y

---

### Post by DBQ on 2008-07-11
Thank you very much!  I now see that its very easy to copy text from the system clipboard.

However, I believe there is a down side to this -- it seems like merely highlightighg text in some outside application can mess up the emacs clipboard.  Some times you want the clipboard to be modified only when you actually do the copy operation externally.  You see what I mean?

---

### Post by shifty2 on 2008-07-12
Emacs works on a different clipboard to most other applications, effectively the default clipboard for X. You can paste from the clipboard that is, for example, used in gtk applications by using the "<copy>" "<paste>" buttons on the edit menu on the menu bar.

It is a bit of a pain getting used to the fact that any selected text ends up on the clipboard, but once you get used to it it works very well - I use that almost exclusively now over Ctrl-C Ctrl-V etc.

Once you begin to pick up some (emacs) lisp it becomes a lot easier to configure - stick with it, its worth it!

---

### Post by mali2297 on 2008-07-12
> **badperson said:**
> by middle mouse button, do you mean the scroll wheel?
also, do you know how to do that with keystrokes?
bp

To paste from the X clipboard, you can press Shift+Insert (as an alternative to using the mouse).

---

### Post by Ruhe on 2008-07-13
And what about turning in CUA? 

You can turn it on throug Options menu:
C-x/C-c/C-v cut and paste (CUA)

or in your .emacs file:

```

;; worry about other custom variables
;; this entry may already exist in .emacs file
(custom-set-variables
 '(cua-mode t nil (cua-base))) 

```

---

