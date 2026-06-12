---
title: "How to install themes"
date: 2012-08-02
forum: New to Ubuntu
---

### Post by SergioMax on 2012-08-02
I have ubuntu 12.04 and I am trying to install a gtk3 theme but when I try to add the shell extensions for the gnome tweak tool (advance settings) it goes fine on the terminal and seams to install fine but when I click on shell extensions nothing appears therefore I cant activate any themes I have downloaded.

I am a newbie on any lunix os but I want to make this works, so please if anyone know how I can make this work let me know.

thanks

---

### Post by uzumakifahim on 2012-08-02
Welcome you to the world of Linux and Ubuntu Forum. Here is the link to download lots of themes. 

[http://gnome-look.org/index.php?xcontentmode=167](http://gnome-look.org/index.php?xcontentmode=167)

Most of the time you'll get installation instruction along with the downloaded package, if not share your problem here.

---

### Post by SergioMax on 2012-08-02
Thank you, I do know about the website. That is where I downloaded a couple of themes I wanted to try. But like I said before my problem is not about finding themes but the fact that I cant see anything on the shell extensions tab on advance settings (gnome tweak tool). The instructions tell me to use the terminal and type some commands to install the shell extensions option but no matter how many times I restart the computer it never shows anything on the shell extensions tab and that is where I need to go to apply the themes.

---

### Post by uzumakifahim on 2012-08-02
What desktop environment you are using? Is it Unity or Gnome shell?

---

### Post by SergioMax on 2012-08-02
Gnome shell

---

### Post by blade4 on 2012-08-02
Try Installing the User-Theme GNOME Shell extension from PPA. For that, simply copy-paste the following commands into Terminal. 

sudo add-apt-repository ppa:webupd8team/gnome3 
sudo apt-get update 
sudo apt-get install gnome-shell-extensions-user-theme


Hope this helps

---

### Post by SergioMax on 2012-08-02
Still didn't worked. I have tried other similar commands the same way and it all goes well on the terminal side but when I go to the shell extensions tab nothing shows up its all blank.
That's my problem for some reason it is not showing the shell extensions but it is installed

---

### Post by blade4 on 2012-08-02
I suppose you could try reinstalling gnome shell , but before that , try out myunity 

sudo apt-get install myunity 


I know you're using gnome shell but trying this can't do any harm

---

### Post by SergioMax on 2012-08-02
Thanks, myunity seams to be working.

I do have another question though. I can change themes and icons with myunity but there is no way to add extensions this way correct?
For example to change the dock and how it looks and stuff like that. All that seams to be only with the gnome shell.
If it is so, how can I make the gnome shell extensions to work.

---

### Post by blade4 on 2012-08-02
I've never used myunity and have limited experience with gnome shell so I can't say much , but if you're looking for dock modifications , I suggest installing cairo-dock . Its one the best linux docs available 

Cheers

---

### Post by uzumakifahim on 2012-08-03
That's great to know that Myunity is working good for you. If you want to add different extensions for Gnome-shell, then extensions.gnome.org would be a great place for you. This site will help you to get excellent extensions for gnome-shell. Not only that, this site will also show you the status of any extension, whether it's installed or not, if you visit that from your gnome-shell desktop. You just need to press the button on/off on that website to use a extension.

Moreover, if you want docks in ubuntu, then you have several choices, like
1. AWN
2. Docky
3. GLX/Cairo dock
4. Simdock

you can choose any of this. Each dock will give you panel to administer the dock.

Hope these information will help you.

---

### Post by drpjkurian on 2012-08-03
go to [https://extensions.gnome.org/](https://extensions.gnome.org/) for shell extension. I affirm uzumakifahim's suggestion

---

### Post by SergioMax on 2012-08-03
Thanks for the info

---

