---
title: "VIM - plugin to execute files inside vim"
date: 2013-04-09
forum: Programming Talk
---

### Post by sollidsnake on 2013-04-09
Hi!
At my university I frequently have to open new files, write the code, compile and execute, without much project design. I use vim as my editor and I find it annoying open a terminal window, compile and run the program every time. I know vim has makeprg but it's not much flexible.

So I decided to write a vim plugin to easy the run/compile process inside vim. I started the project today and it has about 80 lines. It's still very unmature but it serves my needs for now. I plan to constantly work on it and make it the most complete and flexible as possible.

Well, I just wanted to share the idea. I know it's very little but I'm sharing for everyone who likes the idea and have interest to use, participate or suggest. 

[https://code.google.com/p/vim-easyrun/source/checkout](https://code.google.com/p/vim-easyrun/source/checkout)

---

### Post by trent.josephsen on 2013-04-09
:make, not flexible? I'm not sure I understand what your plugin is supposed to do that can't be done, and done very easily, with :make (or just :!./programname for that matter).

On another note, pick spaces or tabs for indentation, but don't mix them -- or if you do, at least put the tabstop on the "universal" 8 spaces. I don't want to start another indentation holy war but at least pick a style that doesn't break when it's `cat`ed.

---

### Post by sollidsnake on 2013-04-09
The main idea of the plugin is to make all the configuration to execute the program for you. You just open the file and execute the command :VERun. It will autodetect the type of the file you're working (cpp, c, python etc) and execute. Right now I just pushed a implementation to autodetect the python version of the file you're working. So :VERun will check the python version you're working by the file header and do the work for you.

It also has support for makefile but I haven't spent time on it yet.

About the spaces/tabs, I mean using only spaces. If there are tabs in there were my mistake. I'll check it later.

---

### Post by sollidsnake on 2013-04-09
My problem with :make is that you need to configure it for every file/project you're working. If you working on a sh script, for example, you need to set makepkg=sh % for your :make work. You need to do that for every file type. Of course you could but an autocmd in your vimrc, but you that wouldn't be much flexible. It wouldn't be much clean to check for your python version inside an autocmd in your vimrc. So I thought creating a plugin for this would be the right approach.

---

### Post by trent.josephsen on 2013-04-09
Ah, I see. I rescind my criticism :)

I use make (the actual utility) for most personal projects anyway, so :make (or :make target) is a great tool. When I'm scripting, I usually have a terminal open anyway. So.. I guess I'm not really the target demographic for this plugin, but it still sounds kinda cool.

Cheers!

---

### Post by sollidsnake on 2013-04-09
Thank you for the replies.
Don't need to be sorry for your criticism, it's my fault I haven't well documented it yet. I just wanted to read some opinions before spending my time on it.

And yes, the make tool itself is really awesome. The focus of the plugin (in the c scope) is simple files or small projects. I never meant to replace the make tool.
Anytime soon I'll try to develop a better integration with make(tool) and makefile for bigger projects for the plugin. I really like doing everything inside vim :)

---

