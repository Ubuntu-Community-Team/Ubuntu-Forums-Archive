---
title: "How do you get that cool rotating cube thing?"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by Bigtime_Scrub on 2008-05-06
I have Advanced Desktop setting installed. 

I went in there and check off the rotating cube box and the water effects and nothin. Nada. 

Im very disappointed :(

---

### Post by kk0sse54 on 2008-05-06
you sure you have compiz installed and running (which should be on by default). Also you sure you used the right commands? Stupid little things like that got me stuck when I tried to do it the first time.

---

### Post by tjwoosta on 2008-05-06
if you go to System-Preferences-Appearance  then click the visual effects tab does it let you choose extra?

---

### Post by jman0591 on 2008-05-06
Sometimes compiz won't even start unless you have appropriate drivers installed.  This would be my first guess, since it didn't work for me with the open-source nvidia drivers, but did with the restricted drivers.

---

### Post by dark_harmonics on 2008-05-06
to see why it isnt working go to a terminal and type compiz --replace . Compiz is the program that renders the effects you checked there (im assuming you installed the compizconfig-settings-manager). If compiz --replace fails could you post the results of that command? You might need to edit the /usr/bin/compiz file and add the line SKIP_CHECKS=YES to it near the beginning. Also the output of glxinfo|direct and what kind of video card can help us help you. if you just installed ubuntu checking the system--> administration --> hardware drivers for any restricted drivers that need installed might help too.

---

### Post by Bigtime_Scrub on 2008-05-06
> **dark_harmonics said:**
> to see why it isnt working go to a terminal and type compiz --replace . Compiz is the program that renders the effects you checked there (im assuming you installed the compizconfig-settings-manager). If compiz --replace fails could you post the results of that command? You might need to edit the /usr/bin/compiz file and add the line SKIP_CHECKS=YES to it near the beginning. Also the output of glxinfo|direct and what kind of video card can help us help you. if you just installed ubuntu checking the system--> administration --> hardware drivers for any restricted drivers that need installed might help too.

kong@kong-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2572 (rev 02) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

---

### Post by dark_harmonics on 2008-05-06
ok can you try that fix?

put the line SKIP_CHECKS=yes in the beginning part of the /usr/bin/compiz file and see if that gets it working for you.

---

### Post by HotShotDJ on 2008-05-06
> **Bigtime_Scrub said:**
> I went in there and check off the rotating cube box and the water effects and nothin.For the rotating cube, make sure you have both "Desktop Cube" and "Rotate Cube" selected. (For additional coolness, enable "Cube Reflection" and "3D Windows").  You'll also need to make sure that you have your Workspace Switcher set for 4 columns and 1 row to get a cube.  Now you should be able to rotate the cube by pressing ctrl+alt+left_mouse_button simultaneously.

---

### Post by dark_harmonics on 2008-05-06
After doing a search on your error "There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly." i saw a few different causes. Some people needed the right drivers to fix it. Other fixes were a bit more complicated. Do you know what kind of video card you are using?

---

### Post by Bigtime_Scrub on 2008-05-06
> **dark_harmonics said:**
> After doing a search on your error "There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly." i saw a few different causes. Some people needed the right drivers to fix it. Other fixes were a bit more complicated. Do you know what kind of video card you are using?

NO :( I got this computer from a friend and I put Ubuntu on it because it was running on Windows 2000 Professional. It might be a Raedon 9500 but Im not really sure.

On the Plus side Ctrl-Alt-Left button mouse spins and rotates the 2-d screens kinda nice.

---

### Post by NeoGreen on 2008-05-06
What type of video card do you have installed on your machine?  Here are some instruction I used to install Compiz Fusion [http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml]("http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml")

---

### Post by Lori700698 on 2008-05-06
I followed these instructions for the box, coolest thing I ever saw!  My son also helped figure out the buttons to push for fire, water, and screen effects!

[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

---

### Post by ucal on 2008-05-06
2d screens?  How many desktops do you have running right now?  Bottom right corner, there should be four if you want a cube, 5 if you want a pentagonal prism thingy, 6 hexagonal, so on and so forth.  To edit the amount of desktops you have, rightclick on one of the desktop icons, and chose preferences.  You should be able to edit the setting there.  Hope this helps!

---

### Post by Bigtime_Scrub on 2008-05-06
I think I need to set the # of virtual desktops to 4...

---

### Post by tjwoosta on 2008-05-06
yea if you have the flipping screen it means that compiz is working, you just need to add more desktops 

the way i did it was go to the advanced desktop effects settings and then go to general options click the desktop size tab (for cube you will want 4 for horizontal, the rest should be at 1)

---

### Post by Bigtime_Scrub on 2008-05-06
> **Lori700698 said:**
> I followed these instructions for the box, coolest thing I ever saw!  My son also helped figure out the buttons to push for fire, water, and screen effects!

[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

OMG thank you. Its works great.

This things looks awesome.

Thank you everybody.

---

### Post by HotShotDJ on 2008-05-06
> **HotShotDJ said:**
> You'll also need to make sure that you have your Workspace Switcher set for 4 columns and 1 row to get a cube.Didn't I just say that a page ago? :wink:  Always check the simple stuff before digging into the more complex stuff.

---

### Post by dark_harmonics on 2008-05-06
> **Bigtime_Scrub said:**
> NO :( I got this computer from a friend and I put Ubuntu on it because it was running on Windows 2000 Professional. It might be a Raedon 9500 but Im not really sure.

On the Plus side Ctrl-Alt-Left button mouse spins and rotates the 2-d screens kinda nice.

HAHA yea you were already there at that point!! I was thinking too deeply on it when i read that you couldnt get any settings to work!

---

