---
title: "New User"
date: 2012-12-31
forum: New to Ubuntu
---

### Post by Mike Zahorik on 2012-12-31
I'm using Ubuntu 9.10 and have been attempting to us gnome-device-manager. Can't find it, Package Manager will not set it up and there is a problem when I attempt to download it from one of the mirrors. What am I doing wrong?
Mike

---

### Post by Cheesemill on 2012-12-31
You are using an outdated version of Ubuntu. 9.10 reached end-of-life in April last year (2011), meaning it no longer receives any support, bug-fixes or software updates (and hasn't done for nearly 2 years). One of the effects of this is that the repositories are moved off-line, meaning that you can no longer use the package manager or any of the mirrors to download software.

I would highly recommend installing a version of Ubuntu that is still being supported, for example 12.04 has support until 2017.

---

### Post by Mike Zahorik on 2012-12-31
Well....... I had 12.10 on my machine for a while, but I went to the library and got a book on Ubuntu. The book is very interesting but is written for Ubuntu 9 and most everything that the book suggests didn't work  on 12.1. Besides I very much dislike the graphical interface and much more prefer the menu interface that 9.10 has. it is rather difficult to jump into some new with a reference to use to help out. 

I tried very hard to find a menu user interface much like that of 9.1 for 12.10, but was not seccessful in getting anything to work.

Mike

---

### Post by Cheesemill on 2012-12-31
You can make 12.04 look almost identical to the old versions by using the Gnome classic session rather than the default Unity session.
Or you could stick with Unity and read reference guides to that instead:
[https://help.ubuntu.com/12.04/ubuntu-help/index.html](https://help.ubuntu.com/12.04/ubuntu-help/index.html)

There is also the option to use Xubuntu instead which has a similar menus and panels set up.

In fact there are several different options available to you, the only one I wouldn't recommend is using an outdated version of Ubuntu as your system will be using software that has bugs and security problems that will never get fixed.

---

### Post by Mike Zahorik on 2012-12-31
Thanks for replying. I did have a XUbuntu set up for a while, but balled it up somehow and never really got it working. I also tried to get the gnome menus on 12.10, but also had trouble getting that going also. I see that you are recommending 12.04. Should I use that instead of 12.10. I was secussful in making a 12.10 64 bit DVD to load it.  

Mike

---

### Post by Cheesemill on 2012-12-31
I would recommend 12.04 for a new user as it is more stable and supported for longer.

If you go for 12.10 you will have to upgrade your OS in just over a years time whereas 12.04 is supported until 2017.

---

### Post by Mike Zahorik on 2012-12-31
OK..... I can do that. Then can you suggest
1. How to install the gnome menu's --- would that be through the package manager?
2. Do you know of a physical paper reference that I can read to help out and bother you guys a lot. I'm an old man attempting to fill my retirement time by learning something new. Besides I'm tired of contributing to the MicroSoft empire.
3. I've been reading about things like Device manager and other system tools. Where can I find out more about this?

Thanks I appreciate your help 

Mike

---

### Post by superDave972 on 2012-12-31
If you are using Ubuntu 12.04, you can easily install the Gnome DE by using the Ubuntu Software Center.

---

### Post by Mike Zahorik on 2012-12-31
I'm downloading it now, probably take a few more minutes. My hardware is old and slow, much like me.  First thing I'll do is attempt to get gnome de to work. Is that it's complete name?

Mike

---

### Post by superDave972 on 2012-12-31
DE was just my abbreviation for Desktop Environment and it is not part of the "Gnome" name.

When I installed Gnome through the Software Center, I just searched for 'gnome' and found it that way.

If you prefer, you can also just type the following command into a terminal. It may be faster to install the Gnome DE that way.
```
sudo apt-get install gnome-session-fallback
```

---

### Post by Mike Zahorik on 2012-12-31
While I'm waiting for the 12.04 download to complete. I looked up gnome de and frond that I can use the terminal and a few commands

sudo apt-get install gnome-session-fallback

sudo apt-get install gnome-panel

I know a little here. I can get the terminal up and running and also understand what sudo is. apt-get install is almost English and I figure I know this. How does one find or know the remainder of these commands?

Mike

---

### Post by Mike Zahorik on 2012-12-31
Sorry.... I must have been typing as you were.

---

### Post by superDave972 on 2012-12-31
No worries. Also, I am not sure what you mean by the "remainder of these commands." If you are looking for a directory containing a list of all commands that you can enter into a terminal prompt, that list would be nearly endless.

I find most of my terminal commands by using the forums or Google. I do believe that if you want to install something from the Software Center, "sudo apt-get install [name of package]" usually does the trick.

---

### Post by Mike Zahorik on 2012-12-31
I have to profess ignorance here. What I was referring (thanks to you) is the package name.

I just did a search on ebay and found a book "Ubuntu 12.04" selling for about $35. It is any good? I have not spent that much on my computers. My neighbors seem to just throw away their machines after they become stuck. So I have cobbled together a number of machines of varies flavors and Os's. And given away a few to the local kids who are having fun experiment with them. 

Anyway I'm pretty cheap (fixed income and all that stuff). So I chock on those kind of book prices. I know that you may say look on the internet, But my eye sight is not as good as it used to be and after a while looking at the screen I have to give up. Books don't do that.

Well...... the download of 12.04 is almost done. I'll burn a DVD and load it up and try a few things and most likely be back here later.

Thanks, Mike

---

### Post by speedwlk on 2012-12-31
Along with the Unity DE, I prefer to use ClassicMenu Indicator. I have found this setup quite useful.

To install ClassicMenu Indicator, you need a PPA [see here: [http://www.florian-diesch.de/software/classicmenu-indicator/]](http://www.florian-diesch.de/software/classicmenu-indicator/])

For info regarding adding PPAs, see here [https://help.ubuntu.com/community/Repositories/CommandLine#Adding_Launchpad_PPA_Repositories](https://help.ubuntu.com/community/Repositories/CommandLine#Adding_Launchpad_PPA_Repositories)


Have a nice day.

EDIT: I am providing info regarding ClassicMenu Indicator, because the OP wanted to know about menu driven options for Ubuntu 12.04 or 12.10.

---

### Post by Mike Zahorik on 2012-12-31
Will I have 12.04 up and running. I tryed gnome-session-fallback and get it installed. Did with the SUDO and the software center. But..... All it does is to add a menu bar with a bunch of items that are not very useful. I'm looking for menus like I saw in Ubuntu 9.10 and I want to get rid of the icon along the side of my display.

Mike

---

### Post by Cheesemill on 2012-12-31
To change session you have to log out and then select the new session on the log in screen (click the button next to your name). You want to choose 'GNOME Classic' to get the Gnome 2 style menus.

---

### Post by Mike Zahorik on 2012-12-31
I don't have a login page. I selected to login auto at the onset. I also dislike passwords and things that are locked down. How would I do what you say?
Thanks
Mike

---

### Post by Mike Zahorik on 2012-12-31
Well..... I logged out and the machine asked for me to log in with my password, but there was no mention of any session or choices to be made.

Mike

---

### Post by Cheesemill on 2012-12-31
> **Mike Zahorik said:**
> I don't have a login page. I selected to login auto at the onset. I also dislike passwords and things that are locked down. How would I do what you say?
Thanks
Mike
You will have to turn off automatic log on to change the session. Once you have used the classic session you can turn on auto log on again, your last session gets remembered and used by default.

---

### Post by Cheesemill on 2012-12-31
> **Mike Zahorik said:**
> Well..... I logged out and the machine asked for me to log in with my password, but there was no mention of any session or choices to be made.

Mike
Did you click on the round button to the right of your name to open the session menu?

---

### Post by Mike Zahorik on 2012-12-31
Well... I finally got it. When you log in you have to click on the upper right corner icon to get to the choices. It all seems to work now. This is the reason that I do not like to have icons or any encrypted stuff, unless you are familiar with it you are lost. I like to see English. My 80 year old brain (must less my eyes can see) doesn't seem to be able to get around those confusing icons.

Anyway, I appreciate the help. New I'll move on to the next item. I want to learn more about Ubuntu and see if I can make this program work as everyone says it will.

Thanks very much

Mike

---

### Post by Bashing-om on 2012-12-31
Mike; Hi !

In spite of the fact you can not look at a screen prolonged. This is the official documentation for ubuntu in general and 12.04 in particular; And means to obtain it in hard copy edition:
[http://ubuntuguide.org/wiki/Ubuntu_Precise](http://ubuntuguide.org/wiki/Ubuntu_Precise)
[INDENT][INDENT][INDENT]hth <== BDQ

[/INDENT][/INDENT][/INDENT]

---

### Post by Cheesemill on 2012-12-31
> **Bashing-om said:**
> Mike; Hi !

In spite of the fact you can not look at a screen prolonged. This is the official documentation for ubuntu in general and 12.04 in particular; And means to obtain it in hard copy edition:
[http://ubuntuguide.org/wiki/Ubuntu_Precise](http://ubuntuguide.org/wiki/Ubuntu_Precise)[INDENT][INDENT][INDENT]hth <== BDQ

[/INDENT][/INDENT][/INDENT]

That isn't official.

The official documentation is here:
[https://help.ubuntu.com/12.04/ubuntu-help/index.html](https://help.ubuntu.com/12.04/ubuntu-help/index.html)

---

