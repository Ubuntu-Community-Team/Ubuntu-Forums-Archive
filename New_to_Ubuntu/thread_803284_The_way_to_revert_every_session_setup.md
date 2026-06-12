---
title: "The way to revert every session setup"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by shewenhao on 2008-05-22
Hi, Every body. i am new here.

I want to know the method to revert Ubuntu session setup to original point.

I had some experiences to rebuild the gnome. I lose my title bar before on any windows in ubuntu. Then I just delete gnome gnome2 gconf etc things then log in again. Every thing back to the original point.It was good for me.

Now I have some problem about the session set up and tired about this. I would like to revert every thing in the session to the original point. Is there any way to do this? Thanks lot!

---

### Post by shewenhao on 2008-05-22
Hi, Every body. i am new here.

I want to know the method to revert Ubuntu session setup to original point.

I had some experiences to rebuild the gnome. I lose my title bar before on any windows in ubuntu. Then I just delete gnome gnome2 gconf etc things then log in again. Every thing back to the original point.It was good for me.

Now I have some problem about the session set up and tired about this. I would like to revert every thing in the session to the original point. Is there any way to do this? Thanks lot!

---

### Post by N.N. on 2008-05-22
When you log in, gnome-session will be executed by the login manager. Gnome-session uses the contents of the ~/.gnome2/session to determine which applications to run at start-up.

You can revert this file to its original state by removing references to all unwanted applications from it. In order to do this properly you must familiarise yourself with the syntax of the file. Do so by looking through the default session file for GNOME, i.e., run the following command in a terminal: ```
cat /usr/share/gnome/default.session
```

Alternately, a more simple solution is to delete the session file in ~/.gnome2/. Doing so forces GNOME to revert to the default session. Beware, however, that the default GNOME session file might not be the default Ubuntu session file, so it might lack certain applications that you'd expect to run at start-up (the network manager applet, for instance). You should be able to remedy this fairly easily, though, as you can just add them from "System" > "Preferences" > "Sessions".

---

### Post by shifty_powers on 2008-05-22
heh, btw, most forums don't like you posting duplicate threads on exactly the same problem ;)

---

### Post by shewenhao on 2008-05-22
Hi, sorry for that duplicate posting...It was an accident.

---

### Post by shifty_powers on 2008-05-22
heh thats ok, happens to us all, but just wanted to point it out ;)

did n.n.'s post help you?

---

### Post by shewenhao on 2008-05-22
I guess the second way is what I did before that I click the alt+ctl+F1 then I deleted the ~/.gnome/ folder then I click the alt+ctl+F7 to go back to log in then every thing back.

Just little question about the first way to use "cat /usr/share/gnome/default.session"
What do you mean is : I should find this default.session file and compare this with my own session file under  "~/.gnome2/session ", the I could follow the standard default.session file to help myself to know what I should delete or what I should keep, right?:)

---

### Post by shewenhao on 2008-05-22
> **shifty_powers said:**
> heh thats ok, happens to us all, but just wanted to point it out ;)

did n.n.'s post help you?
hihi, it quite helps me out. I already thanked hime and you. and just asked few more questions. :)

---

### Post by N.N. on 2008-05-22
> **shewenhao said:**
> I guess the second way is what I did before that I click the alt+ctl+F1 then I deleted the ~/.gnome/ folder then I click the alt+ctl+F7 to go back to log in then every thing back.

Just little question about the first way to use "cat /usr/share/gnome/default.session"
What do you mean is : I should find this default.session file and compare this with my own session file under  "~/.gnome2/session ", the I could follow the standard default.session file to help myself to know what I should delete or what I should keep, right?:)

Yes, that's what I meant. I already replied to your PM, but I'll try to explain things more clearly here:

When editing your session file you must be aware of the following: (a) the numbering of entries, referred to as "clients", must remain correct, and (b) the number of clients, as specified in the num_clients variable, must match the number of clients listed in your session file. In other words, "the clients must be numbered from 0 to the value of num_clients - 1."

To clarify, look at the following session file: ```
[Default]
0,id=117f000101000120985156800000055600000
0,RestartStyleHint=2
0,Priority=40
0,Program=gnome-panel
0,CurrentDirectory=/home/wangberg
0,CloneCommand=gnome-panel --sm-config-prefix /gnome-panel-hdCbYO/ 
0,RestartCommand=gnome-panel --sm-config-prefix /gnome-panel-hdCbYO/ --sm-client-id 117f000101000120985156800000055600000 --screen 0 
1,id=117f000101000120991380000000055760012
1,RestartStyleHint=2
1,Priority=20
1,Program=metacity
1,CurrentDirectory=/home/wangberg
1,DiscardCommand=rm -f /home/wangberg/.metacity/sessions/117f000101000120991380000000055760012.ms 
1,CloneCommand=metacity 
1,RestartCommand=metacity --sm-client-id 117f000101000120991380000000055760012 
2,id=117f000101000120985156800000055600001
2,RestartStyleHint=2
2,Priority=40
2,Program=nautilus
2,CurrentDirectory=/home/wangberg
2,CloneCommand=nautilus --sm-config-prefix /nautilus-rTogIC/ 
2,RestartCommand=nautilus --sm-config-prefix /nautilus-rTogIC/ --sm-client-id 117f000101000120985156800000055600001 --screen 0 
3,id=117f000101000120985157100000055600004
3,RestartStyleHint=1
3,Program=update-notifier
3,CurrentDirectory=/home/wangberg
3,CloneCommand=update-notifier --sm-config-prefix /update-notifier-Sb7dRL/ 
3,RestartCommand=update-notifier --sm-config-prefix /update-notifier-Sb7dRL/ --sm-client-id 117f000101000120985157100000055600004 --screen 0 
4,id=117f000101000120985157100000055600005
4,Program=gnome-power-manager
4,CurrentDirectory=/home/wangberg
4,CloneCommand=gnome-power-manager --sm-config-prefix /gnome-power-manager-dvroqI/ 
4,RestartCommand=gnome-power-manager --sm-config-prefix /gnome-power-manager-dvroqI/ --sm-client-id 117f000101000120985157100000055600005 --screen 0 
5,id=117f000101000121085261100000055750006
5,Program=firefox
5,CurrentDirectory=/home/wangberg
5,CloneCommand=firefox 
5,RestartCommand=firefox --sm-client-id 117f000101000121085261100000055750006 --screen 0 
6,id=117f000101000121089491600000055750009
6,RestartStyleHint=0
6,Program=amarokapp
6,RestartCommand=amarokapp -session 117f000101000121089491600000055750009_1210894923_739776 
7,id=117f000101000120986548500000055760006
7,RestartStyleHint=0
7,Program=pidgin
7,CurrentDirectory=/home/wangberg
7,DiscardCommand=/bin/true 
7,CloneCommand=pidgin --display :0.0 
7,RestartCommand=pidgin --session 117f000101000120986548500000055760006 --display :0.0 
8,id=117f000101000121090284800000055650001
8,RestartStyleHint=0
8,Program=evolution-alarm-notify
8,CurrentDirectory=/home/wangberg
8,CloneCommand=evolution-alarm-notify 
8,RestartCommand=evolution-alarm-notify --sm-client-id 117f000101000121090284800000055650001 --screen 0 
9,id=117f000101000121090286400000055650003
9,Program=fast-user-switch-applet
9,CurrentDirectory=/
9,CloneCommand=fast-user-switch-applet 
9,RestartCommand=fast-user-switch-applet --sm-client-id 117f000101000121090286400000055650003 --screen 0 
10,RestartCommand=bluetooth-applet --singleton 
11,RestartCommand=gnome-at-visual -s 
12,RestartCommand=jockey-gtk --check 60 
13,RestartCommand=/usr/lib/evolution/2.22/evolution-alarm-notify 
14,RestartCommand=tracker-applet 
15,RestartCommand=xdg-user-dirs-gtk-update 
16,RestartCommand=trackerd 
17,RestartCommand=pactl load-module module-x11-xsmp 
18,RestartCommand=/usr/lib/gnome-volume-manager/gnome-volume-manager --sm-disable 
19,RestartCommand=/usr/bin/system-config-printer-applet 
20,RestartCommand=nm-applet --sm-disable 
num_clients=21
```

This session file lists 21 clients, which means that it tells gnome-session to start 21 applications upon log in. That's a large number of applications. Using this session file will therefore slow down the start-up process significantly.

To remedy this, one could reduce the number of applications specified in the file. For instance, one could remove entries 5 (firefox), 6 (amarok), 7 (pidgin), 8 (evolution), 9 (fast user switch applet), 10 (bluetooth), 11 (visual help), 12 (check for driver updates), 13 (evolution notification applet), 14 (tracker applet), 16 (tracker daemon), and 19 (printer applet).

Simply removing the lines, however, is not enough. One must also edit the numbers at the beginning of the remaining lines so that correct numbering of clients is preserved. Additionally one then has to edit the value of num_clients to reflect the actual number of specified clients. If one removed 12 clients and the original number of clients was 21, then only 9 clients remain. Therefore, one must set the value of num_clients to 9.

EDIT: I guess you could do all this from "System" > "Preferences" > "Sessions" as well.

---

### Post by klaasvanschelven on 2008-05-22
I'm not sure what you mean exactly with a number of the words you use...

What do you mean "rebuilt"? Using a compiler and as root? Or playing around with the settings from your user profile? There's a bunch of directories in your home directory that are hidden (starting with ".") and govern the look and feel of your user profile. You could start looking there.

---

