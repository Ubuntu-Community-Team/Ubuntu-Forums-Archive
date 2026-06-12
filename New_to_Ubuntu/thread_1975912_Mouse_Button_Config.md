---
title: "Mouse Button Config"
date: 2012-05-08
forum: New to Ubuntu
---

### Post by Phailed on 2012-05-08
First things first, let me know how I'm doing this wrong, this is my first post on the forums. I only started using Ubuntu a couple weeks ago, and I have lots to learn.

Essentially, I have a logitech mouse in perfect working order, and I'd like to be able to bind commands to the extra buttons on my mouse. I upgraded to Ubuntu 12.04 lastnight, the upgrade seems fine, except for btnx. When I was running 11.10, I installed btnx, and after a short while, managed to get it to work for me. I worked out that i had to use the terminal commands 'sudo (something i forget)' to actually apply the stuff I chose in btnx. I think it was 'sudo btnx cfg' but i could be wrong.

Anyhow, on upgrading to 12.04, btnx was no longer installed, and when I opened the software centre, it didnt let me install, said something about not being able to find btnx. I searched the internet, and found this website [http://askubuntu.com/questions/129996/how-to-set-volume-control-using-mouse-shortcut-in-ubuntu-12-04](http://askubuntu.com/questions/129996/how-to-set-volume-control-using-mouse-shortcut-in-ubuntu-12-04)
After downloading the 'main program' and 'gui', I apparently successfully installed btnx. Once i started it up, my existing mouse commands etc were already there (a little confusing but I wont complain). 
Sadly, the mouse commands were not applied/working. On 11.10 the way I applied the settings was by typing into the terminal (as stated above). However, now the terminal does not even recognize btnx? and when i click restart btnx, a window pops up saying Failed to execute command: "/etc/init.d/btnx restart". Make sure btnx is installed correctly.
After copying the command into the terminal, it does nothing.

This post is far to long and detailed im sure, but some help would be awesome. I've tried searching for solutions on forums/google, but they either dont apply or work.

I'm totally fine with using a program other than btnx, I simply dont know any others. Please keep in mind, although I want to get to know how to use ubuntu, im no computer whiz and I'm not too familiar with the Ubuntu and its associated jargon,

---

### Post by jtarin on 2012-05-08
[If your mouse is similar to this one you might try these configs.]("https://help.ubuntu.com/community/Logitech_Marblemouse_USB")
For Ubuntu 10.04 and newer

---

### Post by Phailed on 2012-05-08
Its a normal mouse, Just with some extra buttons. One of these to be precise
[http://www.logitech.com/en-nz/gaming/mice-keyboard-combos/devices/optical-gaming-mouse-g400](http://www.logitech.com/en-nz/gaming/mice-keyboard-combos/devices/optical-gaming-mouse-g400)

---

### Post by stinkeye on 2012-05-08
Never used btnx.
If you can't get it to work, have a look at easystroke.
I have the same mouse and is very easy to bind commands to spare buttons and gestures.
See [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=10495426&postcount=11")

---

### Post by Phailed on 2012-05-08
Awesome. Thanks heaps. Exactly what I was looking for

---

### Post by stinkeye on 2012-05-08
No problem.
**Tip:** If you use the mouse gestures, change the gesture button to right mouse.
Just release the mouse as soon as you complete the gesture so it doesn't bring up the the right click menu.
Easier to use than middle click.

---

