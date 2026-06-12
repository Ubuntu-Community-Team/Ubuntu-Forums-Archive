---
title: "I must be a nOob if I can't google the answer..  Samsung Chromebook ARM"
date: 2013-12-01
forum: New to Ubuntu
---

### Post by kensavell on 2013-12-01
Greetings and Happy Holiday season.

I first installed Suse Linux on my Win95 machine back in '99 and it was a fun experience piecing everything together.  I tinkered with it off an on for a few months, then abandoned the awesome Compaq tower it was installed in.  

A few years later I partitioned my laptop HD, and installed another copy of Suse and that went well - So I've had some exposure to Linux but it is pretty dated now, and haven't played with it in over 10 years.

I picked up some Samsung Chromebooks for the family to use instead of constantly replacing their computers, since they only use internet on them.  The Chromebook is an ideal solution to a non-tech family that only wants to FB, Netflix, Email, etc.  But my son (now 13) is missing Steam & Minecraft.  So yesterday I went on a mission to install Linux on the Chromebook.

I've learned that Steam won't run on an ARM processor, so this morning, I decided to sit down and figure out how to run Minecraft - And here's my issue.....

For the life of me I cannot get the Chromebook to boot back into Ubuntu!  Every google search, forum thread seems to point me back to installation techniques.  I've installed it, and had it running well last night; fixed the touchpad issue by modifying that keyboard file from GB to US, and everything was working well.

I rebooted, and left Developer Mode, and the device rebooted into ChromeOS as I expected, but now, I cannot get it to reboot into Ubuntu.  I've put it into developer mode, and I expected it to boot Ubuntu, but it just keeps going to Chrome.  

I partitioned the HD, and did not use the SD method, so is there a key combination I need to use at the "OS Verification is OFF" screen?  If I use Ctrl-D, it automatically boots ChromeOS, and if I let it time out, it also boots ChromeOS.

Any pointers?

Thanks

---

### Post by kensavell on 2013-12-01
So I stumbled across this ...  ([http://www.howtogeek.com/162120/how-to-install-ubuntu-linux-on-your-chromebook-with-crouton/](http://www.howtogeek.com/162120/how-to-install-ubuntu-linux-on-your-chromebook-with-crouton/))

[h=3]Removing Crouton and Restoring Your Chromebook[/h][LEFT][COLOR=#333333][FONT=Verdana]If you decide you&#8217;re done with Linux, you can easily get rid of the scary boot screen and get your internal storage space back.[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]Just reboot your Chromebook normally to get back to the scary warning screen at boot-up. Follow the prompts on your screen (tap the Space bar and then press Enter) to disable Developer Mode. When you disable Developer Mode, your Chromebook will clean everything up, restoring you to a clean, safe locked-down Chrome OS system and overwriting all the changes you&#8217;ve made to your Chromebook&#8217;s software.




Probably explains why I can't boot Ubuntu - I've removed it by leaving developer mode...  [/FONT][/COLOR][/LEFT]

---

### Post by kensavell on 2013-12-01
Figures that it takes finally posting a question before I discover the answer.  

I originally used this walkthrough  [http://chromeos-cr48.blogspot.com/2013/05/chrubuntu-one-script-to-rule-them-all_31.html](http://chromeos-cr48.blogspot.com/2013/05/chrubuntu-one-script-to-rule-them-all_31.html)  but failed to catch the part about switching back and forth.  

Using the directions in my previous post, the shift+ctrl+alt+arrows works well.  The desktop environment isn't as elegant, but it gives me something to dabble with.

---

### Post by kensavell on 2013-12-01
Well, I removed the xfce version and started over.

Following this walkthrough -->  [http://chromeos-cr48.blogspot.com/2013/05/chrubuntu-one-script-to-rule-them-all_31.html](http://chromeos-cr48.blogspot.com/2013/05/chrubuntu-one-script-to-rule-them-all_31.html) with just a minor adjustment.

in step 4, I used curl -L -O [http://goo.gl/s9ryd;](http://goo.gl/s9ryd;) sudo bash s9ryd ubuntu-desktop lts  

Then had to adjust the trackpad by going to the terminal and executing the following

mkdir ~/backup
sudo mv /usr/share/X11/xorg.conf.d/* ~/backup/

cd /usr/share/X11/xorg.conf.d/
sudo wget [http://craigerrington.com/chrome/x_alarm_chrubuntu.zip](http://craigerrington.com/chrome/x_alarm_chrubuntu.zip)

sudo unzip x_alarm_chrubuntu.zip
sudo rm x_alarm_chrubuntu.zip
sudo gedit /usr/share/X11/xorg.conf.d/10-keyboard.conf

then change gb to us in the text window that pops up, save the file and close it and reboot

then to switch back to Chrome, I followed this walkthrough mostly  [http://terrybritton.com/create-shortcuts-to-easily-switch-between-chrome-os-and-chrubuntu-1006/](http://terrybritton.com/create-shortcuts-to-easily-switch-between-chrome-os-and-chrubuntu-1006/)

Step 5 was modified to this 
     alias chromeos='sudo cgpt add -i 6 -P 0 -S 0 /dev/mmcblk0;sudo reboot'

and step 11 I edited the sudo vim .bashrc as directed except changing it to this 
     alias ubuntu='sudo cgpt add -i 6 -P 5 -S 1 /dev/mmcblk0;sudo reboot'

And that seems to have worked.

---

