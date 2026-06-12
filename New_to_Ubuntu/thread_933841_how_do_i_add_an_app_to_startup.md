---
title: "how do i add an app to startup?"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by ubunt2guy on 2008-09-29
I want my gMail applet to startup when i boot ubuntu.  is there a startup folder?

thanks

---

### Post by drs305 on 2008-09-29
System, Preferences, Sessions, StartUp Programs. Add, and insert the command to start the app.

This will start an app after you log in. If you wanted an app to start during the system's initial boot or one that requires root privileges  a command is normally placed in one of the /etc folders. If that is what you need ask for more specifics.

---

### Post by ubunt2guy on 2008-09-29
> **drs305 said:**
> System, Preferences, Sessions, StartUp Programs. Add, and insert the command to start the app.

This will start an app after you log in. If you wanted an app to start during the system's initial boot or one that requires root privileges  a command is normally placed in one of the /etc folders. If that is what you need ask for more specifics.

thanks alot.  I just need to know what the command would be.  the folder looks like this:
 
/home/kevin/.checkgmail


still learning basic commands so any help would be much appreciated

---

### Post by cyberbrain_12 on 2008-09-29
> **drs305 said:**
> System, Preferences, Sessions, StartUp Programs. Add, and insert the command to start the app.

This will start an app after you log in. If you wanted an app to start during the system's initial boot or one that requires root privileges  a command is normally placed in one of the /etc folders. If that is what you need ask for more specifics.

I still interested on the second option !
Can plz specify the file to edit on /etc and how exactly...
Cause i'm still using alias on the .bashrc file and it 's a pretty tricky and sounds to me for beginner ! :P
Thunks !

---

### Post by stoogiebuncho on 2008-09-29
I don't use this applet, but I think the command is just  

```
checkgmail
```

Try it out in the terminal sometime when the applet isn't already running.  If it works, you know what to add to the sessions startup programs.

---

### Post by cyberbrain_12 on 2008-09-29
> **stoogiebuncho said:**
> I don't use this applet, but I think the command is just  

```
checkgmail
```

Try it out in the terminal sometime when the applet isn't already running.  If it works, you know what to add to the sessions startup programs.

No sorry :D i meant that i need to edit the programs which start up with my session not the gmail apllet so that's why i'm asking how can i add other programs, a way to do that is to do it through the session " System > Preferences > Session" but still a beginner way and i try to get more knowledges :wink:

But thinks any way !

---

