---
title: "random logs me out"
date: 2012-05-15
forum: New to Ubuntu
---

### Post by hktrout on 2012-05-15
Hi,

I am currently using Ubuntu 12.04 64bit. 
For some reasons, it randomly logs me out of the screen while I am on Internet or work on something with my computer. It happened about 4 to 5 times today. It happened about once or twice per day before, but now, it looks like it gives me more problems than it did before.. Could anyone helps me on this issue ?  I am not sure if this relates with the driver I installed recently.. but about a week ago, I installed the latest Nvidia driver and it seems like it is the cause of issue.. 

Thanks

---

### Post by ryantierp on 2012-05-15
Hi
Did it logg you out once or twice a day even before you installed the latest Nvidia driver?
When you are logged out, can you start a consol using "Ctrl + Alt + F2" ?

Br

---

### Post by Lisiano on 2012-05-15
Might I ask where you got the nvidia drivers? Did you get them from the ubuntu-x-swat PPA or from the ubuntu repositories? Or did you get them somewhere else?

---

### Post by hktrout on 2012-05-16
> **ryantierp said:**
> Hi
Did it logg you out once or twice a day even before you installed the latest Nvidia driver?
When you are logged out, can you start a consol using "Ctrl + Alt + F2" ?

Br

No. It never logged me out before I installed the Nvidia driver. Because I was just using 17 inch monitor,I didn't need to install Nvidia driver although Nvidia graphic card was already equipped in computer.. But I needed the latest driver after I connected my computer to 30 inch monitor.

Yes. I can start a console by pressing ctrl+alt+f2 from log out screen

Thank you

---

### Post by hktrout on 2012-05-16
> **Lisiano said:**
> Might I ask where you got the nvidia drivers? Did you get them from the ubuntu-x-swat PPA or from the ubuntu repositories? Or did you get them somewhere else?

Hi, I got followings code from google and just ran it.

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current

Thanks

---

### Post by Lisiano on 2012-05-16
That's the proper way to use the new nvidia drivers.
You could try using a newer driver (The new 302.07 beta driver). Maybe there is a bug in this one for your particular card.
For the new beta driver, refer here [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
I will not provide instructions on how to install it until you tell us you want to try it, note that it could become messy trying to get back to an older driver if you try the new one.

The driver might be even less stable than the current one or might be way better. It all depends on if you want to risk it.

But if you aren't that adventurous, you can boot using a LiveCD, download [this file](http://bazaar.launchpad.net/~xorg-edgers/xorg-server/xorg-pkg-tools/view/head:/xorg-edgers-live-test), place it somewhere you know (For example the home directory) then switch to a TTY (Ctrl+Alt+F1-F6) and type in ```
sudo service lightdm stop
sudo sh *~/xorg-edgers-live-test*
sudo apt-get install nvidia-graphics-drivers
sudo service lightdm start
```where the italic part is where the file is located, ~/ is a shortcut to Home.

---

### Post by Lightstar on 2012-05-16
I got the same problem with the 32bit version of 12.04.

I have no idea if nvidia is the cause for my problem since I only did a dist upgrade, nvidia was already installed from previous ubuntu 11.10.   It's really odd.

I had no problem with it on previous ubuntu.

---

### Post by euthydemus on 2012-05-17
I am having the same problem with 12.04AMD64. More concerning is that it doesn't recognize my chipset. If I go to Settings > Details it shows Graphics Unknown. I am using the updated nvidia driver now to see if that makes a difference.

---

