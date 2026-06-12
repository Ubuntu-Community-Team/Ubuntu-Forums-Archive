---
title: "Automate driver install"
date: 2010-07-02
forum: Programming Talk
---

### Post by Pithikos on 2010-07-02
Hi!

I have currently installed Ubuntu at my mom's computer and as I will move back to my studentapartment after summer I am a bit afraid of what happens if something goes wrong with her installation. My biggest concern is the wifi driver that is not a part of Ubuntu(none of Ubuntus modules could make the card function properly), so I had to install as a third party driver. Recently the kernel of the Ubuntu installation got updated and I had to install the wifi driver again. Is it normal that you have to do like that every time the kernel updates?

Anyway I was looking for some help in automating the installation of the driver with just one click(just like .exe in Windows). So in case if the wifi card doesn't work she will be able to install/reinstall the driver from an icon on the desktop or something similar. Currently I am taking a summer course in python and as python is implemented in Ubuntu I was wondering if it can be done with it and how. Or is there some easier alternative? I am not a proff but I am learning. The commands I want in the script are just some make/make install/cd/cp/reboot. Cheers!

---

### Post by ju2wheels on 2010-07-02
A bash script would probably be best, you can take the same commands you are already using to recompile the drivers and throw them in a bash script without modification almost with the exception of a little flow control.

---

### Post by soltanis on 2010-07-02
Yeah on Fedora there was a system called akmod which would check to make sure you had a driver compiled against your latest kernel, and if you didn't it would go ahead and compile it on the fly for you. My Googling around doesn't seem to find a similar solution for Ubuntu (sad, really). However I am pretty sure you should be able to automate building as the above poster said.

akmods would recompile every time there was an update to the kernel. So, you could write a script that runs on boot that performs the same process (obviously it will slow down booting when it does compile). You could achieve this by adding a script to */etc/rc5.d/* that 1) checks the current module to see which kernel it was compiled for, 2) checks the current kernel (use **uname(1)**) and then 3) optionally compiles and then inserts the module into the kernel.

Read online on how to properly write init scripts or just look in that directory for some examples.

---

### Post by ju2wheels on 2010-07-02
DKMS is the new way of doing what soltanis is referring to btw...

---

### Post by Pithikos on 2010-10-11
well I forgot to subscribe to this so didn't get the feedback in time. Since then I have learned some bash scripting and I feel really amazed by the power and flexibility it gives! I recently ran into some crashing problems and in 5 minutes I had already a script to log what I wanted and solve my problem.

Haven't tryied DKMS but that looks promising though a bit more complicated. Thanks for the answers anyhow :guitar:

I also noticed that Ubuntu ships with DKMS already in but still didn't make much sense of it. Will probably need some deeper linux-knowledge to get into that.

---

### Post by cgroza on 2010-10-11
You can do it with the os library. Just create an executable .py file:

import os
os.system("command")

Hope it helps.
PS: The command must be in "" so it takes it as a string not variable, but you knew that already.

---

