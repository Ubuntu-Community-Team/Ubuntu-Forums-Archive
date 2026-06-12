---
title: "[SOLVED] Installing build-essentials"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by getitright on 2008-09-20
Hi,

I have a hole in my bucket situation. Having installed Ubuntu on an old laptop that needs Ndiswrapper and Windows driver for the wireless card to be installed, I am told that installation of build-essentials is a prerequisite. Trying to install build-essentials I am informed that on line access is required, however this needs the wireless card to be operational! 

Is there an alternative way of installing build-essentials?

---

### Post by quinnten83 on 2008-09-20
you don't have a wired port on your router?
How are you posting the forum now?

---

### Post by bhadotia on 2008-09-20
Build essential comes with the ubuntu cd. Well you will require build essential if you want to install ndiswrapper. And actually build-essential is a meta package the actually installs a collection of compliers and related packages as dependencies.

And to install it from the CD go to System>Administration>Software Sources and check the box next to ubuntu cd in the first tab. Close the window and reload.

Then open the terminal (Applications>Accessories>Terminal) and paste thew following command:
 sudo apt-get install build-essential

Then you can download the Ndisgtk and ndiswrapper packages (along with dependencies) from a computer having the net connection and manually install it.

---

### Post by Shazaam on 2008-09-20
```
build-essential
```
no S on the end. :)

---

### Post by bhadotia on 2008-09-20
> **Shazaam said:**
> ```
build-essential
```
no S on the end. :)
Oh yeah :popcorn:
Thanks:)

---

### Post by getitright on 2008-09-20
Bhadotia. Tried your solution everything went well until I tried to install build-essential. Following a message informing me of the size of the installation I was asked if I wished to proceed to which I entered Y.

I then got the following in the Terminal window:

"Media Change: Please insert the disc labelled
'Ubuntu 8.04 Hardy Heron -Release i386 (20080423)
in the drive '/cd rom/' and press enter"

Inserted the disc and pressed enter and the same request appeared, as it did each time enter was pressed.

Any thoughts?

---

### Post by anewguy on 2008-09-20
If all you are doing is getting your wireless to work, you don't need build-essential, as you don't need to compile anything.

Boot up your Linux, put in the LiveCD you installed from, and then open the CD under the "places" menu.  Navigate to /pool/main/n/ndiswrapper and install the 2 packages listed simply by double-clicking on each.

Once installed, you can then start using ndiswrapper to install your Windows XP driver for your wireless.

Also, you may want to download/transfer to your Linux box the ndisgtk package since it is a gui'd interface to ndiswrapper and may make things easier for you.

Dave :)

---

### Post by getitright on 2008-09-21
anewguy great advice, have now installed ndiswrapper. What part does ndis gtk play in the installation of the windows driver?

---

### Post by anewguy on 2008-09-21
> **getitright said:**
> anewguy great advice, have now installed ndiswrapper. What part does ndis gtk play in the installation of the windows driver?


ndisgtk is a gui'd front-end to ndiswrapper.  It will allow you to do everything in a window rather than using the command line to work with ndiswrapper.



Dave :)

---

### Post by getitright on 2008-09-21
anewguy, thanks. I followed your advice and installed the Windows driver using ndisgtk. Everything appeared to go OK. Using command line


'ndiswrapper -l' 

got back the information that the Driver had been installed OK. I the proceeded to load the module using command lines:

'sudo depmode -a

sudo modprobe ndiswrapper'

and got the display 'FATAL. Module ndiswrapper not found'

I know that this is straying away from my original query but have you any advice before I instigate a new thread?

---

### Post by anewguy on 2008-09-21
Not sure why it would say that unless it was a miss spelling.  If the ndiswrapper command works and shows the driver, I would edit the /etc/modules file and add a new line that says ndiswrapper to it, then save, exit, and reboot.  Then check under network manager and see if your wireless networks are being detected.

Dave :)

---

### Post by getitright on 2008-09-22
anewguy. I have looked in Places and cannot see a modules folder in /etc..

---

### Post by bhadotia on 2008-09-22
> **getitright said:**
> anewguy. I have looked in Places and cannot see a modules folder in /etc..
It is not a folder its a file.

You can use the 'lsmod' command to find out which modules are loaded at present in your computer.

Which how-to are you following and what Wi-fi card do you have? This information  might be helpful in solving the problem.

Abhishek.

---

### Post by getitright on 2008-09-22
anewguy. Omitted to say that I had added ndiswrapper to /etc/modules in the Terminal. Still no joy.

---

### Post by bhadotia on 2008-09-22
> **anewguy said:**
> Not sure why it would say that unless it was a miss spelling.  If the ndiswrapper command works and shows the driver, I would edit the /etc/modules file and add a new line that says ndiswrapper to it, then save, exit, and reboot.  Then check under network manager and see if your wireless networks are being detected.

Dave :)

> **getitright said:**
> anewguy. Omitted to say that I had added ndiswrapper to /etc/modules in the Terminal. Still no joy.


Have you tried restarting the computer?
> **bhadotia said:**
> It is not a folder its a file.

You can use the 'lsmod' command to find out which modules are loaded at present in your computer.

Which how-to are you following and what Wi-fi card do you have? This information  might be helpful in solving the problem.

Abhishek.

What is your NIC (post output of lshw -C network)and which how to (please post the link) are you following?

---

