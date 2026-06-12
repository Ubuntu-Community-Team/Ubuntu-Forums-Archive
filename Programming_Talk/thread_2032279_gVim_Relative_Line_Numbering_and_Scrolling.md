---
title: "gVim Relative Line Numbering and Scrolling"
date: 2012-07-23
forum: Programming Talk
---

### Post by theLured on 2012-07-23
Hello, I love the relative line numbering in vim, but when I want to see a lines number that's off the screen, I can't find out what it is.

When I scroll, the cursor is forced to the top of the screen, this then resets all the relative line numbers.

I want to be able to see the 200th relative line number, I just want to have a glance at it, and then go back to my current location to run a command like '200dd'

Has anyone got any idea how to do this?
After a while of googling, people say that vim has to keep the cursor on the screen.
Isn't there a way to just take a quick peek at the lines below without moving the cursor?

---

### Post by MadCow108 on 2012-07-23
you can jump to the location before scrolling with ctrl+o and back again with ctrl+i
this also works over multiple buffers, very useful when you are jumping around following a call stack.

you can also change the offset at which vim starts scrolling with
set so=number

---

### Post by theLured on 2012-07-24
Thanks for the reply.
This doesn't seem to keep the relative numbers to the line I want, since the cursor is moving.

Is there not a way to 'mark' a line, so even if the cursor moves down, the relative line numbering will stay on the marked line?

It'd be really handy for running a macro on about 200+ lines

And now I've solved it by using a work around.

**Solution:**
I've started to use vim's Visual mode to delete things, rather than counting lines, it's easier to see and use.
```
I do this by going into the normal mode and pressing a capital V.
I move down a few lines to select and press a lowercae x
It deletes all my lines, and it's easier to see.
```


**Solution for macros:**
Whilst writing this, I did a quick google for 'vim macro visual' and found this page
[http://stackoverflow.com/questions/3337926/vim-macro-on-every-line-of-visual-selection]("http://stackoverflow.com/questions/3337926/vim-macro-on-every-line-of-visual-selection")

With thanks to the comment from rampion, I can now highlight a few lines and run the macro on them all by highlighting them.
using the line :'<,'>normal @a

```
I do this by making my macro work on one line,
e.g. type this to make a macro assigned to the key 'a', and it
will put a # at the start of each line
qa0#q
then press a capital V to enter visual mode, move a few lines down and press
:normal @a

```

**Solution: macro on specific lines:**
sometimes you want to do a macro on lines with only a certain word
e.g.
We want to delete a single word using dw on these lines, to delete the word 'not'
```
this is a test
this is not a test
this is a test
this is not a test
this is a test

this is not a test
this is not a test
this is a test
```
We do it by
```

make the macro assigned to the letter a
Type this, it'll take us to the start of the line, skip over 2 words
and delete the current word
    qa02wdwq
OR, use a search to delete the word 'not'
    qa0/not<Press Enter Key>dwq

Now we can highlight the lines and run
:g/not/ normal @a
Only the lines with the word 'not' were altered, that's pretty cool.

```

We can also use the '.' modifier to repeat on multiple lines
```

press the 'i' key and make a change to a line
go back to normal mode and press a capital V
highlight a few lines and run
:normal .
Veeeerry handy. VIM Rocks

```


**EDIT:**
For anyone wondering how my relative lines are set up here's how
I've added these lines to my .vimrc file
```
au FocusLost * :set number
au FocusGained * :set relativenumber
```

Them lines will make vim show relative line numbers whilst the window has focus, and the absolute line number when it's lost focus. Very handy if you've set your mouse to 'focus follows cursor'.

I've also set it up so that when I switch between insert mode and normal mode, the numbers change
```
autocmd InsertEnter * :set number
autocmd InsertLeave * :set relativenumber
```

---

