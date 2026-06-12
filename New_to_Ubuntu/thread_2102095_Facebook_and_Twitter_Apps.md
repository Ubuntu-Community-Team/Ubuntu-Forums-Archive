---
title: "Facebook and Twitter Apps"
date: 2013-01-06
forum: New to Ubuntu
---

### Post by ianb72 on 2013-01-06
I was watching the video for the upcoming Ubuntu Mobile phone OS and they showed the Desktop version having Facebook and Twitter updates coming directly to your desktop where your Mail icon is, top right hand corner.
I was wondering how I went about getting these apps installed on my desktop?

---

### Post by iMurshaq on 2013-01-06
there arent any "facebook" desktop apps for ubuntu but if you check the sofware center you should be able to find some programs that will work for you like notification alerts, and programs similar to tweetdeck.

Good luck!!

---

### Post by ianb72 on 2013-01-06
Cheers

> **iMurshaq said:**
> there arent any "facebook" desktop apps for ubuntu but if you check the sofware center you should be able to find some programs that will work for you like notification alerts, and programs similar to tweetdeck.

Good luck!!

---

### Post by Rocklobster690 on 2013-01-06
> **ianb72 said:**
> I was watching the video for the upcoming Ubuntu Mobile phone OS and they showed the Desktop version having Facebook and Twitter updates coming directly to your desktop where your Mail icon is, top right hand corner.
I was wondering how I went about getting these apps installed on my desktop?

Facebook & Twitter can run as web app's in Quantal. 

[http://www.webupd8.org/2012/09/unity-webapps-available-in-ubuntu-1210.html](http://www.webupd8.org/2012/09/unity-webapps-available-in-ubuntu-1210.html)
[http://www.youtube.com/watch?feature=player_embedded&v=L2YNR1KU1Xs](http://www.youtube.com/watch?feature=player_embedded&v=L2YNR1KU1Xs)

Ubuntu for phones will be supporting both HTML5 and native apps.

---

### Post by Rocklobster690 on 2013-01-08
To install web apps in Precise and **Quantal**:

```
sudo add-apt-repository ppa:webapps/preview
sudo apt-get update
sudo apt-get install unity-webapps-preview
```

Browse to Twitter or Facebook using Firefox (this also works for Chromium but requires a plugin). You should get a pop up asking to install a service and once completed an icon will appear in the launcher.

As far as I'm aware these are the HTML5 apps that will be available in Ubuntu for phones. 

Give it a try :D

---

