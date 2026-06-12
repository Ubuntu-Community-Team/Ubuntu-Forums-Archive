---
title: "Window Menu Bar Issue"
date: 2011-10-18
forum: New to Ubuntu
---

### Post by ryman90 on 2011-10-18
[SIZE=2]Hello everyone again.I installed Ubuntu Natty (11.04) a while ago and while installing all the necessary applications required,I also installed CompizConfig Settings Manager (ccsm) for better display effects.

This was working fine until day before yesterday,but since then due to some unknown reason,the title bar of each application or any of the folder that I open are not displayed properly leading to the following problems :
1) The minimize,maximize,close buttons get disappeared at start-up.
2) even the show desktop button when clicked shows  [/SIZE]"*your window manager does not support the show desktop button, or you are not running a window manager*"[SIZE=2] and the window switcher also doesnt work.

They are only restored when I run the command  *"compiz  --replace"* in the terminal everytime after the system boots up
This command restores all my windows back to normal as they were after I had installed Natty

Please help me with a solution that will restore my windows back to normal permanently and which doesnt involve typing [/SIZE][SIZE=2]"*compiz  --replace"*[/SIZE][SIZE=2] everytime in the terminal after boot.

Thanks a million
[/SIZE]

---

### Post by computerandu on 2011-10-18
You may try resetting the unity ...try and tell me if it works:

[http://www.computerandyou.net/2011/06/23/how-to-reset-unity-to-get-rid-of-messed-up-compiz-setting/](http://www.computerandyou.net/2011/06/23/how-to-reset-unity-to-get-rid-of-messed-up-compiz-setting/)

---

### Post by ryman90 on 2011-10-19
> **computerandu said:**
> You may try resetting the unity ...try and tell me if it works:

[http://www.computerandyou.net/2011/06/23/how-to-reset-unity-to-get-rid-of-messed-up-compiz-setting/](http://www.computerandyou.net/2011/06/23/how-to-reset-unity-to-get-rid-of-messed-up-compiz-setting/)
Thanks for the suggested solution,sir but it doesnt seem to work.The terminal says [I]"The program 'unity' is currently not installed.  You can install it by typing:
sudo apt-get install unity"[/I] 
and when I installed it first and then resetted it using "Unity --reset" the desktop was restored back to Unity if this is what you mean by Unity [http://upload.wikimedia.org/wikipedia/en/e/e1/Ubuntu_11.10_Final.png](http://upload.wikimedia.org/wikipedia/en/e/e1/Ubuntu_11.10_Final.png)

But the problem has now compounded  and either *"compiz  --replace"* [SIZE=2]or* "*[/SIZE]*metacity  -replace"* has to be done on every reboot with the terminal has to be kept undisturbed for undefined time and if its closed then it calls for a reboot as I virtually cant access anything simultaneously.

I think,my desktop environment has gone bust as there seems to be a clear conflict of Compiz,Unity and Metacity.

Please help me to restore it back to the classic Gnome interface with all my menus back to normal using the default Window manager and nothing fancy like Unity or Compiz..
Thanks again

---

