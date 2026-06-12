---
title: "Real Player Installation"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by groeswenphil on 2008-05-25
Hi group.
I've downloaded Real Player.
How do I install it?
It's sitting on my desktop....and I know that I've got to set my terminal so that it reads the files on the desktop.
Remind me how to do that.
Yhanks,
Phil

---

### Post by t0p on 2008-05-25
So what kind of file is it? A .deb?  A .tar.gz archive?

To access files on your Desktop with terminal you need to open terminal and type:
```
cd Desktop
```
Next type
```
ls
```
and you'll get a list of the contents of your Desktop.
If you post that list, I might be able to help you further.

---

### Post by drs305 on 2008-05-25
This is my entry from an earlier post:

There may be better options, but if you really want realplayer 11, you can download it from here: [http://www.real.com/linux](http://www.real.com/linux)

Personally, I would wait for some better recommendations for whatever you want to use it for.

If you still want RealPlayer 11, what you will download is a .bin file. If you do install it, keep the folder Realplayer that is created once you are finished. The reason is that bin files install programs outside synaptic and apt-get/aptitude and cannot be uninstalled via those means. Inside the Realplayer folder are the uninstall scripts that won't be available should you delete that folder after installation.

That post is here: [http://ubuntuforums.org/showthread.php?t=806680](http://ubuntuforums.org/showthread.php?t=806680)

But, if I recall, you would change into the folder with the bin file. Then:
```
chmod a+x RealPlayer11GOLD.bin
```
This will turn the file's icon into a blue diamond.

Then in terminal to start the installation:
```
./RealPlayer11GOLD.bin
```

Don't forget to save the Realplayer folder created during the install so you can run the .postuninst.sh script to uninstall it should you decide to do so. Uninstall won't be available with synaptic or apt-get/aptitude.

---

### Post by groeswenphil on 2008-05-25
Thanks..........that worked. I suppose moving the files is OK?
Phil

---

### Post by drs305 on 2008-05-25
> **groeswenphil said:**
> Thanks..........that worked. I suppose moving the files is OK?
Phil

Yes. I moved mine to a backup folder. You may have to put it back in the original location for the uninstall script to work properly.

---

