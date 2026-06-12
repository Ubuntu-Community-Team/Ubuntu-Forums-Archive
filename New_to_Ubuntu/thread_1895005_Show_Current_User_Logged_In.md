---
title: "Show Current User Logged In"
date: 2011-12-13
forum: New to Ubuntu
---

### Post by prenger745 on 2011-12-13
Just moved my computers from Ubuntu to Lubuntu.  So far the change has been pretty painless.  One thing that is bugging me is I have no way of knowing which user is currently logged into the machine.  Is there anyway to put the current users name into the top panel?  Even if I click the power icon, it doesn't show which user is currently logged in.  My wife, son, and I all share the computer and all 3 of us have different logins.

Thanks,
Dan

---

### Post by jtarin on 2011-12-13
An open terminal should tell you.

---

### Post by Dangertux on 2011-12-13
Typing 

```

sudo who

```

Should show you who is logged into what from where. Hope this helps

---

### Post by kemtnbkr on 2011-12-14
Offhand, I don't know of a way, but then again I've never tried to do this since I'm the only one using this machine.  I believe that is possible to do using Conky if I recall correctly; however, this is hardly a perfect solution- I know you're looking for a better way.  

I'm also running Lubuntu, and Conky was a massive pain to set up with Openbox and such.  If you do decide to do that, I can help you out with the config file- it came down to guesswork at one point.  I just have a 'vanilla' setup still because I had enough messing with it just to get it to display properly :)

---

### Post by SlugSlug on 2011-12-14
a nice simple 
```
w
```
in terminal will do

---

### Post by MartijnNL on 2011-12-14
If the lubuntu panel has launchers like ubuntu, you could create a launcher which runs this command:

```
echo $USER
```

But set it to run in a terminal.

Or if you want a nice graphical message instead, install 'zenity' and create a launcher which runs:

[CODE}zenity --info --title=User --text=$USER[/CODE]

This should **not** be run in a terminal.

I'm not sure the first one will work, the second one probably will. I've tried it on a Xubuntu system with Avant Window Navigator.

But again, it will only work if you can add launchers to run any command to the panel.

---

### Post by amjjawad on 2011-12-14
> **prenger745 said:**
> Just moved my computers from Ubuntu to Lubuntu.  So far the change has been pretty painless.  One thing that is bugging me is I have no way of knowing which user is currently logged into the machine.  Is there anyway to put the current users name into the top panel?  Even if I click the power icon, it doesn't show which user is currently logged in.  My wife, son, and I all share the computer and all 3 of us have different logins.

Thanks,
Dan

Hello there,

Thank you for choosing and using Lubuntu :)

I read the other suggestions and I guess all will work for you but I think you are looking for something else.

Nothing is prefect and NO OS is prefect, period. That is a fact. However, it would be nice to have such feature by default. I may discuss that with my team (Lubuntu) and see if it's possible to do this with 12.04 but NO promises here because:
1- I'm a member but not a developer.
2- We don't have enough resources and our developers has a lot more work to do that just adding such features.

So please, don't set your wishes too high :D

In the mean time, I'd suggest to go through the current suggestions made on this thread and see which one is best suit your needs :)

Thanks!

---

### Post by prenger745 on 2011-12-14
Thank you for all the answers.  They are all great work arounds but not exactly what I am looking for as amjjawad said.  I basically want to be able to look at the screen and know right away which user it is on.  In Ubuntu, I believe the user was in the top right of the top panel.

I was also thinking about this as well and I came up with editing the wallpaper graphic myself. So mine would be the default Lubuntu wallpaper but I would edit it and put my name in the actual graphic.  Its not perfect and wouldn't be practical if lots of users logged onto the machine but there are just 3 of us.

---

### Post by MartijnNL on 2011-12-15
Thinking about your wallpaper solution I came up with something else. As your wallpaper may be covered by windows, it is also possible to set a background for the panel. You could create a background image for that with the names on it.

Have a look at this for example:
[http://pclosmag.com/html/Issues/201010/page07.html](http://pclosmag.com/html/Issues/201010/page07.html)

It seems you can set the background on the Appearance tab of the panel settings. Ideally the image should have the height of your panel. Normally you would make it 1 or 2 px wide (as the image is repeated horizontally), but in your case you might want to make it wider (perhaps as wide as the screen, otherwise your name will be repeated as well).

---

### Post by SteveDee on 2011-12-15
> **prenger745 said:**
> ...They are all great work arounds but not exactly what I am looking for...I basically want to be able to look at the screen and know right away which user it is on....

How about this...

- Right-click on clock/calendar
- Select "Digital Clock" settings
- Change "Clock Format" to something like this: %R Dan
- Repeat for all user accounts

Update: if you want to automate this, so any user name is displayed, you just need to write a simple app to run when user logs on which does the following:-
 - opens /home/{user}/.config/lxpanel/Lubuntu/panels/panel
 - searches for "ClockFmt="
 - changes this line to include time format + truncated output from "who" command

---

### Post by MartijnNL on 2011-12-15
> **SteveDee said:**
> 
 - changes this line to include time format + truncated output from "who" command

Nice idea, but I would just use the output of "echo $USER" then. No need to truncate the output in that case.

---

### Post by amjjawad on 2011-12-15
> **SteveDee said:**
> How about this...

- Right-click on clock/calendar
- Select "Digital Clock" settings
- Change "Clock Format" to something like this: %R Dan
- Repeat for all user accounts

Update: if you want to automate this, so any user name is displayed, you just need to write a simple app to run when user logs on which does the following:-
 - opens /home/{user}/.config/lxpanel/Lubuntu/panels/panel
 - searches for "ClockFmt="
 - changes this line to include time format + truncated output from "who" command

Hello SteveDee,

Amazing and good one :) didn't try it yet (I don't need that - I'm the only one who is using this machine) but I'll do that later for sure.

Could you please write that as a nice simple and informative HOWTO and post it on my Lubuntu One Stop Thread? I'll add it to the Users' Contributions Section :)

Thanks!

P.S.
Until we find another way, this will be the one to go IMHO :)

---

### Post by SteveDee on 2011-12-16
> **amjjawad said:**
> ...could you please write that as a nice simple and informative HOWTO and post it on my Lubuntu One Stop Thread?...


Sorry amjjawad, I can't do that.

Please see my response here: [http://ubuntuforums.org/showthread.php?p=11541798#post11541798](http://ubuntuforums.org/showthread.php?p=11541798#post11541798)

---

### Post by amjjawad on 2011-12-16
> **SteveDee said:**
> Sorry amjjawad, I can't do that.

Please see my response here: [http://ubuntuforums.org/showthread.php?p=11541798#post11541798](http://ubuntuforums.org/showthread.php?p=11541798#post11541798)

No need to be sorry, I totally understand and respect your opinion :)

Once I'll find a better idea, I'll write that simple HOWTO myself and update the HOWTOs section on my thread :)

---

