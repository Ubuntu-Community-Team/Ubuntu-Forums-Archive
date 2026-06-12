---
title: "Monitor says &quot;out of range&quot;"
date: 2012-10-02
forum: New to Ubuntu
---

### Post by moread on 2012-10-02
Hello! I must say I'm an absolute beginner. So I beg your pardon if I've chosen the wrong section to post my thread. It's just some hours I've installed Ubuntu 12.04 and found out this community. My problem is the following: 

After having downloaded and installed Ubuntu 12.04 at first things seemed to work well but then at the first reboot I have any ideas of what happened:
When I chose ubuntu from the grub my moniter goes blank and says "out of range" and I can only hear ubuntu starting up without seeing nothing. I've read lots of articles here and on other sites but I had no success in solving my problem. The more similar thread I've found was this: 

[http://ubuntuforums.org/showthread.php?t=1969868]("http://ubuntuforums.org/showthread.php?t=1969868")

but I had his same problems. if I write:

[I]Xorg -configure
mv ./xorg.conf /etc/X11/
nano /etc/X11/xorg.conf[/I]

it says: "Gtk WARNING: Cannot open display"

and if I try writing:

[I]sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer[/I]

I have no idea of how launching Grub-customizer (as described at point 3.) because the monitor is still blank. :(
I also tried to reinstall the whole OS from the CD but the problem is still there :(:(

Please help me

---

### Post by thatguruguy on 2012-10-02
What kind of graphics card do you have? Also, what kind of monitor do you have?

---

### Post by Bucky Ball on 2012-10-02
Welcome.

Grub Customizer don't think will help in this situation. That is for pimping your grub, basically. Changing list order, adding colours/graphics ... etc. Has nothing to do with tweaking graphics on the desktop and grub seems to be working fine, anyway. It is the graphics in the install that seems to be giving problems.

Try this: When you get to the menu list at boot, choose the kernel you want to launch but hit 'e' to edit it rather than enter to launch. Add this to the end of the line that says 'quiet splash' or just quiet or just splash:

nomodset

Follow directions at bottom of the screen to save and boot. What happened? If you have success, check 'Additional Drivers' and see if there's anything in there for your graphics card. If not and if you haven't done an update, do one using the Update Manager and have another look.

---

### Post by thatguruguy on 2012-10-02
You may also want to read [this]("http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it").

---

### Post by Bucky Ball on 2012-10-03
> **thatguruguy said:**
> You may also want to read [this]("http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it").

OP has already installed Ubuntu. Your link refers to booting to a black screen from the LiveCD. ;)

---

### Post by thatguruguy on 2012-10-03
> **Bucky Ball said:**
> OP has already installed Ubuntu. Your link refers to booting to a black screen from the LiveCD. ;)

That's the first part of the answer given on that page. Scroll down. It shows the following:
> 
**Black/purple screen *after* you boot Ubuntu for the first time**

  This usually happens because you have an Nvidia or AMD graphics card, or a laptop with *Optimus* or switchable graphics, and Ubuntu does not have the proprietary drivers installed to allow it to work with these. 
  The solution is to boot Ubuntu *once* in nomodeset  mode (your screen may look weird) to bypass the black screen, download  and install the drivers, and then reboot to fix it for ever.
  
[LIST]
[*]Start your computer, and press the Shift when booting up, to get the Grub menu. Use the arrow keys to navigate/highlight the entry you want (usually the first one).
  [IMG]http://i.stack.imgur.com/8RYuZ.png[/IMG]
[*]Press e to edit that entry, which will show you the details:
  [IMG]http://i.stack.imgur.com/0Cfhc.png[/IMG]
[*]Find the linux entry as shown above, use the arrow keys to get to it, and then  press the End key to get to that line's end (which may be on the next line!). 
  [IMG]http://i.stack.imgur.com/1y5tf.png[/IMG]
[LIST]
[*]Enter nomodeset as shown, and press Ctrl+X to boot to where you can successfully install your graphics drivers.
[/LIST]
 
[/LIST]
    
[LIST=1]
[*]Try the [Alternate Installer]("http://www.ubuntu.com/download/desktop/alternative-downloads#alternate") - this is a text based installer that might work better than the liveCD depending on your hardware.
[*]If you have an Nvidia Optimus card you should NOT install nvidia drivers, just use the built in driver, see here:
[LIST]
[*][How well do laptops with Nvidia Optimus work?]("http://askubuntu.com/questions/36930/how-well-do-laptops-with-nvidia-optimus-work")
[/LIST]
 
[*]If you still can't install Ubuntu then unfortunately you've probably run into a hardware specific bug, please see here: [How do I report a bug?]("http://askubuntu.com/questions/5121/how-do-i-report-a-bug")
[/LIST]

---

### Post by Bucky Ball on 2012-10-03
> **thatguruguy said:**
> That's the first part of the answer given on that page. Scroll down.

Second answer on the page, though, under a different heading:

> Black/purple screen *after* you boot Ubuntu for the first timeThus the confusion. Apologies. ;)

First answer:

> If you are trying to install Ubuntu

---

### Post by thatguruguy on 2012-10-03
> **Bucky Ball said:**
> 
Thus the confusion. Apologies. ;)


No need to apologize. I was mostly responding to you so that the OP (or others with the same issue) wouldn't see your comment, and decide not to visit that page. It has some helpful information, and it's laid out well.

---

