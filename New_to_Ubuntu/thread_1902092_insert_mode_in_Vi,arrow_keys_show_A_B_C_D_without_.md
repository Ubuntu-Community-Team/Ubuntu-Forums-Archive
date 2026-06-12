---
title: "insert mode in Vi,arrow keys show A B C D without moving"
date: 2011-12-29
forum: New to Ubuntu
---

### Post by shan88 on 2011-12-29
i`m new to vi editor.when i press arrow keys to navigate the cursor
in vi it gives A B C D other than move the cursor.i`m using Ubuntu 11.04.plz somebody can fix my problem i`l be really grateful.

---

### Post by shan88 on 2011-12-30
Please somebody help me

---

### Post by Jack Brown on 2011-12-30
reach vim docs online at :
[http://vimdoc.sourceforge.net/htmldoc/help.html#help.txt](http://vimdoc.sourceforge.net/htmldoc/help.html#help.txt)


what you're looking for is there.  also pasted it below

```
*help.txt*    For Vim version 7.3.  Last change: 2010 Jul 20              VIM - main help file                                      [k]("http://vimdoc.sourceforge.net/htmldoc/motion.html#k")       Move around:  Use the cursor keys, or "[h]("http://vimdoc.sourceforge.net/htmldoc/motion.html#h")" to go left,           [h]("http://vimdoc.sourceforge.net/htmldoc/motion.html#h")   [l]("http://vimdoc.sourceforge.net/htmldoc/motion.html#l")             "[j]("http://vimdoc.sourceforge.net/htmldoc/motion.html#j")" to go down, "[k]("http://vimdoc.sourceforge.net/htmldoc/motion.html#k")" to go up, "[l]("http://vimdoc.sourceforge.net/htmldoc/motion.html#l")" to go right.     [j]("http://vimdoc.sourceforge.net/htmldoc/motion.html#j") Close this [window]("http://vimdoc.sourceforge.net/htmldoc/windows.html#window"):  Use ":q<Enter>".    Get out of Vim:  Use ":qa!<Enter>" (careful, all changes are lost!).  Jump to a subject:  Position the cursor on a [tag]("http://vimdoc.sourceforge.net/htmldoc/tagsrch.html#tag") (e.g. |[bars]("http://vimdoc.sourceforge.net/htmldoc/help.html#bars")|) and hit ["]CTRL-]]("http://vimdoc.sourceforge.net/htmldoc/tagsrch.html#CTRL-).    With the mouse:  "[:set]("http://vimdoc.sourceforge.net/htmldoc/options.html#:set") [mouse]("http://vimdoc.sourceforge.net/htmldoc/options.html#%27mouse%27")=a" to enable the mouse (in xterm or [GUI]("http://vimdoc.sourceforge.net/htmldoc/gui.html#GUI")).             Double-click the left mouse button on a [tag]("http://vimdoc.sourceforge.net/htmldoc/tagsrch.html#tag"), e.g. |[bars]("http://vimdoc.sourceforge.net/htmldoc/help.html#bars")|.     Jump back:  Type [CTRL-T]("http://vimdoc.sourceforge.net/htmldoc/tagsrch.html#CTRL-T") or [CTRL-O]("http://vimdoc.sourceforge.net/htmldoc/motion.html#CTRL-O") (repeat to go further back).  Get specific help:  It is possible to go directly to whatever you want help             on, by giving an argument to the |[:help]("http://vimdoc.sourceforge.net/htmldoc/helphelp.html#:help")| command.             It is possible to further specify the context:                              *help-context*               WHAT            PREPEND    EXAMPLE                   [Normal]("http://vimdoc.sourceforge.net/htmldoc/intro.html#Normal") mode command      (nothing)   [:help]("http://vimdoc.sourceforge.net/htmldoc/helphelp.html#:help") [x]("http://vimdoc.sourceforge.net/htmldoc/change.html#x")               [Visual]("http://vimdoc.sourceforge.net/htmldoc/visual.html#Visual") mode command      v_       [:help]("http://vimdoc.sourceforge.net/htmldoc/helphelp.html#:help") [v_u]("http://vimdoc.sourceforge.net/htmldoc/change.html#v_u")               [Insert]("http://vimdoc.sourceforge.net/htmldoc/insert.html#Insert") mode command      i_       [:help]("http://vimdoc.sourceforge.net/htmldoc/helphelp.html#:help") [i_<Esc>]("http://vimdoc.sourceforge.net/htmldoc/insert.html#i_%3CEsc%3E")               [Command-line]("http://vimdoc.sourceforge.net/htmldoc/cmdline.html#Command-line") command      :       [:help]("http://vimdoc.sourceforge.net/htmldoc/helphelp.html#:help") [:quit]("http://vimdoc.sourceforge.net/htmldoc/editing.html#:quit")               [Command-line]("http://vimdoc.sourceforge.net/htmldoc/cmdline.html#Command-line") editing      c_       [:help]("http://vimdoc.sourceforge.net/htmldoc/helphelp.html#:help") [c_<Del>]("http://vimdoc.sourceforge.net/htmldoc/cmdline.html#c_%3CDel%3E")               Vim command argument      -       [:help]("http://vimdoc.sourceforge.net/htmldoc/helphelp.html#:help") [-r]("http://vimdoc.sourceforge.net/htmldoc/starting.html#-r")               Option              ''       [:help]("http://vimdoc.sourceforge.net/htmldoc/helphelp.html#:help") ['textwidth']("http://vimdoc.sourceforge.net/htmldoc/options.html#%27textwidth%27")   Search for help:  Type "[:help]("http://vimdoc.sourceforge.net/htmldoc/helphelp.html#:help") word", then hit [CTRL-D]("http://vimdoc.sourceforge.net/htmldoc/scroll.html#CTRL-D") to see matching             help entries for "[word]("http://vimdoc.sourceforge.net/htmldoc/motion.html#word")".             Or use ":helpgrep word". |[:helpgrep]("http://vimdoc.sourceforge.net/htmldoc/helphelp.html#:helpgrep")|  VIM stands for [Vi]("http://vimdoc.sourceforge.net/htmldoc/intro.html#Vi") IMproved.  Most of VIM was made by [Bram]("http://vimdoc.sourceforge.net/htmldoc/intro.html#Bram") [Moolenaar]("http://vimdoc.sourceforge.net/htmldoc/intro.html#Moolenaar"), but only through the help of many others.  See |[credits]("http://vimdoc.sourceforge.net/htmldoc/intro.html#credits")|.
```


you might also find nano to be a little bit easier to use, i.e. use of cursor arrows

---

### Post by shan88 on 2011-12-30
Thank you for the reply jack.can`t we set the configurations in vi to move cursor using arrow keys?

---

