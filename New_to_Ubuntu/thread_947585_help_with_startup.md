---
title: "help with startup"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by rajcool13 on 2008-10-14
Hey everyone, I'm a complete noob at ubuntu (although i've been using it for a few days now and it BLEW MY MIND when i first saw it --> i've been a windows user for around ten years so i guess that explains the excitement :)) and i'd appreciate your help on this issue.

I have a problem with startup in ubuntu, specifically with the desktop effects. anytime i login, i have to right click on the desktop and enable the "Extra" option for the visual effects to start showing up. After i do that, i then have to go into the compiz settings manager and reselect all the options (desktop cube, widget, etc). This tends to get a bit annoying at times, given that i set up my widget layer under compiz yesterday and now after restart, pressing F9 does nothing (yesterday it showed all my widgets). so essentially this is a 2 part question, consisting of

a) How do you have the visual effects enabled on startup such that i dont have to reselct all the options under the compiz configuration manager?

and 

b) how do i get my widget layer to run on startup as well? (i'm currently running the widget layer alongisde screenlets --> as in under the behaviour tab in widget windows, i have the command set to "name = screenlet.py" without the quotations.

Thanks a lot in advance

---

### Post by SpenceMakesSense on 2008-10-14
if you go to system-administrator theres a slecetion called sessions. If you open that it has a list of startup programs. To get compiz to start on startup add the following command
```
compiz --replace
```
Im not on ubuntu right now(school -.-)so session could actually be under system-preferences.
You will be asked to enter the name and description. Which you can make whatever you want b ut make sure the command is that.

---

### Post by rajcool13 on 2008-10-14
okay amazing, thank you for that spencemakessense, that worked like a charm.

however, although compiz now loads on startup, the screenlets do not. is there a command i need to add under sessions in order to make that launch all the screenlets i added as well?

---

### Post by SpenceMakesSense on 2008-10-14
Sorry Im not sure on the command for those for I have no experience with them. Only thing I can help is that if you can find out the command to start them you can add them to sessions as well. If it boots from an icon maybe right click the icon look at properties and it mmight tell you the command in there. :-k

---

### Post by rajcool13 on 2008-10-14
okay i got it to work by checking the "start on login" box under the screenlets settings.

thanks a lot for your help :)

---

