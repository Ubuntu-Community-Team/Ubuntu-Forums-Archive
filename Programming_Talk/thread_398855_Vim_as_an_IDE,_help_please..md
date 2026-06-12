---
title: "Vim as an IDE, help please."
date: 2007-04-01
forum: Programming Talk
---

### Post by Hendrixski on 2007-04-01
I bought an old laptop to amuse myself, and eclipse is just too memory intensive for it.  I used to use vi a long time ago so I figured I'll try vim as an IDE... but now I'm having trouble setting up the command completion in vim.

I apt-got the latest vim-full, and I compiled exuberant-ctags 5.6 from their site (apparently the version in the repo's is one that needs a patch).  Then I added this to my vimrc
```
filetype plugin indent on
set tags+=~/.vim/systags
```
and ran the ctags command
```
ctags -R -f ~/.vim/systags /usr/include/qt3/ 
```

Then in a hello world program I declare
```
int main(int argc, char *argv[]){
        QApplication app(argc, argv);
        app.
```
So when I hit CTRL X CTRL O after app it should give me a list of functions in QApplication, right?  All it tells me is that Omni "pattern not found".

If I type :tag <tab> it cycles me through thousands of random words (ditto CTRL X CTRL ] . :-(  I thought I followed the documentation to a T (vimdocs.sourceforge.net)...  [SIZE="4"]Can anybody tell me what I'm missing or doing wrong?[/SIZE]

---

### Post by WiseElben on 2007-04-01
I just began trying out Vim, but Ctrl X Ctrl P is what I use.

---

### Post by Keffin on 2007-04-03
There is currently no built in omni-completion (vims term for the kind of completion you are after) for C++. There is built in support for plain C and the other languages listed by using :help compl-omni-filetypes

Have a look at the omnicppcomplete script on vim.org ([http://www.vim.org/scripts/script.php?script_id=1520](http://www.vim.org/scripts/script.php?script_id=1520)), which adds this functionality for C++. If I remember correctly the help file even uses an example of generating and using tags for Qt. I found it reasonable after a quick play a while ago, though I couldn't manage to create and/or use tags for the standard library.


FYI to WiseElben, I'm pretty sure Ctrl-X Ctrl-P is the same as just Ctrl-P. This function is for general purpose word completion and does not restrict available results based on context. e.g. doing Ctrl-P after typing myStruct-> in a C program file will not restrict the results offered to only members of the myStruct structure. It's still damn useful though :).

---

### Post by Hendrixski on 2007-04-03
SWEET
It worked.  The link you posted has an extra ")" so at first it doesn't find it.  then I copied the files of the script into ~/.vim/ and followed the instructinos in the doc file (adding 2 lines to .vimrc bascly)  and BANG!  it worked.

THANKS!

---

### Post by Hendrixski on 2007-09-05
Hey, when I hosed my computer recently, I tried re-installing and I had some problems getting this all set up, when I started to edit a file and tried to run omnicomplete I'd get an error
```
"E713: Cannot use empty key for Dictionary"
```
turns out this is a known bug. [http://www.mail-archive.com/vim@vim.org/msg13302.html](http://www.mail-archive.com/vim@vim.org/msg13302.html)
Basically, just save the file once before onmicompleting stuff on it.

---

