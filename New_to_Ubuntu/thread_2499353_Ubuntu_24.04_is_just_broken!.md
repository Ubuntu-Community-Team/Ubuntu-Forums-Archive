---
title: "Ubuntu 24.04 is just broken!"
date: 2024-07-23
forum: New to Ubuntu
---

### Post by guitronimo on 2024-07-23
Hi all, 

before i cause a rant...

Anyone else saying 24.04 is just borken? 

Its not that i was giving up quickly... But after having trouble installing Ubuntu Server 24.04 for a simple NAS, i tried Ubuntu 24.04 Deskotp (after MONTHS) and still ran into completely idiotic things like: 
"Your Installer needs an update" up to "We are sorry, we cannot render the icons in your Gnome correclty". 

Whats going on?! And yes... I have tried various differnt Computer gens up to 13th gen Intel here - staring from 3th gen... 

Kind regards! Honestly!

PS: Not a newbie here... I know how to fix stuff - i mean google does - but just WHY?! 

Repair this please.... 24.04 is worst Linux ever made.... cmon, we were commandline ninjas before... we dont need new challenges...

---

### Post by Tadaen_Sylvermane on 2024-07-23
I'd first off have to say from my own experience where did you get this download from? This stuff simply doesn't happen in my experience, rather 24.04 has been ridiculously reliable for me the past couple months. My server was also put on 24.04 via chroot installation 3 months ago, no trouble whatsoever. Hell I've never even heard of errors like this. If it's an official download then you should check the hash. This is not remotely like my experiences, or really anyone else in my Linux circles.

---

### Post by Rubi1200 on 2024-07-24
You only mention two "problems".

1. I have seen the message about there being an update for the installer. You can choose to ignore it and continue or let it download the latest version. Either way, it should not prevent installation or cause issues from my experience

2. As far as icon rendering, have you tried going to Appearance and selecting a different theme? Did it make a difference?

Are there other issues?

---

### Post by ActionParsnip on 2024-07-24
Why a desktop OS for a NAS? Its a server feature. You don't need the GUI here.....

---

### Post by spufidoo2 on 2024-10-03
I've just upgraded to 24.04, and although the OS itself isn't broken, practically every Python program I have written is. NOT ONE of the external (think "pip install...") libraries I need have worked, and the only way I have managed to install them successfully is to "pip install <package name> --break-system-packages"

Also, my IBM Db2 instance has broken - it won't even start:
db2start: error while loading shared libraries: libaio.so.1: cannot open shared object file: No such file or directory

I installed libaio, using sudo apt-get install libaio1t64 libaio-dev, but nothing has changed.

---

### Post by mrdc76 on 2024-10-06
Are you using the system provided version of Python? If you are, it was also upgraded, which potentially breaks things. Use pyenv to install Python versions for programming and pipenv to create environments for each project.

---

