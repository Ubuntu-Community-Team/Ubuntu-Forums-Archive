---
title: "Installing video card"
date: 2012-02-16
forum: New to Ubuntu
---

### Post by John Redcorn on 2012-02-16
Hello,

I have had Ubuntu for about 2 days now and am really struggling.

First off, I am running Ubuntu 11.10 32 bit.

I am trying to install my graphics card (Nvidia GeForce 7800 GT OC) 

I am currently using my on board graphics card and it is working fine, but the second I install my card things go bad. Basically the load screen is just staying that Dark purple/grey color and nothing ever happens from there. It just stays that way and won't boot up.

So far I have tried installing the startup manager and changing my setings to 1024x768 and 24 bit color. No joy.

Also I have downloaded the nvidia drivers and ran it in the terminal, but I get the error: nvidia-installer must be run as root.

Any help would be awesome!!

Thanks!

---

### Post by kimberlite on 2012-02-16
Hi,
Did you try to run installer with sudo prefix?

---

### Post by John Redcorn on 2012-02-16
No I haven't.  I understand what sudo prefix means....but would you be able to explain that process in a little more detail??

I can access the terminal...that is about as much as I know so far. I do have a lot of experience in CLI's though.

---

### Post by haqking on 2012-02-16
> **John Redcorn said:**
> No I haven't.  I understand what sudo prefix means....but would you be able to explain that process in a little more detail??

I can access the terminal...that is about as much as I know so far. I do have a lot of experience in CLI's though.

dont do it in X

Run using sudo

sudo sh <filename.run>

follow prompts

Instructions are on Nvidia website where you got the file

[http://us.download.nvidia.com/XFree86/Linux-x86/295.20/README/index.html](http://us.download.nvidia.com/XFree86/Linux-x86/295.20/README/index.html)

---

### Post by John Redcorn on 2012-02-16
Okay I did what you said, by typing sudo sh NVIDIA-etc etc.
It gives me and error: You do not appear to have an NVIDIA GPU supported by 295.20 NVIDIA Linux graphics drivers installed in this system.

I take this error as, my card isnt installed. Well it isn't. I can't load ubuntu when my video card is installed, it just hangs up on the load screen.

=(

---

### Post by haqking on 2012-02-16
> **John Redcorn said:**
> Okay I did what you said, by typing sudo sh NVIDIA-etc etc.
It gives me and error: You do not appear to have an NVIDIA GPU supported by 295.20 NVIDIA Linux graphics drivers installed in this system.

I take this error as, my card isnt installed. Well it isn't. I can't load ubuntu when my video card is installed, it just hangs up on the load screen.

=(

is the 295.20 file you downloaded the right file for your GPU then ?

---

### Post by haqking on 2012-02-16
choose appropriate driver here [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

---

### Post by John Redcorn on 2012-02-16
Yes it is the correct file. I have a GeForce 7800 and the drivers is for the GeForce 7 series. I downloaded the 32 linux one.

I guess the error about the GPU not supported is just a WARNING. So I hit okay and it gives me a second error: You appear to be running an X server; please exit X before installing.


Thanks so much already for the help!!

---

### Post by kimberlite on 2012-02-16
Hold down SHIFT key while starting the box. This will load GRUB menu, than select recovery mode. It will prevent to load X server and give you some option including "root terminal". Than you change to directory when your driver program resides (eg. cd /home/yourname/yourdriver) after that you can try to run again: sudo sh <filename.run>. HTH, Kimberlite

---

### Post by John Redcorn on 2012-02-16
Okay I figured out how to run the terminal and turn off X server by doing Ctrl Alt F1 and typing in sudo service lightdm stop #.

I then am able to start the install but I eventually get more errors:

First off: The distribution provided pre-install script failed! Continue anyway? YES!

progress bar goes then:

ERROR: Unable to load the kernel module 'nvidia.ko' . This happens most frequently when this kernel module was built against the wrong or improperly configured kernel sources, with a version of gcc that differs from the one used to build the target kernel, or if a driver such as rivafb, nvdidiafb, or nouveau is present and prevents the NVIDIA kernel module from obtaining ownership of the nvidia graphics devices, or nvidia gpu installed in this system is not supported by this nvidia linux graphics driver release.

I am heading to lunch. I'll be back in an hour!

Thanks!

---

### Post by kimberlite on 2012-02-16
This thread may help you out:
[http://ubuntuforums.org/showthread.php?t=1467074](http://ubuntuforums.org/showthread.php?t=1467074)
Cheers

---

### Post by John Redcorn on 2012-02-16
ACK!!! SO CLOSE!!

thanks kimberlite, that link helped a lot. 

Here is where I stand now:

I have my video card installed and am now getting to the desktop!! Yay!

BUT now if I hit ctrl alt f1 the screen just goes black! I can't get back now without hitting ctrl alt f7.

Then it got worse...I stopped the gui service by **sudo service lightdm stop #**

and now the screen is just black and I can't get out with my little "cheat".

---

### Post by John Redcorn on 2012-02-16
Okay after 15+ hours at this I am done. From the research I have done this video card just doesn't work well with Ubuntu.

Do you guys think I might have better luck with another version of Linux? Any suggestions?

---

### Post by haqking on 2012-02-16
> **John Redcorn said:**
> Okay after 15+ hours at this I am done. From the research I have done this video card just doesn't work well with Ubuntu.

Do you guys think I might have better luck with another version of Linux? Any suggestions?

Well it seems to work ok with UBuntu

[http://openbenchmarking.org/s/NVIDIA%20GeForce%207800%20GT](http://openbenchmarking.org/s/NVIDIA%20GeForce%207800%20GT)

---

### Post by John Redcorn on 2012-02-16
Okay I didn't give up. I was just very frustrated :P

Where I am at now....I got the video card drivers installed! 

Now the problem is:

I log in and it just sticks after I hit enter with my password. Doesn't ever log in. I am trying to set up dual monitors...I think I should have expressed that in my original question. If I just wanted one monitor everything would be working fine just using the on board graphics.

I think I may have screwed up configuring my video card settings. I will spend more time on it tomorrow!

Thanks for all of your help so far.

---

### Post by haqking on 2012-02-17
> **John Redcorn said:**
> Okay I didn't give up. I was just very frustrated :P

Where I am at now....I got the video card drivers installed! 

Now the problem is:

I log in and it just sticks after I hit enter with my password. Doesn't ever log in. I am trying to set up dual monitors...I think I should have expressed that in my original question. If I just wanted one monitor everything would be working fine just using the on board graphics.

I think I may have screwed up configuring my video card settings. I will spend more time on it tomorrow!

Thanks for all of your help so far.

Dual monitors should be very easy.

From the nvida control panel, just choose twinview and thats usually it or choose seperate X depending on what you need or want

I have all the latest hardware and various Linux are running fine on it all across dual 1920x1080p monitors

---

### Post by John Redcorn on 2012-02-17
What about this Xinerama option???

---

### Post by haqking on 2012-02-17
> **John Redcorn said:**
> What about this Xinerama option???

similar things

[http://www.phoronix.com/scan.php?page=article&item=387&num=1](http://www.phoronix.com/scan.php?page=article&item=387&num=1)

---

### Post by John Redcorn on 2012-02-17
I think in my haste I messed up a little. I activated twinview and xinerama.... should I disable xinerama through the terminal? It is set to xinerama="1" so just make it 0 or empty?

---

### Post by haqking on 2012-02-17
> **John Redcorn said:**
> I think in my haste I messed up a little. I activated twinview and xinerama.... should I disable xinerama through the terminal? It is set to xinerama="1" so just make it 0 or empty?

it depends, are you having a problem of some sort ?

If you are then make changes, if you are not then dont fix what isnt (yet) broken ;-)

---

### Post by John Redcorn on 2012-02-17
I can't login! Once I enter my password on the login screen I hit enter and both monitors turn on, and it just sits on that login screen. I can move my mouse between both monitors...so thats good! If I hit ctrl-alt-f1 I can access the terminal just fine though...so I need to change my video card settings through the CLI and I am having a hard time figuring that out.

Yesterday I was about to get to this 
[http://forums.fedoraforum.org/showthread.php?t=269839](http://forums.fedoraforum.org/showthread.php?t=269839)
screen but now I can't figure out how to get there through the terminal

I tried typing sudo /etc/X11/xorg.conf but that didn't work. If you know how to get to the screen that looks like the above link that would be a huge help! (And if to turn off xinerama I need to put a 0 instead of a 1)

---

### Post by John Redcorn on 2012-02-17
Success!!!! I am finally up and running. I was about to reset my xorg.conf file and boot again so I could try to change the nvidia X settings over again. This time I just turned on twinview and it seems to be working so far!

Woohoo!

Thank you guys so much for your help! I can't believe it's working!

---

### Post by haqking on 2012-02-17
> **John Redcorn said:**
> Success!!!! I am finally up and running. I was about to reset my xorg.conf file and boot again so I could try to change the nvidia X settings over again. This time I just turned on twinview and it seems to be working so far!

Woohoo!

Thank you guys so much for your help! I can't believe it's working!

cool glad we could help.

Remember to mark the thread as solved using thread tools.

Cheers

---

