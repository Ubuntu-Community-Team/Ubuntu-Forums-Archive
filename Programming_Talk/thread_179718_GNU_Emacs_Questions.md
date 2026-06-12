---
title: "GNU Emacs Questions"
date: 2006-05-20
forum: Programming Talk
---

### Post by bieber on 2006-05-20
So, I'm trying to learn to use GNU Emacs as my web dev and programming editor, and have a couple of questions that are giving me trouble at the beginning. Is there a way to have it automatically indent like most IDEs do, and also to carry indentation down from line to line? Also, how do I go about executing shell commands from within Emacs, for compiling and such?

---

### Post by oscar on 2006-05-20
To open a shell:
```
Alt-x shell
```
To go back to the last buffer (your file):
```
Ctrl-x b
```
To kill the current buffer:
```
Ctrl-x k
```

For indenting html (php and some other embedded languages as well) get html-helper-mode
```
sudo apt-get install html-helper-mode
```
Indentation is a little primative but it is there.

To insert a tab manually:
```
Ctrl-q TAB
```

I got this from an O'Reilly book "GNU Emacs Pocket Reference"

---

### Post by bieber on 2006-05-20
Okay, so it will indent to the appropriate location if I hit <tab> while on a line, but I have to manually push the <tab> key.  Anyone know if there's a way to have it do that automatically?  Also, I can set the number of spaces to indent, but I can't find a way to make it indent using the tab character.  Any ideas on that one?

---

### Post by rplantz on 2006-05-20
If you go to [www.gnu.org](www.gnu.org) you can get the manual for emacs. Under "Software" on the right, click on "GNU Documentation." Then "Books In Print" on the left.

You can insert a newline (go to the next line) with it indented the same amount as the current line with ctrl-j. (I learned that from the manual.)

---

### Post by rydow on 2006-05-21
I have not coded html but for c/c++ I find the following useful:
- ctrl c c  indent from mark to current cursor position.
- alt x compile   and write your compilation command
- ctrl c ` to jump to next error in compilation buffer
- alt x grep and alt x grep-find to find stuff in files

Have a look someones cheat sheet (e.g. mine [http://members.chello.se/rydow/emacs_tips.html](http://members.chello.se/rydow/emacs_tips.html))

Also for word completion I use the below in my .emacs
;; Tab Expand
(global-set-key (kbd "C-M-<tab>") 'dabbrev-expand)
(define-key minibuffer-local-map (kbd "C-M-<tab>") 'dabbrev-expand)

For programming ctags may be used for fast navigation between files. 

Cheers
Jonas

---

### Post by Arndt on 2006-05-24
[QUOTE=bieber]Okay, so it will indent to the appropriate location if I hit <tab> while on a line, but I have to manually push the <tab> key.  Anyone know if there's a way to have it do that automatically?  Also, I can set the number of spaces to indent, but I can't find a way to make it indent using the tab character.  Any ideas on that one?[/QUOTE]

While writing continuous material that you want to get indented automatically, the command Ctrl-J is perfect. It can be thought of as doing a Return followed by a Tab command.

As for using tabs to indent, there is an elisp variable indent-tabs-mode. If it is set to nil (Lisp parlance for "no", sort of), indentation will use only spaces, otherwise tabs if possible (and tabs by default are set at every eighth position, but I think that can be changed too). However, even if it is set to t (meaning "yes"), it is the editing mode in the buffer in question which decides whether to obey it. It seems to be t by default. What is it you're editing?

Anyway, to change it, go to the buffer named *scratch*, type in

```
(setq indent-tabs-mode t)
```

and press Ctrl-J just after the ) has been entered. This sets the variable. To inspect its value, just do Ctrl-J on its name:

```
indent-tabs-mode
```

---

### Post by Eric_T on 2006-05-24
Just found about Electric C, and it's great! Just type C-c C-a, then emacs automatically jumps to a new line and indents after a semicolon or bracket. To get a closed parentheses, M-( .  I hate typing () then arrow back to write...](*,) 
Is there a way to make this command run every time I open a C source file in emacs? 

Also, I have to press Syntax Highlighting every time as well, is there a way to automate that?
EDIT: I just had to press "Save Options"...

---

### Post by Eric_T on 2006-05-24
[QUOTE=rydow]I have not coded html but for c/c++ I find the following useful:
- ctrl c c  indent from mark to current cursor position.
- alt x compile   and write your compilation command
- ctrl c ` to jump to next error in compilation buffer
- alt x grep and alt x grep-find to find stuff in files


Cheers
Jonas[/QUOTE]


Just wanted to point out that it's C-x ` to jump to next error...;)

---

### Post by jaypeasy on 2006-05-24
The ubuntu repositories contain packages specifying emacs modes that are useful for programming in most languages. With Python for example, you can install the python-mode package which will do things like automatic indentation, commenting and uncommenting code blocks, sending regions of code to the python interpreter etc.

---

### Post by kiwibird on 2006-06-13
[QUOTE=Eric_T]Is there a way to make this command run every time I open a C source file in emacs? [/QUOTE]
Use a hook. It's a special type of emacs magic: 
[http://www.emacswiki.org/cgi-bin/wiki/ModeHooks](http://www.emacswiki.org/cgi-bin/wiki/ModeHooks)

So if you edit your .emacs and put in:
```
(add-hook 'c-mode-hook 'the-command-that-you-want-run) 
```
that might work. Although if the C-c C-a command is a toggle, you might turn it on and off every time you open a file, it can probably be run with an argument, in that case, you'd have to do a 
```
(add-hook 'c-mode-hook (lambda () (the-command the-argument)))
```

An even easier way might be to find the setting in your customization though (M-x customize), something like "auto-newline-insertion" ?

---

