---
title: "HowTo: Change the Gnome Main Menu Icon"
date: 2007-07-11
forum: Outdated Tutorials &amp; Tips
---

### Post by aysiu on 2007-07-11
[The last tutorial on this](http://ubuntuforums.org/showthread.php?t=260362&highlight=logo) was for 6.06 (Dapper).

As of this writing, the current Ubuntu release is a year later at 7.04 (Feisty).

Some people will recommend trying to hunt down every instance of *distributor-logo.png* or *distributor-logo.svg* and replacing them one by one.

Others recommend using a custom icon through *gconf-editor* (some people swear by this method, but it did not work for me).

The simplest way to do it (and I forget which thread I read this in, but kudos to whomever suggested it first) is to create a folder in your home directory for the icon theme you use and then put your custom icon in there.

For example, if you're using the *Human* icon theme, create this directory structure (the new custom logo is in bold): ```
/home/*username*/.icons/*Human*/scalable/places/**distributor-logo.png**
``` Then press Alt-F2 and type ```
killall gnome-panel
``` Now you should have your custom logo instead of the Ubuntu logo!

---

### Post by kevinlyfellow on 2007-07-12
You may also need to edit ~/.icons/Themename/index.theme depending on your theme

I needed to create the folder ~/.icons/Themename/scalable/places/ and then edit ~/.icons/Themename/index.theme to read (notice the last entry "scalable/places")
```
Directories=scalable/apps,scalable/filesystems,scalable/mimetypes,scalable/devices,scalable/emblems,scalable/places
```

and then added the following lines at the end

```
[scalable/places]
MinSize=1
Size=48
MaxSize=128
Context=Places
Type=scalable
```

Edit: And thanks aysiu, I remember trying to change that a long time ago.  I had never had been able to figure it out!

---

### Post by daris on 2007-07-12
[http://forums.debian.net/viewtopic.php?t=14877](http://forums.debian.net/viewtopic.php?t=14877)
and
[http://www.gnome-look.org/content/show.php/Start+icon+Ubuntu+Debian+Suse+Gentoo+Tux?content=52882](http://www.gnome-look.org/content/show.php/Start+icon+Ubuntu+Debian+Suse+Gentoo+Tux?content=52882)

---

### Post by kevinlyfellow on 2007-07-12
> **daris said:**
> [http://forums.debian.net/viewtopic.php?t=14877](http://forums.debian.net/viewtopic.php?t=14877)
and
[http://www.gnome-look.org/content/show.php/Start+icon+Ubuntu+Debian+Suse+Gentoo+Tux?content=52882](http://www.gnome-look.org/content/show.php/Start+icon+Ubuntu+Debian+Suse+Gentoo+Tux?content=52882)

I resorted to rickh of the debian forums before, but it couldn't change everything and was a hassle to maintain.  Aysiu's method was by far easier and all encompassing.

---

### Post by aysiu on 2007-07-12
It's not really my method. I read it somewhere else on the forums--I forget where.

The advantages of this method, though, are:

* It doesn't involve messing with system files and having to back up and/or rename them

* It's user-specific, which means it won't mess with other users' menu icons and will be preserved if you have a separate /home partition

* It's simple--it doesn't involve a lot of steps or the downloading and installation of a separate application

* It replaces only one icon instead of many

---

### Post by ferronica on 2007-07-23
thanks buddy "aysiu" i tried many tricks even gconf-editor all waste 3 hours wasted using gconf-editor, after reading your idea just in second everything done 100% perfect thanxxxxxxxxxxxxx [http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

---

### Post by blairellis on 2007-07-26
Im going to ask a simple question here that I am sure most of you know, but as a nooborz to Ubuntu, I am still finding challenging.

I don't have any sub folders in my .icons folder. Is this something that can only be done to a themed up Ubuntu or can this be the only change made? I guess since I am still learning, I am not understanding some of what has been said.

Any help would be awesome :) Thanks!

---

### Post by aysiu on 2007-07-26
You create the subfolders if they don't exist.

In the example I gave before, I just had the ~/.icons folder.

So I created a Human folder inside of that.
Then I created a scalable folder inside the Human folder.
Then I created a places folder inside the scalable folder.

None of those folders were there before.

---

### Post by digeratiX on 2007-08-13
I have tried all methods and nothing is working at all, why is that?

---

### Post by aysiu on 2007-08-13
> **digeratiX said:**
> I have tried all methods and nothing is working at all, why is that?
Can you give more details?

---

### Post by CowzRule on 2007-08-13
The name of the custom icon you use still has to be "distributor-logo" if you use the standard "Menu Bar". If, like me, you use "Main Menu", then the icon needs to be named "gnome-main-menu". Also, the icon doesn't have to be svg. png will work.
Here's mine [IMG]http://i12.tinypic.com/520tb8i[/IMG]

---

### Post by digeratiX on 2007-08-13
Well I tried the very first thing in this post and it never worked. 

Next I tried everything here [http://forums.debian.net/viewtopic.php?t=14877](http://forums.debian.net/viewtopic.php?t=14877) and had the same issues that CocoAUS has, simply doesnt work.

Maybe great detail needs to be noted on how to properly create your image to be used?
I dont know, I just know that nothing has worked.

I used fireworks to take an image and resize it and save as a png and it didnt work no matter where it was placed.

Currently I am using glossy as a theme and it uses GNOME icons. Simple stuff, just not working.

---

### Post by aysiu on 2007-08-13
> **digeratiX said:**
> Well I tried the very first thing in this post and it never worked. 

Next I tried everything here [http://forums.debian.net/viewtopic.php?t=14877](http://forums.debian.net/viewtopic.php?t=14877) and had the same issues that CocoAUS has, simply doesnt work.

Maybe great detail needs to be noted on how to properly create your image to be used?
I dont know, I just know that nothing has worked.

I used fireworks to take an image and resize it and save as a png and it didnt work no matter where it was placed.

Currently I am using glossy as a theme and it uses GNOME icons. Simple stuff, just not working.
Can you post the output of these commands? ```
cd /usr/share/icons
ls
cd ~/.icons
ls
```

---

### Post by digeratiX on 2007-08-13
Here you go.

digerati@ubuntu:~$ cd /usr/share/icons/

digerati@ubuntu:/usr/share/icons$ ls
application-default-icon.png  default      HighContrastInverse  Tangerine
cab_extract.png               default.kde  Human                Tango
cab_view.png                  gnome        locolor              whiteglass
Crux                          handhelds    Mist                 xchat_mini.xpm
crystalsvg                    hicolor      redglass

digerati@ubuntu:/usr/share/icons$ cd ~/.icons
[email]digerati@ubuntu:~/.icon[/email]s$ ls
[email]digerati@ubuntu:~/.icon[/email]s$ 

If you were expecting something to be in ~/.icons dont, I deleted each item I had created after it didnt work.

---

### Post by aysiu on 2007-08-13
> **digeratiX said:**
> Here you go.

digerati@ubuntu:~$ cd /usr/share/icons/

digerati@ubuntu:/usr/share/icons$ ls
application-default-icon.png  default      HighContrastInverse  Tangerine
cab_extract.png               default.kde  Human                Tango
cab_view.png                  gnome        locolor              whiteglass
Crux                          handhelds    Mist                 xchat_mini.xpm
crystalsvg                    hicolor      redglass

digerati@ubuntu:/usr/share/icons$ cd ~/.icons
[email]digerati@ubuntu:~/.icon[/email]s$ ls
[email]digerati@ubuntu:~/.icon[/email]s$ 

If you were expecting something to be in ~/.icons dont, I deleted each item I had created after it didnt work.
Where's Glossy in the /usr/share/icons list, though?

---

### Post by digeratiX on 2007-08-13
Well maybe this can help some.

This is what I am seeing and using.

[IMG]http://69.92.75.2:8080/junk/pictures/ubuntu-glossy-desktop.jpg[/IMG]

---

### Post by CowzRule on 2007-08-13
> **digeratiX said:**
> Well I tried the very first thing in this post and it never worked. 

Next I tried everything here [http://forums.debian.net/viewtopic.php?t=14877](http://forums.debian.net/viewtopic.php?t=14877) and had the same issues that CocoAUS has, simply doesnt work.

Maybe great detail needs to be noted on how to properly create your image to be used?
I dont know, I just know that nothing has worked.

I used fireworks to take an image and resize it and save as a png and it didnt work no matter where it was placed.

Currently I am using glossy as a theme and it uses GNOME icons. Simple stuff, just not working.

Try this. Inside your ".icons" folder make a folder titled "gnome". Inside there make one titled "scalable". Inside there make one titled "places". Now put your custom icon titled "distributor-logo" inside the "places" folder.
[IMG]http://i15.tinypic.com/4zcnvwo[/IMG]

[IMG]http://i11.tinypic.com/6bbjt3l[/IMG]

---

### Post by hype on 2007-08-13
Good how to.
I have one question tho, which is quite off-topic infact: do you know a way to modify the text from gnome-menu? (Applications Places System)

---

### Post by CowzRule on 2007-08-13
> **hype said:**
> Good how to.
I have one question tho, which is quite off-topic infact: do you know a way to modify the text from gnome-menu? (Applications Places System)

You can change the color of the letters by changing some settings in a file called ".gtkrc-2.0". It's a hidden file located in your home folder.
If it's not there, create it and add the following:
```

style "panel"
{
fg[NORMAL] = "#ffffff"
}

```
The letters ffffff will make the text white. [color="#CF3030"]CF3030 is this color[/COLOR]

---

### Post by digeratiX on 2007-08-14
I will try this in the morning and see.

---

### Post by digeratiX on 2007-08-14
Nothing is working still. Tried it on two Ubuntu boxes and nada, even jpg and making one in inkscape and saving as svg has no effect.

---

### Post by CowzRule on 2007-08-14
> **digeratiX said:**
> Nothing is working still. Tried it on two Ubuntu boxes and nada, even jpg and making one in inkscape and saving as svg has no effect.

I followed my own advice and I've got the same problem as you. I thought I had it figured out because I noticed in the /usr/share/icons/gnome/scalable/places folder that the distributor-logo icon is actually a link to a icon titled start-here. However, when I renamed my custom icon in /home/scott/.icons/gnome/scalable/places to start-here, it still didn't work.
So here's what I did. I copied the gnome icon folder from /usr/share/icons to my /home/scott/.icons folder. I then renamed the folder to my-icons. Then inside that folder is a file titled index.theme. I opened it with gedit and replaced the word Gnome (all of them, just use the "Replace" button) with My Icons. Then I placed my custom distributor-logo icon in the /scalable/places folder. I also deleted all those "number x number" folders because I downloaded some custom icon packages and those weren't in there and I never had any problems. Then just go and select your My Icon theme.
Another thing about doing it this way is if you want to replace any other icons you have a nice easy place to do so.

---

### Post by digeratiX on 2007-08-14
Amazing it is still not working and I have no clue why. 

I did just as you said, and used an icon that someone else on this board is useing and it will not work.

The icon still exists on the application menu.

Does it have to be svg, named something else or what?

[IMG]http://67.60.112.91:8080/junk/pictures/ubuntu-glossy-desktop2.jpg[/IMG]

---

### Post by CowzRule on 2007-08-14
Did you do a ```
killall gnome-panel
```in the terminal? Also, try placing your custom icon in the /.icons/my-icons/scalable/apps folder (so it's in both folders). And if there's a file titled icon-theme.cache, delete it.
As far as svg or png, I don't think it really matters, I've used both types and both have worked.

I've attached a test icon package. Their the same gnome icons with a custom distributor-logo icon. Just drag and drop it on the Theme window and it will install then ask you if you want to switch to them.

I posted that blue Gnome foot icon. I had to convert it from svg to png so that I could upload it to the picture hosting site I used.

---

### Post by digeratiX on 2007-08-14
Yes I ran the cmd and yes I copied the distributor-logo to the apps directory and yes it still does not change the applications menu icon.

Why do I have to be the one that this doesnt work for.

I want to create my OWN icons. I cant even get these test icons to work.

---

### Post by CowzRule on 2007-08-14
First, I edited my above post to include a test icon package to try.

The only other thing I can think to do is this:
Right click the panel and select "Add to Panel". In the window that pops up, scroll to the bottom and look for "Menu Bar". See if it's using your custom icon. If it is, add to your panel and get rid of the other one.

If that doesn't work, I'm at a loss to figure out why it wont work. Maybe it works for myself and other because we've customized our panels.
If I think of anything else I'll post it. I know how frustrating getting something to work that works for everybody else and not for you. I'll keep watching this thread so if you got any more questions I'll try to help.
Good Luck.

---

### Post by digeratiX on 2007-08-14
Its not doing it, thanks for all your help.

---

### Post by olavjunior on 2007-08-17
Works perfect! Thanx :)

---

### Post by Hubi17 on 2007-08-17
I was messing around for a long time until with CowzRule's method it worked. Only I did not remove the *number x number* folders, because then it would not work. So I placed my custom Icon for the Main Menu Icon into the Places folder of each *number x number* folder and now its working. Only problem i still have is that my panel is sized at 24 pixel, and if I resize it the Main Menu Icon doesn't scale like all the other normal icons. Somehow it refuses to use the scalable icon.
But it works at my normal setting so I'm happy.
Thanks a bunch everyone for the great HowTo!!!

---

### Post by aysiu on 2007-08-17
I think the use of scalable v. #x# might depend on the original theme itself and how it defines its folders. In my example, I used the Human theme, which allows for a scalable folder.

---

### Post by Hubi17 on 2007-08-17
I also have a scalable folder with the icon in it, but somehow Gnome doesn't want to accept it then. I am also using the Human theme, and after my first try with only the scalable icon, the icon showed up in the "add to panel" window, but once i added the Main Menu or the Menu Bar it was the old logo again. Thats why I'm confused now report how I did it.

---

### Post by oni5115 on 2007-09-18
I have had a lot of trouble trying to get this working.  I tried using gconf editor without any luck at all.  I tried using the method posted here without any luck.  Finally, I decided to copy the Human theme from /usr/share/icons to /home/USER_NAME/.icons/ and try to replace the "start-here" image.  First I tried 24x24, it failed.  Then I did 22x22 and it worked!  I finally had my custom icon.

I then set out to modify the Glass Icon theme.  I copied the entire 22x22 folder, removed everything but places.  then removed everything in there except: distributor-logo.png, gnome-main-menu.png, and start-here.png.   If everything is working properly, when you copy and paste start-here.png, it should change the way the other two icons look automatically.

I then edited index.theme to have:
```
Directories= ... all the default directories**,22x22/places**
```

```
[22x22/places]
Size=22
Context=Places
Type=Fixed
```

I then switched back to the Glass Icons and BAM I now have a cool black and green logo to fit the rest of my theme.  The icon does not resize automatically, but at least it works.  I am guessing that if I bothered to make folders for all the sizes, that it might get bigger as I increase the bar size, but I really don't care to bother with it.

One thing I would like to point out is that I tried using the scalable/places folder, and had the index.themes looking at the proper directory and settings as posted previously.  It simply did not work for me.  Maybe the scaling only works for svg's?  It certainly did not work for png files, at least not for me.

---

### Post by mbp84 on 2008-05-01
I am bringing this back from the dead for a quick question,   I changed my theme to crashbit and I love the theme but my main menu Icon is one I hate and I want to change it.  How can I change that to what i want?

---

### Post by Kagee on 2008-08-12
I had to follow oni5115's example. 
Create 22x22/places, place start-here.png there (22x22 px) and modify the index.theme-file.

---

### Post by johnny9794 on 2008-08-12
A while back when I was using 7.10, it took a few days by myself to get the main menu icon changed, lots of messing, changing, reinstalling and this is the most simplest way that I found how to change the main menu icon for 7.10. for gnome icons with any theme. The attachment is at the bottom with a gnome foot icon and instructions. This does not work with 8.04.1. , thats what I'm seeking now is to change the main menu icon for 8.04. but no find on that yet.

EDIT: Solved on 8.04 Hardy that worked for myself.
[http://ubuntuforums.org/showpost.php?p=5575870&postcount=24](http://ubuntuforums.org/showpost.php?p=5575870&postcount=24)

---

### Post by Jim Danner on 2010-05-14
I guess the quick and easy way to do this using [Ubuntu Tweak]("http://ubuntu-tweak.com/") has eliminated the need for this manual solution, but still... you might want to know exactly what you're doing, or you might want to use an .svg picture instead of the .png that Ubuntu Tweak requires. The method explained in this thread is now much more reliable than before.
[LIST=1]
[*]Create or find an icon, exactly 24 x 24 pixels, in SVG or PNG form, and save it as *start-here.svg* or *start-here.png* respectively. Inkscape can make nice SVG files, GIMP is good at PNG's (you can install these programs in the Software Center). I prefer SVG because it's going to look good even if you have to resize it later for some reason. *EDIT:* An SVG file doesn't even have to be 24x24; any size will do... because it's scalable.
[*]Find out what icon theme you are using. Easiest is System... Preferences... Appearance, Customize..., Icons. For example you might be using Humanity.
[*]In Places... Home Folder find the folder .icons (maybe you must press Ctrl+H to see it as it is hidden). Create a subfolder named the same as your icon theme, and inside that create further subfolders so as to have:
~/.icons/Humanity/apps/24/ (in your case *Humanity* might be something else).
[*]Put the *start-here.svg* or *start-here.png* file inside that *24* folder
[*]Log out and in again, or restart the panel (Alt+F2 and type *killall gnome-panel* and hit Run)
[/LIST]
I have never got this method to work. And now it's so easy...

---

