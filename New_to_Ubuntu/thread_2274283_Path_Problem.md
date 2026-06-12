---
title: "Path Problem"
date: 2015-04-19
forum: New to Ubuntu
---

### Post by bmurray-mapolce on 2015-04-19
I have built some executables and they are in /home/stuff. I cannot run them from my login. I know that the
path statement has to be updated so everyone can use these commands. How do I do this?

[FONT=Menlo]murrayb@Syslog-Server1:/home/stuff$ ls -ltr[/FONT]
[FONT=Menlo]total 24[/FONT]
[FONT=Menlo]-rwxr-xr-x 1 murrayb murrayb 1815 Apr 16 18:31 [COLOR=#34bd26]**minutely**[/COLOR][/FONT]
[FONT=Menlo]-rwxr-xr-x 1 murrayb murrayb   23 Apr 16 18:35 [COLOR=#34bd26]**findlog0**[/COLOR][/FONT]
[FONT=Menlo]-rwxr-xr-x 1 murrayb murrayb   10 Apr 16 18:36 [COLOR=#34bd26]**follow**[/COLOR][/FONT]
[FONT=Menlo]-rwxr-xr-x 1 murrayb murrayb   26 Apr 16 18:36 [COLOR=#34bd26]**livelog**[/COLOR][/FONT]
[FONT=Menlo]-rwxr-xr-x 1 murrayb murrayb  477 Apr 17 14:15 [COLOR=#34bd26]**bziptimestamp**[/COLOR][/FONT]
[FONT=Menlo]-rwxr-xr-x 1 murrayb murrayb  522 Apr 17 14:20 [/FONT][COLOR=#34BD26][FONT=Menlo][B]timestamp

I am trying to use [/B][/FONT][/COLOR][FONT=Menlo][COLOR=#34bd26]**livelog and follow**[/COLOR][/FONT]

---

### Post by The Cog on 2015-04-19
I would be inclined to put them somewhere that is on everybody's path rather than changing everybody's path. /usr/local/bin is intended for local machine-specific installs and will already be in everybody's path.
```
sudo cp /home/stuff/livelog /home/stuff/follow /usr/local/bin
```
The copies will be read-only to everyone except root, which is good for security.

---

### Post by bmurray-mapolce on 2015-04-19
That worked exactly as I wanted. Thank You very much for the advice.

---

