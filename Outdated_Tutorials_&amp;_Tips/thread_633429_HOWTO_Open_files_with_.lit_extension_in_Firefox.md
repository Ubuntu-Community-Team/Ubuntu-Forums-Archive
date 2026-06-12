---
title: "HOWTO: Open files with .lit extension in Firefox"
date: 2007-12-06
forum: Outdated Tutorials &amp; Tips
---

### Post by &#1050;&#1085;&#1077;&#1083;&#1077; on 2007-12-06
This guide is about OpenBerg Lector  open-source, e-book reader which allows you to read files with .lit extension in  Firefox web browser. Web site of the project where you can read more about it: [ http://openberg.sourceforge.net/?page_id=6]("http://openberg.sourceforge.net/?page_id=6")

You will need Firefox web browser, if you don't have it already, open a terminal window and type:
```
sudo apt-get install firefox 
```

Install the OpenBerg Lector add-on for FireFox. Go to the next page with your FireFox web browser and choose install: [https://addons.mozilla.org/en-US/firefox/addon/5275]("https://addons.mozilla.org/en-US/firefox/addon/5275") 

You'll need unrar as well, so if you don't have it already installed, type the following in terminal:
```
sudo apt-get install rar unrar 
```

Download and install Libtommath package with the following commands:
```
wget http://ace-host.stuart.id.au/russell/files/debian/sarge/libtommath/libtommath_0.37-1_i386.deb
sudo dpkg -i libtommath_0.37-1_i386.deb 
```

And the ConvertLit with:
```
wget http://ace-host.stuart.id.au/russell/files/debian/sarge/clit/clit_1.8-1_i386.deb
sudo dpkg -i clit_1.8-1_i386.deb 
```

You should inform OpenBerg Lector about the paths of the fresh installed aplications. FireFox/Tools/Add-ons/OpenBerg Lector-preferences/CBR Comic books, unrar aplication: /usr/bin/unrar, Lit eBooks, ConvertLit application: /usr/bin/clit. 

That would be it. I hope that this guide works for all of you. Enjoy reading.

---

### Post by akparker on 2008-01-15
Thank you for the instructions.

I'm a Linux noob, so I didn't know syntax for executing clit.

However, it is explained quite well here:

[http://ubuntuforums.org/showthread.php?t=35674&highlight=clit&page=2](http://ubuntuforums.org/showthread.php?t=35674&highlight=clit&page=2)

Keith :)

---

