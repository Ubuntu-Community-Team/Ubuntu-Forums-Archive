---
title: "Programbar (minimize, close..) of all windws missing."
date: 2013-07-18
forum: New to Ubuntu
---

### Post by Jackie9 on 2013-07-18
Hello,

I'm new to ubuntu (and Linux) and I probably pressed some buttons I shouldn't have. Now the top part of all open windows are missing. I cannot close, minimize, move around or change the size of any windows. (And the alt+tab and ctrl+tab hotkeys stopped working too). Since this happend I have also had some problems with the cursor. I can't click anything with text and I have to shut down and turn in back on to get it to work again.:confused:
The last thing I did before the problem occured was trying to get the cube to work (in compiz). It sort of did, but since I got this problem I tried to change it back. Didn't solve it though. 

Hoping someone here can help me, please. :)


- Jackie9

---

### Post by deadflowr on 2013-07-18
Did you re-enable the unity plugin in compizconfig-settings-manager?
The standard practice for enabling cube, is
set desktop workspaces in general options>desktop size horizontal=4+, vertical=1.
disable unity plugin
enable desktop cube> disables desktop wall.
enable cube rotate.
enable 3d windows(sometimes this is broken)
re-enable unity plugin.
When re-enabling, as with disabling, anything in compiz, it causes the system to run berserk for a minute as it tries to re fix itself.

If you've done all this then you can follow this for resetting the defaults
[http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)

It's also important to note that when resetting the desktop wall after running the cube setup, to follow the procedure the same way(ie, disable unity plugin enable wall, enable unity plugin, etc)

---

### Post by Jackie9 on 2013-08-14
Sorry for the late reply. The the forum shut down and my vacatin got in the way.

Sorry to say, but I can't remember what I did any more. :-/
I don't care much about the cube now. I just want my programbar back, and hopefully my hotkeys as well. 
Reseting compiz sounds good to me. I'll try that. 

Thank you :)

---

### Post by Jackie9 on 2013-08-14
Oh, I forgot to mention. I have Ubuntu 12.04. I should probably use the old commands, then? :P

---

### Post by Jackie9 on 2013-08-14
...aaaand I don't have Unity either. 
since I have allready made the n00b mistake of just having a go at it, while not being certain of what the heck I was doing, could someone please help me out so that I don't mess things up even more? :p 

To repeat the problem. I mucked around with compiz. Programbar and hotkeys disappeard. I want them back.
Ubuntu 12.04, gnome,  no Unity. :)

---

### Post by deadflowr on 2013-08-14
> **Jackie9 said:**
> Oh, I forgot to mention. I have Ubuntu 12.04. I should probably use the old commands, then? :P

Yes.
The link I provided earlier states a link to the older versions.

---

### Post by deadflowr on 2013-08-14
> **Jackie9 said:**
> ...aaaand I don't have Unity either. 
since I have allready made the n00b mistake of just having a go at it, while not being certain of what the heck I was doing, could someone please help me out so that I don't mess things up even more? :p 

To repeat the problem. I mucked around with compiz. Programbar and hotkeys disappeard. I want them back.
Ubuntu 12.04, gnome,  no Unity. :)

Somehow, I'm not understanding this.
But anyway try this
Open up compiz-config-settings-manager
If need be you can do this through a terminal
(ctrl + alt + T)
```
ccsm
```
will launch the program.
Then in the left side panel click on preferences
Then find reset to defaults.
Then after the craziness subsides(which most likely will happen) Get back to the main ccsm window and find unity plugin.
(or whatever it is called)
and click on it and mark the check box to enable it.
Then wait for the craziness to run its course and hopeful the desktop will return to its original state.

It is important to note that when making changes, DO NOT do anything and just wait it out. 
The screen can go wacky, and might seem like it broke, but it's simply readjusting the settings.
This may take anywhere from several seconds to a minute or two.

---

### Post by Jackie9 on 2013-08-14
Ok, not much happend. Can't say it went crazy at all, but checking the box for Unity plugin and a pop-up appaear. Since the programbar is still missing (including half of every pop-up windows), I can't see what it says, only the buttons on the bottom part of it (switch on OpenGL and do not turn on Unity plugin). Just to make sure, I'm not going to make it worse by turning on OpenGL, right?

---

### Post by Jackie9 on 2013-08-14
The programbar is still missing, though..

---

### Post by deadflowr on 2013-08-14
I should have mention that if you get pop ups asking you to either enable something or not, to choose the options which are highlighted.
Usually you'll notice one of the choices highlighted with orange or some color.
Choose those.

---

### Post by Jackie9 on 2013-08-14
Ok, "do not turn on ubuntu plugin" is the one highlighted. :-/

I should mention, probably not necessary (just to be sure), that it's not the unity bar with icons on the side of the screen I'm missing, but the oportunity to minimize, hide close and move the minimized window around that's the problem.

---

### Post by Jackie9 on 2013-08-14
Removed double post

---

### Post by deadflowr on 2013-08-14
Is Windows Decorations enabled?

Edit: If you open up the appearance setting in system settings(you can also get there by right click and change desktop background)
Under the wallpaper listing should be a dropdown bar. By default it should say ambiance, I think.
Try clicking on that and seeing if selecting another theme helps.

---

### Post by Jackie9 on 2013-08-14
I've allready tried that but it didn't work. :-/

---

### Post by Jackie9 on 2013-08-14
Hm, tried again. It worked for firefox, but in all the other programs it's still missing.. :-/

---

### Post by Jackie9 on 2013-08-14
Changing the apperance settings didn't work either. :confused:

Thank you for trying to help me by the way. Having the programbar back in firefox is a big improvement at least.



I just discovered that if I maximize all programwindows the program bar appears, but when they re minimized it disappear again, and I still can't move the windows around.
Also, now I hve the problem that I can't access the other desktops.

---

### Post by deadflowr on 2013-08-14
So to recap.
You have a panel across the top of the screen.
You have the launcher going down the left side.
You have min,max,close if you maximize the window.
But normal window mode has no min,max,close, and cannot be dragged/moved.

Is that it?

---

### Post by Jackie9 on 2013-08-14
No launcher ging down the left side. 

I would like to share a screen shot. That would probably make it alot easier, but I can't see how I can do that here.

---

### Post by deadflowr on 2013-08-14
Since all our methods, which normally work, have gone for naught, maybe a reinstall of the ubuntu-desktop will help.

Look over this link
[http://gourgi.wordpress.com/2009/09/27/re-install-ubuntu-desktop-metapackage-and-reinstall-its-dependencies/](http://gourgi.wordpress.com/2009/09/27/re-install-ubuntu-desktop-metapackage-and-reinstall-its-dependencies/)

hopefully, maybe, resetting it will bring it back to the default setting.

I've also seen this method as well

[http://askubuntu.com/questions/95458/how-do-i-reinstall-unity](http://askubuntu.com/questions/95458/how-do-i-reinstall-unity)

Though I do not know which method is better.

As for taking a screenie, just press the prntscrn button or your ketboard(might say print screen) and then click save.
The pic will automatically be saved in the Pictures folder in the Home folder.
Then click on the paperclip(attachments) icon in the forums replybox toolbar and upload your pic from the Pictures folder.

---

### Post by Jackie9 on 2013-08-14
Ok, thank you. 
I don't know if I'll try tonight it's late here. 
Was looking for the paperclip, but found it. :P 
Thank you for all your help. Linux doesn't seem s scary to a n00b when help can be found. :) Hopefully I get the hang of things sooner or later.

This is my program window when normal. 

[ATTACH=CONFIG]245369[/ATTACH]

---

### Post by Jackie9 on 2013-08-15
Reinstalling ubuntu desktop did not work, or it only worked partially. In LibreOffice I can nw see the program bar again, but firefox is still a problem. 
I tried to reinnstall firefox as well, but it didn't help. 

Also I have gnome, and not unity so I didn't try your second link.

---

### Post by deadflowr on 2013-08-15
Coming back I noticed gnome classic.
Not sure whether or not it'll help, but here
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

---

### Post by Jackie9 on 2013-08-15
Thank you. :) 
I'll keep looking and post if I find a solution. :)

---

