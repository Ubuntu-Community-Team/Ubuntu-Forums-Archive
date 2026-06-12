---
title: "Installing gog.com games using .sh"
date: 2018-05-12
forum: New to Ubuntu
---

### Post by jbh54enwiler on 2018-05-12
I bought several games from gog.com because they said they would work on Linux.  However, the download took the form of a bash script that opened in emacs.  It said that I had to mark the script as executable, so I did that.  Several times.  In both chmod and the gui file browser.  Every time it returned the same error saying it needed to be marked executable.  I also installed Steam and that works, but I'd have to buy my games all over again.  Anything I could do to fix this would be great!

---

### Post by wildmanne39 on 2018-05-12
Please post the readme files in between code tags using the # button above the message window and someone will most likely take a look.

---

### Post by oldos2er on 2018-05-12
Shell scripts are made to be run in a terminal, and if you downloaded them they're likely in your Downloads folder, so you would run something like ```
cd Downloads

chmod +x game.sh

sh ./game.sh
``` where *game* is the script name. You may or may not need to use sudo in front of that last command, if the script wants to write files outside of /home/user.

---

