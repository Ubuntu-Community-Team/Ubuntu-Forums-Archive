---
title: "Vim folding question"
date: 2009-05-23
forum: Programming Talk
---

### Post by mcai8sh4 on 2009-05-23
Greetings all!

I have a little question, not sure if it's possible, but here goes.

I'm currently programming for an MCU in c using vim. I have set in my .vimrc
```
map <f3> :set foldmethod=indent<cr>
```

Since I use vim for most of my programming/scripts/editing ini files/taking notes... I don't want folding to happen by default.

So I open my program press 'F3' and the indent method folds everything just how I want it... apart from one aspect - comments.

Since I'm thick, some parts of the code have a large block of comments. Most of the time, I don't need them - so I'd like to fold them out of the way.

Unfortunately, using the indent method doesn't allow you to set folds manually.
I've found this : [http://vim.wikia.com/wiki/VimTip108#Indent_folding](http://vim.wikia.com/wiki/VimTip108#Indent_folding)
but I think this will fold every file when I open them.

So the question is (preferably still being able to use 'F3' to turn the folding on when I want) how can I fold by indent - but still be able to manually fold comments if required?

How does everyone else handle their folds in vim.

Thank you for your time.

---

### Post by dotancohen on 2012-01-05
Have you considered wrapping the comment in an if or while? The compiler will optimize it away anyway.

---

