---
title: "How do I change the startup splash screen?"
date: 2012-07-03
forum: New to Ubuntu
---

### Post by Scorch13 on 2012-07-03
So I'm running ubuntu 12.04 LTS. Wanted to know how I can completely customize my startup which includes the wallpaper, logo etc.

I searched on this and found ubuntu Tweak and Boot Manager etc but they don't install. I do it through the terminal. They use 'ppa' for download and I always get a 404 error, the download never completes. 

Need help, i'm new to linux so don't know much.

---

### Post by archeryguru2000 on 2012-07-03
Not sure if this is the method that you've tried... but here is a link to a relatively easy installation of UbTweak.

[[COLOR="Blue"]_ubuntu-tweak_[/COLOR]]("http://www.liberiangeek.net/2012/04/install-ubuntu-tweak-0-7-in-ubuntu-12-04-precise-pangolin/")

Make sure you copy & paste the commands correctly (to avoid any 404 errors with the hyperlinks).  Good luck and let us know if all goes well.

~~archery~~

---

### Post by Scorch13 on 2012-07-04
I searched on it and have Ubuntu Tweak installed but for some reason I can't change the startup screen. I only see the screen I wanted at login and that too for less than a second. And the logo does not change at all.

---

### Post by baizon on 2012-07-04
You have to unlock that option. There is a lock icon in the upper right corner.

---

### Post by Scorch13 on 2012-07-04
I did unlock it and applied the changes.

Edit: This is what I did in the first place. That is I unlocked it changed the logo and splash screen. The logo never appeared when I restarted and the splash just for a fraction of a second.

---

### Post by baizon on 2012-07-04
OK, are your Wallpaper .png or .jpg?
I had to copy there wallpaper to: /usr/share/backgrounds (as root), because my wallpaper wasn't in the boot partition (was in /home) and the drive wasn't mounted. That fixed my problem.

---

### Post by Scorch13 on 2012-07-05
The logo is .png and wallpaper .jpg.
What are the correct formats? And also the resolution.

---

