---
title: "[vim] dark colors and gnome-terminal"
date: 2009-06-20
forum: Programming Talk
---

### Post by pikkio on 2009-06-20
Hi! I just installed the "darkspectrum" color scheme, resembling the Oblivion theme for gedit.

Unfortunately, it seems to only work well with gvim (GTK+ GUI for vim). On gnome-terminal and konsole, colors are a total mess. I tried with other color schemes, and results are the same. With dark themes, for example, the background remains pure white. Even foreground colors are wrong and I can note random bold highlighting on keywords.

I then put "set t_Co=256" in my .vimrc, but even though colors changed a little bit, the issue still remains.

I think I should edit some options in gnome-terminal, but I've got no clue. Any ideas?

Thanks :)

---

### Post by svamppi on 2009-06-20
Vim color themes are different for gvim, basic terminal and "multi-color" terminal. I recommend the CSApprox plugin [http://www.vim.org/scripts/script.php?script_id=2390](http://www.vim.org/scripts/script.php?script_id=2390) which allows you to use any gvim color theme in a 256-color capable terminal. You probably need to either set t_Co=256 in your .vimrc or change TERM=xterm-256color in your .bashrc for it to work.

---

### Post by vijiboy on 2012-03-12
thanks svamppi. CSApprox does it correctly. previously I used set t_co=256, and export TERM = "xterm-256color" but still had some colors left out.

---

### Post by nothingspecial on 2012-03-12
Please don't bump very old threads to the top.

Closed.

---

