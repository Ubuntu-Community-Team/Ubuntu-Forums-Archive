---
title: "vi(m): Edit multiple files without saving"
date: 2010-10-25
forum: Programming Talk
---

### Post by yc2 on 2010-10-25
Hi,

Sorry for a question that my friend Google might resolve, but I am behind a firewall and all is hard now ;)

When I jump between files in vi (:n#), is it then possible to leave (and return to) a file where I haven't saved changes (w). As it seems now (vi and vim) I must save changes before leaving a file for the next.

Thanks

---

### Post by sikander3786 on 2010-10-25
Ctrl + X and 'N' to say no to changes.

Doesn't that work?

---

### Post by yc2 on 2010-10-25
What I would like to do is to keep the changes until a come back to the file again, but I do not want to write them to disk. maybe that is not possible.

When I try the ctrl/x command in vim command-mode I just hear a "click", it seems not to be allowed.

Sorry for adding one question: Syntax highlighting works for C, but not for php. Is that possible to cure? (And preferably also JavaScript)

/add: I think I found the answer to the added question:  SET SYN=PHP  seems to do it.


Thanks

---

### Post by geirha on 2010-10-25
I usually don't find it problematic to save when switching files, though I have noticed that if you use split window (with :split or :vsplit), you don't need to save while moving between the open windows. To move between the open windows, use ^W<direction>.

---

### Post by yc2 on 2010-10-25
yes, the inability to save is not a big issue. I used CLI-editors a lot in the 70's and 80's and now I find I am returning more and more to vi. So I have better try finding a quick and pleasant working environment.

I haven't yet found a color scheme I quite like. I am getting a little older and should wear reading glasses, but I don't. I prefer light background, but I think that somehow makes the text not stand out enough.

Here the text comes out better, but I would like to try the background lighter
:highlight Normal ctermfg=grey ctermbg=darkblue
Changing the command to lightblue does not make a difference.

All the colorschemes I can find on the Internet do not seem to be installed in the verison I am running.

How do I install colorschemes. (In the 80's we only had b/w ;) )
And how do I find which ones are installed. (:colorscheme does not work)  (OK I found the reply to this one: colorscheme<space><tab>)

---

### Post by yc2 on 2010-10-25
It only seems possible to set color for the first file edited.

If I open more files by
:n myfile
they all come out in black background.

For the first file I edit I can change colors with
:colo desert
:colo morning

But this does not work for other files opened with :n

It looks like a bug, but considering the qualities of vi(m), I guess I just haven't found out how to do it yet.

---

### Post by ja660k on 2010-10-25
this may or may not be relevant... 
:vsp <path/to/file>

splits the window vertically
use ctrl+w to switch between files to edit.
:qall to quit all.
or :q! to quit each window.

i hope thats what you meant?

---

### Post by krazyd on 2010-10-25
enter this (or just put in your .vimrc):

```
set hidden
```

then use :e to edit new files rather than :n

also, to have your colours persist across sessions, put them in your .vimrc. My personal favourite is [darkspectrum]("http://www.vim.org/scripts/script.php?script_id=2215"), which works great in the terminal with [this plugin]("http://www.vim.org/scripts/script.php?script_id=2390").

---

### Post by yc2 on 2010-10-25
> **krazyd said:**
> enter this (or just put in your .vimrc):
```
set hidden
```
then use :e to edit new files rather than :n
...

Thank you everyone for good ideas.

Thank you Krazyd, you gave the solution to my original question. I tried your advice, it works. (I yet don't understand how, though.;) ) There is always a solution in vim.

I will check more about colorschemes and come back. Now time to sleep in the region I reside

Thanks guys.

---

### Post by spjackson on 2010-10-25
> **yc2 said:**
> 
When I jump between files in vi (:n#), is it then possible to leave (and return to) a file where I haven't saved changes (w). As it seems now (vi and vim) I must save changes before leaving a file for the next.

In vim, if you want to be able to temporarily leave a modified buffer in order to visit another file, you need to enable this feature with
```

 :set hidden

```which allows modified buffers to be hidden.

---

### Post by yc2 on 2010-10-25
Sorry, one more question

If I edit several files with
:set hidden
:e

Is there any way to close individual files being edited? If I make :q all of vi closes (unless there are modified files open).

---

### Post by spjackson on 2010-10-25
> **yc2 said:**
> Sorry, one more question

If I edit several files with
:set hidden
:e

Is there any way to close individual files being edited? If I make :q all of vi closes (unless there are modified files open).
For general information on working with multiple buffers in Vim see [http://vim.wikia.com/wiki/Vim_buffer_FAQ](http://vim.wikia.com/wiki/Vim_buffer_FAQ)
To list buffers
:buffers
and to delete (close) a buffer,
:bdelete
followed either by the name or the number of the buffer.

---

### Post by krazyd on 2010-10-25
Also :bd is shorthand for :bdelete and with no argument, it just deletes the current buffer.

---

### Post by geirha on 2010-10-25
If you use a dark background in the terminal (e.g. grey on black), try ```
:set bg=dark
``` and it should use brighter foreground colors.

---

### Post by yc2 on 2010-10-26
Thanks guys, very useful help.

I've got reasonably used to the macros now. Using macros in a CLI-editor is nice, I think. Easy to understand the macros if they must be edited.

Thanks for many good advice on the multi-file aditing. The situaion is OK, but I can't get it into exactly what I want. - I know what you are thinking: "This guy is trying to make vim into something it isn't" ;)

I can edit multiple files in either of two ways
1.
:set hidden
:e myfile_2
Here I can leave a modified file open without saving. However, The files do not list with :buffers command and I cannot close them one by one.

2.
:n myfile_2
Here I can list files with :buffers and I can close them individually by :bd. However, I cannot leave modified files open without saving them before hitting :n#.

If this is the situation, just let me know and I will have to choose which one to get used to.

Thanks.

---

### Post by spjackson on 2010-10-26
> **yc2 said:**
> I know what you are thinking: "This guy is trying to make vim into something it isn't" ;)

I confess that I don't normally use vim like this. For substantial editing I will use multiple gvim windows. I am used to using emacs in a terminal with multiple buffers because it has always had that feature, whereas vi didn't.

Having said that, vim does work for me to do what you have described, using the documentation at the link I quoted before plus the help within vim itself. 
> 
I can edit multiple files in either of two ways
1.
:set hidden
:e myfile_2
Here I can leave a modified file open without saving. However, The files do not list with :buffers command and I cannot close them one by one.
That works for me, so I don't know why it doesn't work for you. It is possible to enable/disable certain features when building vim, and Ubuntu has different vim packages with various sets of features. However, since some aspects of multiple buffers are working for you, I wouldn't think that this would be the explanation.
> 
2.
:n myfile_2
Here I can list files with :buffers and I can close them individually by :bd. However, I cannot leave modified files open without saving them before hitting :n#.
You still need :set hidden (which you can of course put in .vimrc) in order to be able to leave modified buffers without saving, and from the way I read your explanation, you are not doing that in option 2.

---

### Post by yc2 on 2010-10-26
Thank you for having the patience. Also for supplying the information that it should be possible to open several files (not only in multiple window/split screen mode, but where only one file is seen at a time) and jump between them without saving the modified files. I should also be able to close them one by one, not only all at once.

Mistakes easily happen when one tries out new things. I now know that it is not a "lack of features" in vim It should be possible to do this using the commands I have been advised. I will go through it all again and read more of the supplied information.

I'll be back with the result in a not too distant future, I hope. :)

Thanks.

---

### Post by yc2 on 2010-10-26
I had missed the set hidden with the n-command. Now it is in my .vimrc. Thanks for noting.

It works fine now, I think. I can edit multiple files and jump between them without saving and also delete individual buffers.

It took some time to find the :bd!4 command. I tried :bd4! which does not work. But now all is OK. I also often slip into :bd#4 (analogous to :n#4) istd of the correct :bd4. OK, I was tired ;)


These are the commands I'm using:

```

:n my_second_file - open new file
:n# - jump to most recently used buffer
:n#3 - jump to buffer #3
:ls - list buffers
:bd - delete the curent buffer (:bd! if modifications not written)
:bd4 - delete buffer #4  (:bd!4 if modifications not written)

```

Thanks for your time and patience guys, any further suggestions appreciated :) But the thread is solved now.

---

### Post by krazyd on 2010-10-28
> **yc2 said:**
> 
I can edit multiple files in either of two ways
1.
:set hidden
:e myfile_2
Here I can leave a modified file open without saving. However, The files do not list with :buffers command and I cannot close them one by one.


much of vim's power lies in its plugins. there is a package called 'vim-scripts' in the repositories. if you install it, it makes it easy to install/remove popular plugins.

Once it's installed, run 'vim-addons' to list the available plugins, and then 'vim-addons install <plugin>' to install.

I use 'bufexplorer' from that package to manage buffers. Press <Leader>be (this is usually \be) to display the list of buffers. Then when a buffer is highlighted press 'd' (delete) to remove (close) it.

If you would like to learn more about vim's full potential, I think this is a good start:
[http://stackoverflow.com/questions/tagged/vim?sort=votes](http://stackoverflow.com/questions/tagged/vim?sort=votes)

---

### Post by yc2 on 2010-10-29
Thanks for all good suggestions. I am very happy with vi.

I would still like to try a whiter background, please compare with gedit in screen-shot. I just haven't found such a default colorsceme. Since I change computer sometimes, it is good if I can set the colors quickly and easily.

Sorry for not reading more, I have been a little busy lately.

I must sometimes run my Ubuntu server via Windows from Internetcafes and I tried gvim. It gives a whiter background. I am sure vim has it too, I just haven't found it yet.

This will not brighten the background:
:highlight Normal ctermfg=black ctermbg=white

I will gradually study add-ons. I am maybe not so flexible when it comes to editors, I want the same stuff to work in all variants I am using. But flexibility naturally increases as you get used to it and can modify it quickly.

Thanks for all help, absolutely of great value.

---

