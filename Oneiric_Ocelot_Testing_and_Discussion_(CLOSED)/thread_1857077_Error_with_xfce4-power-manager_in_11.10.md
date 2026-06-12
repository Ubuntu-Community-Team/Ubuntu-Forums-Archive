---
title: "Error with xfce4-power-manager in 11.10"
date: 2011-10-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by kill4killin on 2011-10-09
This may or may not be an 11.10 specific error but I thought since I'm running 11.10 I should probably start here.

**_Background:_**
I installed Ubuntu 11.10 today to my Asus 1215b netbook. This worked just fine, no issues at all once everything was updated. The problem was that I had intended to install Xubuntu 11.10 but didn't catch it until after I had finished the install this time (don't ask how I didn't notice sooner, I was half asleep I guess). I installed the xubuntu-desktop package figuring this would be fine. It worked just fine but one small issue that's bugging me, hopefully someone can help me out.

**_The Problem:_**
I can't seem to get xfce4-power-manager to start. I tried running it with the --no-daemon argument and found the following error. I'm not quite sure what any of this means, though. I'm hoping the output makes sense to someone here and can point me in the right direction or knows what's going on.
```
tw3@MiniStar:/etc/xdg/autostart$ xfce4-power-manager --no-daemon

(xfce4-power-manager:3170): xfce4-power-manager-WARNING **: could not map keysym 1008ffa8 to keycode

The program 'xfce4-power-manager' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadName (named color or font does not exist)'.
  (Details: serial 330 error_code 15 request_code 150 minor_code 11)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

---

### Post by effenberg0x0 on 2011-10-09
Question: Do you have xfs installed? If so, does removing it changes (or gets rid of) this error message?

Regards,
Effenberg

---

### Post by rburkartjo on 2011-10-10
power manager doesnt work on my end also

---

