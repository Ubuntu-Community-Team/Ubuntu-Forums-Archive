---
title: "Screen Zoomed in HELP"
date: 2012-04-19
forum: New to Ubuntu
---

### Post by Zachiryus on 2012-04-19
I just installed ubuntu 11.10 on my computer and my screen is so far zoomed in that i can't see the whole page of certain things such as system settings i can't see all the settings no matter what i do please help. i already tried using zoom in and zoom out functions.

I can in fact see all of the system settings if i use workspace switcher and switch to the workspace under the one that system settings is open on i am able to see the bottom of the page but this is extremely irritating please help.

---

### Post by hakermania on 2012-04-19
I think it's a resolution issue. Check if  you can apply the things said on this page on how to change resolution thought terminal, if you are not able to access it through the 'settings' program: [http://www.tricksfind.in/2011/04/how-to-set-resolution-via-terminal-in.html](http://www.tricksfind.in/2011/04/how-to-set-resolution-via-terminal-in.html)

---

### Post by audiomick on 2012-04-19
> **Zachiryus said:**
>  i already tried using zoom in and zoom out functions.

Which zoom functions?

It sounds like you need to do ctrl+- a few times. That should get you back out to a normal view. The zoom in that seems to have been invoked is
ctrl++

---

### Post by Zachiryus on 2012-04-19
> **hakermania said:**
> I think it's a resolution issue. Check if  you can apply the things said on this page on how to change resolution thought terminal, if you are not able to access it through the 'settings' program: [http://www.tricksfind.in/2011/04/how-to-set-resolution-via-terminal-in.html](http://www.tricksfind.in/2011/04/how-to-set-resolution-via-terminal-in.html)

After trying the terminal commands on the page i realized it is definitely a resolution issue. However,       the (-s 0) setting is what it is already on is there a lower setting that you know of?

---

### Post by Zachiryus on 2012-04-19
i recently installed ubuntu 11.10 and i noticed that everything was extremely large (zoomed) someone already helped me find out the issue however i can not solve it quite yet. the issue was that my resolution is off. my xrandr setting is already 0 (lowest) but my everything is still too large for me to be able to work properly. please help!

---

### Post by NikTh on 2012-04-19
Hi ,
i think that your problem will solve easyest if you give more info .. 
```
lspci -nn | grep VGA
cat /etc/lsb-release
``` 
Thanks

---

### Post by Zachiryus on 2012-04-20
sorry for the late reply... 
lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV43 [GeForce 6600] [10de:0141] (rev a2)

---

### Post by nothingspecial on 2012-04-20
Merged

---

### Post by NikTh on 2012-04-20
> **Zachiryus said:**
> sorry for the late reply... 
lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV43 [GeForce 6600] [10de:0141] (rev a2)

see the output of this command 
```
apt-cache policy nvidia-current
``` 
if nvidia is installed then do 
```
sudo nvidia-xconfig
``` 
and reboot to see if problem fixed.

---

