---
title: "HP Pavilion DV6500 loaded with Ubuntu 16.10 needs better NIVIDIA driver"
date: 2017-01-23
forum: New to Ubuntu
---

### Post by vanvonu on 2017-01-23
The IT guy at my library loaded Ubuntu 16.04 onto my tired old HP Pavilion DV6500.  After a few days, an upgrade to 16.10 was offered and accepted.  Although many problems disappeared, the worst one remains.  When I'm in Firefox, the screen will go dark and monochrome for various periods.  When in this condition, the computer appears to be locked up, but always comes out, eventually.  He told me that the video driver is not the correct one for the NIVIDIA chip in the machine, but he didn't know where to get a better one. I'm pretty much convinced this is the problem because when I click on dash, the screen goes into a technicolor psychosis, although dash works well enough, once I can find the window and get the cursor into it.  I'm using the computer as my Linux classroom, so please treat me like a complete newbie, because my experience with IBM 1400 assembler and Univac 1100 JCL are of absolutely no use to me, 40 years on:-) Thank you in advance.

---

### Post by DogMatix on 2017-01-23
From what I can ascertain the HP DV6500 laptop (circa. 2007) uses the Nvidia GeForce 8400M GS graphics which seems to require the 340.xx Nvidia Legacy driver which can be found here. 
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

I would also suggest the specs of your laptop are a little lean to be running Ubuntu 16.10 and maybe a more lightweight distro (ie. Xubuntu or Lubuntu) would offer you improved performance.

---

### Post by poorguy on 2017-01-23
I have an hp-pavilion-d4650y / 09/18/2006  / Intel Core2 Duo 6400 / NVIDIA GeForce 7300 LE / 3.0 GB DDR2 and it runs Ubuntu Mate 16.04 really well using the Nvidia proprietary driver. :)

---

### Post by vanvonu on 2017-01-24
I went to the link, downloaded GeForce (seemed to be the thing to do), which told me I had to have Java (which is beyond my comprehension), which locked up my computer with every kind of incomprehensible that I have ever encountered. I guess I'm too ignorant to be even a newbie. In what way are the specifications of my computer too lean to run 16.10?

---

### Post by poorguy on 2017-01-24
Have you tried going into the Dash and using the icon that says Additional drivers and downloading the Nvidia driver from there. 

Mine have always installed without any problems following a restart.

This guide is for Ubuntu 16.04 but should be some help on installing display drivers.

[http://files.ubuntu-manual.org/manuals/getting-started-with-ubuntu/16.04/en_US/screen/Getting%20Started%20with%20Ubuntu%2016.04.pdf](http://files.ubuntu-manual.org/manuals/getting-started-with-ubuntu/16.04/en_US/screen/Getting%20Started%20with%20Ubuntu%2016.04.pdf)

---

### Post by vanvonu on 2017-01-24
The video scramble that I get when I click on dash is the indication I had that the driver wasn't working correctly.
When the IT guy who loaded 16.04 loaded a legacy Nvidia driver, it crashed the OS, twice.
That is why I'm reluctant to install a Nvidia driver, but my reluctance to install Java has proven to be justified for the same reason as Nvidia did.
What are the differences between 16.04 and 16.10, and will they matter to a proprietary driver?

---

### Post by oldfred on 2017-01-24
Never download driver directly from nVidia.
For older systems the version in Ubuntu's repository will works just fine. For those who purchase the very newest nVidia drivers, they probably need to add the ppa which has all the newest drivers compiled to work with Ubuntu.

If you install a different driver you have to totally purge as install of new one does not overwrite old. And if not purged, you get conflicts.

But I have a newer nVidia driver 620GT and the open source driver works just about as well as the proprietary nVidia driver.
So you may not get much performance improvement.

I think the suggestions of one of the lighter weigh flavors is more your solution. 
My older dual core2 laptop with 1.5GB of RAM also turned grey if I tried to load more than one larger program, but that grey told me it was then using swap. And swap is orders of magnitude slower than RAM.

How much RAM does your system have?

---

### Post by vanvonu on 2017-01-26
I'm obviously not qualified to answer the majority of your questions, nor understand what you tell me about things I know nothing about.
Where is the real newbie thread, so I can go there and stop being treated like a moron?

---

### Post by oldfred on 2017-01-26
Post this from terminal:
sudo lshw -short -C memory

If you installed from nVidia with .run type file, follow whatever nVidia instructions are to uninstall it.
Then and only then run this:
 sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms 

Then run this:
      
 # Shows standard repository versions, which is the same as
System Settings, Software & Updates icon, Additional drivers tab
ubuntu-drivers devices 

And just to confirm nothing installed.

 dkms status 

Then you can use System Settings, Software & Updates icon, Additional drivers tab or command line to install correct driver or 340.xx
      
 Or you manually choose correct entry in list.
sudo apt-get install nvidia-XXX

---

