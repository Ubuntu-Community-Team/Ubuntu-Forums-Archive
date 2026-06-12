---
title: "webpages not loading correctly"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by newbiebme on 2008-09-15
Hey everyone, my husband talked me into using the linux and ubuntu system and so far it's ok. Our computer is a double boot if that matters. But when I visit some webpages using firefox, under the linux part, some web pages don't load right. Because when i enter information or click certain links nothing happens. But then I restart the computer and use Windows that same webpage is totally different, has more on it and links actually work. Am I missing something? Please help, I'm sick of restarting the computer to use windows because I can't figure Linux,Ubuntu, Firefox out. Thanks in advance:) One more thing I should mention: my husband is overseas so he's not at my disposal to help me.

---

### Post by Idefix82 on 2008-09-15
Can you give an example of a web page which doesn't show correctly? Maybe you need some plugins like flash player.

---

### Post by knix on 2008-09-15
> **Idefix82 said:**
> Can you give an example of a web page which doesn't show correctly? Maybe you need some plugins like flash player.

Flash is often neede, as well as Java.
Can you try Opera and let us know how it works?

---

### Post by tuxxy on 2008-09-15
How did you install Java & Flash?

---

### Post by Bucky Ball on 2008-09-15
Perhaps try installing ubuntu-restricted-extras from Synaptic Package Manager under System->Administration.

There are some instructions for installing Flash10 here:

[http://ubuntuforums.org/showthread.php?t=917488](http://ubuntuforums.org/showthread.php?t=917488)

Second post down.

---

### Post by newbiebme on 2008-09-18
Maybe Flash is what I need, because Oprah didn't load right. I thought since Flash is on the Windows side of the computer it would be on Linux too. I'm not even sure how to install something. I've tried downloading things and the manager thing pops up and I hit extract but nothing happens. And are the package icons of downloaded apps supposed to be on my desktop? thanks for the help
I tried this line by line:cd /tmp
wget [http://download.macromedia.com/pub/l..._070208.tar.gz](http://download.macromedia.com/pub/l..._070208.tar.gz)
tar -zxvf flashplayer10_install_linux_070208.tar.gz
cd install_flash_player_10_linux
./flashplayer-

and it said not found or no such directory

---

### Post by billgoldberg on 2008-09-18
> **newbiebme said:**
> Maybe Flash is what I need, because Oprah didn't load right. I thought since Flash is on the Windows side of the computer it would be on Linux too. I'm not even sure how to install something. I've tried downloading things and the manager thing pops up and I hit extract but nothing happens. And are the package icons of downloaded apps supposed to be on my desktop? thanks for the help

Go to applications -> accessories -> terminal

there copy/paste this

sudo apt-get install ubuntu-restricted-extras

You will need to give in your password [the one you log into the computer with] and it might be that you will have to enter "y" after that.

If it's done, restart firefox and you should be good.


--

Installing stuf in Ubuntu is not the same as installing stuff in Windows.

The programs you download from the web for Windows are not going to run on Ubuntu.

Navigate to Applications -> Add/Remove and there you can install software [make sure all available sources are selected from the drop-down menu on the top]

---

### Post by billgoldberg on 2008-09-18
> **newbiebme said:**
> Maybe Flash is what I need, because Oprah didn't load right. I thought since Flash is on the Windows side of the computer it would be on Linux too. I'm not even sure how to install something. I've tried downloading things and the manager thing pops up and I hit extract but nothing happens. And are the package icons of downloaded apps supposed to be on my desktop? thanks for the help
I tried this line by line:cd /tmp
wget [http://download.macromedia.com/pub/l..._070208.tar.gz](http://download.macromedia.com/pub/l..._070208.tar.gz)
tar -zxvf flashplayer10_install_linux_070208.tar.gz
cd install_flash_player_10_linux
./flashplayer-

and it said not found or no such directory

If you want flash 10 [it's still a beta so there, follow instructions here

[http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/](http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/)

.

---

### Post by billgoldberg on 2008-09-18
Also, the two operating systems share nothing.

They are on different hard drives or hard drive partitions and don't touch each other in any way.

Nothing you will do in Windows will affect Ubuntu nor the other way around.

---

### Post by newbiebme on 2008-09-18
I tried entering this into the terminal and oprah.com still doesn't completely load. 
sudo apt-get install ubuntu-restricted-extras

Good to know about the different hard drives and installing things on linux

---

### Post by Idefix82 on 2008-09-18
OK, I just tried loading this site myself and I think the site is just buggy. Maybe this seems familiar to the more experienced web developers: the error console of the browser is full of errors like
> Warning: Expected ',' or '{' but found 'html'.  Ruleset ignored due to bad selector.
Source File: [http://static.oprah.com/css/index_styles.css](http://static.oprah.com/css/index_styles.css)
Line: 201
I should add that I don't have Java installed, but I haven't found any reference to java in the source code of the page.

Newbiebme, are there any other sites that don't work for you or is this the only one now?

---

### Post by daithi_dearg on 2009-01-16
Hello,

I'm having similar problems as in this message. I have Java and flash 10 installed but I still get errors in my message. The webpage I'm opening is:
[http://www.aspworldtour.com/2008/news_show.asp?rEvent=&rcode=12016](http://www.aspworldtour.com/2008/news_show.asp?rEvent=&rcode=12016)

I get "?" through the webpage. I think it's to do with the ' character.

Regards,
David

---

