---
title: "Problem with frame"
date: 2011-11-07
forum: New to Ubuntu
---

### Post by marenkar on 2011-11-07
Hey guys,

So I have GNOME, Unity and Xubuntu for desktop environments on my laptop. On the Xubuntu side, the frames seem to have a problem. I don't see any of the close,minimize and shrink/expand icons as well as the bar which they are on with any application or folder I open. The top of the current frame I see just includes File, etc. 

Any ideas?

---

### Post by Jose Catre-Vandis on 2011-11-07
In terminal try

```
xfwm4 --replace
```

---

### Post by marenkar on 2011-11-07
So it works temporarily but then I get an error. I close Terminal and then it reverts back into the original problem. 

Sorry, noob here.

Edit: The error given is:

(xfwm4: 5057): xfwm4-WARNING **: Failed to connect to session manager: Failed to connect to the session manager: SESSION_MANAGER environment variable not defined

---

