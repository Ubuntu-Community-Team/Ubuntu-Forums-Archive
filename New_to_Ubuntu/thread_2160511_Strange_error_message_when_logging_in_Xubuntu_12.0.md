---
title: "Strange error message when logging in Xubuntu 12.04"
date: 2013-07-07
forum: New to Ubuntu
---

### Post by marinecomm on 2013-07-07
Every time I log in, for some reason, I get a little box that pops up in the middle of my screen that says:

invalid option: -session

It just started yesterday and I'm not sure what's causing it. I'm running Xubuntu 12.04 64-bit.

---

### Post by Toz on 2013-07-07
Can you post back the contents of your .xsession-errors log file like this:
```
pastebinit $HOME/.xsession-errors
```
...and post back the link that is generated?

Perhaps there is more information in that log file that can help identify the source of that message.

---

### Post by marinecomm on 2013-07-07
Per your request:

[http://paste.ubuntu.com/5852674/](http://paste.ubuntu.com/5852674/)

---

### Post by Toz on 2013-07-07
Nothing regarding this is listed in that log file. Can you run the following command in a terminal window and post back the results? It will query your user autostart files and post back the executable file properties. Perhaps we can identify it there:
```
for file in $HOME/.config/autostart/*; do echo "-----$file-----"; cat $file | grep -i exec; done
```

---

### Post by marinecomm on 2013-07-07
-----/home/jason/.config/autostart/Alsavol.desktop-----
Exec=/usr/local/bin/alsavol.py
-----/home/jason/.config/autostart/blueman.desktop-----
-----/home/jason/.config/autostart/bluetooth-applet.desktop-----
-----/home/jason/.config/autostart/Conky.desktop-----
Exec=conky
-----/home/jason/.config/autostart/deja-dup-monitor.desktop-----
-----/home/jason/.config/autostart/docky.desktop-----
Exec=docky
-----/home/jason/.config/autostart/Fusion Icon.desktop-----
cat: /home/jason/.config/autostart/Fusion: No such file or directory
cat: Icon.desktop: No such file or directory
-----/home/jason/.config/autostart/gnome-sound-applet.desktop-----
-----/home/jason/.config/autostart/OpenOffice.org 3.4.1.desktop-----
cat: /home/jason/.config/autostart/OpenOffice.org: No such file or directory
cat: 3.4.1.desktop: No such file or directory
-----/home/jason/.config/autostart/qstart.desktop-----
cat: /home/jason/.config/autostart/qstart.desktop: No such file or directory
-----/home/jason/.config/autostart/ubuntuone-launch.desktop-----
-----/home/jason/.config/autostart/Volbar.py.desktop-----
Exec=/usr/local/bin/volbar.py

---

### Post by Toz on 2013-07-07
Nothing there either. How about in your cached sessions:
```
for file in $HOME/.cache/sessions/*; do echo "-----$file-----"; cat $file | grep WM_COMMAND; done
```

---

### Post by marinecomm on 2013-07-07
-----/home/jason/.cache/sessions/thumbs-jason-p7-1299c:0-----
cat: /home/jason/.cache/sessions/thumbs-jason-p7-1299c:0: Is a directory
-----/home/jason/.cache/sessions/Thunar-20230262a-a780-499e-8a40-5cdc1c97f1e2-----
-----/home/jason/.cache/sessions/Thunar-21baa5275-405b-4731-ae94-effb150ccfa6-----
-----/home/jason/.cache/sessions/Thunar-21e85bc2f-3538-48e8-84cb-1fe44251b90d-----
-----/home/jason/.cache/sessions/Thunar-22793ef23-3105-46cb-b675-41017bd2f0c2-----
-----/home/jason/.cache/sessions/Thunar-234e436a8-3dbc-4d54-84c6-b5b2d06e96cb-----
-----/home/jason/.cache/sessions/Thunar-24585cb23-7423-4c0d-bb06-8da146cca2d4-----
-----/home/jason/.cache/sessions/Thunar-24f771904-377c-43dd-bbdb-a5836189309f-----
-----/home/jason/.cache/sessions/Thunar-25396707d-f375-488e-bc15-3b7cdb17b548-----
-----/home/jason/.cache/sessions/Thunar-265b60278-9265-4ab9-80e2-6bc43b3d7444-----
-----/home/jason/.cache/sessions/Thunar-2792986f7-8d16-4b7a-be16-0798d1f4424c-----
-----/home/jason/.cache/sessions/Thunar-28b8d7fb6-c98b-4bb8-89c2-74f3eb20a2eb-----
-----/home/jason/.cache/sessions/Thunar-2979d2982-36a2-48f0-ae27-d8d97b762fd3-----
-----/home/jason/.cache/sessions/Thunar-29af12bc7-334d-495f-acce-b5ed5be86fa5-----
-----/home/jason/.cache/sessions/Thunar-2c5aca66e-2e73-4f09-ae43-0e28c9e2ce17-----
-----/home/jason/.cache/sessions/Thunar-2d2c58676-5357-4fb1-8f2c-c61286eff16c-----
-----/home/jason/.cache/sessions/Thunar-2d5bc9a7d-ff6f-4583-9a2f-38e335d025d6-----
-----/home/jason/.cache/sessions/Thunar-2d7f59bd5-4d49-41ec-afee-d98fff752251-----
-----/home/jason/.cache/sessions/Thunar-2f592ac07-a0ac-4e97-9b7d-bd988d55e102-----
-----/home/jason/.cache/sessions/Thunar-2fc5ea784-ea8c-42a4-a01d-cb6ab636de84-----
-----/home/jason/.cache/sessions/xfce4-session-jason-p7-1299c:0-----
-----/home/jason/.cache/sessions/xfce4-session-jason-p7-1299c:0.bak-----

---

### Post by Toz on 2013-07-07
Still nothing. Can you post back the contents of "/home/jason/.cache/sessions/xfce4-session-jason-p7-1299c:0"?

---

### Post by marinecomm on 2013-07-07
Had to reboot my computer and this time the error message didn't show up. I guess whatever it was has worked itself out. :shrug: Thank you for all your time and help.

---

### Post by kdrejer on 2013-11-12
I'll just borrow this thread as i have the same issue in Xubuntu 13.10
I've followed the steps in this thread. Can anybody determine the cause here?

[http://paste.ubuntu.com/6407405/](http://paste.ubuntu.com/6407405/)

----$file-----"; cat $file | grep -i exec; done
-----/home/kristoffer/.config/autostart/blueman.desktop-----
-----/home/kristoffer/.config/autostart/chromium-browser.desktop-----
Exec=/usr/bin/chromium-browser --no-startup-window
-----/home/kristoffer/.config/autostart/ClearRssScreenlet.desktop-----
Exec= python -u /usr/share/screenlets/screenlets-pack-basic/ClearRss/ClearRssScreenlet.py
-----/home/kristoffer/.config/autostart/CopyAgent.desktop-----
Exec=/opt/copy/x86/CopyAgent
-----/home/kristoffer/.config/autostart/Copy.desktop-----
Exec=/opt/copy/x86/CopyAgent
-----/home/kristoffer/.config/autostart/docky.desktop-----
Exec=docky
-----/home/kristoffer/.config/autostart/dropbox.desktop-----
Exec=dropbox start -i
-----/home/kristoffer/.config/autostart/gnome-sound-applet.desktop-----
-----/home/kristoffer/.config/autostart/xscreensaver.desktop-----

--$file-----"; cat $file | grep WM_COMMAND; done
-----/home/kristoffer/.cache/sessions/thumbs-kristoffer-U31SG:0-----
cat: /home/kristoffer/.cache/sessions/thumbs-kristoffer-U31SG:0: Is a directory
-----/home/kristoffer/.cache/sessions/xfce4-session-kristoffer-U31SG:0-----
-----/home/kristoffer/.cache/sessions/xfwm4-25b47800d-9c0e-4b1b-84ac-237caf38c71e.state-----
  [WM_COMMAND] (1) "chromium-browser"
-----/home/kristoffer/.cache/sessions/xfwm4-2dd9ee3b5-2dc2-43fd-a06c-bfde1b2bf8d8.state-----
  [WM_COMMAND] (1) "chromium-browser"

---

### Post by Toz on 2013-11-12
This one is really odd since it looks like an application is auto-starting that is trying to be started with an incorrect parameter. And yet, as you can see, none of your autostart applications are passing a "-session" option. 

Can you try clearing out your sessions cache anyways to see if it helps? To do so, go to **Settings Manager -> Session and Startup -> Session (tab)** and click on the "Clear saved sessions" button? Then logout and back in again to see if you still get the message. 

If you still get the message popping up, I'd be interested in seeing a screenshot of it.

---

### Post by kdrejer on 2013-11-13
The message is gone now :)

---

### Post by Mephisto Pheles on 2014-01-17
I just ran into the same problem, I installed Spotify for Linux yesterday, that's obviously where it comes from. 
I found a file /home/username/cache/sessions/xfce4-session-mephisto-xxxxxx
There I noticed 
 > Client6_RestartCommand=spotify,-session,2d5fe8cb0-400a-4bbe-9ab6-575d5ac640ab_1389910178_907424
Client6_Program=spotify
Client6_UserId=mephisto
Client6_RestartStyleHint=0
Count=7

 Is it safe to edit that file?

Nothing else is using the -session option.

System is stable and everything including spotify is running fine ... despite the error.

---

### Post by Bucky Ball on 2014-01-17
Would people stop 'borrowing' this thread and post new ones??? You stand a better chance of getting help as this one is marked 'Solved'. You may scream but no one will hear you. ;)

---

