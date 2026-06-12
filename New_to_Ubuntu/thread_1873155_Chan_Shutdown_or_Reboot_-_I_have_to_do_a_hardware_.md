---
title: "Chan Shutdown or Reboot - I have to do a hardware (pull the power)"
date: 2011-10-31
forum: New to Ubuntu
---

### Post by crjackson on 2011-10-31
I have seven systems running Oneiric. Some are desktops, some are laptops. Some are Intel systems, others are AMD system. Some have nVidia cards, other have intel and amd.

They all have one common problem. You never know if they will shutdown or reboot. You clcik on the menu item and it prompts, you answer the prompt and it goes away as if the show you the middle finger.  You can play this game for hours, but you will lose 99% of the time.

The only way I've been able to cope with this is to open a terminal and issued ```
sudo shutdown -P now
``` and it works like a dream from there.

So, I made a little 2 line bash script called shutdown.sh on my desktop and I use the to shutdown now. It works fine, but I need to refine it a bit so my wife and kids will use this rather than running back to windows as they do.

I've even assigned the pretty little red power-button icon to it. I need some help to finish if you would pleas...

When the shutdown shell is invoked, it pops up a box  -run in terminal-  -Display-  -run-

selecting the terminal is the only way to run it and it immediately asks for a password before continuing.

Is their a way that I can pass the password inside the script without the terminal waiting for user input?  I want everyone to click the shutdown button and walkaway know that the compute WILL power-off or restart as needed.

Any helpful ideas are appreciated.

---

### Post by CatKiller on 2011-11-01
Use gksudo rather than sudo and you'll get a nice password prompt and you won't need to use a terminal window.

Or you could give more details about what your actual problem with the power applet is.

---

### Post by matt_symes on 2011-11-01
Hi

What happens if you call ConsoleKit using dbus to shutdown and reboot ?

These two should shutdown and reboot.

```
dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Restart

dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Stop
```

Have a play with them and report back on their efficacy.

Kind regards

---

### Post by crjackson on 2011-11-01
> **matt_symes said:**
> Hi

What happens if you call ConsoleKit using dbus to shutdown and reboot ?

These two should shutdown and reboot.

```
dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Restart

dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Stop
```

Have a play with them and report back on their efficacy.

Kind regards

Thanks, I'll do that and see what happens.

---

### Post by crjackson on 2011-11-01
> **CatKiller said:**
> 
Or you could give more details about what your actual problem with the power applet is.

Okay, I'll work with the gksu, I didn't think about that. Well actually I did think about it I just didn't try it. I didn't realize that gksu would invoke a gui box. I knew it should be used with running a gui function, but I didn't know it a gui built in too.

Exactly what more details can I give you? I just know that using the built in shutdown tool is sketchy at best. It's only works about 30% of the time. The rest of the time I have to force it with sudo (or now gksu). Please tell me what details are needed and if it's complicated, how to get them.

---

### Post by matt_symes on 2011-11-01
Hi

> They all have one common problem. You never know if they will shutdown or reboot. You clcik on the menu item and it prompts, you answer the prompt and it goes away as if the show you the middle finger. You can play this game for hours, but you will lose 99% of the time.

This should not be happening and that makes me think it may be an issue with consolekit or maybe pam (or maybe even dbus).

Catkiller's solution is very good. It does not get to the root of the problem though. However these things can take time to track down and Catkiller's solution would be a good quick fix.

Kind regards

---

### Post by anewguy on 2011-11-01
If you want to completely bypass having the password anywhere in the scripts and not asked for, you can do this as well.  It's been well over a year, so I'd have to go back looking for a while, but basically it goes in one of the system config files saying that command "x" (which would be your shell script) is run as su, as an example, which bypasses the password prompt.

I also, however, agree that there is something much more basic to blame here.  Perhaps it's a combination of such things as APIC and ACPI settings, or perhaps there is a process in the background that won't shut down.

Dave ;)

---

### Post by matt_symes on 2011-11-01
Hi

> **anewguy said:**
> If you want to completely bypass having the password anywhere in the scripts and not asked for, you can do this as well.  It's been well over a year, so I'd have to go back looking for a while, but basically it goes in one of the system config files saying that command "x" (which would be your shell script) is run as su, as an example, which bypasses the password prompt.

I also, however, agree that there is something much more basic to blame here.  Perhaps it's a combination of such things as APIC and ACPI settings, or perhaps there is a process in the background that won't shut down.

Dave ;)

This is a solution as well. You can edit your sudoers file to remove the password prompt for shutdown or reboot. 

@OP. Can you be a bit more explicit on what excatly is happening when you try to shutdown ?

Kind regards

---

### Post by crjackson on 2011-11-01
> **matt_symes said:**
> Hi



This is a solution as well. You can edit your sudoers file to remove the password prompt for shutdown or reboot. 

@OP. Can you be a bit more explicit on what excatly is happening when you try to shutdown ?

Kind regards

I want to turn off the computer. I move my mouse pointer over to the top right corner where there is a cog icon. I click on the cog and get a drop down menu. The last item on the menu is shutdown, so I move my mouse pointer over top of the word shutdown and left click on that. Then a pop-up visualises in the center of my screen. Two of the selections presented are Restart and Shut Down. Then I move my mouse pointer to Shut Down and left click on it. The dialogue box goes away. That's it, it doesn't shut down or do anything else. It just acts like I did nothing. If I select Restart, it does the same thing.

There are no user selected applications running. I just sits there... If I open up a terminal session and type sudo shutdown -P now, it shuts down quick, fast and in a hurry.

---

### Post by crjackson on 2011-11-01
> **matt_symes said:**
> Hi

What happens if you call ConsoleKit using dbus to shutdown and reboot ?

These two should shutdown and reboot.

```
dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Restart

dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Stop
```

Have a play with them and report back on their efficacy.

Kind regards

So far (I haven't done a lot of testing yet) both of these work.

gksu works to a point, and hangs at the shutdown splash sometimes. Some times it shuts it down properly.

---

### Post by matt_symes on 2011-11-02
Hi

That may suggest that dbus and console kit and pam are working but the problem is higher up.

If you want to keep testing those commands to make sure they work and post back when you are happy. We can then look at why it's failing when run from the menu.

Kind regards

---

### Post by crjackson on 2011-11-02
> **matt_symes said:**
> Hi

That may suggest that dbus and console kit and pam are working but the problem is higher up.

If you want to keep testing those commands to make sure they work and post back when you are happy. We can then look at why it's failing when run from the menu.

Kind regards

Okay I'll do that. I'll try to shut down the normal way and then when it fails I'll try using the commands you provided.

I don't know if this is a clue or not, but it seems to happen more often after I've installed or removed an application, or after a few hours of up time.

If I have just booted up and and done nothing I usually have no problem.

---

### Post by crjackson on 2011-11-02
I just got a bunch of updates and when it finished it asked to restart.  Needless to say, the restart button on the update manager didn't work, the shutdown button under the cog didn't work either. However this worked
```
dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Restart
```

Also, if you'll look at this thread, you'll see I'm not the only one having this problem.

[http://ubuntuforums.org/showthread.php?t=1865725](http://ubuntuforums.org/showthread.php?t=1865725)

---

### Post by matt_symes on 2011-11-02
Hi

Open a terminal and type

```
/usr/lib/indicator-session/gtk-logout-helper --shutdown
```to display the shutdown dialog. Press the shutdown button as you used to do.

Post the results from the terminal back here.

Can you also post the pertinent part of your ~/.xsession-errors log file.

Kind regards

---

### Post by crjackson on 2011-11-02
> **matt_symes said:**
> Hi

Open a terminal and type

```
/usr/lib/indicator-session/gtk-logout-helper --shutdown
```to display the shutdown dialog. Press the shutdown button as you used to do.

Post the results from the terminal back here.

Can you also post the pertinent part of your ~/.xsession-errors log file.

Kind regards

Okay, it did shut down but it took about 30sec. This was after a reboot, so I would have to say it's not a good indicator of what typically happens. On my next failed attempt to shut down normally, I'll put this in the terminal again and see what happens.

After pasting in the command, the dash dockbar went away, and the top panel when away. The wallpaper and files on my desktop were still showing. It stayed that way for roughly 30 seconds, and then continued with a slow shutdown.

It's nothing like shutting down from the terminal which takes about 3-5 seconds tops.

Error log attached...

---

### Post by matt_symes on 2011-11-02
Hi

I was hoping to see the .xsession-errors file and the terminal output when it fails to shutdown. Can you also put the time it fails to shutdown into your next post to make it easier to look in the log file.

Saying that, after your last post i am not sure xsession-errors log file will help but it may eliminate.

In the meantime you can create an executable script with that dbus message in to shut the computer down without requiring a password if you want. Place it on the desktop or so.

I think we are eliminating things.

Kind regards

---

### Post by crjackson on 2011-11-03
> **matt_symes said:**
> Hi

I was hoping to see the .xsession-errors file and the terminal output when it fails to shutdown. Can you also put the time it fails to shutdown into your next post to make it easier to look in the log file.

Saying that, after your last post i am not sure xsession-errors log file will help but it may eliminate.

In the meantime you can create an executable script with that dbus message in to shut the computer down without requiring a password if you want. Place it on the desktop or so.

I think we are eliminating things.

Kind regards

I'll note the time on next occurrence. I already did put the dbus scripts on the desktop for shutdown / reboot. They work great. I even gave them shutdown and restart icons. If I could just get them to move into the dash bar.

---

### Post by crjackson on 2011-11-06
Okay, so here is my final solution until a proper bug fix comes out.

In dash > applications > system I found independent launchers for shutdown and restart.

I dragged the launchers to the desktop. Then I made a folder ~.custom-launchers and moved the 2 items from my desktop to the hidden folder.

Next, I opened the properties of each one, and changed the commands to the dbus commands that Matt gave me (above).

Once the commands were changed, I was able to drag the new buttons directly into the Dash bar. Done!

No more pop up box for run or anything. If I click it, it's instant!

I'm not marking this thread solved, until the actual bug has a fix...

---

### Post by crjackson on 2011-11-11
> **matt_symes said:**
> Hi

What happens if you call ConsoleKit using dbus to shutdown and reboot ?

These two should shutdown and reboot.

```
dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Restart

dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Stop
```

Have a play with them and report back on their efficacy.

Kind regards

Matt, having ample time to try these commands on all of my systems, I just wanted to tell you that this was a perfectly reliable workaround.

I was wondering if you have a similar command for logging out.

---

### Post by matt_symes on 2011-11-11
Hi

> I was wondering if you have a similar command for logging out.

```
dbus-send --session --type=method_call --print-reply --reply-timeout=5000 --dest=org.gnome.SessionManager /org/gnome/SessionManager org.gnome.SessionManager.Logout uint32:1
```

As a work-around, i'm glad it's working. 

If you ever want to dig deeper and try to find the root cause of the problem then just shout. Not tonight though ;)

Kind regards

---

### Post by crjackson on 2011-11-11
> **matt_symes said:**
> Hi



```
dbus-send --session --type=method_call --print-reply --reply-timeout=5000 --dest=org.gnome.SessionManager /org/gnome/SessionManager org.gnome.SessionManager.Logout uint32:1
```

As a work-around, i'm glad it's working. 

If you ever want to dig deeper and try to find the root cause of the problem then just shout. Not tonight though ;)

Kind regards

Thanks, I do want to find the real cause, let me know when you want to start.

---

### Post by crjackson on 2011-11-14
> **matt_symes said:**
> Hi



```
dbus-send --session --type=method_call --print-reply --reply-timeout=5000 --dest=org.gnome.SessionManager /org/gnome/SessionManager org.gnome.SessionManager.Logout uint32:1
```

As a work-around, i'm glad it's working. 

If you ever want to dig deeper and try to find the root cause of the problem then just shout. Not tonight though ;)

Kind regards

can't force logout with this command. Needed to logout today and ubuntu wouldn't let me, so I tried this command in the terminal and it returned no results. Had to hit the dbus restart launcher to get out of it.

---

### Post by matt_symes on 2011-11-14
Hi

> **crjackson said:**
> can't force logout with this command. Needed to logout today and ubuntu wouldn't let me, so I tried this command in the terminal and it returned no results. Had to hit the dbus restart launcher to get out of it.

That's odd. It works in my 10.04 install. What version of Ubuntu are you using ?

Kind regards

---

### Post by crjackson on 2011-11-14
> **matt_symes said:**
> Hi



That's odd. It works in my 10.04 install. What version of Ubuntu are you using ?

Kind regards

11.10 - The command worked after a reboot, but I didn't need it at that point.

---

### Post by matt_symes on 2011-11-15
Hi

> **crjackson said:**
> 11.10 - The command worked after a reboot, but I didn't need it at that point.

Maybe Ubuntu was just having a funny 5 minutes. Keep playing with the command and see if it works.

Kind regards

---

### Post by crjackson on 2011-11-15
> **matt_symes said:**
> Hi



Maybe Ubuntu was just having a funny 5 minutes. Keep playing with the command and see if it works.

Kind regards

I'll give it some more time.

---

