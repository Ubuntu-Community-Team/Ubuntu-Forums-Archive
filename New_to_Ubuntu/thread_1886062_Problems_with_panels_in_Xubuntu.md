---
title: "Problems with panels in Xubuntu"
date: 2011-11-24
forum: New to Ubuntu
---

### Post by hamstermoon on 2011-11-24
I can't seem to get a handle on the panels in Xubuntu. My perfect desktop would be a Mac-like set-up using Docky and with a panel at the top. 
 
Apparently you CAN use Docky (and get rid of the dock-like panel at the bottom) but everytime I try to alter the top panel I never seem to be able to get the things to line up to the right. It is always to the left, and I don't seem to be able to move them about like I could in Gnome, which is frustrating. 
 
Is there some sort of preference I have to change?

---

### Post by raja.genupula on 2011-11-24
are you sure that panel was not locked ?

---

### Post by dave0109 on 2011-11-24
Right click on the panel, select Panel -> Panel Properties.  Then ensure that you have Panel1 chosen in the selector at the top, and click on the Items tab.  It may be that the things you are adding to the panel are being added above the "Window Buttons" option, and hence they're showing on the left.  Click on "Window Buttons" and us the UP arrow to move it to the second item in the list, so it's underneath "Applications Menu".  Then, everything else should be on the right hand side.

You can also delete the panel at the bottom, which is acting as a dock and run up Docky instead.

Go to the Settings Manager -> Session and Startup -> Application Autostart and in there, there should be Docky which is unchecked (at least it is on my defauly Xubuntu install).  Click on Docky.  That said, I don't think it's actually installed on my system, but you can obviously pull it down from the Software Centre.

---

### Post by hamstermoon on 2011-12-06
Do I have to have the Window Buttons there? (I prefer to use Docky for that). 

What I notice is that when I remove the buttons that is when everything charges over to the right - I think that might have caused my problem!

---

