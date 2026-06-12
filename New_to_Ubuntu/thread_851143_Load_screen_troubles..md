---
title: "Load screen troubles."
date: 2008-07-06
forum: New to Ubuntu
---

### Post by pikabuntu on 2008-07-06
i downloaded the k desktop so i could switch back and forth between that and gnome, but now whenever it is loading before the login screen i see the kubuntu logo and a blue load bar

---

### Post by jualin on 2008-07-06
That's normal, you can switch from KDE to Ubuntu by simply changing it in Options, Sessions, in the log in screen.

---

### Post by nothingspecial on 2008-07-06
From memory thats just one of the things that go with the territory of having multiple desktops installed. It still boots into Ubuntu when you select it doesn`t it? Even if you get the blue splash screen?

---

### Post by pikabuntu on 2008-07-06
> **nothingspecial said:**
> From memory thats just one of the things that go with the territory of having multiple desktops installed. It still boots into Ubuntu when you select it doesn`t it? Even if you get the blue splash screen?

Yeah, i was just wondering how to change the splash screen

---

### Post by jualin on 2008-07-06
> **pikabuntu said:**
> Yeah, i was just wondering how to change the splash screen

> sudo ln -sf /usr/lib/usplash/usplash-default.so /usr/lib/usplash/usplash-artwork.so
sudo dpkg-reconfigure linux-image-$(uname -r) Someone suggested this in another forum. This is the [link]("http://linuxfud.wordpress.com/2006/08/13/changing-from-ubuntu-to-kubuntu/"). I don't know if this applies to Hardy Heron but you can give it a try, I cannot try it myself because I am not in my Ubuntu machine now.

---

### Post by jualin on 2008-07-06
I also found this online, even though this is not what you want is a way to customize the splash screens to make them unique. I thought that you might be interested in [gnome-splashscreen-manager]("http://packages.ubuntu.com/dapper/gnome/gnome-splashscreen-manager")

---

