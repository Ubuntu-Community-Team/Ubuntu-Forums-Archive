---
title: "How to make family PC w/ login screen for two users, that don't use passwords?"
date: 2013-05-02
forum: New to Ubuntu
---

### Post by queazy03 on 2013-05-02
Hi,

I'm very new to Xubuntu and just installed Xubuntu 13 Raring Ringtail for the family PC that my brother & father will use.  They want to use separate user accounts (so they can separate their different firefox bookmarks & wallpaper backgrounds etc).  They would like to access their separate accounts just like they did with Windows XP, where once the computer booted up there was a login screen and they just had to click on their name to enter into their user account (no password needed).  

How can I do this with Xubuntu?  Thank you.

---

### Post by nerdtron on 2013-05-02
I don't know a way for multiple user accounts for logging in just by clicking. I think this will be a good time to teach them about security. Just setup simple password for each of them and tell them to type it when logging in.

---

### Post by grahammechanical on 2013-05-02
In 13.04 we have a utility called User Accounts. There must be something similar in Xubuntu 13.04. There we can set Automatic Login On or Off. The user account will still need to have a password set. As the only user on my machine I have never tried to do what you want to do. But User Accounts is where I would try to do it.

Set up two new user accounts. Set them both as Standard user. I assume that you are set up as Administrator. Then set the slider for each account to have Automatic Login as ON. See if that works.

Regards.

---

### Post by queazy03 on 2013-05-02
> **grahammechanical said:**
> In 13.04 we have a utility called User Accounts. There must be something similar in Xubuntu 13.04. There we can set Automatic Login On or Off. The user account will still need to have a password set. As the only user on my machine I have never tried to do what you want to do. But User Accounts is where I would try to do it.

Set up two new user accounts. Set them both as Standard user. I assume that you are set up as Administrator. Then set the slider for each account to have Automatic Login as ON. See if that works.

Regards.

Hi,

I've actually done something like that already and have created both accounts, set them up as users with automatic login (that does not require passwords).  However the issue is that on startup Xubuntu does not bring up a login screen like this example in Windows XP (the OS they are most familiar with), like the example at  "[http://imgur.com/7BSqDRD](http://imgur.com/7BSqDRD)".

Instead what happens when they power on the computer is 


[LIST=1]
[*][SIZE=3]Ubuntu asks if we want to load it or advanced options or Memtest
[/SIZE]
[*][SIZE=3]Xubuntu loads...and goes straight into the administrator account, skipping the option to allow either user account to login.
[/SIZE]
[/LIST]


**1) **Ubuntu asks if we want to load it, or advanced options or Memtest.  See picture 2nd from top on right hand side at "[http://i.imgur.com/vIUQri1.jpg](http://i.imgur.com/vIUQri1.jpg)", please note that problem stated in this picture has already been solved.
[COLOR=#ff0000][I][SIZE=2]**Eventually I want the "Start Ubuntu" option to be automatically selected, so my family can just press power button on PC and have it automatically load up, how can I do this?**[/SIZE]
[/I][/COLOR][COLOR=#ff8c00]
[/COLOR]**2) **Xubuntu loads and goes straight into administrator account, skipping option to allow either user to login before hand. 
 ***[COLOR=#ff0000]Is there a way to have it present an account login screen on start-up similiar to [/COLOR]"[http://imgur.com/7BSqDRD](http://imgur.com/7BSqDRD)"?***
[COLOR=#ff8c00]
[/COLOR]**3) **Lastly, I am also trying to install some third party software like IrfanView (from "[www.irfanview.com]("http://www.irfanview.com/")") or printer software, and I get "An error occured when loading the archive".  See "[http://imgur.com/Xk3eiP5](http://imgur.com/Xk3eiP5)".  I have no idea what I am doing wrong.  
***[COLOR=#ff0000]How can I install third party software without receiving this error?  [/COLOR]***

Thank you.

---

### Post by nerdtron on 2013-05-02
> **queazy03 said:**
> [COLOR=#ff8c00]
[/COLOR]**3) **Lastly, I am also trying to install some third party software like IrfanView (from "[www.irfanview.com]("http://www.irfanview.com/")") or printer software, and I get "An error occured when loading the archive".  See "[http://imgur.com/Xk3eiP5](http://imgur.com/Xk3eiP5)".  I have no idea what I am doing wrong.  
***[COLOR=#ff0000]How can I install third party software without receiving this error?  [/COLOR]***


You want Infraview as a photoviewer or photo manager? That is a .exe Windows installer which will not work under Linux. You should install WINE first.

Now, how do you install WINE? It is in the Software Center. While you are at the Software Center, you should look at other native alternatives to Infraview like Shotwell or other image viewers.

---

### Post by gordintoronto on 2013-05-02
> **nerdtron said:**
> You want Infraview as a photoviewer or photo manager? That is a .exe Windows installer which will not work under Linux. You should install WINE first...

Irfanview works beautifully in WINE, but you might wish to have a look at Linux applications which do similar things. However, I have not found one which will link to GPS coordinates in a photo, as Irfanview can.

In Xubuntu, you have Synaptic Package Manager to install Linux applications. It's not the way we installed programs in Windows.

---

### Post by queazy03 on 2013-05-03
I think I found something that will answer my question about logins.

Take a look at 
[http://askubuntu.com/questions/113500/why-am-i-not-asked-for-password-at-startup](http://askubuntu.com/questions/113500/why-am-i-not-asked-for-password-at-startup)


It seems my solution will be to edit the "/etc/lightdm/lightdm.conf" file, and change "autologin-user=" to a value of "false".


However the issue is that whenever I try to edit this file with Mousepad, it does not allow me to save because it says permission is denied. This is very strange because I am logged in as the administrator. 



How can I properly edit & save this file?

> **nerdtron said:**
> You want Infraview as a photoviewer or photo manager? That is a .exe Windows installer which will not work under Linux. You should install WINE first.

Now, how do you install WINE? It is in the Software Center. While you are at the Software Center, you should look at other native alternatives to Infraview like Shotwell or other image viewers.

Oh, I didn't know that.  I will try Shotwell.

Thank you, looking forward to any advice.

---

### Post by nerdtron on 2013-05-03
> **queazy03 said:**
> 


It seems my solution will be to edit the "/etc/lightdm/lightdm.conf" file, and change "autologin-user=" to a value of "false".

How can I properly edit & save this file?



By the way, the software center in Xubuntu is Synaptic Package Manager. Just search for the app you like and hit install.

For editing text files as administrator: (Be careful when using this method. You might delete or alter something about the system)
Press Alt+F2
```
gksu thunar
```

Provide your password and navigate to the location of the file. In your case, /etc/lightdm/ then open the lightdm.conf file.
You should be able to edit and save it now.

---

