---
title: "Log in problem in GNOME 3.12"
date: 2014-05-07
forum: New to Ubuntu
---

### Post by tusharkoshti on 2014-05-07
Hello Friends , 
I have just upgraded Ubuntu 12.04 to 14.04. 
I wanted to install GNOME 3.12. I followed following commands :

sudo apt-get update && sudo apt-get dist-upgrade 

sudo add-app-repository ppa:gnome3-team/gnome3-staging

sudo apt-get update && sudo apt-get dist-upgrade 

But now after restarting , password is required to log in. I didn't set any password.  
I just know only one password which is required after entering any command with "sudo". 
At log in screen , there are 2 session , one is session with my name and another is Guest session.
 In Guest session there written Log in. But if you hit enter , message is "Failed to start session". 
Did I make any mistake ? 
I think I didnt check whether I have GNOME 3.10 or not and just started to install GNOME 3.12. 
But now how to solve this problem ?
Please help.

---

### Post by kc1di on 2014-05-07
I'm not sure I understand exactly what's going on, but before you install gnome 3.12 were you using unity?  if so when you get to the login screen where it asks for your password.  you should find an option to open up in unity instead of gnome.  see if that works if it does let us know we'll go from there. 

Depending upon which Desktop manager you have install the option would be in different places if it's lightdm then in the upper right corner of the signin box there is a little round emblem click on that and select ubuntu from the list provided.

---

### Post by tusharkoshti on 2014-05-07
Before GNOME 3.12 , I was using Unity. ( I think it is by default.) 
GNOME  is the first software I have installed apart from few codec for movie and one theme. 
There was no log in screen before installing GNOME. I used to get Desktop screen directly. 
There is no any upper right corner of the signing box. 
There is only 2 session. 
1st one is Tushar (it's my name) and below there is space to enter password. 
2nd one is Guest session. Below there is written "Log In". We have to just press Enter to enter Guest session.
I can't enter password in Guest session.

---

### Post by bobmoyer on 2014-05-07
the guest session doen not require a password by default, to remove it I would suggest installing ubuntu-tweak if that is your desire.The main account of tushar would require a password to access. When you login,click on the ubuntu symbol in the boxwith your name and you should be able to select one of the gnome desktops(I prefer gnome-fallback myself)

---

### Post by tusharkoshti on 2014-05-07
There is no any symbol in the box with my name.
Only my name , and guest session. No ubuntu symbol ;(

---

### Post by philinux on 2014-05-07
[http://www.omgubuntu.co.uk/2014/05/upgrade-gnome-3-12-ubuntu-14-04?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2014/05/upgrade-gnome-3-12-ubuntu-14-04?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

 I think you were supposed to install gnome 3.10 from the repos first.

---

### Post by tusharkoshti on 2014-05-07
@ philinux :

I have installed gnome 3.12 from the link you have given.
But now problem is how to start Ubuntu to remove gnome 3.12 ?

---

### Post by philinux on 2014-05-07
Do the ppa purge from a recovery session I guess would be one way.

---

### Post by tusharkoshti on 2014-05-08
@philinux :
Can u tell me please , how to do ppa purge from recovery ?

---

### Post by slickymaster on 2014-05-08
> **tusharkoshti said:**
> @philinux :
Can u tell me please , how to do ppa purge from recovery ?

During boot press and hold the left Shift key. This will bring up the Grub2 menu from where you can select "Advanced options for Ubuntu".
[IMG]http://i.stack.imgur.com/01e8n.png[/IMG]
[SIZE=2][FONT=arial][COLOR=#333333]After that you will be able to select the kernel you wish to boot in *"Recovery mode"*:[/COLOR][/FONT][/SIZE]
[COLOR=#333333][FONT=UbuntuRegular][IMG]http://i.stack.imgur.com/UP5j7.png[/IMG][/FONT][/COLOR]
[SIZE=2][FONT=arial][COLOR=#333333]This will lead you to the advanced options. By selecting *"Enable networking"*  not only you'll gain access to your network and the internet for upgrades or downloads, but will also **mount your hard drives in read/write mode** to edit files.[/COLOR][/FONT][/SIZE]
[COLOR=#333333][FONT=UbuntuRegular][IMG]http://i.stack.imgur.com/fdmNg.png[/IMG][/FONT][/COLOR]
[SIZE=2][FONT=arial][COLOR=#333333]After the network has loaded, and the file system is mounted you will be presented again with the menu, from where you choose *"Drop to a root shell prompt"*:[/COLOR][/FONT][/SIZE]
[COLOR=#333333][FONT=UbuntuRegular][IMG]http://i.stack.imgur.com/tHkmh.png[/IMG][/FONT][/COLOR]
[SIZE=2][FONT=arial][COLOR=#333333]Note that you are root in this shell. Hence no sudo is needed for administrative tasks. This also means that you'll have full access to all files, and may cause irreversible damage to your system if you make a mistake.[/COLOR]
[COLOR=#333333]
In that root shell just run the command to purge whatever ppa you want[/COLOR]```
[COLOR=#333333]sudo ppa-purge ppa:name_of_the_ppa[/COLOR]
```[/FONT][/SIZE]

---

### Post by kansasnoob on 2014-05-08
GNOME 3.12 breaks Unity, but the GNOME and GNOME CLassic sessions are usable (albeit a bit buggy) if you install 'gnome-shell-extensions' and 'mutter':

```
sudo apt-get install gnome-shell-extensions mutter
```

---

### Post by tusharkoshti on 2014-05-09
@slickymaster :
I did what u suggest. 
I ran following command on command prompt. 

sudo apt-get install ppa-purge

sudo ppa-purge ppa:gnome3-team/gnome3-staging 

After successfully running above command I restarted PC ( it was not restarted automatically) 
but in vain. Problem could not be solved. Still I am getting Log in session ( with no password known)

---

### Post by tusharkoshti on 2014-05-09
@ kansasnoob :

Are you saying that I should run your code on command prompt from recovery session ?

---

