---
title: "new to ubuntu"
date: 2012-03-18
forum: New to Ubuntu
---

### Post by Schoza on 2012-03-18
Hey all
ok i'm totally new to ubuntu, thought it was about time i learnt how to use it
i'm in the prossess of building a new system (just waiting for the cpu and a few minor components) so i really need to start doing my homework
i have just a few questions that u might be able to help me with
1. can you please recommend any good books for ubuntu
2. my partner and myself do a lot of online banking, i know trojans and viruses are minimal but do i need additional security
3. what is the best alternative programs for photoshop, acdsee (photo), flash player, download accelerator any other reccommended programs would be appreciated
that will do for the moment i'm sure i will be back
thank you

---

### Post by Rodney9 on 2012-03-18
Welcome.

1. Help Guide to Ubuntu Oneiric version 11.10

[http://ubuntuguide.org/wiki/Ubuntu_Oneiric](http://ubuntuguide.org/wiki/Ubuntu_Oneiric)

Linux is Not Windows

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Very good pictorial Install Guide

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

10 Things to after Installing Ubuntu

[http://www.omgubuntu.co.uk/2011/10/10-things-to-do-after-installing-ubuntu-11-10/](http://www.omgubuntu.co.uk/2011/10/10-things-to-do-after-installing-ubuntu-11-10/)



2. Linux is very secure, but security is always up to your habits and your hardware.
You can check your router here - [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)
You should achieve full stealth in the 'All Service port Scan'


3. For Photo editing I use The Gimp and RawTherapee, there are many choices, have a look in the 'Software Centre'

When you install Ubuntu it will ask you if you want to install mp3/flash etc .

For other software it depends what you want to do - here a couple of comparison tables -

[http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software)

[http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)



Rodney

---

### Post by Schoza on 2012-03-18
Cheers

---

### Post by Holdolin on 2012-03-18
Rodeny9 pretty much sumed it up.  No need to get a book, unless of course you want the confort of a printed copy.  There is quite a bit of documentation online.  If you run into any problems feel free to ask.  Welcome to the forums and to the goodness that is Ubuntu :)

---

### Post by Nytram on 2012-03-19
The web site in my signature contains a lot of Ubuntu learning material which you might find useful.

---

### Post by ubuntu27 on 2012-03-19
> **Schoza said:**
> Hey all
ok i'm totally new to ubuntu, thought it was about time i learnt how to use it

....

3. what is the best alternative programs for photoshop, acdsee (photo), flash player,


a) Photoshop ----> [Gimp]("http://www.gimp.org/"), etc

b) acdsee----> [GThumb]("https://live.gnome.org/gthumb"), Mirage, etc

c) [Adobe]Flash Player ----> Adobe Flash Player, [GNU Gnash]("https://www.gnu.org/software/gnash/"), LightSpark.
If you want to install Adobe Flash player, I recommend you to install it with the aid of a Firefox Plugin called [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") that will do it automatically for you.

d) Search for it in "Ubuntu Software Center" ;-) 

[How to install Software in Ubuntu Linux]("http://www.psychocats.net/ubuntu/installingsoftware")

---

### Post by Ghost_Mazal on 2012-03-19
The download manager I use is Firefox's downthemall. It is a Firefox add-on and works well.

---

### Post by HiImTye on 2012-03-19
> **Ghost_Mazal said:**
> The download manager I use is Firefox's downthemall. It is a Firefox add-on and works well.
I use uGet + aria2 and the FlashGot extension in FF

---

### Post by Mark Phelps on 2012-03-19
We've been getting LOTS of complaints from folks whose online banks only accept Internet Explorer for web access.  If that is the case with your banks, then you are out of luck.  Except for very old versions, IE doesn't work in Linux.  You should check out what your banks require.

---

### Post by mastablasta on 2012-03-19
> **Mark Phelps said:**
> We've been getting LOTS of complaints from folks whose online banks only accept Internet Explorer for web access. If that is the case with your banks, then you are out of luck. Except for very old versions, IE doesn't work in Linux. You should check out what your banks require.
 
indeed. afterall Internet Explorer is the most secure browser so that makes sense. :p
 
but seriously sometimes banks only use frame.net in connection to IE and there are some alternatives for this or workarrounds. 
 
still i do know that for example my wife's pro account only works in windows, while some other banks here also have linux support. though i am not sure how good their support actually is.

---

### Post by woxuxow on 2012-03-19
unfortunately there is not any download manager better than idm or fdm in gnu/linux

i use uGet+aria2 they work together it's just not bad
and there is too many other choice like kget - multiget - jdownloader and ...

---

### Post by Schoza on 2012-03-20
thank you all for the tips 
cool forum

---

### Post by ubuntu27 on 2012-03-23
> **Schoza said:**
> 
3. what is the best alternative programs for photoshop, acdsee (photo), flash player, **download accelerator** any other reccommended programs would be appreciated
that will do for the moment i'm sure i will be back
thank you

In my humble opinion, the best Download Manager for Linux is [JDownloader]("http://www.jdownloader.org/"). It is not in Ubuntu's repository, but you can download the sh file and install it.

Oh, they also have Ubuntu PPA. So you can instal from there.

See: [How to install Software from PPA]("https://help.launchpad.net/Packaging/PPA/InstallingSoftware")

[How to use Launchpad PPA]("http://www.webupd8.org/2012/02/how-to-use-launchpad-ppa-add-remove.html")


In summary, you have to open the [terminal]("http://www.psychocats.net/ubuntu/terminal"), and then type the following to add JDownloader's PPA

```
sudo add-apt-repository ppa:jd-team/jdownloader
```, press ENTER and type your sudo password.

and, now you should update the Respository by

```
sudo apt-get update
```

Now, that the repository (list of apps) is up to date, you can install JDownloaders by

```
sudo apt-get install jdownloader
```.


WIth that the installation is finished.

JDownloader will check for updates on the first run, so don't be alarmed.



Good Luck!

---

