---
title: "Pause Rhythmbox/Banshee from another application?"
date: 2008-11-03
forum: Programming Talk
---

### Post by MadsRH on 2008-11-03
Hi
This is not related to any project I'm doing - I'm simply looking for some information :-)
The question should probably be posted at the Gnome/KDE related site, but I just wanted to get kind of a "Yes, this can be done if..." or a "No way!" answer. 

_My question is:_ **Is there a way to pause Rhythmbox (or Banshee) from another application?**

Say you were listing to some music and you got an incoming Skype call. Would it be possible to allow Skype (I know Skype is proprietary software and we can't change the code) to pause the music and turn it back on when the call is terminated?






	
Many people have now had enough of hearing about *Windows 7* and I'm sorry for bringing it up again, but I would just like to refer to a video I saw where Larry Osterman talks about new audio capabilities. So if you don't vomit every time you hear the M$ word, this video (57 min) is very interesting and inspirerring. [CLICK HERE...]("http://channel9.msdn.com/posts/Charles/Inside-Windows-7-Larry-Osterman-on-new-audio-capabilities/")

[B]
//MadsRH[/B]
[anotherubuntu.blogspot.com]("anotherubuntu.blogspot.com")

---

### Post by MadsRH on 2008-11-04
:confused: Does no one know anything about this?

---

### Post by cobalaminco on 2008-11-04
hey,
what i do is setup a shortcut keyboard (system>preference>Keyboard Shortcuts) for pausing, so i can pause whenever i want!

---

### Post by stylishpants on 2008-11-04
Most of the popular players these days implement a scriptable interface:

```
banshee --pause
rhythmbox-client --pause
```

---

### Post by MadsRH on 2008-11-04
> **stylishpants said:**
> Most of the popular players these days implement a scriptable interface:

```
banshee --pause
rhythmbox-client --pause
```

Okay, perhaps that could do it. So the messaging application would have to detect if Banshee, Rhythmbox, Amarok or whatever is running and then run the --pause command for that application???

---

### Post by linkmaster03 on 2008-11-04
Yep, you got it. It could detect if the program was open, and if it was, it could send that pause command as stylish noted.

---

### Post by m_duck on 2008-11-04
I think you could send the --no-start option to rhythmbox as well:
```
rhythmbox-client --no-start --pause
```
so it would pause if it is running and be ignored if not.

---

### Post by OutOfReach on 2008-11-04
Another option would be to use **dbus**.
It is a good way to communicate between applications without typing in commands.
Most music players do have accessible dbus interfaces. I know for a fact that Banshee does.

---

