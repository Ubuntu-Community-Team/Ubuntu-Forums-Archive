---
title: "Default Screenshot App Bug?"
date: 2012-08-11
forum: New to Ubuntu
---

### Post by d4m1r on 2012-08-11
Hey guys, I don't remember the name of the default screenshot package but I think there is a bug with it and I am wondering if anyone else is seeing the same thing or can confirm it....Basically, whenever you have any dropdown loaded from the top menu bar (where the clock, speakers, network icon, etc are) and you try to take a screenshot, it just does nothing.....

I am having an issue with a top menu bar icon and I am trying to take a screenshot of it to better describe the issue so this is very annoying. Anyone else seeing this or can confirm it? :confused:

---

### Post by vasa1 on 2012-08-11
> **d4m1r said:**
> Hey guys, I don't remember the name of the default screenshot package but I think there is a bug with it and I am wondering if anyone else is seeing the same thing or can confirm it....Basically, whenever you have any dropdown loaded from the top menu bar (where the clock, speakers, network icon, etc are) and you try to take a screenshot, it just does nothing.....

I am having an issue with a top menu bar icon and I am trying to take a screenshot of it to better describe the issue so this is very annoying. Anyone else seeing this or can confirm it? :confused:
You may have to use interactive mode.
Run this from a terminal: ```
gnome-screenshot -i
```

And use "delay" as explained here: [http://ubuntuforums.org/showthread.php?t=1866180&highlight=screen](http://ubuntuforums.org/showthread.php?t=1866180&highlight=screen)

---

### Post by d4m1r on 2012-08-11
Thanks for the reply but;

1) I'd like to do this with the stock screenshot app (just by pressing prt scr on my keyboard) and that's how it should work.

2) That method still does not work. The dropdown is only shown when there is focus on it, so it closes the second I hit take screenshot (even when using interactive mode) and is NOT captured. Try it for yourself and see.

---

### Post by vasa1 on 2012-08-11
> **d4m1r said:**
> Thanks for the reply but;

1) I'd like to do this with the stock screenshot app (just by pressing prt scr on my keyboard) and that's how it should work.

2) That method still does not work. The dropdown is only shown when there is focus on it, so it closes the second I hit take screenshot (even when using interactive mode) and is NOT captured. Try it for yourself and see.

That's why you need to use a delay :)

---

### Post by vasa1 on 2012-08-11
> **d4m1r said:**
> Thanks for the reply but;

1) I'd like to do this with the stock screenshot app (just by pressing prt scr on my keyboard) and that's how it should work.
...
All the best with that.

---

### Post by d4m1r on 2012-08-11
The delay doesn't help, it comes to the same result. As soon as I hit "Take Screenshot" the top menu icon dropdown closes because I am switching focus to the gnome-screenshot -interactive window :(

---

### Post by Perfect Storm on 2012-08-11
May be try Shutter instead: [http://shutter-project.org/about/](http://shutter-project.org/about/)

---

### Post by vasa1 on 2012-08-11
> **d4m1r said:**
> The delay doesn't help, it comes to the same result. As soon as I hit "Take Screenshot" the top menu icon dropdown closes because I am switching focus to the gnome-screenshot -interactive window :(
Set the delay to 10 sec (when you get more comfortable you may reduce it). **_THEN_** make your drop down menu appear and just wait....

---

### Post by ads52 on 2012-08-11
It may be overkill but you will find infinitely more options available to you for both taking a screenshot and also processing the resulting image by using the screen capture facility of gimp. Found at:

File --> Create --> Screenshot

Sorry can't help mending the default screenshot maker :(.

---

### Post by d4m1r on 2012-08-11
> **vasa1 said:**
> Set the delay to 10 sec (when you get more comfortable you may reduce it). **_THEN_** make your drop down menu appear and just wait....

Ah, that makes sense now....This might be the only solution as I don't want to use a 3rd party app like shutter. However, still kinda lame that the default screenshot package has such an issue (does nothing when a top menu dropdown is shown) :(

---

### Post by d4m1r on 2012-08-12
Is anyone **able** to take a screenshot with a top menu icon dropdown displayed? Could someone test it quickly on their setup? Maybe it's just an issue on my end...

---

### Post by ads52 on 2012-08-12
I have just tried it and I can confirm what vasa posted: works if you set a delay for the screenshot, not instantly when the dropdown menu is used.

---

### Post by stinkeye on 2012-08-12
Try taking the screenshot in the Unity2d session.
I've found screenshots in compiz of dropdowns or menus a bit hit or miss.
Still need to set a delay though.

---

### Post by deadflowr on 2012-08-13
Screenshot is an application also. If in default Ubuntu install, open dash type screenshot and launch it. It will launch the screenshot program where you can set a delay, like what vasa1 described. I think the inability to capture dropdown menus with the printscreen button has to do with the fact that it is integrated into the menubar system.

---

### Post by vasa1 on 2012-08-13
> **deadflowr said:**
> Screenshot is an application also. If in default Ubuntu install, open dash type screenshot and launch it. It will launch the screenshot program where you can set a delay, like what vasa1 described. I think the inability to capture dropdown menus with the printscreen button has to do with the fact that it is integrated into the menubar system.

I don't know the technicalities but it's possible that things like drop-down menus are sensitive to what the next key press or mouse click is. If it isn't one of the options present in the menu, the menu closes or doesn't allow the key press or mouse click to register. As I said I don't know the technicalities :(

I'm not sure that this is limited to Unity. I see it with Xfce as well.

---

### Post by deadflowr on 2012-08-13
> **vasa1 said:**
> I don't know the technicalities but it's possible that things like drop-down menus are sensitive to what the next key press or mouse click is. If it isn't one of the options present in the menu, the menu closes or doesn't allow the key press or mouse click to register. As I said I don't know the technicalities :(

I'm not sure that this is limited to Unity. I see it with Xfce as well.

Yeah, it's hard to say why it behaves as it does. I'd be reluctant to advise the OP to file a bug report, because I feel it seems like the kind of behavior that would be labelled 'won't fix'. 
And besides, depending on whether the OP can get it to work, the workarounds of launching the screenshot through the terminal or application menu and setting the delay works well enough.
Setting the delay to five seconds seems to be more than enough time to set the page with dropdown menus staged.

---

