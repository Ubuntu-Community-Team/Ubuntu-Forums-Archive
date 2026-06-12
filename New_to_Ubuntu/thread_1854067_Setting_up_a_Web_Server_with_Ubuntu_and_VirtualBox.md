---
title: "Setting up a Web Server with Ubuntu and VirtualBox"
date: 2011-10-03
forum: New to Ubuntu
---

### Post by fendermaniac on 2011-10-03
):P

I am very new to this and I have very little tech experience.  Right now I am trying to set up a development server so I can develop websites.  I tried WAMP and XAMPP on my windows PC, but Magento, which is the website software I'm using has errors on windows.  I was told setting up Linux on VirtualBox would be the best solution.

I installed VirtualBox and downloaded the ISO for Ubuntu.  I then configured it. Now I'm at the command prompt section and I have absolutely no clue what I'm doing.  

I followed some video on YouTube on how to set up my IP address and DNS servers, but I don't think I had set that up right.  Does anyone have any resources that might be useful to me?

Thanks,

Joe

---

### Post by bodhi.zazen on 2011-10-03
Traditionally servers do not have graphical interfaces. If you want a graphical interface, I suggest webmin.

Next stop is the server guide :

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

---

### Post by MG&amp;TL on 2011-10-03
[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

[http://Linuxcommand.org]("http://linuxcommand.org/")[URL="http://ubuntuforums.org/Linuxcommand.org"]
[/URL]

---

### Post by drdos2006 on 2011-10-03
Here is a HOWTO which I found comprehensive and invaluable. Uses Webmin to allow your browser to connect and modify your server settings.
You could also install the Desktop plus install and run the server as a virtual machine using Virtualbox and that is how I run my testing websever.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.550_all.deb

Install with :
sudo dpkg -i webmin_1.550_all.deb

Add extra libraries with :
sudo apt-get -f install

```

regards

---

### Post by BEEDO on 2011-10-04
I installed both the desktop 11.04 (with LAMP) and server 11.04 on XP in VB and face the same challenges. Here are a few links and a command I found useful:

 [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

[http://linuxcommand.org/](http://linuxcommand.org/)

[https://help.ubuntu.com/community/Nano](https://help.ubuntu.com/community/Nano)

> sudo apt-get install vim 

vimtutorThe last is for an editor, like nano.

You'll probably want to bring in files from your Windows system, hopefully someone here can help you, since I am still trying to figure out how to do it gracefully.

---

