---
title: "unable to open gedit"
date: 2014-03-19
forum: New to Ubuntu
---

### Post by Chas_Seadon on 2014-03-19
Hi I'm unable to run gedit.  i have tried from su but get "Cannot open display"
I have tried all the remedies recommended in forums i have searched and reinstalled Ubuntu.
I also get status1: Autolaunch error: X11 initialization failed. \n
any ideas appreciated

---

### Post by steeldriver on 2014-03-19
Hello and welcome to the forums

Can you please post the error you get when trying to open gedit from a terminal as your** regular user** (i.e. the user who you are logged in to the Ubuntu desktop as)?

It's normal for GUI programs to be unable to open the user's display when run as root (i.e. via su or sudo)

---

### Post by codingman on 2014-03-19
Please! I insist! Do NOT run most anything as superuser unless you REALLY know what you're doing. Run it the normal way as steeldriver advised.

---

### Post by Chas_Seadon on 2014-03-21
Well this is emarrassing as i seem to be able to gedit from a terminal window in the GUI.  i did make some changes and it seemed to me that x11 intialisation error was down to the Nvidia driver.

As a newbie i was having problems (and still am) with capturing the X server screen.

this led me to run the terminal in teh GUI and gedit worked.  however i am not sure i am out of the woods yet.
this is teh output from the nv log file 

chas@ubuntu:~$ gedit
chas@ubuntu:~$ grep /var/log/Xorg.0.log -e EE
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    32.585] (II) Loading extension MIT-SCREEN-SAVER
[    36.231] (EE) Failed to load module "nv" (module does not exist, 0)
[    36.352] (EE) Failed to load module "nv" (module does not exist, 0)
[    36.717] (EE) open /dev/fb0: No such file or directory
chas@ubuntu:~$ 

Why would the nv module not exist and would this cause any issues

---

### Post by Chas_Seadon on 2014-03-21
i am still unable to aluch gedit from the x screen when i exit the GUI i get
cannot open display:
run gedit --help fro more options etc..

maybe thats how its supposed to be 

i tried it from su and get the same

No problem with using su on this box as its my test machine to play about with..

---

### Post by steeldriver on 2014-03-21
What version and flavor of Ubuntu are you running (Ubuntu / Lubuntu / Xubuntu)? How exactly are you launching gedit "from the x screen"? what do you mean by "when i exit the GUI"?

---

### Post by mcduck on 2014-03-21
> **Chas_Seadon said:**
> i am still unable to aluch gedit from the x screen when i exit the GUI i get
cannot open display:
run gedit --help fro more options etc..

maybe thats how its supposed to be 

i tried it from su and get the same

No problem with using su on this box as its my test machine to play about with..

Can you clarify this a bit? Are you trying to start Gedit from desktop or from a console (as in "outside of the GUI")?

It's a graphical program and therefore needs at least X running. (And if you have desktop running, but for some reason want to launch Gedit from a TTY, you'll need to specify the display where to launch the application, for example "DISPLAY=:0 gedit").

If you want a simple text editor for command-line use I recommend using *nano*.

---

### Post by codingman on 2014-03-21
Can you please clarify what you are trying to say? Why is it that you don't open gedit from the Dash or menu? Try Alt-F2, and type in gedit, you should be able to launch it from there if you wish to.

---

### Post by Chas_Seadon on 2014-04-21
Ok solved this thanks i reinstalled Ubuntu, for the record i am using 12.04 all is well now thanks.. CS

---

