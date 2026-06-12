---
title: "Unity - can't make sloppy focus work"
date: 2012-08-22
forum: New to Ubuntu
---

### Post by zcacogp on 2012-08-22
Hello, 

I've been using Ubuntu 12.04 since it came out, but used the Gnome3 desktop as I originally didn't get on with Unity. However I have decided to give it another go, and am getting on well with it. 

However I am struggling to get Sloppy Focus to work on my desktop machine. In "Advanced Settings" I have "Windows Focus Mode" set to "Sloppy", and I have opened gconf-editor and gone to /-apps-metacity-general and set "Focus Mode" to "Sloppy" there as well. However it still won't do sloppy focus. 

I know this is possible as I have another machine (a Dell laptop) which 12.04 on it, and with these settings it runs sloppy focus quite well. 

What other settings are there which may prevent sloppy focus from working on my desktop machine? I don't know whether it's relevant but it's an nvidia 6600 graphics card, running nvidia-current drivers and is otherwise fine. 

(Also, what's the difference between gconf-editor and dconf-editor? They seem to cover many of the same settings, but aren't identical.) 

Thanks, in advance, for any help. 


Oli.

---

### Post by mcduck on 2012-08-22
The Advanced Setting (and gconf option) both apply to Metacity and Mutter, Gnome's window managers. However the Unity session uses Compiz as it's window manager, so you need to install CompizConfig Settings MAnager and configure the window focus mode there.

...although the global tool bar option used by default in Unity would probably cause you some troubles with sloppy window focus. 

(and also gconf is outdated now and replaced by dconf/gsettings. So you might want to move to using dconf-editor instead ;))

---

### Post by zcacogp on 2012-08-22
MCDuck, 

Thanks for your answer. I have Compiz Config Manager installed (CCSM), and General Options - Focus and Raise Behaviour - Click to Focus is unticked. I have tried ticking it and unticking it again and it makes no difference - sloppy focus still doesn't happen. What am I doing wrong? 

You're right about sloppy focus not working well with the window controls at the top of the screen, and this is what originally put me off using Unity (I like sloppy focus a lot!) However I am coming back and giving it a try as I am not getting on that well with Gnome3, and (subjectively) things seem to work more smoothly with Unity. Maybe the answer is to try MATE or something like that .... 

Thanks for the advice about gconf-editor - that's very helpful. 


Oli.

---

### Post by zcacogp on 2012-08-22
OK, it now works. I logged out and back in again and sloppy focus is as it should be. Thanks for your help mcduck. 

(Not sure why the logout-login trick made any difference; when I have previously used compiz the changes have taken effect immediately.) 


Oli.

---

### Post by mcduck on 2012-08-22
Yeah, I remember sometimes running into same issue about Compiz not applying the settings immediatelly. Never found a reason for that, but as long as logging out or restarting Compiz works to apply the settings that isn't too much of a problem. Great that you got it working, anyway. :)

---

