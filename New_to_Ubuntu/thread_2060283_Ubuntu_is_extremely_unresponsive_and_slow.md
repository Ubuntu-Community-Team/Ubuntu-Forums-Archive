---
title: "Ubuntu is extremely unresponsive and slow"
date: 2012-09-19
forum: New to Ubuntu
---

### Post by Deomdu on 2012-09-19
I installed Ubuntu using the Windows installer today. I encountered a severe problem right away.

When I tried to install something, updates or new software, the system was unresponsive for 1-5 minutes, no noise from the internal HDD during that time. Then after that time all of a sudden the internal HDD started working, Ubuntu started the programs I tried to run during the unresponsive time and the installation bar progressed. It seemed to me like it was in some kind of "pause state".

Then after about 20 seconds the system became unresponsive again. No installation or download progress, no response. Sometimes even the mouse cursor freezed. After several minutes the whole thing started over.

This is not how I remember Ubuntu, is there a problem with the new version? Is there a problem with using the Windows installer? At first I thought my external HDDs would be the problem, I unplugged them and I kinda had the feeling that Ubuntu ran a little faster after that, but I think that's just my imagination.

Since I just installed Ubuntu I don't really know how things are when I'm not updating or installing anything. The Nvidia driver installtion alone took over 1 hour and the 50+ MB download was really slow because of those "unresponsive times" where nothing happened.

This doesn't seem normal though, installing new software and drivers shouldn't bring the system to a halt for several minutes, several times, this sure doesn't happen with Windows 7.

Am I doing something wrong here, has anyone any idea what might be the problem?
Thank you very much in advance, I really like Ubuntu and I could really use some help here.

---

### Post by I8NY on 2012-09-21
Well since it is new install and you don't have much progress the easiest fix would be to reinstall it.  This time burn a disc or use a usb thumb drive to boot off of to install ubuntu.  During the installation have Ubuntu get it's own ext3 partition so it doesn't get slowed down using the windows NTFS.  This is a weird glitch but right now reinstalling is the quickest fix.  Btw what are the system specs if reinstalling doesn't fix it?

---

### Post by NikTh on 2012-09-21
Hi , 
if Windows 7 running well on you PC , then Ubuntu should running well too. Except if you are unlucky with hardware incompatibility. 

So I am not even asking for specs. 
Wubi , Yes. Wubi is not  a regular installation. Is a Virtual install of Ubuntu inside Windows. Ubuntu gives you this opportunity just for testing the Operating System. Also Ubuntu gives you the LiveCD so you can test the O.S from there too. 
Of course it will be slower and with more problems (wubi I mean) cuz Ubuntu is outside of native environment - filesystem (ext4) . It is running in NTFS . 

So my suggestion is to uninstall wubi , just go to Control Panel (Windows) and add/remove programs , you will see Ubuntu listed there. Just a regular program of Windows. Unistall it . 

Then create a bootable Usb with unetbootin : [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
After a successful creation , boot from Usb and click "Try Ubuntu" . Explore - Test - Navigate to Ubuntu. If everything works well , then probably everything will work well on a regular install. 

If you decide to proceed with a regular dual-boot (and not wubi) , then post back here for further help or just look an example here :  [http://www.youtube.com/watch?v=LokDqte3sA4&feature=related](http://www.youtube.com/watch?v=LokDqte3sA4&feature=related)

Thanks

---

### Post by khelben1979 on 2012-09-21
> **I8NY said:**
> During the installation have Ubuntu get it's own ext3 partition so it doesn't get slowed down using the windows NTFS.

If it's a new installation of the latest Ubuntu I would not recommend EXT3 over EXT4, actually. Because of the improvements made with EXT4 I would say that it would be safe using, old Ubuntu releases I would have recommended EXT3 for reasons of stability and less risks of data loss.

Another thing, I would like to make a note here which might help you out with this Deomdu: if you have skills to check on for dust inside the casing and check the temperatures of your computer in your BIOS to make sure nothing is wrong with it, I've experienced in some cases that it can cause the slowdown and issues you have noted down here.

---

### Post by oldos2er on 2012-09-21
> **Deomdu said:**
>  The Nvidia driver installtion alone took over 1 hour and the 50+ MB download was really slow because of those "unresponsive times" where nothing happened.


What type of internet connection do you have? What are your hardware specs?

---

### Post by newb85 on 2012-09-21
+1 to NikTh's advice.  

Ubuntu's inclusion of the Wubi installer on their Download page with absolutely no explanation that it's only intended for experimental installs is a travesty.

---

