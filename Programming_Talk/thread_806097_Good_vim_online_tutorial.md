---
title: "Good vim online tutorial?"
date: 2008-05-24
forum: Programming Talk
---

### Post by danbuter on 2008-05-24
I've finally decided to tackle vim and learn it well. I was hoping one of you might know of a good online tutorial that goes step-by-step through the various vim commands. I really don't want a list of commands, I want "Now type :K to do this...". Thanks!

---

### Post by LaRoza on 2008-05-24
> **danbuter said:**
> I've finally decided to tackle vim and learn it well. I was hoping one of you might know of a good online tutorial that goes step-by-step through the various vim commands. I really don't want a list of commands, I want "Now type :K to do this...". Thanks!

```

sudo aptitude install vim

```

Go to my wiki.

---

### Post by danbuter on 2008-05-24
I did check your wiki. It is a list of commands, not a step-by-step tutorial, unfortunately.

---

### Post by LaRoza on 2008-05-24
> **danbuter said:**
> I did check your wiki. It is a list of commands, not a step-by-step tutorial, unfortunately.

No it isn't...

[http://laroza.pbwiki.com/References](http://laroza.pbwiki.com/References)

---

### Post by srs on 2008-05-24
Vim comes with its own tutorial, write 
```
vimtutor
```
on the command line.

---

### Post by dwhitney67 on 2008-05-24
LaRoza

You mean install "vim-full" right?

```
$ sudo apt-get install vim-full
```

_Basic_ tutorial is available below; full-blown tutorial is available at: [ftp://ftp.vim.org/pub/vim/doc/book/vimbook-OPL.pdf](ftp://ftp.vim.org/pub/vim/doc/book/vimbook-OPL.pdf)

```
-----  Insert Mode -----

i = enter insert mode at current cursor position

o = enter insert mode on the line below current cursor position

shift-o = enter insert mode on the line above current cursor position

esc = exit insert mode

arrow keys = move cursor around


----- When NOT in Insert Mode -----

j (or down arrow) = move cursor down

k (or up arrow) = move cursor up

l (or right arrow) = move cursor right

h (or left arrow) = move cursor left

x = delete single character at the current cursor position

r = replace character (with new character) at the current cursor position

u = undo previous changes

dd = delete current line where the cursor is

p = paste after the current cursor position

shift-p = paste before the current cursor position


----- Advanced Insert Mode Commands -----

s = delete single character and enter insert mode

shift-c = delete current line and enter insert mode


----- Repeating Commands -----

Certain command can be invoked more than once by specifying the number
of "instances" the command should be run.  For example:

10dd = delete 10 lines, starting from where the cursor is positioned

5x = delete 5 characters, starting from where the cursor is positioned
```

---

### Post by LaRoza on 2008-05-24
> **dwhitney67 said:**
> LaRoza

You mean install "vim-full" right?

```
$ sudo apt-get install vim-full
```


No, just vim.

vim-tiny is installed by default. vim has all the features of vim, and vim-full has useless things like a gvim and such.

---

### Post by dwhitney67 on 2008-05-24
> **LaRoza said:**
> No, just vim.

vim-tiny is installed by default. vim has all the features of vim, and vim-full has useless things like a gvim and such.

I wouldn't call gvim useless... not that I ever use it of course.

---

### Post by LaRoza on 2008-05-24
> **dwhitney67 said:**
> I wouldn't call gvim useless... not that I ever use it of course.

It has a GUI, not really that useful to me.

---

### Post by Joeb454 on 2008-05-24
Here's a link I found [http://blog.interlinked.org/tutorials/vim_tutorial.html](http://blog.interlinked.org/tutorials/vim_tutorial.html)

And I preferred just using a list off commands, so I could see what I wanted to do, then find the command to do that :)

---

### Post by cdtech on 2008-05-24
I was just lookin over the vi editor, Why would anyone spend so much time just to edit a file?
```

>> To write (save) to file and quit  -->   :wq
                                            :x
                                            ZZ   (no colon)
```

Just to save and exit an editor?

You got ta' be kiddin me..

I'll stick with my simple pico....

LOL!

---

### Post by LaRoza on 2008-05-24
> **cdtech said:**
> I was just lookin over the vi editor, Why would anyone spend so much time just to edit a file?
```

>> To write (save) to file and quit  -->   :wq
                                            :x
                                            ZZ   (no colon)
```

Just to save and exit an editor?

You got ta' be kiddin me..

I'll stick with my simple pico....


What do you mean? I can do things faster with Vim than with another editor.

---

### Post by dwhitney67 on 2008-05-24
LaRoza -- I thought you would be smarter not to bite onto that "lure".  Unsubscribe to this thread before you spend eternity comparing pico vs. vim.  Really, who cares which is better/faster/sexier?

---

### Post by LaRoza on 2008-05-24
> **dwhitney67 said:**
> LaRoza -- I thought you would be smarter not to bite onto that "lure".  Unsubscribe to this thread before you spend eternity comparing pico vs. vim.  Really, who cares which is better/faster/sexier?

I don't subscribe to anythreads.

---

### Post by slavik on 2008-05-24
Here's the learning curve comparisons for the most popular editors out there. :)

[img]http://bc.tech.coop/blog/images/curves.jpg[/img]

---

### Post by LaRoza on 2008-05-24
> **slavik said:**
> Here's the learning curve comparisons for the most popular editors out there. :)

[img]http://bc.tech.coop/blog/images/curves.jpg[/img]

That is great!

---

