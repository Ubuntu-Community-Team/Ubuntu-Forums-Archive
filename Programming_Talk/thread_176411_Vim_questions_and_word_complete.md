---
title: "Vim questions and word complete"
date: 2006-05-14
forum: Programming Talk
---

### Post by Freddd on 2006-05-14
Hi!

1. Where shall I put my plugins?
/etc/vim/ 
or 
/usr/share/vim/

2. Do anyone know how to install the plugin word_womplete.vim properly? 
[http://www.vim.org/scripts/script.php?script_id=73](http://www.vim.org/scripts/script.php?script_id=73)

I can get it to work but not to activate it by default? What is the correct approach? I have read the instructions but it doesn't help ](*,)  
I got it to work by invoking it in a ftplugin file (.c extension) but not via the gvimrc :(

Answers much appreciated.

---

### Post by yaaarrrgg on 2006-05-15
I usually create a folder under my home directory called .vim/plugin/

Also, is your config flie named correctly?  I created a file in my home directory named .vimrc   ... it is fired when the vi starts.  Also, the "autobuffer" command will let you fire events for specific file types.

---

### Post by Freddd on 2006-05-15
[QUOTE=yaaarrrgg]I usually create a folder under my home directory called .vim/plugin/[/QUOTE]Okey, seems good, how do you make sure that your plugins are loaded when you put them in that directory? Is that done by vim by default or do you source them in your gvimrc?

[QUOTE=yaaarrrgg]Also, is your config flie named correctly?  I created a file in my home directory named .vimrc   ... it is fired when the vi starts.  Also, the "autobuffer" command will let you fire events for specific file types.[/QUOTE]My vimrc works, but I think I will use the same locations as you anyway, seems good? Anything I need to tihnk of to get it work, or is it only to drop the files?

I got the word_complete to load by adding this in my gvimrc:
:autocmd BufEnter * call DoWordComplete()

---

### Post by yaaarrrgg on 2006-05-15
AFAIK, the ~/.vim/plugin/ directory should be scanned when vim starts.  You shouldn't need to source them if they are dropped here.  Although some plugins (like yours) need an aditional command to actually start the plugin.... either added to .vimrc or typed manually after vim starts.  This is so you can turn it on and off if needed.

---

### Post by Freddd on 2006-05-18
yaaarrrgg or anyone else that might know, do you know how to get dictionary completion to work? I have tried to do as written in this guide without success:
[http://vim.sourceforge.net/tips/tip.php?tip_id=91](http://vim.sourceforge.net/tips/tip.php?tip_id=91)

Would really appreciate help on this, would be really nice to get it to work. As it is now, I keep getting pattern not known when I try; ctrl-n or ctrl-p

---

### Post by ow50 on 2006-05-18
[QUOTE=Freddd]yaaarrrgg or anyone else that might know, do you know how to get dictionary completion to work? I have tried to do as written in this guide without success:
[http://vim.sourceforge.net/tips/tip.php?tip_id=91](http://vim.sourceforge.net/tips/tip.php?tip_id=91)[/QUOTE]
It should work as explained in that link. For example, I use filetype specific dictionaries with the following in my .vimrc:
```
set complete+=k
autocmd FileType * exec('set dictionary+=~/.vim/dict/' . &filetype)
```
I have for example a file ~/.vim/dict/python, that has all Python keywords and that is in use whenever I edit a file of filetype "python".

Keep in mind that using dictionary completion for an actual human language from /usr/share/dict/ can be unbearably slow.

---

### Post by Freddd on 2006-05-18
Still doesn't work ](*,)

The .gvimrc works fine to load but the completions never find anything when I try to use it.

---

### Post by yaaarrrgg on 2006-05-18
It might help to do this the long way first.  You might try this:
 
create a text file named /tmp/text.txt that has a few words, one word per line. 

then when you are in vi, do 
 
```
 
:set dictionary+=/tmp/test.txt 

``` 
 
next, when you are in insert mode, type the first part of a word, and then hit ctrl-X ctrl-K.  This should complete the word.

---

### Post by Freddd on 2006-05-18
[QUOTE=yaaarrrgg]It might help to do this the long way first.  You might try this:
 
create a text file named /tmp/text.txt that has a few words, one word per line. 

then when you are in vi, do 
 
```
 
:set dictionary+=/tmp/test.txt 

``` 
 
next, when you are in insert mode, type the first part of a word, and then hit ctrl-X ctrl-K.  This should complete the word.[/QUOTE]Thanks once again for trying to help me. I followed your guide carefuly, added test.txt file to my home folder ie /tmp/test.txt

Opened a new document with gvim and entered the command:
:set dictionary+=/tmp/test.txt 

I get the following when going to insert-mode and writing the half part of the word and then entering the commands ctrl-X ctrl-K:
Dictionary completion (^K^N^P) Pattern not found

Why doesn't it work :-| 
Plugins and other stuff are no problem at all..

---

### Post by yaaarrrgg on 2006-05-18
oops.. I have a typo.  Should create a file named /tmp/test.txt

If that still doesn't work, then the other word complete plugin you installed might possibly be redefining something.  You might try removing the other plugings and retesting.

---

### Post by Freddd on 2006-05-18
I got it to work by putting test.txt in my home folder ie home/test.txt But it doesn't seem good to have all those here, what might be wrong? :-k

---

### Post by Freddd on 2006-05-18
Now it works with other directories too :) I will check if it work with gvimrc

---

