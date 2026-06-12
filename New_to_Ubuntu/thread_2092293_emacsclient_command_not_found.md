---
title: "emacsclient: command not found"
date: 2012-12-07
forum: New to Ubuntu
---

### Post by vimothy on 2012-12-07
Hi all,

New user of Ubuntu (and emacs for that matter).

Running a 32-bit Ubuntu 12.04 virtual machine on a 64-bit Win7 host.

My problem is as follows:

Open emacs 23 and turn on server mode using the command =M-x server-start=. 

Server mode seems to be running (if I try to turn it on again, emacs tells me that a server is already running), but I'm not a very experienced user of emacs, so am somewhat unsure.

Open a Bash shell and try to call emacsclient to edit some arbitrary script. I.e., type =emacsclient [filename]=.

Terminal returns error message:

=emacsclient: command not found=

EDIT: It occurs to me that, even though I am quite a new user of Ubuntu, this might not be the best place for this question. Mods should of course feel free to move it if they think there is a more appropriate location. Thx

EDIT: Managed to solve the problem by running =sudo apt-get install --reinstall emacs23-bin-common=.

Not sure how to mark the thread as *solved*, though.

---

