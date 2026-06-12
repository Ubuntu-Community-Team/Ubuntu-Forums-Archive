---
title: "How do I exit the X server, terminate all OpenGL applications, etc...?"
date: 2014-01-05
forum: New to Ubuntu
---

### Post by tessawong on 2014-01-05
I wish to install NVIDIA-Linux-x86_64-331.20.run on Ubuntu 12.04.3 LTS (x64)

I was reading the article (URL is [http://us.download.nvidia.com/XFree86/Linux-x86_64/331.20/README/installdriver.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/331.20/README/installdriver.html)) and hope that someone show me how to do the following:

1. Exit the X server
2. Terminate all OpenGL applications
3. Ensure that all OpenGL applications have exited
4. Set the default run level such that it will boot to a VGA console
5. Disable the Nouveau driver

I am new to Linux; hence some handholding would be helpful.

---

### Post by monkeybrain20122 on 2014-01-05
You don't need to install the .run file from Nvidia. As I answered in your other thread. Use the xswat ppa
Open the terminal
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvida-331 ppa-purge
```

Then

```
sudo nvidia-xconfig
```

Then reboot. 

 ppa-purge is installed just in case something goes wrong you can use it to remove the ppa and downgrade the packages, but don't worry about it atm.

**EDITED: HOLD IT!!!! **I noticed that you are using 12.04.3 so you are using the raring graphic stack and there may be issues using the ppa. Better wait a bit before you do anything..

Saw this in the xorg-edgers ppa, not sure if it applies to x-swat as well
> WARNING: Do not use this PPA with the precise X backport stacks, aka if  you fresh install of 12.04.2 or newer. You can switch back to a  compatible one by installing xserver-xorg-lts-precise instead if you do want to use these packages but horrible things will happen if you don't.


---

### Post by oldos2er on 2014-01-05
No need to do any of those things. Open Software Center, Software Sources, Additional Drivers tab.

---

### Post by deadflowr on 2014-01-05
> **oldos2er said:**
> No need to do any of those things. Open Software Center, Software Sources, Additional Drivers tab.

Not in 12.04.
In 12.04, just open the dash and search for additional drivers.
It moved to the software sources after Precise.

nvidia-319 is the latest available on Precise through the repos method.
I have no idea what's going on with 12.04.3 and the xswat ppa.

+1 to installing from the repos over installing the run file from nvidia, too many problems crop up when installing from the downloaded file.(Not to mention the arcane way you have to actually install it.)

But in all fairness to the OP
To kill X move to a console(ctrl +alt+F1)
login, enter you password and then run
```
sudo service lightdm stop
```
this will kill X and all the goodies the run on it(ie, opengl stuffs)
Then you'd want to move into the Downloads folder and run the commands you should already have written down to install the file.
After you install the file, either run a reboot(simply type  sudo reboot), or change the stop in the above command to start.

---

### Post by oldos2er on 2014-01-05
Thanks deadflowr.

---

### Post by Yellow Pasque on 2014-01-06
If you absolutely insist on using the .run file, make sure you have dkms installed, or the next kernel upgrade won't be pleasant..

---

