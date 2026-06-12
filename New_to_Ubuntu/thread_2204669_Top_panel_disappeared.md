---
title: "Top panel disappeared"
date: 2014-02-09
forum: New to Ubuntu
---

### Post by dtommy79 on 2014-02-09
Hi,

My brother managed to make all my menu bars disappear. I don't have the top menu where I can log out, and the side menu also disappeared. So right now there is nothing on my screen. 

How can I bring them back?

Thanks

---

### Post by UltimateCat on 2014-02-09
It sounds like part of your desktop envirnment defaults got changed or misconfigured.

Try restarting your computer first.
  **IF** that doesn't work than you might have to operate in console mode only if the links to the articles I posted don't work.

Try the first link.
If that doesn't work I posted 2 other articles that I found that should help-

[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

[http://lifehacker.com/5581364/reset-gnome-when-things-go-wrong-on-your-linux-desktop](http://lifehacker.com/5581364/reset-gnome-when-things-go-wrong-on-your-linux-desktop)
[http://www.rebelzero.com/fixes/ubuntugnome-environment-reset/86](http://www.rebelzero.com/fixes/ubuntugnome-environment-reset/86)


-:-You might want to set up a guest or another user account that does not have administrative privileges-:-

---

### Post by dtommy79 on 2014-02-10
Thanks for the reply. 

I tried those options but no luck. Nothing happens. 

Actually this happened with another user account. When I log in with my user account everything is fine, but when I log in with my brother's all the menus are missing.

---

### Post by G_Ajith_Kumar on 2014-02-10
Hi, There is a post in Ask Ubuntu on this topic at this link: 
[http://askubuntu.com/questions/286088/menu-bar-and-launcher-missing-in-ubuntu-13-04](http://askubuntu.com/questions/286088/menu-bar-and-launcher-missing-in-ubuntu-13-04)

You could try these commands at the terminal


dconf reset -f /org/compiz/ 
  then enter:

  unity --reset-icons &disown

reboot if necessary.

You may also like to read [http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears](http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears)

Good luck!!!!!!!!

---

