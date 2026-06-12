---
title: "Video Resolution 12.0.4"
date: 2012-10-09
forum: New to Ubuntu
---

### Post by kb4not on 2012-10-09
I checked to make sure this wasn't posted elsewhere before this post. So I did an install of 12.0.4 as a stand alone system on a Dell Inspirion N5010. Was working great. Very smooth and fast. As usual, tried to make it look different and put the "Mac-Lion" theme on it and it too worked great. Only issue was the boot splash screen and shut down screen with the "apple" on it was out of center of the screen. I thought I had found a fix for the resolution for just the splash screen. But it wasn't. What I actually did was change the entire resolution of the computer. It was 1366x768 ( not sure what bit it was) and changed it to the highest resolution that was available which was 1024x768-24bit. Now my screen is way out of sorts. Usable, but not right. Any suggestions of how to get it back to the 1366x768???  I used the following screen shot to change the resolution. The other screen shot is of my actual terminal.

---

### Post by DuckHook on 2012-10-09
What did you do to change it to 1024x768?

---

### Post by kb4not on 2012-10-09
Yes that is what I changed it to. Need to get it back to 1366x768.

---

### Post by NikTh on 2012-10-09
Hi , 

can you post the results of these commands  ? 

```
cat /etc/default/grub
```
```
ls /etc/initramfs-tools/conf.d/
```
Thanks

---

### Post by kb4not on 2012-10-09
Will post that later this evening sometime after 9:00PM EST. At work now.

---

### Post by kb4not on 2012-10-09
ok here is what I got with the 2 different commands.
-----------------------------------------------------------------------------------------------------------------
kristy@kristy-Inspiron-N5010:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1024x768-24,mtrr=3,scroll=ywrap"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1024x768-24

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
kristy@kristy-Inspiron-N5010:~$ 

------------------------------------------------------------------------------------------------------
And for the second command

kristy@kristy-Inspiron-N5010:~$ ls /etc/initramfs-tools/conf.d/
resume  splash
kristy@kristy-Inspiron-N5010:~$

--------------------------------------------------------------------------------------------------------------
Thanks for the reply and help.

---

### Post by kb4not on 2012-10-09
delete

---

### Post by kb4not on 2012-10-09
> **DuckHook said:**
> What did you do to change it to 1024x768?
this is how I changed it in the terminal.

---

### Post by NikTh on 2012-10-09
Hi ,

To Undo what you did , (cuz the script you downloaded and ran not applies to 12.04) 

Open a terminal and run bellow commands with order 

```
sudo rm /etc/initramfs-tools/conf.d/splash
``````
sudo sed 's/GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1024x768-24,mtrr=3,scroll=ywrap"/GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"/g' -i /etc/default/grub
``````
sudo sed 's/GRUB_GFXMODE=1024x768-24/#GRUB_GFXMODE=1024x768-24/g' -i /etc/default/grub
``````
sudo sed 's/uvesafb mode_option=$resolution mtrr=3 scroll=ywrap//g' -i /etc/initramfs-tools/modules
``````
sudo update-grub
``````
sudo update-initramfs -u
```Reboot.

Please just **copy-paste** above commands one at time for more accuracy.

Thanks

---

### Post by jmmarchioli on 2012-10-09
this will work in xubuntu 12.04? i have the same problem

---

### Post by NikTh on 2012-10-09
> **jmmarchioli said:**
> this will work in xubuntu 12.04? i have the same problem

No is not for sure. 
Did you run the same script ? 

Do you have the same results in 
```
cat /etc/default/grub
```and
```
ls /etc/initramfs-tools/conf.d/
```**This is not a generic fix**. It is a specific fix for the problem of OP , cuz he ran a script that changed some critical lines in config files. 

Thanks

---

### Post by kb4not on 2012-10-09
Thanks for the reply NikTh. I applied all the commands 1 by 1 and then did the reboot. It started to start with the log on info and once I put the password in, it started to act a little sketchy. It finally came up to the normal resolution for about a minute or so but started to blink and change resolution from normal to very large. Could only see about 1/4 of screen. I was able to do a second reboot and thought it was going to hold that time but started the blinking and resolution changing back and forth. It finally locked up and would not respond to anything, so I powered it down. 

  I must have messed more than the resolution up during the changes that I made. It was a fresh install so no info was lost and I believe I will just do another fresh install this weekend when I get back home. I work on the road and was just tweaking it a little and don't have the disk with me. My ThinkPad that I am using now with a dual boot Windows and Ubuntu has been rock solid since day 1. I have been trying to learn how to work with Ubuntu for a little while but it is coming to me very slow.

  One last question though if you don't mind?? Is there a way to just change the resolution of the boot/splash screen on start up and shut down?? I know I did it in 10.10 but really can't remember what I did. Once again, thanks for all the help.

---

### Post by NikTh on 2012-10-09
> **kb4not said:**
> Thanks for the reply NikTh. I applied all the commands 1 by 1 and then did the reboot.

I just edited my post and added a command. I apologize for that I missed one point. 
Can you run again the commands one by one (from the beginning) ? 

Thanks

---

### Post by NikTh on 2012-10-09
> **kb4not said:**
> .One last question though if you don't mind?? Is there a way to just change the resolution of the boot/splash screen on start up and shut down?? I know I did it in 10.10 but really can't remember what I did. Once again, thanks for all the help.

12.04 is a little more complex in boot - splash - resolution. 

A more safely  way to test if you can change the resolution is to install a program [grub-customizer]("http://ubuntuforums.org/showthread.php?t=1664134") and try to change it from there.

**A general suggestion** : Do not run scripts in blind from any site. 
First open the script with an editor (eg : gedit) check it out , and if you have queries you can post the contents here and leave other people (me not included)***** to read it and see if will apply correctly in your Ubuntu version.

*****I don't know scripting , I can read commands but for this specific problem of yours I know that in 12.04 change the splash screen and/or the resolution is more complex and difficult than other (previous) versions. (of Ubuntu)

Thanks

---

### Post by jmmarchioli on 2012-10-09
well ill try that lines... but dont work in xubuntu :( ill use to have a wide screenn and the funny part is i dont change the screen resolution...and i cant have my old 1366x768...

---

### Post by NikTh on 2012-10-09
> **jmmarchioli said:**
> well ill try that lines... but dont work in xubuntu :( ill use to have a wide screenn and the funny part is i dont change the screen resolution...and i cant have my old 1366x768...

Did you download and ran the same script ? "fixplymouth" ? 

If yes , then you can try to run the commands again ( I added 2 new commands) and see . 

**BUT ONLY **if you run the SAME script as OP .

Thanks

---

### Post by kb4not on 2012-10-09
> **NikTh said:**
> I just edited my post and added a command. I apologize for that I missed one point. 
Can you run again the commands one by one (from the beginning) ? 

Thanks
I will see if it will boot back up to get to the terminal. Just tried it and I hear it but the screen is now just black. If it won't boot normally, is there a way to do like safe mode in Windows??

---

### Post by NikTh on 2012-10-09
> **kb4not said:**
> I will see if it will boot back up to get to the terminal. Just tried it and I hear it but the screen is now just black. If it won't boot normally, is there a way to do like safe mode in Windows??

Yes,

2 options

1st boot from recovery mode . Recovery mode is listed in grub menu . If you haven't grub menu at startup , then hold down the [Shift] key during boot until grub menu loads. 
When you boot from recovery mode , at the opened window select "FailSafeX" . See if boots correctly in low graphics.

2nd option is from a LiveCd/Usb. Boot from there and "Try Ubuntu" . Then we must follow another method to mount your drive and find the affected files.

Thanks

---

### Post by kb4not on 2012-10-09
> **NikTh said:**
> Yes,

2 options

1st boot from recovery mode . Recovery mode is listed in grub menu . If you haven't grub menu at startup , then hold down the [Shift] key during boot until grub menu loads. 
When you boot from recovery mode , at the opened window select "FailSafeX" . See if boots correctly in low graphics.

2nd option is from a LiveCd/Usb. Boot from there and "Try Ubuntu" . Then we must follow another method to mount your drive and find the affected files.

Thanks
OK I got it in recovery mode with the shift key method. But once in there I could choose the FailSaFeX mode and it would warn me about the graphics and then lock up. No mouse or keyboard options. I'm pretty sure at this point that I must have changed much more than the resolution. It's acting very erratic now so I do believe that I will just do the fresh install this weekend. The Mac-Lion them was working great and so was the system until I started trying to tweak the boot/splash resolution. Live and learn I guess. Thank you very much for the help and I will work with the gedit next time first.

---

### Post by NikTh on 2012-10-10
> **kb4not said:**
> OK I got it in recovery mode with the shift key method. But once in there I could choose the FailSaFeX mode and it would warn me about the graphics and then lock up. No mouse or keyboard options. I'm pretty sure at this point that I must have changed much more than the resolution. It's acting very erratic now so I do believe that I will just do the fresh install this weekend. The Mac-Lion them was working great and so was the system until I started trying to tweak the boot/splash resolution. Live and learn I guess. Thank you very much for the help and I will work with the gedit next time first.

This is sad. I was almost sure that commands I gave would recover your screen resolution. 
OK, reinstall Ubuntu is always a quick solution , but for me is not a solution or workaround. 
If you want to reinstall Ubuntu I will suggest the way that you don't remove your personal data. (and/or personal config files). 
This way  removes everything being in / root partition (system) and will fix any affected files of the system (you changed).

Choose **"something else"** from the installer and then choose (mark-tick) the partition with Ubuntu and click "change" , in the next window select everything **except **the box to **format the partition** .

**Check out the attached images. **

Thanks and good luck.

---

