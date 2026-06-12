---
title: "[SOLVED] How to access CheckGmail preferences ??"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by WanSheng on 2008-06-02
I'm new to the Linux world and still not very familiar with it ( I installed Ubuntu Hardy last Friday, everything worked out of the box :) ).

I installed checkgmail and when I first launched it it brought me to the Preferences section, but now I don't know how to have access to the Preferences again. I used used to right click on the icon tray, but I unchecked those by error so now when I launch checkgmail I have no graphical interface. (Actually I don't even know if it's launched!)

This is a very newbie question, but how can I access the preferences so that I can check the icons tray back ??

Thank You

Vincent

---

### Post by meltindar on 2008-06-03
Hi WanSheng,

This is indeed strange. I couldn't bring the preferences dialog again without a little hack. You can either reinstall checkgmail app or you can start terminal and type this line:
```
pkill checkgmail; rm ~/.checkgmail/prefs.xml
```

Then start the checkgmail again from 'Applications > Internet > CheckGmail' or with Alt+F2 and just type 'checkgmail'.
First command will turn off your checkgmail instance(s) and the second one will remove the preferences file so the application will think that it has been started for the first time and will bring the Preferences menu again.
HTH

---

### Post by meltindar on 2008-06-03
Oh and if you only want to turn on the tray icon go to 'Applications > Internet' then right-click the CheckGmail icon and click on 'Add this launcher to panel' :)

---

### Post by WanSheng on 2008-06-03
Thanks a lot !

---

