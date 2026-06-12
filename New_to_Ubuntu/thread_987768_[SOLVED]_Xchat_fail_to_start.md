---
title: "[SOLVED] Xchat fail to start"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by wariskampar on 2008-11-19
When I run in terminal, I get this message:

aznan@aznan-laptop:~$ xchat-gnome 
The program 'xchat-gnome' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadImplementation (server does not implement operation)'.
  (Details: serial 534 error_code 17 request_code 145 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Running --sync command did not yield anything either. Please help me

---

### Post by wariskampar on 2008-11-19
Problem solve. Uninstall xchat-gnome and delete ~/.xchat2 dir. Re-install real xchat.

---

