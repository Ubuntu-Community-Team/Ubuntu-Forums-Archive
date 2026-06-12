---
title: "Using WINE to run Portable Apps from my portable HDD"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by scotcella on 2008-08-08
Hi,

I checked the WINE HQ website and it seems that Portable Apps is supported and has a platium rating for Gusty and Feisty, but not yet for Hardy yet- or at least no one has reported it yet.

How I am not clear, and I've tried looking for information on how I can open the .exe file within WINE.

Do I need to configure WINE or does it automatically pop up itself and run? How do I start it?

Any help appreciated!!

---

### Post by ajgreeny on 2008-08-08
Open  terminal and enter ```
wine /path/to/the/setup.exe
```That will install the program you want and should add it to the Gnome menu under **Programs>>Wine>>Programs**  If for some reason it is not in the menu, the exe file for running the program itself will be in your home folder under the hidden folder **~/.wine/drive_c/Program Files/foldername/file.exe** and you can run that with a terminal command easily, though you will need to put that path in " marks, as the path has a space in the **Program Files** name.

---

### Post by statto1977 on 2008-08-08
I've had some issues with this. As mentioned, it gets a platinum rating, but using Gutsy I've noticed a lack of functionality.

On windows PCs it puts an icon in the system tray, but it doesn't do this in linux. That means that every time you want to use it you have to double click on the portable apps icon on the USB drive. It also doesn't allow you to open the pictures/music/video folders, or explore the contents of the USB drive. Most of the programs seem to work though.

If anyone knows of any workarounds it would be helpful.

---

### Post by scotcella on 2008-08-08
Hmm,,

That was clear as mud..   I'm still not sure..  the .exe program is not even showing up under the wine thing. argh..

I went to Applications -> Wine -> Configure Wine -> Drives 

Both my HDDs are showing up, but the Portable Apps .exe files are not there even thought they do show up on a Windows machine.

Nothing is showing up in the hidden folder ~/.wine.

---

### Post by scotcella on 2008-08-08
> **statto1977 said:**
> I've had some issues with this. As mentioned, it gets a platinum rating, but using Gutsy I've noticed a lack of functionality.

On windows PCs it puts an icon in the system tray, but it doesn't do this in linux. That means that every time you want to use it you have to double click on the portable apps icon on the USB drive. It also doesn't allow you to open the pictures/music/video folders, or explore the contents of the USB drive. Most of the programs seem to work though.

If anyone knows of any workarounds it would be helpful.

Wierd.. I can open all my docs without any issues... including photos etc

Edited to add: Although not through the portable apps- as you mentioned- but I can definitely access them through Places -> Computer -> (name of portable drive).

---

### Post by scotcella on 2008-08-08
OMG.. i got it opened..  I don't know how i did it..

before I put in

Applications -> WINE -> Configure WINE -> Applications -> Add application....



And just then I opened my HDD using Places -> Computer, then clicked on my HDD..  and for one wild moment.. i thought **** it and opened the .exe file that shows up (as it always did) and the damn thing opened up right off the bat!!!

Gonna put this in windows and see if the changes I made are there and vice versa etc and if it still works when I remove the HDD from my Ubuntu lappy.

Post back in 10 minutes...........


Edited to add: I feel like an idiot..   you said exactly what I did and I was thinking I was so clever LOL. 
> 
That means that every time you want to use it you have to double click on the portable apps icon on the USB drive. It also doesn't allow you to open the pictures/music/video folders, or explore the contents of the USB drive. Most of the programs seem to work though.

Nonetheless I'm happy to say that Sunbird works well and now I will be able to access my work calendar at home on my preferred ubuntu laptop- even though I have to whore it by using WINE. This is all I wanted..- to access my work calendar as I work from home sometimes.

As you said the apps seem to work.. Now I can see what you mean by not being able to explore your data through Portable Apps itself..

---

### Post by scotcella on 2008-08-08
Hey mate...

Did you say you were using the Gutsy version...

I'm using the hardy version and just found the portable apps on the top panel

See attached pic

---

### Post by waspbr on 2008-08-08
In both my hardies(desktop and laptop) I can run my portable apps through wine, and I am a wine noob, I haven't tinkered with it at all, so you should be safe there. 

I just checked and it even works on intrepid out of the box (w/ wine), so to speak.

---

### Post by statto1977 on 2008-08-10
> **scotcella said:**
> Wierd.. I can open all my docs without any issues... including photos etc

Edited to add: Although not through the portable apps- as you mentioned- but I can definitely access them through Places -> Computer -> (name of portable drive).

Yes, that's what I meant. I didn't feel it should get platinum compatibility - gold would have been more accurate.

> **scotcella said:**
> Hey mate...

Did you say you were using the Gutsy version...

I'm using the hardy version and just found the portable apps on the top panel

See attached pic

I'm using Gutsy, yes, but it appears to be loading the icon in the same place as yours. :)

---

