---
title: "Help needed with Cairo Dock"
date: 2015-10-24
forum: New to Ubuntu
---

### Post by nwpll on 2015-10-24
Hi

Since i did a fresh install my Cairo dock now longer opens on start up. I did a search and went through all 10 pages and found nothing to help me. 
Could someone explain how i get to keep my Cairo dock on screen permanent.

Thanks

---

### Post by deadflowr on 2015-10-24
Is there no longer a cairo session in the login screen?

---

### Post by Dennis N on 2015-10-24
I use Plank, and it needed to be added to startup applications. Perhaps the same is true of Cairo Dock?

---

### Post by nwpll on 2015-10-24
Hi

Sorry i should have said i can only use my Cairo dock after going into Applications menu Computer and online services. Every time i switch on my laptop i have to start my Cairo dock. Before my new install my Cairo dock always opened when i switched on my laptop.

Thanks

---

### Post by deadflowr on 2015-10-24
When you start up at the login screen look to see if you can switch desktops.
If you have Ubuntu login screen (it will have the username and password filed in a semi-transprent box in the left area of the screen)
See if a tiny icon is in the top corner of that username/password box. If so click to see if a cario option is there.
If there is, click on it to select and try logging in.

If, by chance you set it to autologin during install, then simply login as usually and then log out to get to the login screen.

---

### Post by nwpll on 2015-10-24
Hi

Thanks for a speedy reply. The left hand side of my screen has a fault and i can't see anything on the left. I can only see the left of the screen if i do a screen dump that's why i am using a Cairo doc.  

Thanks

---

### Post by deadflowr on 2015-10-24
Yeah, I'm not sure about dealing with a broken screen.

You could try installing the optional lightdm-gtk-greeter and a specialized greeter manager app.
The greeter should be in the default repositories, but the settings gui app, as far as I know, is a ppa.
See here: [http://www.webupd8.org/2014/10/lightdm-gtk-greeter-settings-gui.html](http://www.webupd8.org/2014/10/lightdm-gtk-greeter-settings-gui.html)

the gtk greeter will have the desktop login options in the top right area of the top panel.
And the manager/settings gui will allow you to place the login box in the right side area.

This should allow you to select the cairo-dock option and login, without having to use the leftside.

Just a thought.

---

