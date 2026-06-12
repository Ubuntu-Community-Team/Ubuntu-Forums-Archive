---
title: "Which Skype client to install?"
date: 2018-04-27
forum: New to Ubuntu
---

### Post by wrongusername2 on 2018-04-27
Hi 
          I am trying to install skype on Ubuntu 16.04. Should I install "Skype from Ubuntu Software" or "Skype from Microsoft website". 

 "Skype from Ubuntu Software" gave following error, while "Skype from Microsoft website" installed and is working also.
  
```
Detailed errors from the package manager follow:
snapd returned status code 400: Bad Request

```

If I want o install  "Skype from Ubuntu Software", do I need snap package?
Which client is better? 


TIA

---

### Post by #&amp;thj^% on 2018-04-27
> **wrongusername2 said:**
> Hi 
          I am trying to install skype on Ubuntu 16.04. Should I install "Skype from Ubuntu Software" or "Skype from Microsoft website". 

 "Skype from Ubuntu Software" gave following error, while "Skype from Microsoft website" installed and is working also.
  
```
Detailed errors from the package manager follow:
snapd returned status code 400: Bad Request

```

If I want o install  "Skype from Ubuntu Software", do I need snap package?
Which client is better? 


TIA
Just depends on how either one behaves with your system. ;)
I will show both ways to help if one dose not act correctly.
Canonical has announced (During the 17.10 release) that Skype is now available as a Snap, so it can be installed direct from the Ubuntu-Software or by using snap:
```

snap install --classic skype
```

***Or you can use the link: [https://snapcraft.io/skype](https://snapcraft.io/skype)

Old Method is also availbale:

If you prefer to install it with Debian package manager use the old method:

Refer to the [https://www.skype.com/en/get-skype/](https://www.skype.com/en/get-skype/) page. Then choose the option get Skype for linux Deb.    

A ".deb" file will be downloaded. Open the terminal, install from that directory to the folder where the .deb was downloaded (Or right mouse click in the folder and choose open in terminal). Then run:
```

sudo dpkg -i skypeforlinux-64.deb
```

if it shows any problems with the install run: 
```
sudo apt install -f
```

when it finishes you can delete the skypeforlinux-64.deb file if you choose.
Good luck.

---

### Post by wrongusername2 on 2018-04-27
Thanks, I was able to install using "[COLOR=#000000][FONT=&quot]snap install --classic skype"[/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2018-04-27
:) Enjoy.>> Let us know here in this thread how it works for you over time. 
Kind regards

---

