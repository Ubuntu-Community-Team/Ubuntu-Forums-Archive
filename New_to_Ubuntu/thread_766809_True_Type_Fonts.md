---
title: "True Type Fonts"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Justin Holland on 2008-04-25
Would somebody please help me.  I've got some true type fonts that I downloaded and wish to install.  How do I install them so that I can use them on all Ubuntu applications?

-= Justin =-

---

### Post by mrgooding on 2008-04-25
Hi Justin

I'm not sure myself how to install them, but I think what you're looking for is covered here:

[http://osnovice.blogspot.com/2007/07/fonts-are-ugly-in-ubuntu-gnome.html](http://osnovice.blogspot.com/2007/07/fonts-are-ugly-in-ubuntu-gnome.html)

Hope this helps!

---

### Post by Tsukura on 2008-04-25
The problem I'm having (in 8.04) is that:

1) If you go to System>Prefrences...there is no listing for Fonts like the help file says.

2) Ctrl-l and typing font:/// like the help file says gives me "Couldn't display "font:///". Nautilus cannot handle font: locations.

3) Browsing to the usr>share>font>truetype folder and then dragging the font to it gives me a permissions error.


Everywhere I've looked online and throughout the local help file does not help me in any way. All i'm trying to do is install one little ttf font and it's been 2 days of researching and nothing. I haven't even began to install a software app yet. I'm not sure if it's Linux, Gnome, or Ubuntu Distro...but I'm not happy about it right now.

---

### Post by alsamman on 2008-04-25
> **Tsukura said:**
> The problem I'm having (in 8.04) is that:

1) If you go to System>Prefrences...there is no listing for Fonts like the help file says.

2) Ctrl-l and typing font:/// like the help file says gives me "Couldn't display "font:///". Nautilus cannot handle font: locations.

3) Browsing to the usr>share>font>truetype folder and then dragging the font to it gives me a permissions error.


Everywhere I've looked online and throughout the local help file does not help me in any way. All i'm trying to do is install one little ttf font and it's been 2 days of researching and nothing. I haven't even began to install a software app yet. I'm not sure if it's Linux, Gnome, or Ubuntu Distro...but I'm not happy about it right now.

alright heres what u do
```
 sudo nautilus 
```

then this will give u the ability to access your computer using superuser privileges such that u can modify folders. go to /usr/share/font/truetype from nautilus that pops up when u put in code and just drag fonts in there and ull have no problem hopefully:)

---

### Post by Tsukura on 2008-04-25
Awesome, that worked like a charm.


The only thing was that when I typed sudo nautilus, it gave me a warning that "net usershare info" failed and told me to ask the sysadmin to enable user sharing. It still opened the window and I was able to drag the font and install it...

Is this just a normal message or do I need to enable something?

---

### Post by kostkon on 2008-04-25
> **Tsukura said:**
> Awesome, that worked like a charm.


The only thing was that when I typed sudo nautilus, it gave me a warning that "net usershare info" failed and told me to ask the sysadmin to enable user sharing. It still opened the window and I was able to drag the font and install it...

Is this just a normal message or do I need to enable something?
A simpler way would have been to go to your *Home* folder, select *View -> Show Hidden Files* from the *Nautilus* window and then copy your fonts to the *.fonts* hidden folder.

---

### Post by alsamman on 2008-04-25
> **kostkon said:**
> A simpler way would have been to go to your *Home* folder, select *View -> Show Hidden Files* from the *Nautilus* window and then copy your fonts to the *.fonts* hidden folder.

its funny cause i was trying to add fonts yesterday and someone told me to do that and i found that i did not have a .fonts folder so im just suggesting the way it worked for me

---

### Post by kostkon on 2008-04-25
> **alsamman said:**
> its funny cause i was trying to add fonts yesterday and someone told me to do that and i found that i did not have a .fonts folder so im just suggesting the way it worked for me
I believe you can create the folder yourself if it does not exist.

---

### Post by SunnyRabbiera on 2008-04-25
yeh the new gnome kind of phracks up th fonts:/// option, making things harder then they should be.

---

### Post by Justin Holland on 2008-04-25
I want to thank everybody for their help.  Below is what I found searching Google.  It worked just fine for me.  I'm posting to share this with everybody.

-= Justin =-



The easiest way to install a truetype font is to press alt-F2 and enter the following code (this will open nautilus in the right directory):

gksu nautilus /usr/share/fonts/truetype

Then create a new directory, name the directory whatever you like (choose a name that you remember if you ever need to backup your fonts personal fonts). Copy the fonts into that directory and finally rebuild the font information files by pressing alt-F2, mark 'run in terminal' so you can see the progress and entering the following code:

sudo fc-cache -f -v

<!> Note: After you install a new font, you will need to make sure that programs in which you want to use the new fonts can recognize them. In most cases this is done by closing and reopening the programs; however, some programs may require you to log out and log back in. 



Located on this page: [https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

---

