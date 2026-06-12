---
title: "Ubuntu Software Center download problems"
date: 2012-04-09
forum: New to Ubuntu
---

### Post by joshfischer1108 on 2012-04-09
Help!

I'm new to Ubuntu and I am trying to download some software.  Everytime I try and download I get two pop ups.  The first one states:

Failed to download package files
check your internet connection

the second pop-up states:

Requires installation of untrusted packages.
The action would require the installation of packages from non authorized sources.

I really need to get this to work as I am trying to learn more about this OS and would like to continue downloading software so that I can further my education in developing software.  Please help!

---

### Post by Curtis6767 on 2012-04-09
You could look through this previous thread: [http://ubuntuforums.org/showthread.php?t=1878602&highlight=untrusted+packages](http://ubuntuforums.org/showthread.php?t=1878602&highlight=untrusted+packages)

---

### Post by jerrrys on 2012-04-09
Start with post #2 :)

Open a terminal and enter:

sudo apt-get update

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Any questions?  Post back

---

### Post by oklokl on 2012-04-10
Software Center bug..

[http://ubuntuguide.org/wiki/Ubuntu:Oneiric](http://ubuntuguide.org/wiki/Ubuntu:Oneiric)
Tip
[COLOR=Red]Red txt[/COLOR]
 Is used to change


[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
[https://launchpad.net/](https://launchpad.net/)
Search

[http://www.google.com/](http://www.google.com/)
Search

ex> Tip


or
[https://launchpad.net/~nilarimogard/+archive/webupd8]("https://launchpad.net/%7Enilarimogard/+archive/webupd8")

sudo add-apt-repository [COLOR=Red]ppa:nilarimogard/webupd8[/COLOR]
sudo apt-get [COLOR=Red]update[/COLOR]
sudo apt-get install [COLOR=Red]audacious [/COLOR]
#(Sometimes an error occurs)

or Easily add
#deb add
sudo sh -c 'echo "[COLOR=Red]deb  [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) oneiric main[/COLOR]"  >> \/etc/apt/sources.list.d/[COLOR=Red]webupd.list[/COLOR]'
 sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys [COLOR=Red]EEA14886 [/COLOR]##webupd8team audacious
#(Most Recommended)

sudo apt-get [COLOR=Red]update[/COLOR]
sudo apt-get install [COLOR=Red]audacious [/COLOR]



or Tip.. key gpg License backup 
Ubuntu must have a certificate
 Can install the software.

 
sudo apt-key exportall > testbackupfilekey.asc  
## backup key -> Approved certificate

sudo apt-key add testbackupfilekey.asc 
## add key gpg License
#At the end ought to
[COLOR=Red]sudo apt-get update[/COLOR]


[http://cafe.daum.net/candan/HgwY/57](http://cafe.daum.net/candan/HgwY/57)
Use your favorite ...

---

### Post by daslinkard on 2012-04-10
The **sudo apt-get update** should do the fix in looking at previous posts in regards to this topic.  After you have completed the command listed above try to re-download the package(s).  Hopefully this gets it fixed for you.

---

