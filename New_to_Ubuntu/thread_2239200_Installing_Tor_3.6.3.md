---
title: "Installing Tor 3.6.3"
date: 2014-08-12
forum: New to Ubuntu
---

### Post by dr4zkx on 2014-08-12
[COLOR=#000000][SIZE=2]Hi everyone, I started to learn about ubuntu 2 days ago so I'm a real newbie here with almost zero knowledge. Since last night I've been trying to install tor on ubuntu 14.04 lts. First to install it I used: 

"sudo apt-get install tor-browser"

but then I got the old version which is 3.6.2, when I lauched tor it told me to download 3.6.3 from the website so I did but was not able to extract nor install it directly from the file so I tried:

"wget [https://www.torproject.org/dist/torbrowser/3.6.3/tor-browser-linux32-3.6.3_en-US.tar.xz](https://www.torproject.org/dist/torbrowser/3.6.3/tor-browser-linux32-3.6.3_en-US.tar.xz)
tar -xJvf tor-browser-linux32-3.6.3_en-US.tar.xz
cd tor-browser_en_US
./start-tor-brower"

I was able to use tor 3.6.3 for a while but when I exit and tried to open it I couldn't find it anywhere so I decided to remove it and install it again but after I typed in 

"sudo apt-get remove tor-browser"
 
this appeared on my terminal : "package tor-browser is not installed, so not remove
I tried again from the wget step but still got the same problem. Any help will be very useful for me. Thank you for your time.
*and also if you guys have any website where I can learn how to use Ubuntu that'll be really appreciated. Please shed me some light since I'm so dark [/SIZE][/COLOR][CENTER][COLOR=#000000]:idea: [/COLOR][COLOR=#000000]:idea: [/COLOR][/CENTER]

---

### Post by bradwilliams923 on 2014-08-12
Apt-get is used to install applications from Ubuntu's repositories and  from enabled PPAs. When you installed version 3.6.3 you did it manually  from the tar file and not through apt-get, so apt-get doesn't keep up  with it, and that's why it wasn't removed. You should still be able to  start it with the "./start-tor-browser" command from the right  directory, but it would be more useful to create a .desktop file for the  application in /usr/share/applications. Did you have to use "sudo" when installing the tar file? Also, when browsing the /usr/share/applications directory, do you see an entry for the tor browser?

---

### Post by whitesmith on 2014-08-12
Your problem with Tor illustrates why it's so important to install using the Software Center. For example, an easy (GUI) way to tell whether a package is installed is to go there, type the name of the application, and see if its status is Remove or Install. Obviously, Remove = already installed. Sometimes there will be a situation like this one where the SC is not up to date, forcing you to download something from the developer's site. Normally you can grab a compressed .deb. After decompression simply double-click this file and the Software Center will install it for you, and then you will be able to track it as I described -- or by opening a terminal and:```
dpkg -l | grep Name-Of-Application
```This is better than the manual method because there's persistence of features that allow auditing. I hope I explained this in a way that doesn't demean your intelligence. You mentioned learning. Check out the sites on my sig line.

---

### Post by dr4zkx on 2014-08-13
> **bradwilliams923 said:**
> Apt-get is used to install applications from Ubuntu's repositories and  from enabled PPAs. When you installed version 3.6.3 you did it manually  from the tar file and not through apt-get, so apt-get doesn't keep up  with it, and that's why it wasn't removed. You should still be able to  start it with the "./start-tor-browser" command from the right  directory, but it would be more useful to create a .desktop file for the  application in /usr/share/applications. Did you have to use "sudo" when installing the tar file? Also, when browsing the /usr/share/applications directory, do you see an entry for the tor browser?
Thanks for your answer. No I didn't see the entry for tor browser on the "applications" folder, and I also didn't use "sudo" when install the tar file [CENTER][COLOR=#000000]:-k[/COLOR][/CENTER]

---

### Post by dr4zkx on 2014-08-13
> **whitesmith said:**
> Your problem with Tor illustrates why it's so important to install using the Software Center. For example, an easy (GUI) way to tell whether a package is installed is to go there, type the name of the application, and see if its status is Remove or Install. Obviously, Remove = already installed. Sometimes there will be a situation like this one where the SC is not up to date, forcing you to download something from the developer's site. Normally you can grab a compressed .deb. After decompression simply double-click this file and the Software Center will install it for you, and then you will be able to track it as I described -- or by opening a terminal and:```
dpkg -l | grep Name-Of-Application
```This is better than the manual method because there's persistence of features that allow auditing. I hope I explained this in a way that doesn't demean your intelligence. You mentioned learning. Check out the sites on my sig line.
Thanks for answering. As I mentioned above I've just starting to know linux over 2 days ago so yes my knowledge about the whole thing is very limited as of this moment. I'll definitely learn a lot more from your sign's sites.

---

### Post by dr4zkx on 2014-08-13
Figured. 
Please close the thread, thank you.
Cheers.

---

### Post by mörgæs on 2014-08-13
No, please mark it 'solved' using 'thread tools'. 
Also it would be nice to near what you did to make it work.

---

### Post by dr4zkx on 2014-08-13
> **mörgæs said:**
> No, please mark it 'solved' using 'thread tools'. 
Also it would be nice to near what you did to make it work.
I found a they have a lot of tutorials for linux mint so i changed to that. Ubuntu seems a bit hard for a noob like me

---

### Post by open2reason on 2014-08-13
dr4zkx, 
when next upgrading Tor you may wish to consider visiting and upgrading from the Tor site [https://www.torproject.org/](https://www.torproject.org/) [https://www.torproject.org/download/download-easy.html.en](https://www.torproject.org/download/download-easy.html.en) this being one of the few applications I would consider installing from outside the Ubuntu repos. 
Sometimes the version obtainable from Tor may be in advance of that offered via the repos.

---

