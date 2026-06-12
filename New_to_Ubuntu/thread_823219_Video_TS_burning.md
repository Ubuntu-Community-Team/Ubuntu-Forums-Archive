---
title: "Video_TS burning"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by cjv8888 on 2008-06-09
I have searched for a long time but still have not found a program or package in Ubuntu that can burn a Video_TS file directly to a DVD. Gnomebaker can burn an ISO but I wish to save that extras step of converting a Video_TS movie file to an ISO first.

Anyone has any suggestions?

---

### Post by SunnyRabbiera on 2008-06-09
You can try k3b

---

### Post by Scheater5 on 2008-06-09
It's my understanding that there is data on a DVD aside from merely the TS files themselves - something about telling the dvd reader where certain files are when you select special features (notice TS files often don't include those).  You could call it analogous to a .config file.  Therefore, just burning TS files to a blank DVD will not make it a "DVD."  What you want is to make a data DVD with the folder containing your TS files.  You can make that in just about anything, including Brasero and k3b.  You can then play that on any computer, or possibly a DVD burner that supports video files.

---

### Post by MeTylerDurden on 2008-06-09
[B][SIZE="2"][COLOR="DimGray"]Don't search , don't try and don't even move.. someday we will get our videos to disc (and the earth shook) hopefully before discs go out of fashion...     your parents your leaders those who would call themselves your judges... 

 [SIZE="1"]they shall all be cleansed..      don't sweat it, I just put it all on the backburner[/SIZE][/COLOR][/SIZE][/B]

---

### Post by kelvin spratt on 2008-06-09
You have 2 choices the first is the correct way in either Linux or windows is the save DVD
as a ISO image on your hard drive then all data and the structure of the film is preserved
then burn iso. or use K3B, or Nero for Linux, and burn the complete  audio/vidio ts files structure to disc. the feature in K3B is Hard to find I think its in tools?

---

### Post by jrusso2 on 2008-06-09
> **Scheater5 said:**
> It's my understanding that there is data on a DVD aside from merely the TS files themselves - something about telling the dvd reader where certain files are when you select special features (notice TS files often don't include those).  You could call it analogous to a .config file.  Therefore, just burning TS files to a blank DVD will not make it a "DVD."  What you want is to make a data DVD with the folder containing your TS files.  You can make that in just about anything, including Brasero and k3b.  You can then play that on any computer, or possibly a DVD burner that supports video files.

No this is wrong.  You can burn a DVD from a Video_TS I do it in Nero all the time.  putting it on blank data dvd is not going to work.

---

### Post by fiddledd on 2008-06-09
OK, I'm guessing you are starting with an avi and converting it to .vob, I don't know what you are using to do this. Here's what you need to do to convert an .avi to a DVD:

First you need to convert it to .mpg, you could use Avidemux for this (there are many other ways, ffmpeg, mencoder etc)

Then you need to Author it so you get a VIDEO_TS and AUDIO_TS folder, for this DeVeDe, QDvdAuthor, KDE DVD Authoring Wizard are upto the task.

Then you have to burn those 2 folders to DVD, K3B will do this, but make sure you burn as a Video DVD, not a Data DVD

---

### Post by cjv8888 on 2008-06-09
I cannot find the burn Video_TS feature in K3B, only the burn ISO. Could you indicate again where it is hiding? 
The reason I am looking is that when I author a DVD from an AVI, it is always authored into the Video_TS format.

---

### Post by Unterseeboot_234 on 2008-06-09
I use Kino to make my .vob from DVraw, exported as Other->DVD -> make DVD structure. That gives me a folder named "DVD" inside of that is two folders: AUDIO_TS and VIDIO_TS. Those are what I burn. I just put a blank DVD into my external DVD burner and whatever burning software it is that comes with Ubuntu notices I have blank media and a dialog asks if I want to burn. YES, and I get a window with a button at the top to Write Media. That DVD will run from the first movie clip (no menu).

For a menu, the only program I found that I like is ManDVD. Search for it on the web. A third party was building a deb for it. ManDVD I can have a Play all or play by chapter. Again, ManDVD just makes a DVD folder with AUDIO_TS and VIDEO_TS. I burn JUST those folders, not the DVD folder.

Now, having said that, I cannot play the DVD on Ubuntu. The DVD plays on my home appliance. If I want to play a movie on Ubuntu, I will burn a DIVx using DeVeDe. I play it with Xine. Xine can play the individual .vob files of a DVD, but not from the menu.

If I want to make a copy of a DVD into DIVx, I use K3B. K3B has to have the hard drive and the burner physically connected by cable to the motherboard or it won't work. If K3B does not see the hardware it wants, it screws up ManDV, Kino and all the other stuff I do have working with my external peripherals.

I have a small stack of coasters finding out these things.

---

### Post by RomeReactor on 2008-06-09
> **cjv8888 said:**
> I cannot find the burn Video_TS feature in K3B, only the burn ISO. Could you indicate again where it is hiding? 
The reason I am looking is that when I author a DVD from an AVI, it is always authored into the Video_TS format.

Hi. Look in the 'Tools' section in the menubar; there should be an option to 'Burn to Video DVD'. Then just drop the contents of your VIDEO_TS folder into the one K3B gives you, and burn.

---

### Post by cjv8888 on 2008-06-09
Thanks, I found it.
I have to click on a bar below all those GUI of the options and then it shows up further options that you can burn a videoDVD.

---

### Post by jeepers on 2008-08-03
I am trying to find this option...exactly whereabouts in the tools section is it ?.

cheers

OK found it a t the bottom of the app.

---

### Post by kaston on 2008-11-14
to be more precise, you have to click "further actions" and then pick "new video dvd  project"

---

### Post by OzzyFrank on 2009-01-15
Yup, **K3b** is the shiznit! God, I hated going into Windows just for that! Especially since for data DVDs Ubuntu makes Windows look pale, since I can generate a checksum, burn the disc, then check it. So I am happy now... but have to admit: I am staggered all the other apps I've tried in Ubuntu seem to look at VIDEO_TS folders as something strange, or just some data.

In Windows, the only program I've tried that can't make a playable movie DVD from burning the folder is Nero, which I absolutely hate - as the last time I tried it, it added some of its own files to such a project, which seems highly unnecessary. With K3b you have to specify a movie DVD project, like Nero, but at least it doesn't add extra files, and lets you add extra files of your own, like an md5sum.txt for verification.

---

### Post by biodiesel-bri on 2010-07-10
For anyone trying to do this under 10.04 Lucid Lynx it's still possible under K3B but the option has moved.

Now you have to click the "New Project" button on the left, just below the file link.  Choose "New Video DVD Project" and drop the files (not the directory) from your VIDEO_TS directory into the VIDEO_TS directory that K3B creates.

---

### Post by Steve603z on 2010-07-10
```
mkisofs -dvd-video -o [output iso file location] [Video_TS directory]
```

---

### Post by OzzyFrank on 2010-07-10
Hmmm... I've been suing K3B for years, and the option was never visible for me, but always only accessible via the "More actions..." menu. But hey, if you use it often, just make a button for it (which you can do with K3b).

---

