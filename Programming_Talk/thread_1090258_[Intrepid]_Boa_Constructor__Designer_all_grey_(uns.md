---
title: "[Intrepid] Boa Constructor : Designer all grey (unsuable)"
date: 2009-03-08
forum: Programming Talk
---

### Post by bluediver on 2009-03-08
Using boa constructor for a wxPython application:
Installing boa from synaptic on intrepid desktop platform

Creating a simple wxframe, open the designer:
> A grey windows is displayed,
Adding a container panel:
> A grey square is created (on already grey background)

Conclusion: All object created is grey and thus 'invisible'

On showmedo.com,the tutorial made on windows expects a black grid on dark grey background for the designer. 

Does anyone had already this issue and any workaround or solution ?
(My target app is opensource, 
(My install: ii boa-constructor  0.6.1-4)
cat /proc/version
Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009)

Regards
Bluediver

---

### Post by cmpython on 2009-03-20
On the Boa video I did, yes, the Frame Designer starts off a darker grey color, and so the 1st panel you place on it is "invisible" relative to it.  

But this in no way means it is unusable for that reason.  When I do this in WinXP, I always do, as in the video, these steps:

1. Place a panel on the frame.
2. Drag the edge of the frame slightly to make the panel expand to fill the whole frame.
3. Associate a boxsizer with that panel.
4. Proceed with making my application from there...

As soon as you complete step 2 here, in WinXP or Ubuntu, you will have the precise same thing:  a frame completely filled with a grey panel.  At that point, there is no difference.  Really, there is almost no need for the dark grey background of the "raw frame", since it is immediately covered up by a wxPanel.  You should NOT be putting all your widgets directly on the frame anyway--put everything on a wxPanel.

Also note:  you can make the color of any panel whatever you want, if that helps you in terms of visually identifying panels.  Even Robin Dunn, the creator of wxPython, mentioned he does this sometimes.  Use the Inspector, and unclick the checkbox to reveal a dropdown for colors under BackgroundColour (under the Props tab) (but see error below)

I have noticed that the gridlines are not showing in Ubuntu, though.  That is annoying.  There are certainly some problems with Ubuntu (or Linux generally?  I don't know), such as the one discussed here regarding the Inspector:

[http://tiny.cc/f7B9h](http://tiny.cc/f7B9h) 

and for me the New option is cut off the File menu (you can use the Palette to start a New anything, though, but it is unfortunate it is not there in the Editor, too). Also, in the Inspector, the ability to edit values seems badly messed up.  Normally one does not have to unclick these checkboxes to access the values.  

I think some work needs to be done on the Ubuntu/Linux version of Boa for it to be just as functional as the Win version.  Let's hope that can happen soon.

---

