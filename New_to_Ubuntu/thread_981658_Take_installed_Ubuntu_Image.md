---
title: "Take installed Ubuntu Image"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by balachandarlinks on 2008-11-13
Hai,
  I installed ubuntu 8.10 in my system.I have an internet connection and so i updated and installed many apps in my ubuntu.But my friend doesnt have any internet connection.So **_how can i take the image of my ubuntu(from my harddisk with all apps)_**for my friend..So that he can boot with that ubuntu image to get all apps...plz anyone help...

---

### Post by aysiu on 2008-11-13
Does your friend also have identical hardware? If not, then you should avoid trying to copy the exact image of your Ubuntu machine.

What you can do, though, just for the apps, is copy everything in the /var/cache/apt/archives folder to a portable medium, then to the desktop of your friend's machine and then type these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
cd ~/Desktop
sudo dpkg -i *.deb
```

---

### Post by talsemgeest on 2008-11-13
You can make an image using a program called quickstart, you can get it here: [http://quickstart.phpbb.net]("http://quickstart.phpbb.net/")

Hope this helps :)

---

### Post by Viranh on 2008-11-13
You could also order an Ubuntu DVD and add it as a repository.

---

### Post by balachandarlinks on 2008-11-15
Can i get uduntu repo dvd for free of cost...

---

### Post by talsemgeest on 2008-11-15
You can download it here: [http://nginyang.uvt.nl/intrepid/](http://nginyang.uvt.nl/intrepid/)

---

