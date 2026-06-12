---
title: "My window frame is missing!! Need help!"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by mr.lee on 2008-05-08
This morning I turn on my machine, Ubuntu 7.04, then I realize that each window's frame (which there were the close, minimize and maximize buttons) were missing. So, each windows appear only the content. 

The Alt-F4 that use to close the nearest windows can't be used. And the Alt-Tab shorcut to change to another window below too. And I can't move to the another workspace using workspace switcher or even useing Ctrl-Alt-arrow button.

The last night I didn't install anything. What went wrong? Need help! Emergency! Can't work with this condition. :confused:

---

### Post by hotchkikr on 2008-05-08
if your desktop effects are on, turn them off. 
You might want to check your theme as well.

If you have the nvidia driver installed (you would know if you do) you have to enable rgba graphics in your xorg.conf file (if you are new don't bother...)

---

### Post by strick242 on 2008-05-08
if you are using the normal window manager that comes with ubuntu, enter the following in terminal:  metacity --replace
if you were using emerald type this: emerald --replace

---

### Post by mr.lee on 2008-05-08
desktop effect is off (never on), and metacity -replace responed unknown by the Bash. Any idea? I used the NVDIA driver, and it never have the error since installed 4 months ago.

---

### Post by abn91c on 2008-05-08
sound like you have beryl or compiz enabled, use the emerald theme manager and select a theme that has the missing buttons

---

### Post by mr.lee on 2008-05-08
No, I never use beryl and compiz enabled, and my theme was standard Human Ubuntu. And I dont get what u mean by: select theme that has missing buttons??

---

### Post by hotchkikr on 2008-05-08
ok try running this:

```
nvidia-glx --add-rgba-graphics
```

it should work for you.

---

### Post by glennric on 2008-05-08
Type
```
ps aux | grep compiz
```
and 
```
ps aux | grep metacity
```
The one that gives back the most input is the one you are using.  Then type
```
compiz --replace
```
if it is compiz and 
```
metacity --replace
```
if it is metacity.

---

### Post by heartburnkid on 2008-05-08
I've had this happen a few times myself with the new version; usually restarting Compiz fixes the issue.

Hit Alt-F2 to bring up a Run dialog, and put in:

```
compiz --replace
```

You should see your windows disappear for a few seconds, then reappear with the borders.

I'm not sure if there's a more permanent solution...

I should mention that I've been experiencing this in 8.04, and my solution (such as it is) is only tested in 8.04.  Your mileage may vary.

---

### Post by mr.lee on 2008-05-08
nvidia-glz Bash command not found. And sorry terribly sorry... panicly I put the wrong name, not NVidia, but Intell. I used Intel 945GC. Still no idea of this?

New info: I try System>Preference> Windows, and here is the respond:

Cannot start the preferences application for your window manager

Window manager "unknown" has not registered a configuration tool

---

### Post by abn91c on 2008-05-08
> **mr.lee said:**
> No, I never use beryl and compiz enabled, and my theme was standard Human Ubuntu. And I dont get what u mean by: select theme that has missing buttons??

when you enable the desktop effects the default theme makes the minimize/maximize/close buttons disappear.selecting a new emerald theme or window style may fix it

---

### Post by glennric on 2008-05-08
You need to type the commands exactly as we are giving them to you.  Try cutting and pasting.  He said nvidia-glx not nvidia-glz.  Although the funny thing is that there is no command nvidia-glx as he said, and so you will get the same error.  He meant "nvidia-xconfig --add-argb-glx-visuals" I think.  Not sure though, and it probably won't help anyway.  Try what I said on my last post.  Also check the settings in System-Preferences->Appearance under the Visual Effects tab.

---

### Post by glennric on 2008-05-08
When you were told to type "metacity --replace" before you typed "metacity -replace".  Try typing that the way you were told the first time.

---

### Post by mr.lee on 2008-05-08
Ok I guess I used metacity. So I did try from commandline:

ps aux | grep metacity

and

metacity --replace.

The result was hang in the middle. Windows not dissaper for second like heratnburnkid said. But the frame was appear with still no title and max-minim-close buttons. So I try enabled the desktop effect then disabled again, and everithing works fine. 

Thanks for all of your help! How to put this status to be 'resolved'???

Btw, should the developers put a little attention here, coz it's seems to be some bugs to killed.

Btw, thanks all once again. :popcorn:

---

### Post by pastalavista on 2008-05-08
I had this problem too and fixed it (twice now) by booting in "recovery mode" and selecting "repair X-window" or something like that. The only drawback is it reconfigures the system to default values and bypasses any proprietary drivers so you have to re-enable and re-configure everything. I think they released 8.04 a little too soon because they needed to meet their timetable but there are still daily updates and they'll get all the bugs out of it soon enough, I'm sure.

---

### Post by thebigfatgeek on 2008-08-24
> **strick242 said:**
> if you are using the normal window manager that comes with ubuntu, enter the following in terminal:  metacity --replace
if you were using emerald type this: emerald --replace

Worked for me today on Hardy Heron. Why did it happen though? I had a fresh install, nothing new, no Compiz?

---

