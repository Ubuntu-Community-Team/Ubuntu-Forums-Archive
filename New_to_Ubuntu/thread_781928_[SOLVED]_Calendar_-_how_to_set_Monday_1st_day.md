---
title: "[SOLVED] Calendar - how to set Monday 1st day"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by mkarnicki on 2008-05-04
Hello, I used search function but didn't find it on forums. How can I set Monday to be the 1st day of the week? Thanks.

---

### Post by sailor2001 on 2008-05-04
what calender program are you using? Evolution, gmail, sunbird?

---

### Post by sailor2001 on 2008-05-04
most programs go to edit/preferences/start work week

---

### Post by caro on 2008-05-04
If you are using Evolution, go to Edit > Preferences and on the General tab use the drop down menu to select Monday on Work Week Starts: box.

---

### Post by mkarnicki on 2008-05-04
Thanks guys. I'm using this calendar that pops-up in Gnome in the upper-right corner. And therefore I still don't know how to change it.. I've seen screenshots of somebody else desktop that showed Monday the first day of the week. Please help.. I'm not used to see Sunday as the first day.

---

### Post by mkarnicki on 2008-05-07
*bump* Sorry, but I'd really like to set Monday as the first day of month in the pop-up calendar. Anyone guys/gals ? I'm using Gnome (ubuntu) and this concerns the popup calendar in the upper right corner. I installed English version of ubuntu, but I'm not used to have (as Americans do) Sunday as the first day of the week. Please help.

---

### Post by mkarnicki on 2008-05-24
I'm sorry.. /bump again or re-thread? /

Somebody has to know.. How to fix the upper-right pop-up calendar in Hardy (gnome) to display MONDAY as the first day of the week, please..

---

### Post by mister_pink on 2008-05-24
Bit of a wild guess, but try changing your preferences in evolution. That calender is integrated with the evolution one so it might change it. Mine has monday as the first day, but I never set it and I can't see any other way to!

---

### Post by HotShotDJ on 2008-05-24
> **mister_pink said:**
> Mine has monday as the first day, but I never set it and I can't see any other way to!Mine, on the other hand, has Sunday as the first day of the week, with Monday as the first day of my Work Week.  As with you, I did NOT set it this way, but was set like this by default.  I'm beginning to think that this is an internationalization issue, but I'm not sure how to fix it on the OP's system.

To U.S. users trying to help this person, the issue is NOT the Work Week.  Unlike the United States, most other countries use Monday as the first day of the week and NOT Sunday.  So the calendars on their walls begin the week with Monday, and end the week with Sunday.  I believe THIS is what the OP is trying to accomplish.

---

### Post by mkarnicki on 2008-05-26
> **HotShotDJ said:**
> I'm beginning to think that this is an internationalization issue, but I'm not sure how to fix it on the OP's system.

Thanks for responding. Exactly, I logged-in with Polish interface and I did have Monday as the first day on the left side of my pop-up "gnome" calendar. However I prefer to use the English interface. And I struggle to get used to this calendar.. (does anybody know where are evolution raw config files? maybe there I could find this option..)

---

### Post by drs305 on 2008-05-26
Here is how to change the gnome calendar first day of the week to Monday:

Check which locale you are using (mine is en_US, don't worry about the .UTF ending):
```
locale
```
Next, edit the applicable locale file (for me, en_US, use the result of the previous command if not en_US):
```
gksudo gedit /usr/share/i18n/locales/**en_US**
```
Locate the following line and change the value to 2:
```
first_weekday **2** 
```
Save the file and then:

Update the locales:
```
sudo locale-gen
```
Refresh the desktop:
```
killall gnome-panel
```
The first day should now be Monday \\:D/

---

### Post by mister_pink on 2008-05-26
Woah, maybe this should be a feature request or something to do this a bit more easily. I don't think you can really say that people from country X think the week starts on day Y. If you asked people in the UK, half would say Monday, half would say Saturday and anyone from my uni would say Thursday! (don't ask) So it shouldn't really be a localisation issue.

I had a look in gconf editor thinking it would be in there, that would make much more sense. But really you should just be able to right click and select preferences.

---

### Post by drs305 on 2008-05-26
> **mister_pink said:**
> Woah, maybe this should be a feature request or something to do this a bit more easily. 

I agree - it would be nice to just right click and set it in the calendar. If  you use the command line instructions above, you can probably accomplish it in less a minute or two. The problem is finding the commands ...

---

### Post by mkarnicki on 2008-05-31
**@drs305** YES :popcorn: ! Thank you for your helpful post! Finally there was someone who actually knew where to look for that option ^-^ This will make my life easier haha :D Your post has been thanked!

Have a lovely day ^_^

// I prefer using en_US locale, although I'm a Pole, and Monday is the first day in Poland by default ;)

---

### Post by Stefanie on 2008-05-31
> **drs305 said:**
> Here is how to change the gnome calendar first day of the week to Monday:

Check which locale you are using (mine is en_US, don't worry about the .UTF ending):
```
locale
```
Next, edit the applicable locale file (for me, en_US, use the result of the previous command if not en_US):
```
gksudo gedit /usr/share/i18n/locales/**en_US**
```
Locate the follwoing line and change the value to 2:
```
first_weekday **2** 
```
Save the file and then:

Update the locales:
```
sudo locale-gen
```
Refresh the desktop:
```
killall gnome-panel
```
The first day should now be Monday \\:D/

this is great, you should post it in the subforum "tutorials and tips" and it should be made tutorial of the week :-)

---

### Post by berov on 2008-09-10
Well, I hope someone reads this.

For example, I do not want to change the global settings.
How to do this locally for me only.

I have done the following on the commandline:
```

berov@berov-laptop:~$ vim ~/.profile
#added the following line in my .profile file
export  LC_TIME="bg_BG.UTF-8"
#OR if you want the clock to be in english
export  LC_TIME="en_GB.UTF-8"
#save the file and exit
:x

```
Log Out and then Log In again :)

Now Monday is the first day of the week.
It is still a hack but does not change the global settings.

---

### Post by drs305 on 2008-09-10
berov, 

thanks for sharing that. the more options the better.

---

