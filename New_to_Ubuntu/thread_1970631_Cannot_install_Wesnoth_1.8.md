---
title: "Cannot install Wesnoth 1.8?"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by Bubba3 on 2012-05-01
In my Ubuntu Software Center, If I look for "Wesnoth", I find v1.10 and v1.8. The latter has been rated to be great by many more people. So I wanted to install the later version, but found I could not. There is no "Install" button, and if i click on "More info" it says:

"File not found - There isn&#8217;t a software package called &#8220;wesnoth-1.8&#8221; in your current software sources."

I tried installing it manually, but frankly, this [website]("http://wiki.wesnoth.org/WesnothBinariesLinux") tries to give me v1.10 as well.. 
Both suggested ways to get wesnoth there (Command "sudo apt-get install wesnoth" & the "Click here to install"-link) give me v1.10.

Any suggestions on how to get v1.8?


(Further information: Ubuntu 12, Newbie-User. Oh, and Unity, if that helps...)

---

### Post by ubudog on 2012-05-01
For the PlayDeb, "Click here to install" button, you have to add their PPA, by installing this pacakge:
[http://archive.getdeb.net/install_deb/playdeb_0.3-1~getdeb1_all.deb](http://archive.getdeb.net/install_deb/playdeb_0.3-1~getdeb1_all.deb)
[PlayDeb.net]

Then retry the PlayDeb [version]("http://www.playdeb.net/software/Battle%20for%20Wesnoth").

---

### Post by Bubba3 on 2012-05-02
**Installed the .deb from the first link.**
The second link provides me with:

Ubuntu 12.04: 1:1.10.2-1~getdeb3~precise

(-> **v.1.10, which i already have on my system**.)
I tried to install v1.8 in my software center, but still no "install" button and the same "file not found" error -> **Did not work.** Could it be 1.8 only works on other OS, and not on Ubuntu?

Further advice?
And, if you have the time, could you explain to me what all the .deb-stuff means? What is PPA?
Thanks for your patience, anyway :)

---

### Post by Bubba3 on 2012-05-02
Holy frick, this is embarassing. I actually misread version 1.10 to be v1.1.0 EVERY TIME. and so i thought, well 1.8 is better than 1.1 and wondered why i couldnt install it -.- Sorry... But still, if you could explain to me what the thinking behind your answer was?

---

### Post by ubudog on 2012-05-02
> **Bubba3 said:**
> Holy frick, this is embarassing. I actually misread version 1.10 to be v1.1.0 EVERY TIME. and so i thought, well 1.8 is better than 1.1 and wondered why i couldnt install it -.- Sorry... But still, if you could explain to me what the thinking behind your answer was?

Well, at least you have the latest version.  :P 

.debs are software packages in Debian (what Ubuntu is based upon).  The one you downloaded automatically configured PlayDeb's repository so that you could install the games by clicking the 'Click here to install' button on the site.

I also misinterpreted it, so I thought you were trying to get the latest version.

---

