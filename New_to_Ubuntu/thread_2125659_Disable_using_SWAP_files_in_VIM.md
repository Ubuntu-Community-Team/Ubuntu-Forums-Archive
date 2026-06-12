---
title: "Disable using SWAP files in VIM?"
date: 2013-03-14
forum: New to Ubuntu
---

### Post by DarrenVortex on 2013-03-14
Hello,
I'm a programmer moving from windows to linux :) I didn't create a swap partition when I was installing Ubuntu because with a 4gb ram, I didn't see the need. Now I'm trying to use VIM, but since VIM automatically assumes that a swap partition exists, it tries to save backups into it (If im not mistaken) and since I don't have a swap partition, it fails and interrupts my coding process. I've found articles over how to disable it:
[http://ayaz.wordpress.com/2008/03/31/telling-vim-not-to-create-swap-and-backup-files/](http://ayaz.wordpress.com/2008/03/31/telling-vim-not-to-create-swap-and-backup-files/)
[http://stackoverflow.com/questions/821902/disabling-swap-files-creation-in-vim](http://stackoverflow.com/questions/821902/disabling-swap-files-creation-in-vim)
All these pages refer to a file called "vimrc", but apparently I can't find such file in my $HOME directory. Can someone please help me find this file? I installed gvim through apt-get. Additionally I'd appreciate it if one could tell me how to find the installation directory of any program, in general.
Thanks in advance!:KS

---

### Post by TK999 on 2013-03-14
.vimrc is hidden by default; if it does not exist, feel free to create it:
```

vim ~/.vimrc

```

---

### Post by Cheesemill on 2013-03-14
Are you sure your issue with vim is because you don't have any swap?

I run several machines without swap and I've never had an error from vim.
AFAIK applications can't access your swap space directly anyway, all copying in and out of swap is performed by the kernel.

---

### Post by DarrenVortex on 2013-03-14
I'm not sure why the error was caused but I kept getting "write error in swap file" error at the bottom of vim, and so I assumed that it had to do with the swap partition.
I created the .vimrc file (it didn't exist) and put the configuration lines in, and it looks like it's working now: No interruptions so far. Can't believe it was that easy. Thanks for the tip!

---

### Post by Impavidus on 2013-03-14
Vim creates a .foo.swp file, called a swap file, when you're editing foo and saves this in the same directory as foo. This file is used for recovery in case vim crashes or it terminated by the TERM signal (which triggers an emergency write to the .swp file). As said, this file is in an ordinary partition, so not having a swap partition doesn't matter. There must be a different reason why your vim can't make a swap file.

---

