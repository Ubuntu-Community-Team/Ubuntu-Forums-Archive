---
title: "installing bin files"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by cavrep on 2008-07-11
I have downloaded GoogleEarthLinux onto my desktop. It is a bin file. I right clicked hoping and install program would pop up - no luck. How do i install a bin file?

---

### Post by Dark_Stang on 2008-07-11
Right click, go to properties. Click the permissions tab, and towards the bottom make sure "Allow executing file as program" is checked. Then close that window and double click on it.

---

### Post by shp on 2008-07-11
make it +x (executable)

type into terminal
sudo chmod +x Desktop/GoogleEarthLinux.bin

---

### Post by SunnyRabbiera on 2008-07-11
some binaries are iffy... its usually better to use repositories.
for google earth try medibuntu:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by hyper_ch on 2008-07-11
always use repos (if possible)

---

### Post by barberic on 2008-07-19
I have a similar problem with /home/eric/Desktop/hidpoint1-0.bin on Ubuntu 8.04
It's a mouse config program.
If I double click on the icon on the desktop I get a message 

Couldn't display "/home/eric/Desktop/hidpoint1-0.bin".
There is no application installed for this file type

I then tried the Terminal as suggested in post #3.
Terminal ran OK, uncompressed the file then returned me to a command prompt.
Nothing changed with the .bin file.

There is no repos for this program on the web page.

Do I need to install a program to handle .bin files?
If so what do i need and where would I get it?
Thanks if you can help.

---

### Post by RomeReactor on 2008-07-19
Hi. After making it executable (see post 2 or 3), run either of these in a terminal:
1.- ```
cd Desktop
```
and:
```
sudo ./hidpoint1-0.bin
```

Or

2.- ```
sudo ~/Desktop/hidpoint1-0.bin
```

---

### Post by barberic on 2008-07-19
Thanks RomeReactor
Did that and got message
"Unsupported Kernel version"

The web page claims Ubuntu 8.24 and my Logitech mouse model are supported. 
Hmmmmm

---

### Post by RomeReactor on 2008-07-19
> **barberic said:**
> Thanks RomeReactor
Did that and got message
"Unsupported Kernel version"

The web page claims Ubuntu 8.24 and my Logitech mouse model are supported. 
Hmmmmm

Looks like it's a [known issue on their site]("http://209.85.141.104/search?q=cache:xHh7SEvkg8YJ:www.hidpoint.com/forum/id,54/catid,16/func,fb_pdf/+%22unsupported+kernel+version%22+site:http://www.hidpoint.com/&hl=en&ct=clnk&cd=1&client=firefox-a") ([Two]("http://www.hidpoint.com/forum/func,view/catid,16/id,49/") [more]("http://www.hidpoint.com/forum/func,view/catid,16&id=/id,25/catid,16/") posts on their forum).

---

### Post by barberic on 2008-07-19
Thanks once again RomeReactor.
Guess I didn't dig deep enough on their web page.
I will just put up with the limited mouse functionality until they fix it.

Just installed Linux for the first time this week and enjoying the experience.

---

### Post by RomeReactor on 2008-07-19
You could try searching these forums for your mouse model to see if there are ways to enable more functionality without installing that driver.

---

### Post by barberic on 2008-07-19
Yes, that's how I found hidpoint by searching this and other forums together with a bit of Googling. Always like to try and help myself before posting to any forum. 
Hidpoint reckon they've fixed it a month ago and to download the latest file according to this post on their forum
[http://www.hidpoint.com/forum/func,view/catid,17&id=/id,20/catid,17/]("http://www.hidpoint.com/forum/func,view/catid,17&id=/id,20/catid,17/")
Seeing it was only downloaded today looks like it still don't work.

---

