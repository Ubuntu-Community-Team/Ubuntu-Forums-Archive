---
title: "Alsa problem with retro Desktop appearance"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by soyuz_one on 2008-05-17
This morning I tried to solve an ongoing problem I had with getting the microphone to work for skype on gutsy. Long story short I managed to get it to work by using the following set of commands

#sudo /etc/init.d/alsa-utils restart
#wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2)
#tar -xjf alsa-driver-1.0.14.tar.bz2
#cd alsa-driver-1.0.14
#./configure
#sudo make
#sudo make install

which I got from [http://geekybits.blogspot.com/2007/06/microphones-skype-on-ubuntu.html]("http://geekybits.blogspot.com/2007/06/microphones-skype-on-ubuntu.html")

However once I had finished my phone call I soon discovered that I had no hard control over the volume. Being a newbie I just went for the brute force hard reset solution. When the machine rebooted the desktop had changed (for the worse). It looks like a slightly older version of ubuntu

[http://ubuntuforums.org/album.php?albumid=175&pictureid=534]("http://ubuntuforums.org/album.php?albumid=175&pictureid=534")

Most worringly the laptop has also slowed down significantly and doesn't load some applications at all. I understand the symptoms aren't very well defined but I'm hoping that someone might be able to identify the problem and solution from the commands above.

I'm running Gutsy 7.10 on an X61 Thinkpad.

PS This is my first post so I apolgise if this post isn't the best.

---

### Post by soyuz_one on 2008-05-17
I've also just tried to restart the alsa utility with 

#sudo /etc/init.d/alsa-utils restart

which is one of the commands I used earlier to solve the microphone problem and I got no response from the terminal. Also when I try to access the System -> Preferences -> Appearance I get the following response

[http://ubuntuforums.org/album.php?albumid=175&pictureid=535]("http://ubuntuforums.org/album.php?albumid=175&pictureid=535")

Hopefully this will help diagnose the problem.

---

### Post by soyuz_one on 2008-05-17
Problem solved. Somehow when I was messing around with Alsa, the session default was changed from Gnome to Xclient or failsafe Gnome. I don't understand how that happened but it's fixed.:)

---

