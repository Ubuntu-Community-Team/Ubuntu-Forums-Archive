---
title: "No audio OR video-xfmedia player:why,why,why ??"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by faron45 on 2008-12-02
It's me again folks.Sorry.Damnit,though...I have spent HOURS on this problem & still I cannot seem to get this thing to work for me.I downloaded a 19 second video clip [wmv] from the net yesterday morn & it appears to be in the player but,it just will not seem to play properly.

It seems to go through the motions [status bar moves] but I get no audio or video [black screen].The player [xfmedia player] will not even play professionally burnt [grateful dead records,warner bros,etc.Heh,heh.] cd's.Why,why,why ???

           Tanks fer any/all help
                           :guitar:
                               Rock on Jerry !

Just for info purposes-I have gone through synaptic,reinstalled the media player,installed "xubuntu-restricted-extras,[I think]-I have installed medibuntu repository [synaptic says I have medibuntu keyring installed.Is this the repository ?] And,synaptic also says I have the non free codecs installed.

---

### Post by cariboo on 2008-12-02
To make sure you have the the ubuntu-restricted-extras installed check synaptic to see if they are marked installed. 

You probably need the w32codec from the Medibunutu repositories. You can install the w32codec using synaptic, and while you are at it you might as well install libdvdcss2 so that you can play dvds.

I would suggest you use vlc as a media player, as will play everything I've thrown at it.

If things don't work as you expect them to, reinstalling will not help. Unless you use the pruge option to remove a program, all the configuration files are not removed, so you will be back where you started from. 

Remember Linux is not Windows, most of what you know about computers is totally useless. Learn the Linux way, and it will make you a smarter computer user whether it is Windows or Linux.

Jim

---

### Post by Dedoimedo on 2008-12-02
Hello,

Several suggestions:

1. Run the player from the command line, check the errors/warnings it throw up.
2. Try to install codecs for restricted media as suggested; I also have a tutorial for how to play mp3s on Ubuntu, but the installation of codecs mentioned covers many other properietary formats.
3. Try VLC player; it supports many formats.

Dedoimedo

---

### Post by faron45 on 2008-12-02
cariboo907-I do have the Xubuntu restricted installed but,not the Ubuntu restricted.Should I install that too ? As far as libdvdvdcss2 goes-I only have a cd rom so that wouldn't do me any good would it ? Thanks,Jim.

Dedoimedo-Not real experienced with term.How would I go about that ?

---

### Post by Dedoimedo on 2008-12-02
Open a terminal.
Start typing the name of an application. For example, mplayer, gmplayer, xfmedia.
Tap tab twice; this will display all possible options matching the name.
Run the player of your choice against a media file name; for example, mplayer movie.avi.
Watch for any errors that come up.

Dedoimedo

---

### Post by faron45 on 2008-12-02
Anybody still there ??? Ruh,roh.I hope so.Oh,well...Okay when I type in xfmedia & then I hit "tab" [once] I get "xfmedia         xfmedia-remote

---

### Post by Dedoimedo on 2008-12-02
Hello,
It would be xfmedia ...
Run it against a media file as I've written and see what comes up.
Dedoimedo

---

### Post by faron45 on 2008-12-02
I'm sorry my friend-I'm not sure what you mean by "run it against a media file".I have 1 more ? for you too...when you put a cd into the cd tray,shouldn't it auto play ?

---

### Post by Dedoimedo on 2008-12-03
Did you even read what I wrote?
In my original post regarding the command line:

**Run the player of your choice against a media file name; for example, mplayer movie.avi.**

Dedoimedo

---

