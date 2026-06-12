---
title: "Need bash info, re making using files"
date: 2008-05-05
forum: Programming Talk
---

### Post by Omnios on 2008-05-05
Hi Im playing around with modding scripts and am wondering what are the best ways to make and use config scripts. I am planning of adding to a wine launch script and want to have it so the user can input game info such as game name for launcher directory info where the file is and the exe name for wine to launch the game.

 Also is it possible to add options to a sh.sh as in say ./game.sh -new?

 I did a lot of reading over the last few days but really did not find what I was looking for.

 Basicly the mod takes a script that is currently for one game and I am trying to mod it so multiple games may be configured in the shell and run with game menu names.

 And yest this might not be needed but it gives me a excuse to play with bash scripting.

---

### Post by stroyan on 2008-05-05
It is possible to add options to a shell script.
Arguments to a shell script are accessible as "$@" .
The getopt command is made to help with parsing shell script options.
See "man getopt" and the example shell scripts in /usr/share/doc/util-linux/examples/ .

---

