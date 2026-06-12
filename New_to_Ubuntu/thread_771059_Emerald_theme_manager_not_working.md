---
title: "Emerald theme manager not working"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by metalaxesucks on 2008-04-27
I have the latest Ubuntu Distro, 8.04. I installed several themes from
[http://www.beryl-themes.org/index.php?xcontentmode=102](http://www.beryl-themes.org/index.php?xcontentmode=102)
I tried both Emerald themes & Compiz, but its just not working.
Any ideas/tips?

---

### Post by kg87 on 2008-04-27
just a stab in the dark but, in terminal 

type 
```
emerald --replace
```

and see if that works, Or alternatively

```
compiz --replace
```

I'm a stage further, I've got the fx to work, but have to type replace all the time i restart

---

### Post by Hospadar on 2008-04-27
Is compiz working?  If not, you'll need compiz to work first.  If compiz isn't working, most likely you are having 3d driver issues (proprietary/restricted drivers) or you just havn't turned it on (System->Preferences->Appearance->Visual Effect).  If you want to check your drivers for 3d functionality, try opening up a terminal (Alt-F2 -> "gnome-terminal") and type "glxgears") if you get pretty 3-d gears, you gots some 3d, if not, you've got driver issues.

If compiz isn't working because of driver issues, it's probably not a super big deal, but it'll take some work.

If compiz is working, probably all you need to do is actually start up emerald.  Alt-F2 -> "emerald --replace" should start it up for you.  You may need to go to System->Preferences->Sessions and add that command there to make it start up every time you log in.

Is this at all helpful?
Also note: I suggest using Alt-F2 to start up emerald, because then it doesn't die when you close the terminal.  but the terminal might be more useful for testing because you'll be able to see the error messages if it doesn't work.

EDIT:> I'm a stage further, I've got the fx to work, but have to type replace all the time i restartYou may need to go to System->Preferences->Sessions and add that command there to make it start up every time you log in.

is what you need to do. (there may be other ways of doing it, but this works just fine for me)

---

### Post by metalaxesucks on 2008-04-27
Thanks guys, I don't know what I would do without your help.
I pasted the command in Sessions, & it works beautifully.

---

