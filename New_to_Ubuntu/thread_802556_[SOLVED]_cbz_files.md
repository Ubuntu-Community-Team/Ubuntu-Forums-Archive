---
title: "[SOLVED] cbz files"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by rama76para on 2008-05-21
I was using evince to open/read my comic book collection which I have stored as .cbz files. When I would go to the folder with these files and look at them in icon view, i would be seeing the first image in the collection as the icon. Yesterday i decided to try the comix viewer. Did not like it and I uninstalled it. Now the cbz files are showing a generic icon and not the first image in the collection as they used to. is there a way to fix this?
I'm using ubuntu 8.04 on a compaq nc6220 laptop.

PS I'm new to these forums and so I post here. If there is a more appropriate place, please let me know that as well :)

---

### Post by Anduu on 2008-05-21
Comix probably "hijacked" the mimetype and seeing as it is no longer installed gnome doesn't know what to use to generate a thumbnail.

Right click on a .cbz and check the "Open with" tab and make sure Evince is set as the default application.If it is and you still aren't getting a thumbnail you can try deleting your home/<username>/.thumbnails directory so the thumbnail cache can be regenerated.

---

### Post by SunnyRabbiera on 2008-05-21
all a .cbz file is just a renamed zip file, you can just change the extension to .zip and it will work.

---

### Post by disturbedite on 2008-05-21
just a recommendation here for kde users.  okular (in kde4) supports the reading of comic book archives.  for a separate program geared directly at comic book reading, try qcomicbook.

---

### Post by rama76para on 2008-05-21
Re: Anduu. I will try deleting the thumbnail cache and see. evince already is set as the default app. :)

Re: SunnyRabbiera: Oh, I know that the cbz files are just zip files. I was just looking to get the icons show... that's all :) I kinda like previewing the cover.

Thanks all. I will update once I delete the thumbnails.

---

### Post by arsenic23 on 2008-05-21
If installing evince gave you the thumbnails, then comix replaced the script that evince installed.  When you uninstall comix it removed the thumbnail script and did not put the evince script back.

If you *[COLOR="DimGray"]apt-get remove evince --purge[/COLOR]* and reinstall it you should have your thumbnails back.  ( Though you may still need to purge your thumbnail directory as previously stated. )

---

### Post by rama76para on 2008-05-21
well... removing the thumbnails did not work.

when i try to remove evince, it wants to remove the package called "ubuntu-desktop" as well... is that advisable?

---

### Post by Anduu on 2008-05-21
> **rama76para said:**
> well... removing the thumbnails did not work.

when i try to remove evince, it wants to remove the package called "ubuntu-desktop" as well... is that advisable?

Removing ubuntu-desktop will not hurt anything...it is a meta package which means..well kinda hard for me to explain but when one installs ubuntu-desktop everything Ubuntu comes with is installed with it but it is not required to install Ubuntu...if that makes any sense :p

Try it out...uninstall evince then do sudo apt-get install ubuntu-desktop...it will reinstall evince automatically.

---

### Post by rama76para on 2008-05-21
okay that makes sense. 

Did that. Uninstalled and reinstalled evince/ubuntu-desktop. Everything still the same. no thumbnails for cbz files.

Edit: Just rebooted and everything is back to normal. Big thanks to everyone for your help and advice. :) :)

---

### Post by Anduu on 2008-05-21
Hrmmm...the next logical step would be to run gconf-editor and check evinces thumbnailer settings.Unfortunately I can't tell you what evinces default settings would be for .cbz files as I myself use comix which will have changed all that.

You can fish around in there for yourself to look for anything out of place.Just run gconf-editor and do a search for keys containing "thumbnail" no quotes and check the various values.

---

### Post by Anduu on 2008-05-21
Doh..it seems in the midst of typing my last post it all sorted itself out hehe.

Cool beans! :)

---

### Post by rama76para on 2008-05-21
now looking at the entries in the gconf-editor, it seems to me, i could have just reset the settings for application-cbz and just rebooted... I will try that out sometime :)

---

### Post by arsenic23 on 2008-05-21
Of course if nothing seems to work you could always just take the lazy man's fix and reinstall comix.  It would go back to thumbnailing things and you could just ignore that it is on your system.

---

