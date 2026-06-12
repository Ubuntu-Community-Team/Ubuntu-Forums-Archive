---
title: "CHEAT SHEET: vim"
date: 2006-02-03
forum: Outdated Tutorials &amp; Tips
---

### Post by TimL on 2006-02-03
Hi,

I've just recently created a vim cheat sheet (in PDF format) to help me keep track of all the commands that there are available in this editor. I just thought I'd share it with anyone here who may find vim a bit daunting or just difficult to use!

You can get a copy here: [http://www.tjl2.com/sysadmin/vim-cheat-sheet.html]("http://www.tjl2.com/sysadmin/vim-cheat-sheet.html")

Let me know if you find any errors or typos in it (I think I've found them all).

Cheers,

Tim

---

### Post by sunwave on 2006-02-06
hi !

very useful - thanks a lot!

:cool:

---

### Post by TimL on 2006-02-08
Glad you like it.

I was hoping to include info about the macro/command recording functionality of vim, but I couldn't get it to work properly following the instructions I'd got down!

---

### Post by maulattu on 2006-02-08
Nice one :)

---

### Post by void_false on 2006-02-08
Of course it is an excelent job but what I miss is how to compile and execute program with vim. :(

---

### Post by endersshadow on 2006-02-08
You forgot a very important one!

:set nu! = show line numbers

Otherwise, fantastic quick ref!

---

### Post by Quirky on 2006-02-08
:make

That compiles things. I have it mapped to F5, with mappings to jump the the next and previous errors. Similarly for :grep.

I also recommend reading ":help completion" and adding the CleverTab function to your ~/.vimrc - Tab then "autocompletes" things (variable names, functions, etc). Also, don't forget to use ctags. g] is a life saver when you have to maintain someone else's spaghetti code.

---

### Post by Koybe on 2006-02-08
Nice one! I also get it.

---

### Post by Caboto on 2006-02-09
[QUOTE=Quirky]:make

That compiles things. I have it mapped to F5, with mappings to jump the the next and previous errors. Similarly for :grep.

I also recommend reading ":help completion" and adding the CleverTab function to your ~/.vimrc - Tab then "autocompletes" things (variable names, functions, etc). Also, don't forget to use ctags. g] is a life saver when you have to maintain someone else's spaghetti code.[/QUOTE]
Very nice guide... Will be a great guide for me.
I'm not yet into vim, but is there a file, where the mapped keys are stored? Would be great, to have a configured vim and some examples of mapped keys.

---

### Post by matthew on 2006-02-09
Thank you!

---

### Post by void_false on 2006-02-09
If I type :make then I get
```
make: *** No targets specified and no makefile found.  Stop.

Hit ENTER or type command to continue
```
I want to know how to preform "g++ myfile.cpp" and "./a.out" from vim's command line.

---

### Post by caffinide on 2006-02-09
awesome

---

### Post by marcw on 2006-02-09
[QUOTE=TimL]
I've just recently created a vim cheat sheet (in PDF format) to help me keep track of all the commands that there are available in this editor. I just thought I'd share it with anyone here who may find vim a bit daunting or just difficult to use!
Tim[/QUOTE]

Very nice.  Thanks!

(now if I could only find something similar for awk and sed...)

---

### Post by Quirky on 2006-02-10
[QUOTE=void_false]If I type :make then I get
```
make: *** No targets specified and no makefile found.  Stop.

Hit ENTER or type command to continue
```
I want to know how to preform "g++ myfile.cpp" and "./a.out" from vim's command line.[/QUOTE]

That's because you have no Makefile. For really basic compilation, you can just do this:
```
:!g++ myfile.cpp
:!./a.out
```
You ought to use a Makefile, since it is easier in the long run. The vim combination :! calls an external program but doesn't capture the output, unlike the built in :make command.

---

### Post by NeTo on 2006-02-10
The cheat sheet is excellent! Thank you TimL! Now I can feel confident while using vim :KS

---

### Post by void_false on 2006-02-10
**Quirky**
OMG thanks a lot! That is the thing that I missed so much! :-D

---

### Post by TimL on 2006-03-06
Thanks for the kind comments! I didn't realise there had been this many responses to this thread, as I haven't been getting the email notifications.

endersshadow - thanks for the ':set nu' advice, I didn't know about that one! I've just added it in and it'll be uploaded in the next few minutes.

Cheers,

Tim

---

### Post by rayburn on 2006-03-06
Just downloaded pdf, very good, many thanks!

---

### Post by IYY on 2006-03-06
Very nice. How about you post the source of that PDF too? (Tex? OO?)

---

### Post by TimL on 2006-03-07
[QUOTE=IYY]Very nice. How about you post the source of that PDF too? (Tex? OO?)[/QUOTE]
Nice idea. I've added a link to the OpenOffice Draw .odg source file on the page now. [http://tjl2.com/sysadmin/vim-cheat-sheet.html]("http://tjl2.com/sysadmin/vim-cheat-sheet.html")

I've also licensed it under the Creative Commons Attribution2.5 License so that people know they can freely make changes to it.

Cheers,

Tim

---

### Post by IYY on 2006-03-07
Thanks!

---

### Post by sapo on 2006-03-12
Very nice, i was looking for a good one and now i found it! :mrgreen:

thanx a lot!

---

### Post by TimL on 2006-03-12
Hi all,

Just a quick update: if you have bookmarked the link to my vim cheat sheet page at tjl2.com/sysadmin/personal.html#vim, please update your bookmark to [http://tjl2.com/sysadmin/vim-cheat-sheet.html]("http://tjl2.com/sysadmin/vim-cheat-sheet.html")

I thought my pages were getting a bit long, so I've started restructuring my site a bit. The link to the #vim anchor still works and will do for a while, but there doesn't seem to be a way to make mod_rewrite handle page anchors (I think they are just handled by the browser once the page has loaded), so I will eventually have to break that link.

If you have just bookmarked the PDF, that will still work.

Cheers,

Tim

---

