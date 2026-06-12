---
title: "[SOLVED] Is there a skin for Ubuntu 8.04 that looks like Mac?"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by josh995 on 2008-05-13
Hello. I've had Ubuntu for about a month now, and I really, really like it, a lot better than Windows Vista.

However, I was just wondering if there is a skin for Ubuntu that can make it look like Mac OS X Tiger or Leopard.

If there is, could you please direct me to it? Also, how do I install it? Like I said, I'm brand new to the whole Linux interface, so I don't know how to install or what to type!

I have the newest version.

Thanks a lot, community!!

---

### Post by sdennie on 2008-05-13
I would check out [http://www.gnome-look.org/](http://www.gnome-look.org/).  Specifically the metacity and gtk2 themes.  There are a variety of themes there and, unless they have special instructions, the normal method to install them is just to go to System->Preferences->Appearance, click install and then find the file you downloaded.

---

### Post by dRock1286 on 2008-05-13
[http://sourceforge.net/projects/mac4lin]("http://sourceforge.net/projects/mac4lin")

Walks you through everything...  enjoy!

---

### Post by CJay554 on 2008-05-13
First off your going to need to install emerald

```
sudo apt-get install emerald
```

then go to either gnome-look.org or compiz-themes.org

and find a theme that you like.

then use the emerald theme manager to import the folder with the theme and your set!

heres a good mac theme
[http://compiz-themes.org/content/show.php/Mac4Lin+ver.0.4+Emerald+Theme?content=71995](http://compiz-themes.org/content/show.php/Mac4Lin+ver.0.4+Emerald+Theme?content=71995)

they also use Avant Window Navigator for the bar, which u can get by going into the synaptic manager, then just searching for "avant window manager", check the boxes of the program you want, click apply, and ur set!

---

### Post by Living2007 on 2008-05-13
> **josh995 said:**
> Hello. I've had Ubuntu for about a month now, and I really, really like it, a lot better than Windows Vista.

However, I was just wondering if there is a skin for Ubuntu that can make it look like Mac OS X Tiger or Leopard.

If there is, could you please direct me to it? Also, how do I install it? Like I said, I'm brand new to the whole Linux interface, so I don't know how to install or what to type!

I have the newest version.

Thanks a lot, community!!

I've posted this thread also. Most people voted of Mac4Lin. I would personally recommend it too, but make sure you can connect to the internet, because some of it requires Compiz.

---

### Post by josh995 on 2008-05-13
Alright, well how do I do this? I am downloading, but I'm used to Windows... The easy "install" but ubuntu is different.... I can't figure out how to even get these to show up anywhere, i download it and it's like it just disappears. :(

And, I don't know how to delete programs, so soon my hard drive is going to be full of junk that I can't figure out how to delete. :(

---

### Post by Living2007 on 2008-05-13
> **josh995 said:**
> Alright, well how do I do this? I am downloading, but I'm used to Windows... The easy "install" but ubuntu is different.... I can't figure out how to even get these to show up anywhere, i download it and it's like it just disappears. :(

Place the files at the root of Windows, and reopen it in ubuntu, Mac4Lin requires extcraction from Archive Manager. BRB

---

### Post by josh995 on 2008-05-13
See, I have absolutely no idea what that means. :confused::confused::confused:

I think I am just going to have to live with the boring default look of ubuntu. Love the performance, hate how everything is so hard to do... :neutral:

---

### Post by sujoy on 2008-05-14
it ain't hard really.
just right click on the compressed file, click on extract.
now open up aprearence from system->preference.
in the extracted folder you will find GTK themes, which should be of the form (filename.tar.gz), just drag and drop them in the aprearence window.
now select the new theme, or click on customize and choose the window border and other properties as per you choice.

---

### Post by PinkFloyd102489 on 2008-05-14
Im in the process of making one. I have all the files to do so, it's just finding the time to sift through all of the files and arrange them into an installable package, not to mention writing the install script.


I have one for Vista though. :-p

---

### Post by Living2007 on 2008-05-14
> **josh995 said:**
> See, I have absolutely no idea what that means. :confused::confused::confused:

I think I am just going to have to live with the boring default look of ubuntu. Love the performance, hate how everything is so hard to do... :neutral:

OK I'll be more suscipic.

Once you download the file for "[Mac4Lin]("http://sourceforge.net/project/platformdownload.php?group_id=204373")" (there is also a documentation for you to download and read, I adives to get this), move it to C:\ directory.
Then start Ubuntu and browse for the Windows partition. The downloaded files should be there among all of the other folders.

Once you have found the files, open it and "extract the contents to a location on the Ubuntu Partition.

---

