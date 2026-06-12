---
title: "[SOLVED] What is the command equivalent to the 'Quit' applet on GNOME panel?"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by bhadotia on 2008-09-12
I want to bind that command to a keyboard shortcut in fluxbox.
In case it is not clear what applet I'm talking about - it is the default Quit  button applet (on the top right corner) in GNOME which brings up a splash screen containing buttons for shutdown, logout, restart etc. When I tried to google for the answer all the the links I got talked about the force quit applet (whose equivalent command is killall).

I would be very thankful if someone could tell me about the command.

---

### Post by dhtseany on 2008-09-12
Um, I know the command to reboot and shutdown:

```
$: shutdown -now
```
and
```
$: reboot
```

Hope that helped somehow.

Sean

---

### Post by bhadotia on 2008-09-12
shutdown and reboot commands need sudo and gksu shutdown -h now or gksu shutdown -r now are not working for me. But this applet does not need any such privilages  plus gives a cool splash with many more options.

---

### Post by bhadotia on 2008-09-12
Bump!

---

### Post by bhadotia on 2008-09-18
Bump!

---

### Post by philinux on 2008-09-18
Here you go.

[B]gnome-session-save --kill


[/B]

---

### Post by bhadotia on 2008-09-18
> **philinux said:**
> Here you go.

[B]gnome-session-save --kill


[/B]
  Hey thanks man!

Just curious :From where did you get that command - did you know it or  you searched for it. I searched the hell out of google and still did not find it.

P.S.: I'm not on ubuntu at present so I'm reserving my official thanks untill I test the command:).
Also the thread will remain unmarked (as solved) untill then:popcorn:

---

### Post by philinux on 2008-09-18
I was curious and googled. Since the applet has no properties so you cant see the hidden command.

Googled  - ubuntu keyboard shortcut logout button

Got this.

[http://ubuntuforums.org/showthread.php?t=329436](http://ubuntuforums.org/showthread.php?t=329436)

When you run it from the terminal you get the usual shutdown gui.

---

### Post by bhadotia on 2008-09-18
> **philinux said:**
> I was curious and googled. Since the applet has no properties so you cant see the hidden command.

Googled  - ubuntu keyboard shortcut logout button

Got this.

[http://ubuntuforums.org/showthread.php?t=329436](http://ubuntuforums.org/showthread.php?t=329436)

When you run it from the terminal you get the usual shutdown gui.

Well, this is the command and thank you very much for it.

But unfortunately you cannot bind it to a keyboard shortcut in fluxbox as gnome-session manager is not running there.

When I tried the command from the terminal (after using the key binding that did not work), I got the output that "Could not find the sessions manager". Then I realised that gnome-sessions-manager does does work in fluxbox (you can do that if you want- but thats not worth it). 

Guess, I'll have to try something with the xfce-sessions-manager (Yeah, I got GNOME, KDE(4.1), XFCE and fluxbox)- just hope the command is similar :)

I am marking the thread as solved now (and don't forget the star batch for phil:)).

---

### Post by Elfy on 2008-09-18
Hi - instead of binding to a key I added a sub-menu to my fluxbox menu

>    [submenu] (Quit){}
      [exit] (Log out) 
      [exec] (Reboot) {sudo /sbin/shutdown -r now} <>
      [exec] (Shutdown) {sudo /sbin/shutdown -h now} <>

You also need to add to the sudoers

I added these lines to the end of my sudoers file

> kevin ALL = SHUTDOWN
kevin ALL = NOPASSWD: SHUTDOWN
kevin ALL = REBOOT
kevin ALL = NOPASSWD: REBOOT

Mayber try binding one of those commands.

---

### Post by bhadotia on 2008-09-18
Hi, and thanks for the reply.
What is the sudoers file - never heard of it.
At present I do this in my menu:
```

[seperator] 
      [exec] (Reboot) {gnome-terminal -x sudo shutdown -r now} <>
      [exec] (Shutdown) {gnome-terminal -x sudo shutdown -h now} <> 			 		

```
Coz (as I said before) gksu (or gksudo) doesn't work for me.

And I can still use the gui approach to this by adding the 'xfce-sessions-manager &' to my startup file and using the xfce equivalent to the gnome command (though I have not found it yet).

---

### Post by Elfy on 2008-09-18
I'll give you the sudoers community page rather than tell you, if you are not use to using vi then take note of the beginning where it shows how to use gedit or other instead of vi. It's not a file to get wrong ;)

Basically it is about letting 'you' run the commands in the menu.

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by bhadotia on 2008-09-18
Ok... thanks ... I got to know something new today:)

---

### Post by Elfy on 2008-09-18
great ... I got stuck in the sudoers file with vi - which was something I _didn't_ want to happen lol

But got it right in the end - if you do think you might have caused a problem - don't turn off/reboot it.

---

