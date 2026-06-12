---
title: "HOW TO: Make gaim logo disappear"
date: 2006-04-28
forum: Outdated Tutorials &amp; Tips
---

### Post by amunimanghi on 2006-04-28
Hi!

Do you want to make your logos on your programs vanish. Well you have come to the right place. I have only tried this with gaim on GNOME and it works fine. I'm not sure about KDE, but I'm about 90% sure it would work. Okay, now to the steps:

1. If you are not root, go to the terminal and type in 
```
sudo nautilus
```
NOTE:Only do this when you are 110% sure that you know what your are doing. If you deleate something or screw around you can/will mess up your computer. I've warned you and will not be held responsible if you computer breaks.

2. Next, go to 

```
File Systems => usr => share => pixmaps => gaim
```

3. Look for a file that says [COLOR="Red"]logo.png[/COLOR]

4. This is where I leave you for you descision. You can either edit it or delete it. I advise you to make a back-up of everything you edit. You can do it by two ways:
     a. Make a copy and paste it in a different folder.
     b. Rename it with a number. IE: logo.png => logo1.png
              When you rename it with a number, it doesn't affect anything.

5. I have edited the Gaim logo and canceled the logo and it works like a charm with no errors what so ever. 

6. To see your changes, exit gaim completly. After, load gaim up again and you should see what you did. If you edited it, you will see what you drew. If you cancled it, the logo is not there and it shrunk. (see screenshot)

This method should work with any application. It would be easier if you changed the permissions for that specific folder so you don't to go to the terminal and type sudo nautilus every single time. I don't know how to change permissions using the terminal so i just right click and change it though the properties menu. 

Hope this helps. Have fun!!

-amunimanghi

---

