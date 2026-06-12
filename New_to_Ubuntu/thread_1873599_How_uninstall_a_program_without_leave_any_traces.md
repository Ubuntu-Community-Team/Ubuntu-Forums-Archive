---
title: "How uninstall a program without leave any traces?"
date: 2011-11-01
forum: New to Ubuntu
---

### Post by xavi fernandez on 2011-11-01
Hi, I experienced problems with cheese software, I remove and install again and again and appears the same problem when I tried to open it, the window in black, so I thinking that doesn't install well because must be maybe any files or something from the previous installations. Here I attach the screen shot from the terminal when I tried to open it, after it, the programs open but the window is completely black and not allow me use any option.
I'm running ubuntu 11.10.

Thanks in advance

---

### Post by dFlyer on 2011-11-01
enter the following two commands
sudo apt-get purge cheese
sudo apt-get autoremove

The first command removes cheese
The second command removes any left over libs.

---

### Post by xavi fernandez on 2011-11-02
How for your reply dFlyer, I uninstall the software with the commands you gave me, after that, I install again and I have the same problem, in the terminal appear this, and after that cheese open, but with the black window and don't allow me use any options, are all in grey colour.

---

### Post by gandaran on 2011-11-02
> **xavi fernandez said:**
> How for your reply dFlyer, I uninstall the software with the commands you gave me, after that, I install again and I have the same problem, in the terminal appear this, and after that cheese open, but with the black window and don't allow me use any options, are all in grey colour.
the best way to remove applications is synaptic package manager as it has the option for complete removal (the same as --purge command) but it will not remove the user configuration files, the user files have to be manually deleted from the hidden home user directory, find the home user cheese folder to delete.

---

### Post by fantab on 2011-11-02
> **dFlyer said:**
> enter the following two commands
sudo apt-get purge cheese
sudo apt-get autoremove

The first command removes cheese
The second command removes any left over libs.

After the above

Go to **HOME** folder and **CTRL+H** (this reveals your hidden dot(.)folders) look for the .folder of the application you are trying to remove and DELETE it.

Then **ALT+F2**, type ***gksu nautilus*** (This opens nautilus with root permissions). **Search** for the application you are trying to remove by using search box and if you find any files and folders DELETE them.

---

### Post by 3rdalbum on 2011-11-02
Delete the settings file in your home directory - it's in the .gconf/apps/cheese folder in your home directory. (hidden folder)

Removing the program itself will almost never help. Problems like that are mostly caused by a damaged preferences file, not a corrupted program binary.

---

### Post by xavi fernandez on 2011-11-02
Unfortunately I didn't found any traces from cheese software, this is the screen shot where u sent me. One Question, some one made it works in ubuntu 11.10? Can be a problem of the software?
Thanks a lot!!!

---

### Post by gandaran on 2011-11-02
> **xavi fernandez said:**
> Unfortunately I didn't found any traces from cheese software, this is the screen shot where u sent me. One Question, some one made it works in ubuntu 11.10? Can be a problem of the software?
Thanks a lot!!!
did cheese ever once opened correctly?
if there's no cheese user profile then it's because cheese did never or doesn't work on your system to create the profile
do you have all the media gstreamer plugins installed?
try this command on the terminal
```
gstreamer-properties
```
then use the test buttons to check if the video camera works with any of the different options available

---

### Post by philinux on 2011-11-02
sudo updatedb 

Then

locate cheese

Post back what it locates.

---

### Post by xavi fernandez on 2011-11-02
Thanx Gandaran, I tried what you sent to me and yes, I made the camera works and I listen sonds in test as well, the only thing is that testing the sound from the camera, doesn't opened the camera, I mean, the micro from the camera.

---

### Post by xavi fernandez on 2011-11-02
Thanks Philinux, I just tried what you send me and this are the results, I hope this will help.

---

### Post by Paddy Landau on 2011-11-02
[Linux is not Windows]("http://linux.oneandoneis2.org/LNW.htm"). If you have problems with a program, uninstalling and reinstalling will make no difference whatsoever.

The settings are stored in your home folder (as 3rdalbum said in [post #6]("http://ubuntuforums.org/showthread.php?p=11418167#post11418167")). Simply delete the the folder [FONT=Fixedsys]/home/[yourname]/.gconf/apps/cheese[/FONT].

If you have a problem with Cheese, the problem is probably with your hardware and the drivers, not with the program. I repeat: uninstalling and reinstalling will achieve nothing.

---

### Post by gandaran on 2011-11-02
> **xavi fernandez said:**
> Thanks Philinux, I just tried what you send me and this are the results, I hope this will help.
you don't have cheese installed from this output
install command
```
sudo apt-get install cheese
```
then look for cheese launcher in the applications

---

### Post by 3rdalbum on 2011-11-02
Just took a look in Dconf-editor - it appears that Cheese is using Dconf now instead of Gconf? I'm really not familiar with Dconf so I'm not sure how to go about deleting any Dconf settings.

---

### Post by xavi fernandez on 2011-11-03
I was looking for information in internet and here about the Dconf. files, but the few things that I found I can not understand at all. 
Please, some one knows how to find files there, and remove them? I need to do it for install the cheese hardware and see if is working properly.

Thanks for your help to all.

---

### Post by Paddy Landau on 2011-11-04
> **xavi fernandez said:**
> I was looking for information in internet and here about the Dconf. files, but the few things that I found I can not understand at all. 
Please, some one knows how to find files there, and remove them? I need to do it for install the cheese hardware and see if is working properly.
If you have not changed anything in the dconf settings, then they will be set to their defaults.

You do _***not***_ have to uninstall and reinstall Cheese to reset the settings. Uninstalling and reinstalling will do absolutely nothing to your settings. This is Linux, not Windows. You are making it too complicated.

To reset the settings, you need only delete the relevant folder. Open a terminal and cut-and-paste the following command:```
rm -R ~/.gconf/apps/cheese
```That is all.

---

### Post by xavi fernandez on 2011-11-06
Thanks all for your help, but I think the problem is that cheese doesn't work properly in ubuntu 11.10 and probably not compatible with my toshiba satellite, I just was reading the commentaries from the users in the software center help and mostly all the complaints about cheese was in ubuntu 11.10, for ubuntu 11.04 was perfect.
I hope soon will be fix the problem.

Thanks all again for your time and your patience.

---

### Post by Paddy Landau on 2011-11-06
Yes, I think you are right.

Has a bug been raised for it? If not, you may want to raise a bug yourself.

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

