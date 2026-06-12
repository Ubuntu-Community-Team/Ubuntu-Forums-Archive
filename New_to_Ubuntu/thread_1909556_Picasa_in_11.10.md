---
title: "Picasa in 11.10"
date: 2012-01-15
forum: New to Ubuntu
---

### Post by 2CV67 on 2012-01-15
I have been using Picasa in Ubuntu for several years & have many thousands of pictures tagged & edited.

I just upgraded from 11.04 to 11.10 & can't see how to install Picasa.

It is no longer available via Software Center.
SynApt has gone completely :(
When I visit Picasa site it tells me simply there is no Picasa for my OS.

I installed wine, but that doesn't seem to help.

I suppose I might download Picasa via XP & try to open it in 11.10, but doubt my ability there.

I searched a lot & found methods for overwriting Picasa 3.0 with later versions, but I no longer have 3.0....

Thanks for any suggestions!

---

### Post by Linux1999 on 2012-01-15
Have you tried going into a terminal (ctrl + Alt + Del) and typing "sudo apt-get picaso" It will ask for your password and it could work or not. Reply either way.

-------------------------------------------------------------------
Suggestion 2
If it doesnt work at all throughout this thread you could try and install a older ubuntu into a virtual pc. Information about them here [http://en.wikipedia.org/wiki/Windows_Virtual_PC](http://en.wikipedia.org/wiki/Windows_Virtual_PC) windows vpc wont work so install virtual box (type into google)link here [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads) download it (linux Hosts) create a new vitual pc and open it. It will come with a black screen with a white cursor. Then you can put the disc in and restart the vpc console. If it doesnt do anything go into the vpc consoles boot device and change it to your DVD/CD drive. Then you just install it and dont update it again.

Hope I could help.

---

### Post by Fernhill Linux Project on 2012-01-15
Picassa is fully functional and accessible using picassa web, just go to [https://picasaweb.google.com/home](https://picasaweb.google.com/home) and log in.

---

### Post by 2CV67 on 2012-01-15
Well, thanks for those replies, but...

1.> Have you tried going into a terminal and typing "sudo apt-get picaso" It will ask for your password and it could work or not. Reply either way.
```
sudo apt-get picasa
E: Invalid operation picasa
```

2.> Picassa is fully functional and accessible using picassa web, just go to [https://picasaweb.google.com/home](https://picasaweb.google.com/home) and log in. 
If I go there in XP, I can download Picasa 3.9 OK.
If I go there in 11.10 - it mentions Picasa 3.0 but if I click on that link I just get error 404...

---

### Post by Fernhill Linux Project on 2012-01-16
Hmmm - interesting. I have never installed picassa on a linux box, I just use the on-line interface for uploading, editing and sharing. I am not sure why you are having trouble, but here is how it works for me, I am signed in to google (mail, you tube etc) and then I click on the link I posted you and I am at my picassa homepage and it shows my albums and various options for uploading etc. 
I am using Ubuntu 11.10 and Chromium, maybe chromium works better with googles online services - what browser do you use?

---

### Post by 2CV67 on 2012-01-17
Well - in fact it was simple enough...

I followed some of the instructions from here:
[http://www.webupd8.org/2012/01/install-picasa-39-in-linux-and-fix.html](http://www.webupd8.org/2012/01/install-picasa-39-in-linux-and-fix.html)

Just this bit:
```
cd && wget http://dl.google.com/picasa/picasa39-setup.exe
wine picasa39-setup.exe
```
and it works!

To be honest, it did throw up several fatal-looking error messages & I had to run the wine bit 3 or 4 times before it seemed happy, but anyway Picasa 3.9 is now running OK. :D

Thanks for all suggestions & thanks to webupd8 too!

I wonder why Google can't be bothered to even include simple instructions for Linux/Wine on their site?

And why Ubuntu can't include Picasa 3.9 in SynApt?

Oh - SynApt **_is_** still available from Software Sources. :D

---

### Post by oldfred on 2012-01-17
I installed 3.8 the same way you did.

But I also installed these:

114  wget [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)
  115  sudo wget [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)
  116  sudo chmod 777 winetricks
  117  sudo apt-get install cabextract wine wine-gecko
  118  winetricks allfonts fontsmooth-rgb gecko allfonts

And somewhere I found I had to edit this, not sure if still required with 3.9 or not.
                       /home/fred/.wine/drive_c/Program Files/Google/Picasa3/runtime defaults.ini 
remove chg printer2 to printers
printerURL=https://client4.google.com/providers/printers.html

---

