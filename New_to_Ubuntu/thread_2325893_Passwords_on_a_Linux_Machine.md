---
title: "Passwords on a Linux Machine"
date: 2016-05-26
forum: New to Ubuntu
---

### Post by bob177 on 2016-05-26
I recently purchased a new Dell Computer running Ubuntu. I hooked up the machine and turned it on. The computer ran some installation script and created an account for myself. I then tried to login using the account but it would not let me login in. It would let me login in as guest. However, as guest, I could not create a new account. I then tried booting the machine holding down the shift key hoping to get a Linux shell as root. That did not work. I then called Dell who told me there Linux expert would call me back in 24 to 48 hours. I did not like the answer so I returned the machine.

I am wondering if I did anything wrong. Was the machine defective? 

Bob

---

### Post by pfeiffep on 2016-05-26
From your description I think there are 2 possibilities
- you missed a prompt about password when the script created your account
- the script is defective in some way

---

### Post by bob177 on 2016-05-26
Pete,

Thanks for the response. I am planning on buying a new machine. What steps should I think about doing next time to avoid this problem?

Bob

---

### Post by grahammechanical on 2016-05-26
Machines that come with Ubuntu pre-installed will have what is called an OEM install of Ubuntu. It will have a user name & password chosen by the Original Equipment Manufacturer. The first time that Ubuntu loads we should be given the opportunity to set our location, keyboard, user name & password. See the very end of this wiki page.

> Once the computer was shipped to the end user and he finally boots for  the first time he will be taken to the system setup wizard where he will  be able to set his location, keyboard layout, user name etc.

[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)

Retailers like Dell should provide instruction manuals.

Regards.

---

### Post by SeijiSensei on 2016-05-26
Buy a machine with Windows and install Ubuntu yourself from a [DVD image]("http://cdimage.ubuntu.com/releases/16.04/release/") in a "[dual-boot]("https://www.google.com/search?q=ubuntu.com+dual-boot+install+16.04")" arrangement.  Alternatively install [VirtualBox]("http://www.virtualbox.org/") for Windows, create a "virtual machine," and install Ubuntu into that.

---

### Post by Geoffrey_Arndt on 2016-05-26
Unless a person is a PC-Techie "enthusiast" (in Windows terms . . . a Power User) . . . then (by far) the easiest way to get an Ubuntu machine is to get it preloaded.   

 The odds of a Dell install/OEM script being corrupt is "**very**" unlikely (the scripts come from a master file)  - - so the key thing to prevent this issue from re-occuring is to pay very close attention to the install screens (all 4 or 5 of them) and write down the user name and password.

---

### Post by Mark Phelps on 2016-05-26
While I would agree that buying a new PC with Windows installed (and most likely, this is going to be Win10 these days) is an option, for those unwilling to struggle with the impediments that Microsoft and OEM providers put in place to prevent installing an OS, the much better option is to buy a PC with Ubuntu already installed.

This provides not only a PC that works in Ubuntu, with all the right drivers preloaded, it also prevents the problem of unasked for Win10 Updates suddenly trashing the Ubuntu install -- as does happen from time to time.

---

### Post by buzzingrobot on 2016-05-26
> **bob177 said:**
> 

 Was the machine defective? 

Bob

Almost certainly not. Chances are you didn't type what you thought you were typing when you created your account via that script.

If you buy another preloaded Linux machine, it will have a similar first-use script to set up your account. 

If you buy a new machine with Windows on it *and* want to replace Windows entirely with Ubuntu, it really isn't that difficult.  The installer will happily erase everything on the disk and replace it with Ubuntu. Take a look at this and see what you think: [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop).  Follow the links on that page for guidance on installing Ubuntu.

Preloaded, though, should eliminate concerns about hardware compatibility and driver availability that can sometimes pop up when someone buys the very newest hardware for their Linux installation.

---

### Post by RobGoss on 2016-05-26
I don't think there's anything easier then buying a machine preloaded with Ubuntu the fact that you could not login was by trial and error, you'll be a step ahead on your next purchase

---

### Post by pfeiffep on 2016-05-26
Not having experience with pre-loaded Ubuntu I'm guessing here.

There's a step in the Ubuntu install procedure that requires the installer to enter a userid and a password ... additionally there's a choice to automatically login. 

My "advice" don't get overexcited with a new machine, insure you have a block of time to read the screens that pop up when you first power on, if offered the chance to enter a password keep it to one that you won't forget, you can change it after you've insured the machine is working to your satisfaction. Take a look at the[ Ubuntu install guide]("http://www.ubuntu.com/download/desktop/install-ubuntu-desktop") prior to powering up - start about step #5

---

