---
title: "[SOLVED] VIM not working corectly in ubuntu"
date: 2007-12-26
forum: Programming Talk
---

### Post by SweeeT on 2007-12-26
Hey guys!

I've been using VIM on windows for some time and now I changed to linux Ubuntu... I started using VIM in Terminal and I found out there's a problem.
For example:
#include <iostream>

using namespace std:

int main ()
{

}

And that's where the problem is.. Betwen { and } VIM doesn't automatically "press TAB".. So I have to press TAB every time I it's needed.. When I was using Cygwin in Windows VIM automatically "pressed TAB" for me..

So can anyone tell me how to fix it?

Best Regards!

---

### Post by LaRoza on 2007-12-26
```

sudo aptitude install vim-full

```

You can set your preferences from there, Ubuntu ships with "vim-tiny", very limited.

---

### Post by SweeeT on 2007-12-26
Thank you very much for a fast reply :P I am installing atm and hope it works!

Thanks again!

---

### Post by SweeeT on 2007-12-26
Hey..
I got it installed but I don't know how to set VIM differently.. I went trough the help file but I found nothing that would help solve my problem.. Can you please give further instructions?

Best Regards

---

### Post by LaRoza on 2007-12-26
> **SweeeT said:**
> Hey..
I got it installed but I don't know how to set VIM differently.. I went trough the help file but I found nothing that would help solve my problem.. Can you please give further instructions?

Best Regards

Configuring Vim can be complex or simple, try: [http://vim.wikia.com/wiki/Main_Page](http://vim.wikia.com/wiki/Main_Page)

---

### Post by samjh on 2007-12-26
Shameless plug: [http://ubuntuforums.org/showthread.php?t=564554](http://ubuntuforums.org/showthread.php?t=564554)

Includes a small section of making custom setups.

---

### Post by SweeeT on 2007-12-26
I went trough wiki and samjh's topic and still don't get it.. 

I did sudo apt-get vim full command (which I guess is the same as sudo apt-get vim ) in terminal, went trough wiki and read vimfuf.pdf but there is no answer to my question.. I still cant get VIM to automatically "press TAB" between { and } and places I need it..

Did anyone have the same problem?

---

### Post by LaRoza on 2007-12-26
[http://newbiedoc.sourceforge.net/tutorials/vim/personal-vim.html.en](http://newbiedoc.sourceforge.net/tutorials/vim/personal-vim.html.en)

It is the "autoindent" feature.

---

### Post by SweeeT on 2007-12-26
Man.. 
I tryed :set autoindent in VIM and it didn't work..
I went to etc/vim folder and opened vimrc (there is no dot before vimrc.. Strange..). I added set autoindent and pressed Ctrl+S to save.. I get a message you dont have permissions...
So I went to terminal cd etc/vim and did chmod +rwx vimrc and it told me I dont have permission to set the permissions o.O

I am the administrator of the computer and can't change permissions..
So what do I do to solve that problem?

Best Regards

---

### Post by PaulFr on 2007-12-26
Add the following to your ~/.vimrc file:```
" Set filetype recognition and indenting on
filetype indent on

" For unrecognized filetypes
set autoindent
```So now if you start vim with an existing file or a file with a known file type, it will use the indenting rules for that filetype, otherwise, it will at least follow the autoindent rule to keep your cursor at the same place as the last line. Hope this helps.

P.S. Just noticed your post above. Please make this change in a **.vimrc** file in your home directory. If it does not exist, please create it. Do not edit the system wide vimrc unnecessarily.

P.P.S. FYI, if you start vim on the command line as **vim** with no file name, then vim cannot recognize the language you are using. So using autoindent will not help other than keeping your cursor at same position as last line. If you start vim on the command line as **vim myfile.C**, then vim can recognize the filetype from the extension .C.

One more note :-): If you want syntax coloring on, then you need to add the line ```
syntax on
``` in your .vimrc.

---

### Post by SweeeT on 2007-12-26
> **PaulFr said:**
> Add the following to your ~/.vimrc file:```
" Set filetype recognition and indenting on
filetype indent on

" For unrecognized filetypes
set autoindent
```So now if you start vim with an existing file or a file with a known file type, it will use the indenting rules for that filetype, otherwise, it will at least follow the autoindent rule to keep your cursor at the same place as the last line. Hope this helps.

P.S. Just noticed your post above. Please make this change in a **.vimrc** file in your home directory. If it does not exist, please create it. Do not edit the system wide vimrc unnecessarily.

P.P.S. FYI, if you start vim on the command line as **vim** with no file name, then vim cannot recognize the language you are using. So using autoindent will not help other than keeping your cursor at same position as last line. If you start vim on the command line as **vim myfile.C**, then vim can recognize the filetype from the extension .C.

One more note :-): If you want syntax coloring on, then you need to add the line ```
syntax on
``` in your .vimrc.

Thanks Paul! It's all working now :) It was the filetype indent on thing that made the difference.. Also I had to change vimrc in .vimrc and copy it into my home folder :)
I'll mark thread as solved..

---

