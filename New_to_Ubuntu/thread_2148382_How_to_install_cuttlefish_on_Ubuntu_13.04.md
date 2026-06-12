---
title: "How to install cuttlefish on Ubuntu 13.04"
date: 2013-05-25
forum: New to Ubuntu
---

### Post by todorakiggg on 2013-05-25
I am trying to install Cuttlefish on Ubuntu 13.04 however it is not available in Ubuntu Software Center.
I tried with manually importing the ppa with these, but I got no success:


[COLOR=#233235][FONT=Monaco]sudo add-apt-repository ppa:noneed4anick/cuttlefish[/FONT][/COLOR][COLOR=#233235][FONT=Monaco][/FONT][/COLOR][COLOR=#233235][FONT=Monaco]sudo apt-get update[/FONT][/COLOR][COLOR=#233235][FONT=Monaco][/FONT][/COLOR][COLOR=#233235][FONT=Monaco]sudo apt-get install[/FONT][/COLOR][COLOR=#233235][FONT=Monaco] cuttlefish[/FONT][/COLOR]

So the question I have is: Is this program available for 13.04 and more is it available for 64 bit Ubuntu?

Can anyone recommend another program having similar functionality? I am particularly interested in automating lower brightness on the display when the machine is running on battery.

---

### Post by monkeybrain2012 on 2013-05-25
The ppa is only for 12.04, you can check that by clicking the "published in" tab on the page. You may see if you can just grab the .deb and install it from its archive. [https://launchpad.net/~noneed4anick/+archive/cuttlefish/+packages](https://launchpad.net/~noneed4anick/+archive/cuttlefish/+packages)

It seems to be some kind of tweaktool to put on indicators or some such, there may be other replacements.

---

### Post by lethall1 on 2013-05-25
[https://launchpad.net/cuttlefish](https://launchpad.net/cuttlefish)
[http://www.ubuntuupdates.org/package/extras/precise/main/base/cuttlefish](http://www.ubuntuupdates.org/package/extras/precise/main/base/cuttlefish)

---

### Post by monkeybrain2012 on 2013-05-25
Yeah your links point to Precise packages. That was what I told him.

---

### Post by todorakiggg on 2013-05-25
Ok, so far so good:)
I downloaded the package, but when I try to install it with software center it says the following:

Dependency is not satisfiable: gir1.2-launchpad-integration-3.0 

What does it mean? Software center does not like the package, or there is something else that is needed to make it work?

How I can install this package with terminal commands?

---

### Post by lethall1 on 2013-05-25
in general 
```
sudo dpgk -i /path/to/file.deb
```
but, as was written before, this package is for "Precise"
you have to satisfy all dependencies, that's mean you have to manualy install all packages, that are not in your repository list. 
Try 
```
sudo apt-get install -f
```
or find and download all dependencies (google helps you)

---

### Post by todorakiggg on 2013-05-25
I found nothing so far with Google, but general question, can I break something with installing a package build for an older distribution?

---

### Post by lethall1 on 2013-05-25
In general... yes you can break it. This package is not present in repositories, because it depends from some old package that does not have support now or that package conflicts with some other packages. In first case there would not be problems, in second case you can remove some important packages by installing required, and that important is important for another one and so on...

---

### Post by todorakiggg on 2013-05-25
Well, you convinced me not to give it a try... it took me a while to set up the system in the way it is.
If you guys know any alternative to cuttlefish that I can use on 13.04 will be much appreciated.

---

### Post by Mrokii on 2013-05-27
I have installed CuttleFish without much problems on 13.04. And by that I mean that only three dependencies have to be installed manually:

[https://launchpad.net/ubuntu/raring/+package/liblaunchpad-integration-common](https://launchpad.net/ubuntu/raring/+package/liblaunchpad-integration-common)
[https://launchpad.net/ubuntu/raring/+package/liblaunchpad-integration-3.0-1](https://launchpad.net/ubuntu/raring/+package/liblaunchpad-integration-3.0-1)
[https://launchpad.net/ubuntu/raring/+package/gir1.2-launchpad-integration-3.0](https://launchpad.net/ubuntu/raring/+package/gir1.2-launchpad-integration-3.0)

After that you can install CuttleFish from its 12.10 Repo.

---

### Post by Scott Goodgame on 2013-05-27
It is a precise ppa, but works fine in 12.10/13.04. A ppa is a better option than a .deb because it will update automaticly

echo ' deb [http://ppa.launchpad.net/noneed4anick/cuttlefish/ubuntu](http://ppa.launchpad.net/noneed4anick/cuttlefish/ubuntu) precise main  ' | sudo tee -a /etc/apt/sources.list
sudo apt-get update
sudo apt-get install cuttlefish

---

