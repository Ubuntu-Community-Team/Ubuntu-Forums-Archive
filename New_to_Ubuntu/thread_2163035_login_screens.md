---
title: "login screens"
date: 2013-07-16
forum: New to Ubuntu
---

### Post by kom333 on 2013-07-16
Hello! :D

I have just installed Ubuntu 13.04 on my laptop and I wanted to change login screen. Earlier I found some link, with few solutions. That helped me on Ubuntu 10.04, but now I have some problems. Here 's that link:
[http://www.howtogeek.com/howto/45315/how-to-change-the-ubuntu-linux-login-screen/](http://www.howtogeek.com/howto/45315/how-to-change-the-ubuntu-linux-login-screen/) .

So is there any other way how to change login screen and someone knows it, I 'd very greatful!!! :D

---

### Post by papibe on 2013-07-16
Hi kom333.

From 12.04, the login screen uses the same pic has been set on your desktop's background. If you want to set a custom image, just make sure it is in your ~/Pictures folder.

Let us know how it goes.
Regards.

---

### Post by kom333 on 2013-07-17
Hi papibe. Yes I know that the login screen uses the same pic. But I want some other pic. 
Ok I put selected picture in ~/Pictures folder. What now? How to add that picture on login screen? :D

---

### Post by papibe on 2013-07-17
If I understand correctly you want a custom background for the login screen, that is different from the wallpaper is set on your desktop.

Is that it? If so, take a look at this tutorial: [How To Change LightDM (Login Screen) Background]("http://www.webupd8.org/2011/09/how-to-change-lightdm-login-screen.html").

Let us know if that helped or not.
Regards.

---

### Post by su:bhatta on 2013-07-18
> **papibe said:**
>  so, take a look at this tutorial: [How To Change LightDM (Login Screen) Background]("http://www.webupd8.org/2011/09/how-to-change-lightdm-login-screen.html").



I used that page & this one:
[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

 to get the unity-greeter on my Ubuntu Studio(Xfce DE), which only had the ugly gtk-greeter...

---

### Post by kom333 on 2013-07-18
Yes papibe, you are right, i want custom pic. 

Than you both for your helpful links. ):P I didnt have time to try that advices. I will try it in a few days and let you know the outcome. :D

---

### Post by parl8256 on 2013-07-30
Am I correct in inferring that LightDM is the default display manager for 12.04 (which I am using), at least during log-in? What I'd like to have during log-in is the default background for 12.04, but I'm not sure what it's called. Could I go into a new user and see what the wallpaper is called? Thanks for your support.

I've actually been a member of these fora for a while, but since the recent contretemps, I guess I have a new identity.

Ross

---

### Post by papibe on 2013-07-31
> **parl8256 said:**
> Am I correct in inferring that LightDM is the default display manager for 12.04 (which I am using), at least during log-in?
Yes.
> **parl8256 said:**
> What I'd like to have during log-in is the default background for 12.04, but I'm not sure what it's called. Could I go into a new user and see what the wallpaper is called? Thanks for your support.
You have two alternatives:
[LIST]
[*]You can set your wallpaper inside your desktop using the tool 'Appearance'. LightDM then would select the same one for the login screen; or
[*]You can use the instructions on the link on post #4 and select the location of the picture: /usr/share/backgrounds/warty-final-ubuntu.png
[/LIST]
> **parl8256 said:**
> I've actually been a member of these fora for a while, but since the recent contretemps, I guess I have a new identity.
You can recover your old account, beans and settings. There are several cases like this in this subforum: [Resolution Centre]("http://ubuntuforums.org/forumdisplay.php?f=123"). Read the relevant topics and follow the instructions given there.

In case you are not able to recover your account by yourself, create a new thread in that subforum requesting help.

Let us know how it goes.
Regards.

---

### Post by LinuxUser666 on 2013-07-31
I would say the easiest way to do that is simply do ```
sudo gedit /etc/lightdm/lightdm-gtk-greeter.conf
```
It will open you gedit text editor, this is the output without comments ```
[greeter]
background=/usr/share/xfce4/backdrops/xubuntu-precise-right.pngtheme-name=Greybird-lightdm
font-name=Droid Sans 10
xft-antialias=true
xft-dpi=96
xft-hintstyle=slight
xft-rgba=rgb
show-language-selector=true

```
In part ```
background=
``` just copy your custom picture's address. :D 
Worked for me.

---

### Post by kom333 on 2013-08-16
Thank you LinuxUser666, i tried that but still there are no results. :(

---

