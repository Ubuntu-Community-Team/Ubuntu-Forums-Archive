---
title: "Mouse will only work for maximized windows?"
date: 2013-07-13
forum: New to Ubuntu
---

### Post by SageMiles on 2013-07-13
Hello All. 

Hope you are doing well today. I have a bit of an issue with my ubuntu 13.04 box. I have it setup as headless and it has been working great no worries. Then I did an upgrade and now my mouse only works when the application launched is fullscreen(maximized). If the application is not maximized then the mouse can only move, re-size the application window. It works as it normally should for the desktop as far as right,left clicks are concerned. I have scoured the internet and haven't been able to find a relevant post about control in applications maximized or not. Any ideas anyone?

Oh yeah, I forgot to mention that I was connecting to the box with vnc4server and vncviewer.

---

### Post by farrinux on 2013-07-13
Hello
Your information is a little confusing.  When you say your 13.04 box is "headless" you do mean that it has no monitor as in the case of a server? So the applications you are running are on a client accessing the server?

---

### Post by SageMiles on 2013-07-13
Sorry about that. By headless I mean that yes, there is not a monitor connected to it. I am connecting to the vnc4server from my windows machine running vncviewer. I connect via putty to start the vnc4server session and then I connect with the vncviewer. I connect with vncviewer and then any application that I open on the server, the application gui comes up and I cannot click in the gui unless I maximize the application gui.

The applications that I am running are on the server. It is just an ubuntu 13.04 desktop that I have unplugged the monitor on so I could use it elsewhere. I hope that was a better explanation. Let me know if you need anymore info. Thanks for your reply.

---

### Post by farrinux on 2013-07-13
On to the second part.  You said you did an upgrade.  Was this to the 13.04 box?   Did this come through the "Update Manager"? or did you do it from terminal with

```
sudo apt-get update
```

or

```
sudo apt-get upgrade
```

---

### Post by SageMiles on 2013-07-13
I used the terminal [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get update [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get upgrade[/FONT][/COLOR]

---

### Post by farrinux on 2013-07-13
Have you tried plugging the monitor back in and see if the mouse problem persists.  That would at least rule out the change affecting VNC in someway.

---

### Post by SageMiles on 2013-07-13
When I plug the monitor directly to the box it is just a blank black screen with a cursor. Kinda confused as to why it would be a blank screen when I thought it would just be a mirror of the session that I have running in vnc4server.

---

### Post by farrinux on 2013-07-13
Try tapping space bar a couple of times to wake the system, if not reboot.

---

### Post by SageMiles on 2013-07-13
Ok, I rebooted and got to the login screen. Logged in and I see a different background and window manager while I am physically logged in. Then I go to my windows machine and kick up putty->connect to server->start vnc4server. Then I connect with vncviewer from my windoze box and see a different wm and background from the physical connection. hmmmmmm? Thoughts?

---

### Post by SageMiles on 2013-07-14
The mouse issue seems to be related to themes as when I changed that I regained control of the mouse options for applications.


ahhh haaaaa! It is specific to the oxygen Window Decoration. DOES NOT LIKE IT. So I have changed the Window Decoration to something else and it works peachy now. Thanks for your time Farrinux. Let me know if you can figure out or know why that Windows Decoration would cause that. :P

---

### Post by farrinux on 2013-07-14
You are welcome.  Make sure you mark this as solved.

---

