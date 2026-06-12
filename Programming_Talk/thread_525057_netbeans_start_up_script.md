---
title: "netbeans start up script"
date: 2007-08-13
forum: Programming Talk
---

### Post by Coder_wannabe on 2007-08-13
I am trying to install netbeans 5.5 in Feisty Fawn.  It intalls fine but when the app finally loads all i see is a black screen and menu bar.  I read that you have to add the following to the start up script for netbeans:

export AWT_TOOLKIT=MToolkit

However, I am not sure how to identify the startup script or where to add this line at in the script.  Any advice is more than welcomed.  Thanx.

---

### Post by AlexThomson_NZ on 2007-08-13
I think you'll find the start up script at:

${installed_location}/bin

It's called 'netbeans' (should be the only file there), just use an editor to put that line near the start (after the # comments)

---

### Post by Coder_wannabe on 2007-08-13
Youre a life saver.  Thanks guy!!!!

---

