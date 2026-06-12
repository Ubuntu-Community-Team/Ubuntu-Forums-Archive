---
title: "how do i delete downloads?"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by natedogg23 on 2008-09-22
things like mpgs and movies i dl are always there and i cant find a way to get rid of them.

---

### Post by ibuclaw on 2008-09-22
What program are you using to download them ?

Can you be a little more specific.
Are you getting error messages when you try to delete them? Or is it that you just don't know where they are?

Regards
Iain

---

### Post by oldos2er on 2008-09-22
Right-click on a file, move to trash.

---

### Post by natedogg23 on 2008-09-22
some are from bit torrent not sure about the others. whatever the default is i guess. i dont know where to find them either. the new stuff im getting im opening with bit torrent instead of saving because i dont know where there being saved to

---

### Post by natedogg23 on 2008-09-22
> **oldos2er said:**
> Right-click on a file, move to trash.

there not on the desktop. theyre in recently used if i open them from a playlist from totem and i cant do anything with them from there except open them

---

### Post by ibuclaw on 2008-09-22
You will most likely find them in the top of your /home folder then.

This is "**Places->Home Folder**" in the Ubuntu Menu.

If you can't immediately see it, try searching for the files using the search app. ( "**Places->Search For Files...**" )
Type in a keyword of the file.

Once you find them, deleting them is a simple click and press the Delete key.

Then empty your Trash Folder once you are done. Though, always check that what is in there is right first ;)

Regards
Iain

---

### Post by natedogg23 on 2008-09-22
theyre no there thats why im having trouble

---

### Post by garyed on 2008-09-22
If you know part of the names or extensions you could use the find command.
```
 find / -iname '*.mp3' 
```

You could redirect it to a text file so you could open it in like gedit & go through it.

```
 find / -iname '*.mp3'> findme 
```

---

### Post by misswham on 2008-09-22
If your files are in a folder look to see if the folder has a padlock over it and if it does right click on the folder and go to properties then permissions and look for the tab that says folder access and change it to  create and delete files then u should be able to if that is the problem.

---

### Post by cariboo on 2008-09-22
Most bittorrent (all) programs have a default directory they download to. Have you checked edit-->preferences to see what the default directory is?

If you haven't set a directory to download to, maybe it is time to set one so that you don't run into these problems again.

Jim

---

### Post by lovinglinux on 2008-09-22
Open your BitTorrent client go to "Preferences" or anything like that and look where the client is saving your files. Copy the path and paste it the File Browser.

Open Firefox and look for any download extension, go to the extension properties and look were they are saving files. Copy the path and paste it the File Browser.

---

### Post by natedogg23 on 2008-09-24
would they be internet files or something? i dont know how to get to those either but some buffer when i play them. do internet files get deleted when u clear private data?

---

### Post by lovinglinux on 2008-09-24
> **natedogg23 said:**
> would they be internet files or something? i dont know how to get to those either but some buffer when i play them. do internet files get deleted when u clear private data?

Not necessarily. Sometimes a download extension has the cache folder as default download directory, but usually when you actively download something it is saved somewhere else.

> **natedogg23 said:**
> i dont know how to get to those either but some buffer when i play them. do internet files get deleted when u clear private data?

Where are you clicking to start playing these files?

Temporary Internet files are place under ~/.mozilla/firefox/*profilename*/Cache. I don't remember if the default Firefox setup is configured to delete temporary Internet files, but I guess it should be. Anyways, you can check this in [ Edit > Preferences > Privacy > Private Data]. Select the option "Always clear my private data when I close Firefox", then click the "Settings" button and select cache option.

---

### Post by natedogg23 on 2008-09-24
i can open them in totem but they buffer a few times

---

