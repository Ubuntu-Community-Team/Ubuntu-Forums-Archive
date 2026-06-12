---
title: "Wine and the registry"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by its_jon on 2008-09-12
I have some apps which appear to need stuff from the registry (i think)

I assume I have to copy the registry over somehow into the wine installation as well as the app itself.....

If this is so, I don't know what im looking for yet......

sys32 ? maybe

thanks
john
Scotland

---

### Post by ronnielsen1 on 2008-09-12
What are you trying to run and what errors are you getting?

---

### Post by its_jon on 2008-09-12
Sibelius notation software (like rosegarden)

-serial number is invalid please reinstall sibelius-

---

### Post by gvartser on 2008-09-12
then you need to export the registry key in windows.

regedit -> browse your way to the key: "[HKEY_LOCAL_MACHINE]\[SOFTWARE]\[<etc>]" not sure about the path there.
- *OR press "F2" to search for the application name to find the serial key.*

Then select the key and export it to an .reg file.

This file you then should be able "I think" to import into the wine registry: 

Example:
```
wine <registry_file>.reg 
```

/g

---

### Post by its_jon on 2008-09-12
you lost me at regedit ->

can I do this from Linux or do I have to boot into windows ?

can I not simply copy over the registry wherever it is into wine ?

---

### Post by gvartser on 2008-09-12
No i do not think a copy of the registry will work.

Regedit is run:ed from the windows OS to export the keys you need for your application. Then you need to bring the exported ".reg" file to your Ubuntu machine and import it using wine.

/g

---

### Post by its_jon on 2008-09-12
thanks

---

### Post by Elephantman5 on 2008-09-12
Yeah. Make sure the application you want to run is successfully installed on another OS (Just do this all in Vmware through Linux) and find the key the error is referring to, then extract and copy over.
Or make it easy and just copy the whole windows directory from a windows installation to your .wine/c drive in home folder

---

### Post by its_jon on 2008-09-12
I went for the easy option and copied the widows dior over to the wine-c drive folder..... still get the same error

copied one or two regged proggies over to the wine/programs folder and get similar errors.

Plus the wine reg tool has dissapeared now. guess it was overwritten when I copied over the windows folder.

---

### Post by Elephantman5 on 2008-09-12
> **its_jon said:**
> I went for the easy option and copied the widows dior over to the wine-c drive folder..... still get the same error

copied one or two regged proggies over to the wine/programs folder and get similar errors.

Plus the wine reg tool has dissapeared now. guess it was overwritten when I copied over the windows folder.
Yeh, well the wine reg tool shouldn't really matter.
So windows version works. Cool. Install Mono in synaptic, get all the libraries related, that look important. (You'll see what I'm talking about, Microsoft libraries etc.)

And then, reinstall Wine, (after deleting (keep windows dir from copy) the origional config files, to make a clean slate.)
Then when all that's done, update, restart, reinstall wine, copy the dir over, but only system 32 and the program files from the native windows installation.

---
If none of this works, I suggest you get Crossover at your friendly torrent site.

---

### Post by its_jon on 2008-09-12
Lots and lots of mono stuff already installed ????

---

