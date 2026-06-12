---
title: "stuck at NVIDIA splash screen"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by AppState09 on 2008-05-08
After several days of fighting with this thing, I FINALLY got my NVIDIA drivers installed using Envy. Well, I'm assuming everything is correctly installed. The problem is that when I reboot my system, I get to the NVIDIA logo and it gets stuck. So, I can't actually get to my desktop to see what is/isn't right. 

I'm VERY new at this and was so happy about getting that stupid logo to show up (hopefully meaning the drivers were installed correctly) but now I can't get it to move past that point ](*,)

---

### Post by tbielawa on 2008-05-08
The first step to debugging this will be for you to show us what your /etc/X11/xorg.conf file looks like. Additionally it would be helpful to see what your xorg error log is saying. Try running this once you're hanging at the nvidia logo screen

```
cat /var/log/Xorg.0.log >> ~/xorg.log
```

And then posting that here as well. It may give us some more information to go off of. If you haven't looked at the nvidia forums [http://forums.nvidia.com/](http://forums.nvidia.com/) then you should search there as well for people having similar issues.

---

### Post by AppState09 on 2008-05-08
> **tbielawa said:**
> The first step to debugging this will be for you to show us what your /etc/X11/xorg.conf file looks like. Additionally it would be helpful to see what your xorg error log is saying. Try running this once you're hanging at the nvidia logo screen

```
cat /var/log/Xorg.0.log >> ~/xorg.log
```

And then posting that here as well. It may give us some more information to go off of. If you haven't looked at the nvidia forums [http://forums.nvidia.com/](http://forums.nvidia.com/) then you should search there as well for people having similar issues.


Thank you for your help! 
My only problem now is that I cannot get to ANYTHING once I hit that NVIDIA screen. Is there another way to go about getting that info?

---

### Post by tbielawa on 2008-05-08
> **AppState09 said:**
> Thank you for your help! 
My only problem now is that I cannot get to ANYTHING once I hit that NVIDIA screen. Is there another way to go about getting that info?

Try the following and let us know if you're able to get any results

when you're stuck at the nvidia screen drop to a console, ctrl + alt + f2 and log in there. If it's locked too much to let you do that press ctrl + alt + backspace and it might kill the nvidia loading screen and let you log into something and run that command.

if all of that fail you should still be able to restart the machine in recovery mode (which will suppress xorg trying to come up) and get the contents of your Xorg.0.log file since it's written to disk.

---

### Post by AppState09 on 2008-05-09
> **tbielawa said:**
> Try the following and let us know if you're able to get any results

when you're stuck at the nvidia screen drop to a console, ctrl + alt + f2 and log in there. If it's locked too much to let you do that press ctrl + alt + backspace and it might kill the nvidia loading screen and let you log into something and run that command.

if all of that fail you should still be able to restart the machine in recovery mode (which will suppress xorg trying to come up) and get the contents of your Xorg.0.log file since it's written to disk.



Thank you for your reply!! I actually got so frustrated with it that I finally just reinstalled Hardy. I then installed the driver via a website I found with a compiz-checker on it (told me I didn't have the right driver and gave me the new one). I had to restart, got the black screen. Rebooted again in recovery, logged in and, to my amazement, my driver was installed and in use! However, my screen was all messed up!!! So, now it seems I have a whole new set of problems...ugh....](*,)

I finally went to bed around 3am and had dreams about getting my graphics card working! haha

---

