---
title: "vim, how to set cursor to return to previous position at reedit"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by statmech on 2008-05-10
After editing a file with vim, and then exit the file, upon
reediting the same with vim, the cursor should be positioned at the
previous position when exiting the file.  The information on the
previous location of the cursor (and other vim info) should be stored
in ~/.viminfo.

For some reason, in my installation of Ubuntu 7.10 Gutsy, I did not 
get the cursor to come back to the previous position at reediting.

Any suggestion would be appreciated.

Thanks.

---

### Post by Monicker on 2008-05-10
Check out this section of /etc/vim/vimrc

```
" Uncomment the following to have Vim jump to the last position when
" reopening a file
"if has("autocmd")
"  au BufReadPost * if line("'\"") > 0 && line("'\"") <= line("$")
"    \| exe "normal g'\"" | endif
"endif
```


I uncommented the lines as suggested, and it does indeed go to last position I was at when I open a file again.

---

### Post by statmech on 2008-05-10
Thanks, but it did not work for me.  I did uncomment the lines you pointed out; I must have missed something...

I had the following vim packages installed:

```

   root@rc0224:/home/users/vql# dpkg -l | grep vim
   ii  vim-common                                 1:7.1-056+2ubuntu2           Vi IMproved - Common files
   ii  vim-runtime                                1:7.1-056+2ubuntu2           Vi IMproved - Runtime files
   ii  vim-tiny                                   1:7.1-056+2ubuntu2           Vi IMproved - enhanced vi editor - compact v
   root@rc0224:/home/users/vql#

```

What did you have?  Thanks.

---

### Post by Monicker on 2008-05-10
Do you have a .vimrc file in your home folder?  I believe that would take precedence over /etc/vim/vimrc.

---

### Post by statmech on 2008-05-10
No, I deleted the file ~/.vimrc that I created to try various
solutions that did not work.  Without my ~/.vimrc, uncommenting the
lines you said in /etc/vim/vimrc was not enough.

I finally solved the problem as follows.

First, I also noticed the following lines /etc/vim/vimrc:

```

   " Vim5 and later versions support syntax highlighting. Uncommenting the next
   " line enables syntax highlighting by default.
   "syntax on

```

So I uncommented the above line to get syntax highlighting... But I got an
error message...

So both syntax highlighting and the return of the cursor to the previous
position at reedit did not work.

Search for vim-related packages:

```

   root@rc0224:/home/users/vql# apt-cache search vim
   cernlib-base - common files for Cernlib libraries and programs
   colordiff - tool to colorize 'diff' output
   cream - VIM macros that make the VIM easier to use for beginners
   editmoin - edit MoinMoin wiki pages with your favourite editor
   elvis-tiny - Tiny vi compatible editor for the base system

   ... cut  ...

   vim-addon-manager - manager of addons for the Vim editor
   vim-full - Vi IMproved - enhanced vi editor - full fledged version
   vim-gtk - Vi IMproved - enhanced vi editor - with GTK2 GUI
   vim-latexsuite - View, edit and compile LaTeX documents from within vim
   vim-perl - Vi IMproved - enhanced vi editor - with Perl support
   vim-python - Vi IMproved - enhanced vi editor - with Python support
   vim-rails - plugins for vim to allow easier editing of Rails Applications
   vim-ruby - Vi IMproved - enhanced vi editor - with Ruby support
   vim-scripts - plugins for vim, adding bells and whistles
   vim-syntax-gtk - Syntax files to highlight gtk+ keywords in vim
   vim-tcl - Vi IMproved - enhanced vi editor - with TCL support
   vim-vimoutliner - script for building an outline editor on top of Vim

   ... cut ...

   vim - Vi IMproved - enhanced vi editor
   vim-common - Vi IMproved - Common files
   vim-doc - Vi IMproved - HTML documentation
   vim-gnome - Vi IMproved - enhanced vi editor - with GNOME2 GUI
   vim-gui-common - Vi IMproved - Common GUI files
   vim-runtime - Vi IMproved - Runtime files
   vim-tiny - Vi IMproved - enhanced vi editor - compact version
   root@rc0224:/home/users/vql#

```

I noticed the vim-full package; Install vim-full:

```

   root@rc0224:/home/users/vql# apt-get install vim-full
   Reading package lists... Done
   Building dependency tree       
   Reading state information... Done
   The following extra packages will be installed:
     libruby1.8 vim-gui-common
   Suggested packages:
     cscope vim-doc
   The following NEW packages will be installed:
     libruby1.8 vim-full vim-gui-common
   0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
   Need to get 2681kB of archives.
   After unpacking 8348kB of additional disk space will be used.
   Do you want to continue [Y/n]? Y
   Get:1 http://archive.ubuntu.com gutsy/main libruby1.8 1.8.6.36-1ubuntu3 [1566kB]
   Get:2 http://us.archive.ubuntu.com gutsy/universe vim-full 1:7.1-056+2ubuntu2 [966kB]  
   Get:3 http://archive.ubuntu.com gutsy/main vim-gui-common 1:7.1-056+2ubuntu2 [150kB]                         
   Fetched 2681kB in 16s (160kB/s)                                                                              
   Selecting previously deselected package libruby1.8.
   (Reading database ... 106680 files and directories currently installed.)
   Unpacking libruby1.8 (from .../libruby1.8_1.8.6.36-1ubuntu3_i386.deb) ...
   Selecting previously deselected package vim-gui-common.
   Unpacking vim-gui-common (from .../vim-gui-common_1%3a7.1-056+2ubuntu2_all.deb) ...
   Selecting previously deselected package vim-full.
   Unpacking vim-full (from .../vim-full_1%3a7.1-056+2ubuntu2_i386.deb) ...
   Setting up libruby1.8 (1.8.6.36-1ubuntu3) ...

   Setting up vim-gui-common (1:7.1-056+2ubuntu2) ...

   Setting up vim-full (1:7.1-056+2ubuntu2) ...

   Processing triggers for libc6 ...
   ldconfig deferred processing now taking place
   root@rc0224:/home/users/vql# 

```

Test vim; yes, the cursor did come back to the previous position.
The syntax highlighting also worked.

Thanks for your comment.

Cheers.

---

### Post by Monicker on 2008-05-10
> **statmech said:**
> Thanks, but it did not work for me.  I did uncomment the lines you pointed out; I must have missed something...

I had the following vim packages installed:

```

   root@rc0224:/home/users/vql# dpkg -l | grep vim
   ii  vim-common                                 1:7.1-056+2ubuntu2           Vi IMproved - Common files
   ii  vim-runtime                                1:7.1-056+2ubuntu2           Vi IMproved - Runtime files
   ii  vim-tiny                                   1:7.1-056+2ubuntu2           Vi IMproved - enhanced vi editor - compact v
   root@rc0224:/home/users/vql#

```

What did you have?  Thanks.

Ahh. Yes, I do have the vim-full package installed.

---

### Post by statmech on 2009-01-27
> **statmech said:**
> No, I deleted the file ~/.vimrc that I created to try various
solutions that did not work.  Without my ~/.vimrc, uncommenting the
lines you said in /etc/vim/vimrc was not enough.

I finally solved the problem as follows.

First, I also noticed the following lines /etc/vim/vimrc:

```

   " Vim5 and later versions support syntax highlighting. Uncommenting the next
   " line enables syntax highlighting by default.
   "syntax on

```

So I uncommented the above line to get syntax highlighting... But I got an
error message...

So both syntax highlighting and the return of the cursor to the previous
position at reedit did not work.

Search for vim-related packages:

```

   root@rc0224:/home/users/vql# apt-cache search vim
   cernlib-base - common files for Cernlib libraries and programs
   colordiff - tool to colorize 'diff' output
   cream - VIM macros that make the VIM easier to use for beginners
   editmoin - edit MoinMoin wiki pages with your favourite editor
   elvis-tiny - Tiny vi compatible editor for the base system

   ... cut  ...

   vim-addon-manager - manager of addons for the Vim editor
   vim-full - Vi IMproved - enhanced vi editor - full fledged version
   vim-gtk - Vi IMproved - enhanced vi editor - with GTK2 GUI
   vim-latexsuite - View, edit and compile LaTeX documents from within vim
   vim-perl - Vi IMproved - enhanced vi editor - with Perl support
   vim-python - Vi IMproved - enhanced vi editor - with Python support
   vim-rails - plugins for vim to allow easier editing of Rails Applications
   vim-ruby - Vi IMproved - enhanced vi editor - with Ruby support
   vim-scripts - plugins for vim, adding bells and whistles
   vim-syntax-gtk - Syntax files to highlight gtk+ keywords in vim
   vim-tcl - Vi IMproved - enhanced vi editor - with TCL support
   vim-vimoutliner - script for building an outline editor on top of Vim

   ... cut ...

   vim - Vi IMproved - enhanced vi editor
   vim-common - Vi IMproved - Common files
   vim-doc - Vi IMproved - HTML documentation
   vim-gnome - Vi IMproved - enhanced vi editor - with GNOME2 GUI
   vim-gui-common - Vi IMproved - Common GUI files
   vim-runtime - Vi IMproved - Runtime files
   vim-tiny - Vi IMproved - enhanced vi editor - compact version
   root@rc0224:/home/users/vql#

```

I noticed the vim-full package; Install vim-full:

```

   root@rc0224:/home/users/vql# apt-get install vim-full
   Reading package lists... Done
   Building dependency tree       
   Reading state information... Done
   The following extra packages will be installed:
     libruby1.8 vim-gui-common
   Suggested packages:
     cscope vim-doc
   The following NEW packages will be installed:
     libruby1.8 vim-full vim-gui-common
   0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
   Need to get 2681kB of archives.
   After unpacking 8348kB of additional disk space will be used.
   Do you want to continue [Y/n]? Y
   Get:1 http://archive.ubuntu.com gutsy/main libruby1.8 1.8.6.36-1ubuntu3 [1566kB]
   Get:2 http://us.archive.ubuntu.com gutsy/universe vim-full 1:7.1-056+2ubuntu2 [966kB]  
   Get:3 http://archive.ubuntu.com gutsy/main vim-gui-common 1:7.1-056+2ubuntu2 [150kB]                         
   Fetched 2681kB in 16s (160kB/s)                                                                              
   Selecting previously deselected package libruby1.8.
   (Reading database ... 106680 files and directories currently installed.)
   Unpacking libruby1.8 (from .../libruby1.8_1.8.6.36-1ubuntu3_i386.deb) ...
   Selecting previously deselected package vim-gui-common.
   Unpacking vim-gui-common (from .../vim-gui-common_1%3a7.1-056+2ubuntu2_all.deb) ...
   Selecting previously deselected package vim-full.
   Unpacking vim-full (from .../vim-full_1%3a7.1-056+2ubuntu2_i386.deb) ...
   Setting up libruby1.8 (1.8.6.36-1ubuntu3) ...

   Setting up vim-gui-common (1:7.1-056+2ubuntu2) ...

   Setting up vim-full (1:7.1-056+2ubuntu2) ...

   Processing triggers for libc6 ...
   ldconfig deferred processing now taking place
   root@rc0224:/home/users/vql# 

```

Test vim; yes, the cursor did come back to the previous position.
The syntax highlighting also worked.

Thanks for your comment.

Cheers.

Tue Jan 27 13:32:50 EST 2009

Actually, I recently installed ubuntu 8.04 Hardy on another machine, and after 
installing vim-full, I had to go back to edit the file /etc/vim/vimrc to uncomment 
the code for syntax highlighting and for vim to jump back to the previous cursor
position upon reediting (see previous posts further above).  So just installing vim-full was not enough, at least with
ubuntu 8.04 Hardy.

---

