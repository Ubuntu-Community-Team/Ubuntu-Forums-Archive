---
title: "Windows Partition not in Grub menu"
date: 2012-09-11
forum: New to Ubuntu
---

### Post by Dacendaran on 2012-09-11
EDIT:  Simple fix.  The standard chmod +x filename works to give it the correct permissions.  Problem was forgetting to run sudo update-grub after making it executable. Sorry to take up space.

I was reading through the forum when I saw a post about changing the order of the grub menu so that windows was on top.

I followed the following advice:
> 
Alright, here it is, nice and easy... just like what the guy above said....

1 open /etc/grub.d/30_os-prober with root privleges in gedit.... type sudo gedit in the terminal and open the file.

2 save as 06_os-prober

3 now remove the leftover 30_os-prober .... it will still be there.. type cd/etc/grub.d. type rm 30_os-prober

4 type update-grub

that should do it... 

i'm sure you could just rename it using commands as well, i don't know them... I'm totally new to linux. 


[https://help.ubuntu.com/community/Gr...ing%20GRUB%202](https://help.ubuntu.com/community/Gr...ing%20GRUB%202) -read this if you want to actually know what ur doing

[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml) -read this to learn basic commands.

edit... if that doesn't work you must make the new file executable... I don't know if it retains that property after the save as... to make executable.... read the above grub 2 web page... it gives the command in the custom files section... i did it before even trying to reboot, so i don't know if it was necessary or not..


From the following topic:[http://ubuntuforums.org/showthread.php?t=1308701](http://ubuntuforums.org/showthread.php?t=1308701)

However, now the Windows 7 partition is no longer on the menu at all.  I am hoping that it hasn't been deleted and that it is simple to get back on the menu.  From reading the edit on the post, it seems that it may merely be an issue of making the file executable.  I have been going through the website linked in the post; however, it is not clear to me how to make the 30_os-prober file executable. 

```
$ ls -la /etc/grub.d/30_os-prober
``` gives: ```
-rw-r--r-- 1 root root 7603 Sep 11 11:35 /etc/grub.d/30_os-prober
```

Is there a simple way to make this file executable so that I can get access to my Windows partition back?

---

