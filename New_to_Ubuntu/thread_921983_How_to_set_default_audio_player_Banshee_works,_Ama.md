---
title: "How to set default audio player? Banshee works, Amarok doesn't"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by gregphil on 2008-09-16
Under KDE4.1.1 (kubuntu)

I find that the default player (dragon player) is hopelessly broken.  I installed Amarok and find is can play music and it sounds good, but..... something is wrong with the Amarok program and it tends to cut off the end of files it is playing (I was trying the open office wav files) and if I select "repeat" it plays to the end but restarts partways through so the audio ends up totally scrambled.

So I installed banshee and find it at least seems to play the entire file.  So for now I will use Banshee.

How do I make the KDE system choose Banshee to play audio clips (like at startup and shutdown) so it will stop cutting off the clips half-way?

Thank You

P.S. System settings sound shows use of Intel 82801DB-ICH4 and AD1980

---

### Post by shoot2kill on 2008-09-16
in Gnome it is under

[System] --> [Preferences] --> [Prefered Applications] --> [Multimedia] Tab...

not sure bout KDE if it is same, hope it helps ya...

---

### Post by gregphil on 2008-09-20
I finally got Amarok to work,
 
In Main Menu, system settings, Sound there was  "backend" tab.  That tab offered two options: Xine and Gstreamer.  The default Xine did not work with Amarok, but once I changed it to Gstreamer Amarok started to play files correctly.
 
 
Interestingly enough Banshee stopped working (at all).  I tried switching the "backend" back to Xine, but Banshee stayed broken.
 
So for now my "backend" is set to Gstreamer and I am using the Amarok player.
 
Good Lunk.

---

