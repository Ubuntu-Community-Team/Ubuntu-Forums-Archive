---
title: "Name of distribution"
date: 2012-01-05
forum: New to Ubuntu
---

### Post by benj23673 on 2012-01-05
Ok  so I am very new to all of this, I am trying to install tor for lubuntu so any help or tips would be nice. But basically I need to find the name of my "distribution" or would any of these work since ubuntu and lubuntu are very similar?

Debian unstable (sid) is "sid"
Debian testing is "wheezy"
Debian 6.0 (squeeze) is "squeeze"
Debian 5.0 (lenny) is "lenny"
Ubuntu 11.04 is "natty"
Ubuntu 10.10 or Trisquel 4.5 is "maverick"
Ubuntu 10.04 or Trisquel 4.0 is "lucid"
Ubuntu 9.10 or Trisquel 3.5 is "karmic"
Ubuntu 8.04 is "hardy"

---

### Post by KdotJ on 2012-01-05
If you open up a terminal, and enter the following:

```
cat /etc/issue
```

It will tell you what version you are running. 
For example, when I run it, it says:

```
Ubuntu 11.10
```

as I am running version 11.10

As for Tor, the website seems to give me a download for a tar.gz file. In which case, the distribution is irrelevant.

---

### Post by benj23673 on 2012-01-05
[https://www.torproject.org/docs/debian.html.en#ubuntu](https://www.torproject.org/docs/debian.html.en#ubuntu)

^This is what I am using to install tor. 
Like I said I am very new to this (never used ubuntu before 3days ago) I tried downloading it straight from tor but I could not get it to open or install?

---

### Post by KdotJ on 2012-01-05
Oh yes I see now.
Well from my little knowledge of Tor, I know that they recommend that you use the "browser bundle" which is simply just unzip and go, all sorted for you.

The download page is [here]("https://www.torproject.org/download/download-easy.html.en"), and here is the page which explains about the bundle [here]("https://www.torproject.org/projects/torbrowser.html.en")


I've just literally tested it. Download the one for linux on that page I linked. Once its done, extract it, the go into the new folder and double click "start-tor-browser". The config box should open... more info is on the Tor page (the second one I linked)

---

### Post by benj23673 on 2012-01-05
main@home:~$ sudo apt-get install tor tor-geoipdb
[sudo] password for main:
Reading package lists... Done
Building dependency tree      
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:
 
The following packages have unmet dependencies:
 tor : Depends: libevent-2.0-5 (>= 2.0.16-stable) but 2.0.12-stable-1 is to be installed
E: Unable to correct problems, you have held broken packages.
main@home:~$

---

### Post by benj23673 on 2012-01-05
^the error I have been getting
Do I need special software to extract it with?

---

### Post by KdotJ on 2012-01-05
```
main@home:~$ sudo apt-get install tor tor-geoipdb
```

^^ This isn't the way I tried it.


Did you download the bundle from the page I linked (this link [HERE]("https://www.torproject.org/download/download-easy.html.en"))? As for extracting it, I'm not sure about Lubuntu... if you right-click do you get an extract option? If not, come back and I'll tell you the command to do it manually.

---

### Post by dFlyer on 2012-01-05
from a terminal enter:

lsb_release -a

---

### Post by benj23673 on 2012-01-06
Thank you very much, I did it the way you suggested with the browser bundle and it was already downloaded just not saved anywhere that's why I did not think that it was working. All this is very new to me and it is a little bit of a project I picked up. I was just wondering how you find or know/understand these codes? Is there a place I can go to learn and understand ubuntu more?

---

### Post by benj23673 on 2012-01-06
and one last question I swear, how can you delete repositories from the terminal?

---

### Post by claracc on 2012-01-06
[http://maketecheasier.com/remove-repositories-in-ubuntu/2010/05/27](http://maketecheasier.com/remove-repositories-in-ubuntu/2010/05/27)

---

### Post by I_can_see_the_light on 2012-01-06
> **benj23673 said:**
> **and one last question I swear**, how can you delete repositories from the terminal?

It's no bother, just ask :)

To delete a repository open up a terminal window  and enter: ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```This will create a backup copy of your *sources.list* file.

Now enter ```
gksudo gedit /etc/apt/sources.list
``` Gedit will open and in there will be many lines of text. It's possible to delete lines if you so wish but you can also put a **#** in front of the repository you don't want to fetch packages from. That way it's easier to undo any changes.

However the preferred graphical way of changing this file would be to open the *Ubuntu Software Center* and then go **Edit** > **Software Sources**

To learn more about Ubuntu you can check out: 
[https://help.ubuntu.com/]("https://help.ubuntu.com/")
[http://www.psychocats.net/ubuntu/index.php]("http://www.psychocats.net/ubuntu/index.php")
[http://www.webupd8.org/]("http://www.webupd8.org/")
[http://www.omgubuntu.co.uk/]("http://www.omgubuntu.co.uk/")

---

### Post by KdotJ on 2012-01-06
> **benj23673 said:**
> and one last question I swear

No need for that lol, that's why the forum is here! Ask away..

Just add in another more direct link to the Beginners Guide [HERE]("https://help.ubuntu.com/community/Beginners/FAQ")

It looks like a bit of reading but it will help you understand this unfamiliar environment. Enjoy!

---

