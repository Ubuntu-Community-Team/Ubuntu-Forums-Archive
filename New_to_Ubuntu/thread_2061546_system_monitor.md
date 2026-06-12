---
title: "system monitor"
date: 2012-09-22
forum: New to Ubuntu
---

### Post by james013 on 2012-09-22
I want to put the system monitor gui into the startup applications list. I am unable to find the location on the hard drive of the system monitor.  I presume it is because I do not know the application's true name. Any assistance will be appreciated. Thank you.

---

### Post by diesch on 2012-09-22
You can just drag the  system monitor symbol from the Unity dash into the  startup applications list.

---

### Post by james013 on 2012-09-22
> **diesch said:**
> You can just drag the  system monitor symbol from the Unity dash into the  startup applications list.

Tried it. Did not work.

---

### Post by diesch on 2012-09-22
What exactly did not work? Did you get any  error messages?

---

### Post by james013 on 2012-09-22
> **diesch said:**
> What exactly did not work? Did you get any  error messages?

Dragged it there and dropped it and nothing happened.

I am looking for the file name and location of the system monitor gui so I can navagate there and enter it that way.

---

### Post by Scott Harrison on 2012-09-22
It's called gnome-system-monitor

---

### Post by james013 on 2012-09-22
> **Scott Harrison said:**
> It's called gnome-system-monitor

Found it in /usr/bin/

Thank you for the name. There are two  thousand one hundred and five items listed there. I skipped down to the  first letter 'S' and did not see the 'gnome-' entries.

---

### Post by james013 on 2012-09-22
diesch: Danken Ihnen für die Beratung. Ein Parameter ist zur Verfügung um die Drag and Drop Funktion zu aktivieren?

---

### Post by ausrick on 2012-09-24
I'm running into the drag-and-drop scenario as well, as a number of tutorials have said that.  could it be that my system is running Unity 2D?  the one thing I noticed on some of the You-tube videos is that once they drag it past the dash window and onto the startup applications window, the startup applications window gains focus.  Mine does not do that. it just stays with the dash window being in front.

The particular programs I'm trying to get to run I've browsed and added their desktop files and shell script files and they all fail to load when I log in so I was hoping taking the actual icon from the application list in dash that does exactly what I want it to do when clicking on it would do everything right.

as an aside... is there any log I can look at for when an entry in startup applications doesn't do anything. because there are no error messages, no prompts, or anything. just plain un-informative nothing. :(

--------------------------

Update: I tried dragging again, from the dash home window to the startup apps.  waited, startup apps never rose to the top...

...Then I while still holding the icon hovering over it, alt-tabbed to focus on the startup apps window... and crashed /usr/bin/unity-2d-shell  ...So yes, congratulations to me, "I broked ur OS." :(

So get this... I then, after sending an error report and restarting it, tried again... This time dragging the icon from the dash home to a blank space on the desktop.  This gave me an icon for a locked link file (piece of paper, curled down corner, short-cut arrow icon and a closed padlock icon on it) named <application-name>.desktop on my desktop.  I could then click and drag on this file and drop it into the space where startup apps go in the startup apps window and viola! it actually added the app with the apps description like it actually understood what I was trying to do. (no pages-with-gears icons and "unknown" descriptions like when I was trying to type this stuff in manually.)

So now for me to reboot and see if it actually starts these programs now.  then I might try some other experimentation to see what ways I can make drag-n-drop break or work.

---------------
Update 2:

startup apps are now starting up automatically.  Also, if I navigate to /usr/share/applications/ I can drag from that window into the startup applications window all day long without any problems.  It is just when I pull up Dash Home and search for an app and then drag it from there into the startup applications window that everything goes wrong.

---

