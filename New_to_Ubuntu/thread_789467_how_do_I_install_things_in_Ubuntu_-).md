---
title: "how do I install things in Ubuntu? :-)"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by mitar on 2008-05-10
ok. You probably see this kind of question every day on forum but... I am very new to Linux (I just installed Ubuntu on my laptop) and I don't know how to install certain programs. First I installed Skype which was really simple (just click on Install packages and that's it), but now I want to install xmms and I found some problems with that. It came like archive so I extracted the folder (with many files) and I just can't run the installation file (because I can't find it). Can anyone help me with this.

By the way, what are good programs for burning files, DVD/Divx players for Linux?

---

### Post by Monicker on 2008-05-10
[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by skymera on 2008-05-10
The above links has all th details.

This website: [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
is great for new users, have a read of that too, should clear a few things up and answer a few questions

---

### Post by mitar on 2008-05-10
ok. I installed it. it went to the location (for example) usr/share/doc...), but how do I run it? There is not aplication to be open so I can see the program

---

### Post by N.N. on 2008-05-10
> **mitar said:**
> ok. I installed it. it went to the location (for example) usr/share/doc...), but how do I run it? There is not aplication to be open so I can see the program
What did you install and how did you do it? If you have installed the last.fm music player from Synaptic, for instance, a launcher for that application will be added in the menu at "Applications" > "Sound and Video".

If the program that you installed has a Graphical User Interface (GUI), a launcher will typically be added for it in the menu, as with the last.fm music player. On the other hand, if the program doesn't have a GUI, you can only use it from the terminal. In that case, simply open a terminal and type in the name of the installed application (for instance [FONT="Courier New"]lastfm[/FONT] or [FONT="Courier New"]pdflatex[/FONT]). See also [http://monkeyblog.org/ubuntu/installing/#where_did_it_go](http://monkeyblog.org/ubuntu/installing/#where_did_it_go).

If you didn't install the application from Synaptic, you have probably compiled it as described in [http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source) in which case the executable could be residing in some directory in your home directory. To launch the application, then, you can either use the terminal to navigate to the directory where the application is residing and then launch it as described in the README file that came with the application, or you can add a desktop/menu launcher for the application yourself (see [http://monkeyblog.org/ubuntu/installing/#launcher](http://monkeyblog.org/ubuntu/installing/#launcher)).

---

### Post by mister_pink on 2008-05-10
In general you are much better off not installing things randomly from the internet if you can avoid it. Installing things from System->Admin-> Synaptic is always a better option as these things have been tested and integrated into ubuntu.

To run xmms once its installed you should be able to press Alt+F2 and type xmms. If its installed correctly that should work. I should add - xmms is now out of date, theres several derivative works which are more up to date, for example xmms2 or audacious. 

As for the other question:
Burning DVDs- Brasero comes with ubuntu, k3b offers some more advanced options so you might like to try that.
Playing any media- vlc media player is brilliant.

---

