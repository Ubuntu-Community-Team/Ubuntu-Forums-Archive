---
title: "How to Update Blender to newest release?"
date: 2013-10-23
forum: New to Ubuntu
---

### Post by T_Giegler on 2013-10-23
Why does ubuntu software center not install the latest stable edition of blender modeling software?
I have a new computer and am using Ubuntu 64 bit on it. I am not sure what release of Ubuntu I have. I installed Blender from the Software Center and release 6.2 was installed. I want to use some tools that are not available in 6.2. Blender.org sais that the latest stable release is 6.8. I downloaded the .zip file and unzipped it. I can run Blender 6.8 by double clicking on the icon named Blender inside the unzipped folder. However, the application icon on the Launcher and in dash home still opens the 6.2 release. 
Does anyone have a solution for this?
Thank you,
TG

Sorry it is version 2.62 installed with Software center and 2.68 is the latest stable version. My Ubuntu version is 12.4 LTS.

---

### Post by T_Giegler on 2013-10-23
Sorry it is version 2.62 installed with Software center and 2.68 is the latest stable version.

---

### Post by monkeybrain20122 on 2013-10-23
Blender doesn't need installation. Just download the tarball or zip file from blender and unzip it and click the binary, that's it. Not sure what is the advantage of installing from the repository.

---

### Post by T_Giegler on 2013-10-24
> **monkeybrain20122 said:**
> Blender doesn't need installation. Just download the tarball or zip file from blender and unzip it and click the binary, that's it. Not sure what is the advantage of installing from the repository.

I want to be able to access it from the launch bar or dash home.

---

### Post by monkeybrain20122 on 2013-10-24
> **T_Giegler said:**
> I want to be able to access it from the launch bar or dash home.

You can create a .desktop file and then put it in .local/share/applications (which is a hidden folder in your home directory, open nautilus (the file manager) and press ctr+H or on the drop down.-- the "v" ,-- check "show hidden file" 

Here is a simple .desktop file 
```
[Desktop Entry]
Type=Application
Terminal=false
Icon=/home/uesrname/blender/icons/256x256/apps/blender.png
Exec=/home/username/blender/blender
Name=blender
Categories=Graphics;

```
Open gedit and copy these lines , change "/home/username/blender" to the path where you unzipped the blender folder (It has name like blender-2.6.8-linux.. I renamed it to blender so when there is an update I don't need to change my desktop file, just delete the old one, unzip the new one and rename). Now save it as  something like "blender.desktop" (no quotations)

Remember, after you have made the desktop file, right click it, choose properties and make it executable.

Now put it in .local/share/applications as described earlier, then you will see the launcher in the dash and you can drag and drop it from the dash to the side bar. Sometimes you may need to logout and login for it to show up in the dash, but probably not.

---

### Post by T_Giegler on 2013-10-25
\\:D/ Thank you that worked.I put it in a folder under my home in case I need to do this with other applications. I had to restart to see it in the dash. I named it something other than just blender.desktop to be able to differenciate between it and the one the software center installed. Named the file blendstable.desktop as well as inside the file changed to name=blendstable. I have been told by someone from blender that two versions can run just fine. Saves alot of time. I don't have to go find the folder and remember wich file is the exe. Also your idea to simplify the name of the folder is great.  I can use the same .desktop when I get the latest version and just rename the folder when I unzip it. I found that if I try locking it to the launchbar it reverts to the old  version on the next start. I will be useing it often enough that it  should stay in the reciently used on the dash. Two clicks insted of just one is fine with me. If it has been a while, I can always find it fast by just typing bl into the dash and it comes up.   :cool:  

[Desktop Entry]
Type=Application
Terminal=false
Icon=/home/uesrname/Programs/blender/icons/256x256/apps/blender.png
Exec=/home/username/Programs/blender/blender
Name=blendstable
Categories=Graphics;

---

