---
title: "Ultimate Theme Manager"
date: 2007-09-28
forum: Programming Talk
---

### Post by sharkbaitbobby2 on 2007-09-28
What started as mainly a project to improve my Python skills and learn PyGTK has turned into a serious project. Ultimate Theme Manager allows you to manage themes for any application.* It also has repositories, kind of like Ubuntu's, where you can download themes and theme types*.
  So basically the point of this post is to see if others like my program and if there's bugs, any new ideas, etc. Included is my repository, which includes the [Affinity]("http://affinity-search.googlecode.com/") theme type* and two themes at the moment. I plan on creating a theme type* for the desktop background soon.
  Currently there is barely any documentation, however I think there's sufficient examples included and in the repository if you want to make a theme type or repository for it.
  The application is located at [http://ultimate-theme-manager.googlecode.com](http://ultimate-theme-manager.googlecode.com) and more information can be found there (dependencies, etc.). To install, run 
```
mkdir ultimate-theme-manager && cd ultimate-theme-manager && wget http://ultimate-theme-manager.googlecode.com/files/ultimate-theme-manager-latest.tgz && tar -xvvzf ultimate-theme-manager.tgz && sudo python install.py
```
  This is my first serious project, so please be nice with critiques :)

*To be able to change the themes, etc. of different programs, Ultimate Theme Manager requires theme types, which are basically a set of programs/scripts that change the look or parse the archive of a new theme, etc. See the site for more details.

P.S. I'm sorry if this sounds like an advertisement to my own program, it's not intended to be spam, etc.

---

### Post by slavik on 2007-09-29
umm, screenshots?

also consider making a deb :)

---

### Post by sharkbaitbobby2 on 2007-09-29
> umm, screenshots?
Alright, here's some.
[http://ultimate.theme.manager.googlepages.com/utm1r18.png](http://ultimate.theme.manager.googlepages.com/utm1r18.png)
[http://ultimate.theme.manager.googlepages.com/utm2r18.png](http://ultimate.theme.manager.googlepages.com/utm2r18.png)
[http://ultimate.theme.manager.googlepages.com/utm3r18.jpg](http://ultimate.theme.manager.googlepages.com/utm3r18.jpg)
[http://ultimate.theme.manager.googlepages.com/utm4r18.png](http://ultimate.theme.manager.googlepages.com/utm4r18.png)
[http://ultimate.theme.manager.googlepages.com/utm5r18.jpg](http://ultimate.theme.manager.googlepages.com/utm5r18.jpg)
[http://ultimate.theme.manager.googlepages.com/utm6r18.png](http://ultimate.theme.manager.googlepages.com/utm6r18.png)
[http://ultimate.theme.manager.googlepages.com/utm7r18.png](http://ultimate.theme.manager.googlepages.com/utm7r18.png)

> also consider making a deb :) 
I've never made one before, but I'm pretty sure this works:
[http://ultimate-theme-manager.googlecode.com/files/ultimate-theme-manager-0.1.deb](http://ultimate-theme-manager.googlecode.com/files/ultimate-theme-manager-0.1.deb)

---

### Post by mssever on 2007-10-01
I don't understand what you mean by theme type. Do you mean that you can set different apps to use different GTK themes?

---

### Post by sharkbaitbobby2 on 2007-10-01
> tell me how many post you want 2000.30000.40000..
No, three is fine. Thanks though.

> I don't understand what you mean by theme type.
Ugh, I was afraid of this. A theme type is basically a few files that allow my program to manage (change, add, remove, etc.) the themes of a program. For instance, Firefox allows you to manage themes. A theme type for Firefox would allow Ultimate Theme Manager to manage the themes for Firefox. The alternative to this is just hard-coding all the code to do that (such as opening the archive, parsing xml files, etc.) into Ultimate Theme Manager, but separate theme types are used. 
Unfortunately I can't think of an easier way to explain it or a better name, except for "applications", but that would be misleading. :( (Open to any suggestions)

> Do you mean that you can set different apps to use different GTK themes?
Although that could possibly be something useful, I doubt I could do that and that's not my main intention.

---

### Post by mssever on 2007-10-01
So your program manages themes for applications that already support themes independently of the GTK theme, such as Firefox and bmp. But it doesn't manage themes for apps that simply use the standard GTK theme and can't be themed separately.

Am I correct?

---

### Post by sharkbaitbobby2 on 2007-10-01
> Am I correct?
Partially.
It has the capability to manage themes for non-GTK applications (Firefox, Avant Window Navigator, etc.), but also has the capability to manage the current GTK theme. Unfortunately it can only manage [Affinity]("http://affinity-search.googlecode.com/")'s themes at the moment, but can support GTK, Awn, Firefox, etc. (A theme type for these applications would make that happen, though)
I meant it (probably) couldn't change the GTK themes of separate applications, such as Nautilus having Glossy, Gedit having UbuntuStudio, etc.

So, if it changes the GTK theme, it changes it for any application that uses the current GTK theme, just like gnome-theme-manager.

---

### Post by adamorjames on 2007-10-01
Sounds interesting :popcorn:keep up the great work

---

