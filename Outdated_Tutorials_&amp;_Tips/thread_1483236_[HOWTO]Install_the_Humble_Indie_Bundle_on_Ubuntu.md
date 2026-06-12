---
title: "[HOWTO]Install the Humble Indie Bundle on Ubuntu"
date: 2010-05-14
forum: Outdated Tutorials &amp; Tips
---

### Post by ssj6akshat on 2010-05-14
I have seen that some new users who haven't been introduced to basic Linux practises are confused about how to install the Humble Indie Bundle and I couldn't find a article on the WWW,so I thought to make one.

This article is written for beginner and requires only one optional CLI-fu.(I am still a learner when it comes to Linux)

A)For Aquaria,Penumbra,Lugaru

Step 1.Right click the installer of the game

Step 2.Click Properties>Permissions>Execute and click the check box

Step 3.Double click the installers and the game should install

Step 4.Go to Applications>Games to play

B)For Samorost 2 (Wayyy too much easy)

Step 1.Extract the archive to an easily accessible place

Step 2.Open the .html file in Firefox(make sure you have flash player installed)

C)For Gish 

Step 1.Extract the archive to a easily accessible place

Step 2.Select the gish file depending on your architecture(i.e. gish for 32 bit(x86) and gish 64 for 64 bit(x86_x64).

Step 3.Step 2 and 3 from A

Step 4.Install libopenal1 by going to Terminal and typing-
```
sudo apt-get install libopenal1
```

or go to synaptic and install libopenal1 from there

Step 5.Open to play

D)For World of Goo(Easier than Samorost 2)

Step 1.Open the installer

Step 2.Click 'Install Package'

Step 3.Enter your password

Step 4.Go to Applications>Games to play


One very necessary step for all games-

Don't Pirate!

Enjoy:popcorn::)

:guitar::guitar::guitar:

:popcorn::popcorn::popcorn:

---

### Post by undecim on 2010-05-14
> **ssj6akshat said:**
> Don't Pirate!

Agreed. You can choose your own price for as low as a penny, and there's no DRM, which means that the pirated versions will not be any better than what you would have paid for. And if you aren't willing to pay even a penny for 5 games (6 now with Samorost 2), you obviously don't value the games enough to even spend your time downloading them.

The only reason anyone should ever pirate anything is when the paid product has some form of DRM that makes it inferior to the pirated product. With the Humble Bundle, there's no DRM, you can choose your own price for 6 games, and part of your purchase goes to charity. Why would you pirate that?

---

### Post by ssj6akshat on 2010-05-15
Bump *if someone needs*

---

### Post by kiddykoff on 2010-05-17
I'm having trouble with having these programs allow executing of programs

I've changed the properties by right clicking and i've run the chmod command.

I double click and nothing happens. I run in terminal and it says there is no such command.

---

### Post by ssj6akshat on 2010-05-17
> **kiddykoff said:**
> I'm having trouble with having these programs allow executing of programs

I've changed the properties by right clicking and i've run the chmod command.

I double click and nothing happens. I run in terminal and it says there is no such command.

you will have to cd to the path and run it with ./whatever

or

simply drag the file the terminal and press enter.

Looks like your file is corrupt

---

### Post by VeeDubb on 2010-05-17
> **ssj6akshat said:**
> you will have to cd to the path and run it with ./whatever

or

simply drag the file the terminal and press enter.

Looks like your file is corrupt

I find it EXTREMELY useful to create a directory inside your home folder called 'bin' and add it to your path.  That way you can put links to things like this in that directory, and you'll be able to launch them without having to CD to the directory.

If you install internet explorer using the ies4linux script, it actually does this for you.  Kills 2 birds with 1 stone

---

### Post by Rahabib on 2010-05-19
I am having issues getting Gish to run for me.  I have 10.04 64 bit.  I double click the 64 bit exe and nothing happens.  It is set to executable.  The 32 bit version just brings up a white window with 4 gray boxes and thats it.

---

### Post by K.Mandla on 2010-05-19
Moved to Tutorials and Tips.

---

### Post by dakkar9999 on 2010-05-19
Thanks!  I did buy it and I had a few issues with installation.  Didn't install all of the yet, so I'll keep your instructions handy!

---

### Post by ssj6akshat on 2010-05-20
> **Rahabib said:**
> I am having issues getting Gish to run for me.  I have 10.04 64 bit.  I double click the 64 bit exe and nothing happens.  It is set to executable.  The 32 bit version just brings up a white window with 4 gray boxes and thats it.

can you drag the file into the terminal,run it and post the output here?

---

### Post by Rahabib on 2010-05-21
Ive been a bit busy lately.  When I get home this evening Ill try that.

thanks.

---

### Post by Rahabib on 2010-05-21
here is the error it gives

> error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory

---

### Post by 8jwong14 on 2010-05-21
Thanks for the info.  

I have a friend who still wants to pirate the games even if he can buy it for a penny even though he has access to a credit card and he's not just "trying" it out.  I plan on buying it soon.

---

### Post by ssj6akshat on 2010-05-22
> **8jwong14 said:**
> Thanks for the info.  

I have a friend who still wants to pirate the games even if he can buy it for a penny even though he has access to a credit card and he's not just "trying" it out.  I plan on buying it soon.

You are late.the promotion is over.

---

### Post by Rahabib on 2010-05-24
> **Rahabib said:**
>  			 				error while loading shared libraries: libSDL_image-1.2.so.0: cannot  open shared object file: No such file or directory 			 		

anyone know what this means?  I am am not linux savvy.

---

### Post by ssj6akshat on 2010-05-25
> **Rahabib said:**
> anyone know what this means?  I am am not linux savvy.

try sudo apt-get install libsdl-image1.2

---

### Post by Rahabib on 2010-05-26
well, that did something, but now all I see is a window with a white background and a few gray rectangles.

---

### Post by Rahabib on 2010-05-28
ok I figured it out.

first I had to run 
> sudo apt-get install libsdl-image1.2 	
next I had to run the gish64 application to run the game.  I got white boxes and gray rectangles.  Thats because the config.txt, gish.pla, and gish.his did not install to the directory from which I ran the application (it went one directory out).  So I just copy those 3 files to the same directory as the gish64 app and then run again, and it worked just fine.

---

### Post by tidmarsh on 2010-05-30
When I run gish64 from the file browser, it works just fine. However, I've created a menu item for Gish, and when I run it from the applications menu, I see the same symptoms as Rahabib--a blank window with a few gray rectangles. I've checked and config.txt, gish.pla, and gish.his are all in the same directory as gish64.

Any ideas for how to get the menu item to work?

---

### Post by ssj6akshat on 2010-05-31
> **tidmarsh said:**
> When I run gish64 from the file browser, it works just fine. However, I've created a menu item for Gish, and when I run it from the applications menu, I see the same symptoms as Rahabib--a blank window with a few gray rectangles. I've checked and config.txt, gish.pla, and gish.his are all in the same directory as gish64.

Any ideas for how to get the menu item to work?

How did you create it?

---

### Post by Rahabib on 2010-05-31
> **tidmarsh said:**
> When I run gish64 from the file browser, it works just fine. However, I've created a menu item for Gish, and when I run it from the applications menu, I see the same symptoms as Rahabib--a blank window with a few gray rectangles. I've checked and config.txt, gish.pla, and gish.his are all in the same directory as gish64.

Any ideas for how to get the menu item to work?

make sure you do this

>  			 				sudo apt-get install libsdl-image1.2 			 		

---

### Post by jdunn on 2010-06-05
> **Rahabib said:**
> I am having issues getting Gish to run for me.  I have 10.04 64 bit.  I double click the 64 bit exe and nothing happens.  It is set to executable.  The 32 bit version just brings up a white window with 4 gray boxes and thats it.

I get the window with grey boxes only when I try to run gish or gish64 from the Gnome menus.  They run fine from the CL.  I have 10.04 64 bit.  The libsdl and openal1 packages are installed.

**edit**
Okay.  If you try to run gish from the Gnome menu, config.txt, gish.pla and gish.his all get copied with default values to the home/<username> folder.  Here's a solution that works, assuming your game is installed in /opt/gish153:  Create the bash script /opt/gish153/playgish and add these two lines

```
cd /opt/gish153/
./gish64
```

Make it executable with 'sudo chmod +755 playgish'.  Run this script from Gnome menu.

---

### Post by tidmarsh on 2010-06-19
I created the menu item by right-clicking on the Applications menu, selecting Edit Menus and then clicking the New Item button.

I ran "sudo apt-get install libsdl-image1.2," but it showed that the latest version was already installed, and still no luck with the menu item.

Then I created a script following jdunn's directions and pointed the menu item at the script rather than directly at the gish64 executable, and Bob's your uncle--works fine from the menu.

Thanks for the help, folks.

---

