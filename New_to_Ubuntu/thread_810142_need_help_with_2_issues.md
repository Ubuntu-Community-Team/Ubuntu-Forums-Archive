---
title: "need help with 2 issues"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by Tubby on 2008-05-28
Hi all, when i go to switch off ubuntu, i press the little red thing in the corner and the box that gives you the options to switch off, log off , switch user options does not appear at all, so i have to switch off my pc from the actual pc itself, 
Also when i open up Firefox, all of my Bookmarks have gone, i have tried to use the " Bookmark this page " option and nothing happens ???

any help would be apppreciated.  
thanks

---

### Post by sam_delta on 2008-05-28
have you been force shutting down your computer? if so, try shutting your computer down with without forcing it with ```
sudo init 0
``` and then turn your computer on again , and see if you can now shut your computer down normally.

i duno if its the same problem, but it once happened to me, and it wouldnt work until i actually shut my computer down the correct way (without force shutting ( keeping the power button pressed))

sam

---

### Post by iaculallad on 2008-05-28
As for the bookmark item: Did you change from one profile to another? While bookmarking, did you use other user accounts while saving your bookmarks?
Try looking at this [Mozilla's profile page]("http://support.mozilla.com/en-US/kb/Profiles") for more information.

---

### Post by Tubby on 2008-05-28
sam_delta, i did as you said but still the same result, i just noticed as soon as i click on the red thing the whole bar up top disappears straight away as well.
thanks

---

### Post by iaculallad on 2008-05-28
For the missing "shutdown" option, try doing this:

Navigate to System->Administration->Login Window

In the "Local" tab of "Login Window Preferences", Select/Check "Show Actions Menu" and close the form.

---

### Post by Tubby on 2008-05-28
> **iaculallad said:**
> As for the bookmark item: Did you change from one profile to another? While bookmarking, did you use other user accounts while saving your bookmarks?
Try looking at this [Mozilla's profile page]("http://support.mozilla.com/en-US/kb/Profiles") for more information.

I did change profiles, but not either has the bookmarks i saved, and both of them will not reset any new bookmarks either, just nothing happens when i press the bookmark this page option.
thanks for help, i will check the mozilla support.

---

### Post by zenwalker on 2008-05-28
Have u any chance disable the Power Mgmt services in the sessions apps? Plus ACPI feature in the BIOS. And pass force-acpi parameter to kernel.

---

### Post by Tubby on 2008-05-28
thanks for all your help, i was getting weird things happening so i finished up reloading unbuntu again and every thing is fine again so again thanks everyone for the help.

---

### Post by adobrakic on 2008-05-28
Yeah, sometimes the shutdown button also doesn't work for me. all i do is press ctrl+alt+backspace to restart it, and then try to shutdown again with the button at the top-right.

---

### Post by Bigtime_Scrub on 2008-05-28
If you have to shutdown I dont recommend forcing the issue by hitting the Power Button on your computer. Ive found that doing that too much messes things up. If the icon on your desktop isnt working you can shut down from terminal.

<shutdown -h now>

and to reboot

<shutdown -r now>

That is shutdown and reboot commands from terminal.

---

