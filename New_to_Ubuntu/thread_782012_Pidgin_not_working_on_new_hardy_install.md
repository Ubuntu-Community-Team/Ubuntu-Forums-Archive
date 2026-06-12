---
title: "Pidgin not working on new hardy install"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by dartdog on 2008-05-04
I'm New at all this but set up pidgin after Wubi install of new hardy ISO disk image, on a win XP machine... 

It came up and guided me through set up with buddy list, I got going fine. Took a break exited pidgin. Next start of pidgin  nothing (said starting, then nothing). Rebooted (an old windows trick) and pidgin started but no buddy list, no place to turn it on so all I can do it talk to Freenode and nickserv... 

Exit pidgin;

start again, same behavior IE. No pidgin, but I went into system monitor and killed process... Then Pidgin would start but still no buddy list.

---

### Post by Oldsoldier2003 on 2008-05-04
> **dartdog said:**
> I'm New at all this but set up pidgin after Wubi install of new hardy ISO disk image, on a win XP machine... 

It came up and guided me through set up with buddy list, I got going fine. Took a break exited pidgin. Next start of pidgin  nothing (said starting, then nothing). Rebooted (an old windows trick) and pidgin started but no buddy list, no place to turn it on so all I can do it talk to Freenode and nickserv... 

Exit pidgin;

start again, same behavior IE. No pidgin, but I went into system monitor and killed process... Then Pidgin would start but still no buddy list.

try this
```
sudo killall pidgin
pidgin
```

by trying to start pidgin via terminal you may see some error messages that will help figure out what's going on

---

### Post by dartdog on 2008-05-04
Did as suggested, same behavior, pidgin starts and logs in successfully but no sign of buddy list, no error messages in terminal

---

### Post by Oldsoldier2003 on 2008-05-04
have you tried right clicking the pidgin icon in your notification area?

---

### Post by thumper_e on 2008-05-04
Have you got the setting to show only online members of your buddy list?

Buddies --> Show  click required setting.

=)

---

### Post by dartdog on 2008-05-04
In the window I have there is no such option nothing refers to buddies except "buddy ponce, and there is nothing like that there?

---

### Post by thumper_e on 2008-05-04
How odd,

When you open pidgin what screen does it start on? Are there no more options across the top other than buddy pounce?

See screen shot for startup screen, even if your accounts are disabled it still opens (should!!) to this screen and you can use the menu options across the top to change buddies, accounts, tools and a help.

---

### Post by thumper_e on 2008-05-04
And now for the screenshot oops! lol =)

---

### Post by dartdog on 2008-05-04
> **thumper_e said:**
> And now for the screenshot oops! lol =)

Yup, That is the window that won't show up!!! I only get the dialog window (Conversations...) I once saw the window you snapshotted but not since my original session.

---

### Post by thumper_e on 2008-05-04
Not sure wether this will help, but press ctrl + p to bring up the preferences screen, then click on the interface tab and always show system tray icon. Then on the system tray icon (If it doesn't appear straight away close and re-open pidgin) right click and select show buddy list.

Still no buddies there then follow Buddies --> Show click required setting.

failing that Have you tried to completely remove pidgin and try again?

Hope this helps =)

---

### Post by dartdog on 2008-05-04
> **thumper_e said:**
> Not sure wether this will help, but press ctrl + p to bring up the preferences screen, then click on the interface tab and always show system tray icon. Then on the system tray icon (If it doesn't appear straight away close and re-open pidgin) right click and select show buddy list.

Still no buddies there then follow Buddies --> Show click required setting.

failing that Have you tried to completely remove pidgin and try again?

Hope this helps =)
Tried cntl+p in many places, did get a print contol menu but no preferences screen, the entire buddies screen does not exist for me,,, so the options I think you are referring to are on that part of the interface that is not there. I'm reluctant to de install and reinstall since I am so new to Ubuntu... I had just tried to use what was in the default install...
nothing like you discribed... exited and killed pidgin and restarted stll no buddies

---

### Post by thumper_e on 2008-05-04
To remove it simply go to applications --> add/remove

Type pidgin in the search bar 

uncheck the pidgin box and apply the changes. It should un-install.

To reinstall do the same but check the box next to pidgin.

---

### Post by dartdog on 2008-05-04
Ok I'll get my backbone up! It doesn't work this way so...
Thanks, I'll report back

---

### Post by dartdog on 2008-05-04
Had to use synaptic to remove.. ok, then reinstalled using add/remove.. killed process...(old running pidgin)
 restarted pidgin.. same result, no buddies window...

---

### Post by dartdog on 2008-05-04
No more ideas?

---

### Post by Oldsoldier2003 on 2008-05-04
the screenshot you posted shows you had 1/6 buddies online. did you try expanding the buddy list by clicking the lil triangle next to "Family(1/6)

---

### Post by dartdog on 2008-05-04
Not my screen shot!!! My problem is that window never shows up!

---

### Post by thumper_e on 2008-05-05
Sorry, out of idea's

You should try going to [http://developer.pidgin.im/wiki/FAQ](http://developer.pidgin.im/wiki/FAQ) and seeing if they can offer any help!

---

### Post by SneakyWho_am_i on 2008-05-05
I didn't read every post but did you try just rebooting?

Pidgin has never failed to start for me - except yesterday.
I cleared out ~/.purple but it was to no avail.
Yes, I used killall to kill all pidgin processes.
Also, I said
```
ps -aux|grep pidgin
```

to confirm that nothing had survived it.

Pidgin for some reason, even after I removed all my preferences stuff, just would not even appear in the systray. it was obviously doing SOMETHING because it would rebuild some of the pres if I tried to start it.

So I killed amarok, and basically everything else that ever wants to talk to pidgin through dcop or dbus. No joy.
Also I started it with all extensions disabled through the command line
```
pidgin --help
```
(I think the switch is "-n")

Tried starting it in debugmode
```
pidgin -d
```
The problem may or may not be very clear to a dev. I forgot to save the console output. It was failing some gtk assertion and thus wouldn't start. It wouldn't tell me WHAT assertion had actually failed, only that it had failed one. Something like "failed assertion at gtk::interface" or similar.

I was able to run it as other users, so I copied ~/.purple to another user's homedir, chmodded it as root, and carried on almost as normal

```
~$ sudo cp /home/sneaky/.purple /home/user2/.purple
enter password for this:
~$ sudo chmod /home/user2/.purple 755 #should have used chown?
~$ sudo -u user2 pidgin
```

or something like that. Probably you shold use gksu or something instead of sudo. But the point is it worked as a different user. The problem was resolved when I restarted the computer though.
It is also interesting the finch (which mustn't interact with gtk as it runs in the console) ran with no problem at all.

Hope this helped somebody, or something :)

---

### Post by dartdog on 2008-05-05
Posted bug report then this morning noticed the green dot in my upper menu bar (on right) clicked on it and there it was!!! (I swear I had not seen that dot before:lolflag:)
mark another one up to user error.. (maybe slack documentation:))

---

