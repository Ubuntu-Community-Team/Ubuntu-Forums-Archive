---
title: "Start Menu Problem"
date: 2013-08-14
forum: New to Ubuntu
---

### Post by steve8 on 2013-08-14
[COLOR=#000000]The Start Menu on my panel no longer shows my applications just run and logout is there a way to reset it?[/COLOR]

---

### Post by ibjsb4 on 2013-08-15
Im not for sure since I do not run lubuntu, but looks to me that the menu is part of the package 'lxpanel'.  You can reinstall the panel, this will revert it back to the default panel.

---

### Post by Boab1993 on 2013-08-15
Right click on the panel,

Go to Panel Settings>Add/Remove Panel Items>Add>Menu

The menu should have the picture of a computer screen but test to see if that menu has all your applications.

If not follow, ibjsb4's advice and re-install lxpanel.

If your items do reappear and on this menu and you want the look back go here "/usr/share/lubuntu/images/" and copy the link to the ****-lubuntu-logo.png, right click the panel Panel Settings>Add/Remove Panel Items>Scroll to 'Menu'>Edit>Paste the Path.

You can then delete the old menu, and move the other one into place.

---

### Post by steve8 on 2013-08-16
no neither worked tho i noticed in the applications launcher settings there is no longer any available applications there just gone

---

### Post by Boab1993 on 2013-08-16
Hmm.

Have you changed anything recently on your system?

---

### Post by steve8 on 2013-08-16
no i logged in a few days ago and it was just like that

---

### Post by steve8 on 2013-08-16
could it be a virus

---

### Post by ibjsb4 on 2013-08-16
I wonder if a --purge and reinstall would do any good.  Also in ubuntu there is a menu configuration file in the home folder I would remove before purging.

---

### Post by Boab1993 on 2013-08-16
If it is a virus, its not a very good one.

There'd be no reason to target panels, or applications - given that you havent downloaded anything, therefore a virus would be placed - no user data would be useful if they've already got into your system.

I agree with ibjsb4. This just sounds like lubuntu going a bit AWOL.

A pruge isn't necessary i don't think, it just sounds like your application shortcuts have disappeared, somewhere.

Check /usr/bin for things like 'leafpad' or 'abiword', your applications should still be there.

If not, go with ibjsb4.

I know how to make individual desktop config files, but i imagine that would be a pain to do each one.

Go here: [https://help.ubuntu.com/community/Lubuntu/Documentation](https://help.ubuntu.com/community/Lubuntu/Documentation)

And see if any of their FAQ helps.

I don't know if you can revert to default settings in lubuntu, in relation to this. A re-install would be a quick and easy solution to this really.

---

### Post by eyTkT7Y on 2013-08-18
I'm running Lubuntu 13.04 and this happens to me a lot. I have two systems that have had two different installations of Lubuntu 13.04, and they all did it. For me... just logging out and logging back in typically corrects it. This is apparently such a common problem that the LXDE site has a workaround posted (however, the work around doesn't work). I think they suggested it was a menu cache issue. Their solution is to kill the lxpanel, clear the menu cache, and restart lxpanel. My apologies if I am incorrect in assuming you're having the same issue I am.

---

### Post by steve8 on 2013-08-20
ye none a that worked actually i just re-installed lubuntu now things are back to normal, thanks tho

---

