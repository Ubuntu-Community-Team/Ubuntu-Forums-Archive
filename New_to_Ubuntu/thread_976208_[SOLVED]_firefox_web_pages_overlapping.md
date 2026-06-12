---
title: "[SOLVED] firefox web pages overlapping?"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by islandstone on 2008-11-09
Web pages have components overlapping each other in Firefox 3.03 , 
For example the Search and Username boxes at the forum login overlap each other , see below.
[IMG]http://lh5.ggpht.com/_j3_FbfYEV9U/SRas05ETXkI/AAAAAAAAAN4/qeU3EHhbO9Y/s128/firefox.gif[/IMG]

This is much worse on some sites with lots of embedded content.

And what is the maximum size for images in posts?

---

### Post by bscbrit on 2008-11-09
Are you sure that this is the fault of Firefox or could it be that the site in question is not using standard HTML?  Is this a site that previously rendered correctly and now doesn't as a result of some upgrade to your software?

---

### Post by islandstone on 2008-11-09
I can't seem to repeat this problem now , except for the search overlapping the user name box , here on the forums login page?

I have been changing my graphic drivers (Vesa to Intel) , and also changed bios settings from PCI to AGP . Then upgraded the X Server to current.Perhaps that has improved things? It has allowed me to set Extra visual effects , nice.

---

### Post by islandstone on 2008-11-09
This has got so bad that I now have to use Opera to login to the forums.

---

### Post by bscbrit on 2008-11-09
What were you doing before this problem occurred for the first time? If the fault has only begun since you made some changes, it is a fair bet that they are responsible.  I would suggest switching off the extra visual effects completely and running the computer like that for a while.  Also, let me know which version of Ubuntu you are running, how you installed it (upgrade or clean installation) and your hardware please.

I would also make the suggestion that, in future, you change one thing at a time (e.g. Vesa to Intel drivers, or PCI to AGP) because then you will know what cured your problem and, from that, deduce what caused or contributed to your fault.  It will only ever get fixed permanently if we can identify it and then submit a bug report.  It might not affect you (because once your system is fixed you will be happy!) but you could help other users who have yet to experience this problem.

EDIT OK, I got most of your hardware from your sig but a copy of 'lshw' run from a terminal would be useful.  Thanks.

---

### Post by islandstone on 2008-11-12
> **bscbrit said:**
> What were you doing before this problem occurred for the first time? If the fault has only begun since you made some changes, it is a fair bet that they are responsible.  I would suggest switching off the extra visual effects completely and running the computer like that for a while.  Also, let me know which version of Ubuntu you are running, how you installed it (upgrade or clean installation) and your hardware please.

I would also make the suggestion that, in future, you change one thing at a time (e.g. Vesa to Intel drivers, or PCI to AGP) because then you will know what cured your problem and, from that, deduce what caused or contributed to your fault.  It will only ever get fixed permanently if we can identify it and then submit a bug report.  It might not affect you (because once your system is fixed you will be happy!) but you could help other users who have yet to experience this problem.

EDIT OK, I got most of your hardware from your sig but a copy of 'lshw' run from a terminal would be useful.  Thanks.

I can't exactly remember what I did immediately before it occured , but it would be something to do with graphics/display as I have been trying to resolve that for some time. 

Turned off visual effects to none , no difference yet , 

I downloaded 8.04 lts from ubuntu.com as an iso , burned it and booted from the cd to an empty partition , dual boot with Windows Xp.
I can try to  remove/downgrade the Intel drivers but am no expert , if you tell me what to do I'll try it?

I have set the bios back to pci , no change .

attached output from lshw.

As and aside , I am not seeing any strange graphic behaviour in any other app's , Opera is sharp , pictures display as expected in Gimp and Fspot, I don't play the "big" games , but as a test supertuxkart seems to work OK but only once AGP is set though.

I'm happy to try any suggestions if it will help , and yes I should be more step by step , it sure helps when undoing......I'll start some notes.

---

### Post by DrMega on 2008-11-12
> **islandstone said:**
> Web pages have components overlapping each other in Firefox 3.03 , 
For example the Search and Username boxes at the forum login overlap each other , see below.
[IMG]http://lh5.ggpht.com/_j3_FbfYEV9U/SRas05ETXkI/AAAAAAAAAN4/qeU3EHhbO9Y/s128/firefox.gif[/IMG]

This is much worse on some sites with lots of embedded content.

And what is the maximum size for images in posts?

What is your screen resolution set to?

I have seen the effect you describe on badly written websites that use lots of layers, and are developed with the assumption that all users will have a certain screen res.

---

### Post by detroit/zero on 2008-11-12
I've noticed that sometimes AdBlock and NoScript can cause this to happen on a variety of pages. Are you using either one of those extensions?

---

### Post by islandstone on 2008-11-12
> **DrMega said:**
> What is your screen resolution set to?

I have seen the effect you describe on badly written websites that use lots of layers, and are developed with the assumption that all users will have a certain screen res.

1280x1024 , changing it to 1024x768 makes no improvement.
(Using alt+F2 and gnome-display-properties to adjust it.)

---

### Post by islandstone on 2008-11-12
> **detroit/zero said:**
> I've noticed that sometimes AdBlock and NoScript can cause this to happen on a variety of pages. Are you using either one of those extensions?

Nope , no adblock, no NoScript.

---

### Post by bscbrit on 2008-11-12
You're getting plenty of advice!  In your post 4 you mention that it is getting worse and that you have had to switch to Opera.  Has it improved since you said that, stayed the same or become even worse?

You also mentioned that you were only seeing the problem on this site.  Is that still the case, or are you having the same or similar problems with other sites?  If so, which ones?

---

### Post by islandstone on 2008-11-12
[QUOTE=bscbrit;6161320]You're getting plenty of advice!  In your post 4 you mention that it is getting worse and that you have had to switch to Opera.  Has it improved since you said that, stayed the same or become even worse?

You also mentioned that you were only seeing the problem on this site.  Is that still the case, or are you having the same or similar problems with other sites?  If so, which ones?

Great to get such a response , seems to be worse ....

bios to pci effects off
digitalspy and bbc.co.uk very bad.
bios to pci effects to normal
bbc and digitalspy very bad

bios to agp effects off
digitalspy and bbc.co.uk very bad.
bios to agp effects to normal
bbc and digitalspy very bad

Also the login screen for ubuntu , the username box is positioned bottom right of the screen? should it not be in the middle?

What I don't understand if is this is system settins issue (drivers,display settings,adapter chip etc) why is it only affecting Firefox , doesn't Opera use the same gnome/desktop settings ?

---

### Post by fooman on 2008-11-12
what firefox extensions do you have installed?

is "no squint" one of them?

---

### Post by bscbrit on 2008-11-12
If I were you, I would delete your firefox settings by removing completely the .mozilla directory in your home area.  (The directory is 'hidden' by the preceding '.' so you will have to use (Nautilus) View->Show Hidden Files to have it displayed on the screen).

This will reset your Firefox to an 'as new' setting.  You will lose all saved data (add-ons, extensions, bookmarks etc) so you might want to back up the bookmarks at least.  Do not back it all up because you might just end up copying the same corrupted data back into Firefox again.

The, after you have done that and restarted Firefox again, try looking at the sites that caused you a problem and see if they are improved at all.  If they are no better, then consider removing and re-installing Firefox again.  This problem has not been reported by anyone else which leads me to suspect that there is something unusual about your particular installation.  Perhaps something has been corrupted at some point, but who knows?

The login screen is a different problem and we can fix that once FF is sorted out.

---

### Post by hessiess on 2008-11-12
I am also having a simmaler problem with items in the headder of this website overlapping, Lickly due to my stylish script to change website colours.

---

### Post by bscbrit on 2008-11-12
hessiess - thanks for that.  I wonder what your installation and islandstone's have in common that others do not have?

---

### Post by hessiess on 2008-11-12
list of all the addons I have:

Adblock plus
British english dictionery
Foxmarks
Menu mod
No script
Scrapbook
Stylish
Vimperator

As it dosen't happen on any outher websites (as far as I can tell), Im guessing its a problem with the Cascading stylesheets on this website.

---

### Post by bscbrit on 2008-11-12
It might be poorly designed sites, but the same sites display perfectly well on my FF3 with similar add-ons and extensions. Sites such as the BBC don't usually cause problems although they are very busy pages.  Still, we will hopefully solve it as we go on.

---

### Post by islandstone on 2008-11-12
We have lift off.

Deleted /home/island/.mozilla , restarted firefox.

All sites previously mentioned display perfectly.

And I think I have found the problem , or part of it. I always increase font sizes (bad eyesight) , and anything above 14 in minimum font size repeats the problem. 

My font settings are now install defaults except minimum size set to 14.

I noticed that image zoom extension installed as default? But disabling it made no difference.

Thanks for the help hope this helps Hessies

---

### Post by bscbrit on 2008-11-13
That is good news!

I also have to increase the size of fonts on my pages - and for exactly the same reason.  If you think about it, when the web page was designed then someone probably assumed that the font that they used during the design process was the one that would be wanted by the end user.  It is possible to design to take some variations into account but, if the size of font is outside of that predetermined size range, then it is likely that something on the screen will not fit.

I hope that it does not take you too long to get everything back to the settings that you had previously.  Good luck, and I hope to see you around the forums.

bscbrit

ps - Please use Thread Tools at the top of this page to mark the problem as 'SOLVED'.

---

