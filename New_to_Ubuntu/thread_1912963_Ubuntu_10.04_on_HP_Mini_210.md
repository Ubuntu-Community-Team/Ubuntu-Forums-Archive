---
title: "Ubuntu 10.04 on HP Mini 210"
date: 2012-01-21
forum: New to Ubuntu
---

### Post by tjbearpig on 2012-01-21
Just installed Ubuntu 10.04 on my HP Mini 210-1191NR, wiping out my Windows 7 OS in the process. I've been using Windows for too long and wanted to give Linux a shot. The installation went smoothly, but my drivers are now gone. I went to HP's website to download them, but they are .exe's. I found NDISWrapper, but that only accepts .inf's. I ran a test using Ubuntu's System Testing, my Network Controllers are "Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express", "Fast Ethernet controller (rev 02)", and "Broadcom Corporation Device (rev 01)".

So as of now, I can't connect my netbook to the Internet and I'm a total Linux/Ubuntu newbie... please help! :(

Thanks in advance!

---

### Post by Double.J on 2012-01-21
Hi there! welcome to the forums, we're really glad you're trying ubuntu!

Just to check, you're trying to add a broadcom driver for your wireless chip?

First things first - In ubuntu 90% of software you install comes from online repositories, or repos, especially for drivers, it is usually only in the case of problem graphics cards that you need to go to their site. Installing from the repos can be done in a number of ways, but the most common for new users is the software centre - to open it up click on the icon that looks like a shopping bag on the side panel.

You would have to be connected to the internet through a cable to your router.

In the software centre's serach box type "broadcom" and install the package(s) recommended for your chip [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") You'll have to restart to take effect.

While you're at it, press the windows key and type "additional drivers" then hit return to see if any proprietary drivers are needed on your system. :)

Hop it helps

---

### Post by holycow131415 on 2012-01-21
Hey, does your wired connection work? Try the additional drivers located in the menu of ubuntu.

[http://www.howtogeek.com/howto/17495/how-to-add-proprietary-drivers-to-ubuntu-10.04/](http://www.howtogeek.com/howto/17495/how-to-add-proprietary-drivers-to-ubuntu-10.04/)

---

### Post by Jerry N on 2012-01-21
I just added Mint 9 (Ubuntu 10.04) to my Mini 210 to dual boot with Win 7 basic.  If you have a wired ethernet connection, you will get a message about availability of drivers.  Let Ubuntu install those drivers and you should be good to go with wireless.  You shouldn't have to take any other action than letting Ubuntu do its thing.  I can't tell what you need to do to get wireless to work if you don't have a wired ethernet connection.  Ubuntu won't turn your Mini 210 into a speed demon but it does work adequately.  I have upgraded mine from 1GB RAM to 2GB RAM.  Personally, I don't like the Mini 210s tiny screen and am somewhat sorry that I bought it.  

Jerry

---

### Post by westie457 on 2012-01-21
Hello, it has been a while since I used 10.04 so memory might be a little rusty for some things.

Going on the assumption that you do not have access to use a wired connection and no CD drive boot your system normally then plug in the USB stick you used to install with. When the File Browser opens navigate your way to pool > main > b. here you will see 2 folders open the one called 'build-essential' and double click on the .deb file. After that go to the folder called 'b43-fwcutter' again double clicking on the .deb file.When things have settled down wait for about a minute then click on the Network Manager icon at the top of the screen (left hand end of all the icons on the right), you should see a list of available networks. If you see nothing there then reboot and check again.

Any problems post back here and we will try something else.

---

### Post by tjbearpig on 2012-01-21
Wow, pretty active community... Thanks for the help guys :D

I managed to share my Windows 7 computer's Internet connection with my Mini via a Ethernet cable. Turns out all I had to do is connect to the web and my driver was downloaded and updated automatically when I went to System > Admin. > Hardware Drivers! Very convenient. But I can't really enjoy this OS without knowing how to install programs... I see it's very different compared to Windows and Mac.

How can install programs such as PHP, MySQL Server, Apache Server, Flash, Java, etc.?

---

### Post by westie457 on 2012-01-21
> **tjbearpig said:**
> Wow, pretty active community... Thanks for the help guys :D

I managed to share my Windows 7 computer's Internet connection with my Mini via a Ethernet cable. Turns out all I had to do is connect to the web and my driver was downloaded and updated automatically when I went to System > Admin. > Hardware Drivers! Very convenient. But I can't really enjoy this OS without knowing how to install programs... I see it's very different compared to Windows and Mac.

How can install programs such as PHP, MySQL Server, Apache Server, Flash, Java, etc.?

The majority of Ubuntu programs are kept in repositories and are installed through the Software Center. Search for what you want and click install.

Some can be obtained over the internet by 'Googling', when installing this way find apps that have a .deb file. Download the .deb file that matches the version of the distro you are using and double-click to install through the Software Center, sometimes you will get a warning about installing from an untrusted source, this is a safe-guard for your system.

Sometimes when installing from the internet you can only get 'tar.gz' files. These are compressed archives that contain the source code and have to be compiled. **Not recommended for beginners**, as usually if the read-me file instructions are not followed correctly the install will fail and you will be asking here for help to sort things out.

---

### Post by tjbearpig on 2012-01-21
I've successfully installed XAMPP for Linux thanks to a video tutorial. Can every ".tar.gz" package be installed by typing "sudo tar xvfz '/package_dir/package.tar.gz' -C /opt"?

---

### Post by holycow131415 on 2012-01-21
/opt is probably not the best folder to install all programs that are outside of the software center. I think people usually install programs to the home folder, but i am not sure, because i always install things through .deb files, through PPA's,  or through the software center which in my opinion is best when installing programs =)

---

