---
title: "RealPlayer11"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by silverjohnlong on 2008-05-10
Where can i get hold of RealPlayer11? Can't find it in Synaptic?

---

### Post by Malta paul on 2008-05-10
Hi, [http://www.real.com/linux](http://www.real.com/linux)

---

### Post by silverjohnlong on 2008-05-10
Thanks for the link Paul but would i have to open a terminal and try to install it from there?

---

### Post by lswest on 2008-05-10
> **silverjohnlong said:**
> Thanks for the link Paul but would i have to open a terminal and try to install it from there?

No, real offers .bin files for download (to the best of my knowledge) and so just right-click, under the permissions tab choose to "allow executing" bit, then just type ```
cd /path/to/file
./RealPlayer11GOLD.bin
``` to start the installer, and then it should prompt you for required steps.

---

### Post by Malta paul on 2008-05-10
Me again, If you are not happy converting a .Bin file, Download the RedHat Package which is an .rpm file and convert to a .deb file using 'Alien' this will work OK for you.
Have fun:)

If you need help with alien post again.

---

### Post by silverjohnlong on 2008-05-10
Thanks for the replies both but i am a linux newbie and don't honestly understand all this ".bin" and "permissions" thingies, so i think i'll give it a miss. Only wanted to listen to the UK football play offs.

---

### Post by sdowney717 on 2008-05-10
use mplayer and mplayer plugin for firefox
mplayer is in synaptic package manager.

a '.bin' file when you download it does not have run permissions.
so right clicking it, goto properties, and saying it can execute as a progtam allows it to tun.
You can then right click the file icon and select open, a dialog comes up and select run in terminal, that will start the install.

actually, i used to be able to do that, but when I try, it opens VLC player. Now how did VLC player get associated with .bin files?

I like '.deb' files better since the package manager keeps track of them.
.bin files get installed and I see no easy way to uninstall them.

put up your media link and we can see if it plays.

---

### Post by Malta paul on 2008-05-10
Hi, I know what you feel, don't give up if you want to use Realplayer then lets install, its not rarely hard.

Go to Applications>Accessories>Terminal. As we have to install Alien.
Just type in or copy this:> sudo apt-get install alien < and enter, it will now ask for your password. then press again and Alien is now installed.

Now go to [http://www.real.com/linux](http://www.real.com/linux),> RedHat Packages < and down load to your desktop. You will notice the file has a .rpm extension.

Go again to the Terminal enter: >Sudo alien < and drag the .rpm file to the end of alien (leave a space) hit enter and in the desktop you will see another file the same name but with a .deb extension.

Click on this file and it will now install with Gdebi package installer.

That All there is to it, Have fun:)

---

### Post by SilverOne on 2008-05-10
> **Malta paul said:**
> Hi, I know what you feel, don't give up if you want to use Realplayer then lets install, its not rarely hard.

Go to Applications>Accessories>Terminal. As we have to install Alien.
Just type in or copy this:> sudo apt-get install alien < and enter, it will now ask for your password. then press again and Alien is now installed.

Now go to [http://www.real.com/linux](http://www.real.com/linux),> RedHat Packages < and down load to your desktop. You will notice the file has a .rpm extension.

Go again to the Terminal enter: >Sudo alien < and drag the .rpm file to the end of alien (leave a space) hit enter and in the desktop you will see another file the same name but with a .deb extension.

Click on this file and it will now install with Gdebi package installer.

That All there is to it, Have fun:)

i have tried to follow the steps, but when i put the file on the terminal after pressing enter... it says  " permission denied " any ideas ?

thanks ! 

Best Regards.

NEVERMIND it worked ! thankx... more 1 to your post ! -

---

### Post by SunnyRabbiera on 2008-05-10
or if you really wanted to you could have used the installer deb found in this topic:
[here]("http://ubuntuforums.org/showthread.php?p=4737528")

---

