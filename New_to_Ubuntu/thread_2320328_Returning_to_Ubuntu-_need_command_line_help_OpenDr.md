---
title: "Returning to Ubuntu- need command line help OpenDroneMap"
date: 2016-04-12
forum: New to Ubuntu
---

### Post by luckystar3 on 2016-04-12
Hello all,
I first used ubuntu at 7.04 for a few years before university required me to use win 7. Im using Ubuntu now in a vm and and trying to use a program called open Drone Map. Can anyone tell me how I would accomplish the following? (In bold)

"To run OpenDroneMap on your images** move to a directory of images** and run the following command:

  ../OpenDroneMap/run.py
"

---

### Post by yancek on 2016-04-12
It is telling you to change directories to wherever you have the images.  Use the cd command. Open a termina and if the images are in /home/user/images just:  cd /home/user/images.

---

### Post by Impavidus on 2016-04-13
Going to a directory with images *anywhere* on your system and then running a command using a relative path doesn't make sense. You need an absolute path to that python script (as I assume it is) or put it somewhere in your path and run it as a regular command.

---

### Post by buzzingrobot on 2016-04-13
The example shown on the Github page ([https://github.com/OpenDroneMap/OpenDroneMap](https://github.com/OpenDroneMap/OpenDroneMap)) is
> 
From a directory full of your images, run

  ./run.py


This says, in effect, "look in the current directory for run.py and if it is there, execute it."

"../run.py" amounts to, "look in the directory one level up in the hierarchy for run.py and if it is there, execute it."

Of course, if run.py is not in those specific directories, this won't work.

...which is unusual because typically a script would be installed in one of the standard directories on the system's Path. So a user would enter whatever directory holds images and execute "run.py".

---

### Post by luckystar3 on 2016-04-17
Thanks for the help everyone. Its been a few years since I last used Ubuntu and am glad to be back using it.

---

