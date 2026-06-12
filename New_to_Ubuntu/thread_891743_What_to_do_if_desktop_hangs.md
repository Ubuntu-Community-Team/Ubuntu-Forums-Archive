---
title: "What to do if desktop hangs?"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by zzzonked on 2008-08-16
My desktop is hanging, right now. And I have no idea what to do. The top and bottom panels are not responding to my clicks or cursor hovers for that matter. But Firefox is working fine. So is Pidgin. Weird? I can't log out/shut down/restart, that button is paralyzed together with the top panel. So is forced shut down the only way out? :( Or is there a Task Manager thingy somewhere that can save me?

---

### Post by jrothwell97 on 2008-08-16
You can use GNOME System Monitor, but as that's accessible through the panel it'll take longer to work.

Instead, try this quick and dirty fix. Press Alt+F2, and run

```
killall gnome-panel
```

The panels will disappear. If they don't reappear within the next minute or so, press Alt+F2 again and run

```
gnome-panel
```

If *that* doesn't work, you can try restarting X. Press Control+Alt+Backspace (after saving all your work). The screen will flicker for a bit and you will be returned to the login screen. Try logging in again and seeing if it works this time - if not, then restart X again and use the login prompt to restart the computer.

---

### Post by coolnfunky_raj on 2008-08-16
Hi. I am having the same problem. The top and bottom panels are freezed. For me, the keyboard is not responding either. So I cant type in any shortcut key combination like Ctrl+Alt+Backspace. Any help would be greatly appreaciated. I have to force power off.

I logged in to post a thread about this and I found this thread describing the exact same problem.

---

### Post by jrothwell97 on 2008-08-16
> **coolnfunky_raj said:**
> Hi. I am having the same problem. The top and bottom panels are freezed. For me, the keyboard is not responding either. So I cant type in any shortcut key combination like Ctrl+Alt+Backspace. Any help would be greatly appreaciated. I have to force power off.

I logged in to post a thread about this and I found this thread describing the exact same problem.
If the *keyboard* isn't responding either, it complicates things. You can try just quickly pressing your computer's power button, and then using the mouse to select "Log Out" (or, probably the better option in this case, "Restart", as that means X gets restarted as well).

---

### Post by coolnfunky_raj on 2008-08-16
Thanks jrothwell97. But pressing the power button doesnt show the options as well. I have set the option to "Ask Me" in Power options. It shows up the options box when the computer is working fine, but when the panels freeze, the power button stops responding too. I have to force power off  everytime and it annoys me. It happens quite frequently too, like once every few hours.

---

### Post by quinnten83 on 2008-08-16
> **coolnfunky_raj said:**
> Hi. I am having the same problem. The top and bottom panels are freezed. For me, the keyboard is not responding either. So I cant type in any shortcut key combination like Ctrl+Alt+Backspace. Any help would be greatly appreaciated. I have to force power off.

I logged in to post a thread about this and I found this thread describing the exact same problem.

you can try with <alt>+<backspace>, that usually restarts the X-server. You will have to log in again.

---

### Post by coolnfunky_raj on 2008-08-16
> **quinnten83 said:**
> you can try with <alt>+<backspace>, that usually restarts the X-server. You will have to log in again.

I cant do this as my keyboard stops responding.

---

### Post by zzzonked on 2008-08-16
Alt-F2 doesn't work. But my keyboard is working. So Ctrl-Alt-Backspace worked. But when I logged in, I got a blank screen staring at me for 10 minutes, so I forced shut down anyway :(

---

### Post by Amstell on 2008-08-16
If your keyboard is not working you need to send a sysreq to XLATE mode.

Hit :

Alt + Scr Lk (or whatever your sysreq key is) + r

Now :

Ctrl + Alt + F1

That should get your to a terminal, then just kill or restart whatever is needed.

Check this : 

[http://www.debian-administration.org/articles/457](http://www.debian-administration.org/articles/457)

Cheers

Amstell

---

### Post by coolnfunky_raj on 2008-08-16
> **Amstell said:**
> If your keyboard is not working you need to send a sysreq to XLATE mode.

Hit :

Alt + Scr Lk (or whatever your sysreq key is) + r

Now :

Ctrl + Alt + F1

That should get your to a terminal, then just kill or restart whatever is needed.

Check this : 

[http://www.debian-administration.org/articles/457](http://www.debian-administration.org/articles/457)

Cheers

Amstell

I have not tried this but I doubt it will work as my keyboard freezes. Thanks for the suggestion, I shall try this the next time it freezes. 

I am wondering, instead of finding a way to reboot, is there a way to fix this problem of freezing? This happens quite often for me and I dont want to reboot everytime it happens.

---

### Post by Amstell on 2008-08-16
> **coolnfunky_raj said:**
> I have not tried this but I doubt it will work as my keyboard freezes. Thanks for the suggestion, I shall try this the next time it freezes. 

I am wondering, instead of finding a way to reboot, is there a way to fix this problem of freezing? This happens quite often for me and I dont want to reboot everytime it happens.

A sysreq + r will send the keyboard out to a terminal when you hit Ctrl + Alt + F1, allowing you to restart or kill whatever you need to fix the problem.  

You need to figure out what is freezing up your desktop.  Do you have compiz on?  Does it seem to happen whenever you do something specific?

---

### Post by tahina on 2008-08-16
Just yesterday [I learned]("http://ubuntuforums.org/showthread.php?t=891128") of a magic key sequence that should work when ctrl-alt-F1 or ctrl-alt-backspace fail... 

hold Alt and PrntScrn and press the keys R E I S U B one after the other... That should shut down all kinds of things and then reboot the system.

I haven't tried it,but I'll try it now and see that it isn't a joke... 

Meh...  It wants to take a screenshot... maybe my computer needs to hang for it to work... Googling "reisub" gives a lot of hits associated with rebooting, though...

---

### Post by ingeva on 2008-08-16
> **tahina said:**
> 
I haven't tried it,but I'll try it now and see that it isn't a joke... 


I did. It is! :)

---

### Post by coolnfunky_raj on 2008-08-16
Hi

I rebooted into recovery mode and ran xfix. I also deleted the Cache folder of firefox and since then, I have not had this problem (for about 10 hours now. I used to have the freezing once every few hours). I dont know which fixed the problem (or if it is even fixed), I will report here after a few days.

---

### Post by coolnfunky_raj on 2008-08-16
> **Amstell said:**
> A sysreq + r will send the keyboard out to a terminal when you hit Ctrl + Alt + F1, allowing you to restart or kill whatever you need to fix the problem.  

You need to figure out what is freezing up your desktop.  Do you have compiz on?  Does it seem to happen whenever you do something specific?

I dont have compiz on. The only application I have running every time this happens is Firefox 3. But I cannot blame Firefox for this as I have Firefox open 99.9% of the time.

---

### Post by coolnfunky_raj on 2008-08-22
Ubuntu has not freezed even once these 5 days. So I guess my system is fixed. :)

---

### Post by coolnfunky_raj on 2008-08-31
Hello all

My desktop hanged again. After about 2 weeks. I tried SysRq and Ctrl+Alt+F1 and I was able to reboot without having to force power off. That worked. I am suspecting this is because of Cache of firefox. This is the trend I noticed. 

Initially, the desktop did not hang. But as time passed, desktop began to hang more frequently. Many of the times it happened, I had only firefox open. Then, I cleared my Cache and ran xfix a couple of weeks ago and it was working fine until today. After the hang, I restarted my computer and checked the Cache folder of Firefox. It was 179 MB in size. I have cleared the Cache now and I shall update if my desktop hangs again. 

Any ideas or comments about this?

---

### Post by hansdown on 2008-08-31
For anyone interested, you can get the ubuntu cheat sheet [http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/](http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/)

It has some good info, and the magic escape does work.

I printed a copy that hangs over my desk. Hope this helps somebody.

---

### Post by baruch60610 on 2008-09-04
I've noticed that sometimes when my system is "frozen", it's actually moving very, very slowly.  It may take quite a long time for anything to happen in response to your keystrokes.

I suggest typing Ctrl-Alt-F1, holding that combination for several seconds, and then waiting for a response.  It could take a long time - minutes.  But often if you wait long enough, it will go to a virtual terminal where you can log in and kill off runaway processes.  You may have to wait forever to get things done.  I've had times when just typing in my login name seemed to accomplish nothing - the letters wouldn't even be echoed onto the screen for over a minute.  But if you're getting *any* response, even after a long time, you're not frozen, just very busy.

So get to the virtual terminal and log in.  Use 'top' to see what processes are hogging your CPU cycles (they'll be at the top of the display).  Note the PID and either type 'killall processname' or 'kill PID'.  You may need to sudo to do this, if they're owned by root.

---

