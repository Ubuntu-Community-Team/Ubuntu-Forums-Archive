---
title: "[SOLVED] Thumbnail Generation"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by s.fox on 2008-07-04
Hi everybody.

Just wondering how I would go about generating thumbnail images.  I have a folder with about 50 images in that i need a thumbnail version of.  Is their a quick and easy way to do this in ubuntu?

Thank you to everyone who can help.

---

### Post by s.fox on 2008-07-04
Right,  found out what I need to create my thumbnails.  

After doing a bit more research I have found out that graphicsmagick is what I need.  What is even better that synaptic package manager tells me its installed :)   Sadly i can't seem to find it in my applications menu :(

I guess I have to run it from terminal but not having much luck to be honest.  This is what I am trying at the moment.

```
ashley@ashley-desktop:~$ graphicsmagick
bash: graphicsmagick: command not found
ashley@ashley-desktop:~$ 

```

Can anybody tell me how to run this program?  

Thank you for any help.

---

### Post by silkstone on 2008-07-04
What size thumbnails do you want? Nautilus automatically generates thumbnails of images you view in the file manager when you 'View as Icons', so you could just do that and then find them as .PNG files in ~/.thumbnails/normal

---

### Post by sayakb on 2008-07-04
I have'nt got this installed. Try:
```
ls /usr/bin graphics*
```
And see if you get any relevant names there..

---

### Post by silkstone on 2008-07-04
I've just looked at the description in Synaptic and it says...

Note that unlike ImageMagick, the GraphicsMagick tools are accessed
through a single executable called 'gm'.

---

### Post by s.fox on 2008-07-04
Right,  thanks for clearing that one up :)  I got it running.    I didn't realize that it was a command line program. :lolflag:  

Is their anything a little easier to use?  I would really prefer to do it from GUI.  The thumbnails i am trying to create need to be around 100*100 pixels.

Thanks once again!

---

### Post by s.fox on 2008-07-04
> **silkstone said:**
> Nautilus automatically generates thumbnails of images you view in the file manager when you 'View as Icons', so you could just do that and then find them as .PNG files in ~/.thumbnails/normal

I was actually looking at the thumbnails that the file manager has earlier.  This is going to sound rather silly but...where is ~/.thumbnails/normal :confused:

If i was in my Home folder how would i navigate to it???

Thanks for your time

---

### Post by silkstone on 2008-07-04
It's in your home folder - click on View > Show Hidden Files. ;)

All files and folders beginning with a dot are hidden by default.

The only problem may be deciding which thumbnail relates to which file, unless you know the date the file was first opened in Nautilus, and therefore when the thumbnail was generated.

---

### Post by dfreer on 2008-07-04
> **Ash R said:**
> I was actually looking at the thumbnails that the file manager has earlier.  This is going to sound rather silly but...where is ~/.thumbnails/normal :confused:

~/ Is a special symbol that always points to the current user's home folder. So /home/username/ is the same as ~/.

Any folder that begins with a "." like .thumbnails means it's a hidden folder. An "ls -al" in console or selecting "Show Hidden Folders" in nautilus will show them. Most user preferences are stored in the user's home folder in a hidden folder.

---

### Post by s.fox on 2008-07-04
Thank you so much!  I would never have realized that the . means hidden :)

Final question, why don't i have a preview of the png's when viewing the contents of the folder?  


Once again thanks to all.

---

### Post by silkstone on 2008-07-04
That's a good question! There used to be a preview in Ubuntu 7.04, but I noticed it was missing in Hardy. It could be because the .thumbnails folder can end up with thousands of files, and preview generation would be very slow.

It's quite a good idea to clear it out every so often - the /normal folder can get huge and take up a lot of space. You own the files so you can delete them from Nautilus (or gnome-commander if you have that installed). The thumbnails will be recreated when you next view an image folder, but obviously that will take a little time.

So... if you're happy to get rid of the thumbnail files that are there at the moment, you can delete them, then look at the files you want thumbnails of, and they should then be the only ones in the thumbnails folder.

---

### Post by s.fox on 2008-07-05
Ok, thanks for the heads up.  I will keep an eye on the size of that folder.

You may be interested to know that you do get a preview of the png if you open it with image viewer. Its just something I noticed after I managed to find all the thumbnails I was looking for.

Again thank you so much.

---

