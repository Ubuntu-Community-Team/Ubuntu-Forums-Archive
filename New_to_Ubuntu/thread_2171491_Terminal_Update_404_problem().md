---
title: "Terminal Update 404 problem(?)"
date: 2013-08-31
forum: New to Ubuntu
---

### Post by carmonacr75 on 2013-08-31
:KS Thank you for reading this, God bless you and I hope you are well!  I have just taken the plunge and quit Win8 cold turkey and enjoying Ubuntu for its simplicity.  I have found how to update my aplications with software updater and with terminal.  I am running Saucy Ubuntu 13.04 AMD 64, I chose it because I liked the name lol but if you have time please explain what this version does.  My first question is did I choose the wrong installation?  My computer is a 64 bit Intel processor, The AMD threw me off but the 64 made me install and the errors I will post make me think I should have gone with the i-386 version.  The following errors occur:
Terminal; sudo apt-get update gives these 404s:
W: Failed to fetch [http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/saucy/main/binary-amd64/Packages](http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/saucy/main/binary-amd64/Packages)  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/saucy/main/binary-i386/Packages](http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/saucy/main/binary-i386/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.

Software update gives me some errors but I will post that later in this forum.

---

### Post by ibjsb4 on 2013-08-31
There is no Saucy package.

[http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/](http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/)

---

### Post by carmonacr75 on 2013-08-31
You are correct, I have one called saucy salamander.  Maybe I should reinstall a better known distro which do you recommend?
[URL="http://fridge.ubuntu.com/2013/07/25/13-10-saucy-salamander-alpha-2-available/"]http://cdimage.ubuntu.com/daily-live/current/
[http://fridge.ubuntu.com/2013/07/25/13-10-saucy-salamander-alpha-2-available/](http://fridge.ubuntu.com/2013/07/25/13-10-saucy-salamander-alpha-2-available/)

[/URL]

---

### Post by QIII on 2013-08-31
Hello!

Saucy Salamander (Ubuntu 13.10) is still in development and testing.  It has not made it to final release yet and can be expected to break.

I might recommend that you install Precise Pangolin (Ubuntu 12.04) instead.

Precise was a Long Term Support (LTS) release, which will be supported until April 2017.  If you are new to Ubuntu, I would recommend staying with the biennial LTS releases (which come out in April of even-numbered years, like 12.04) because the release rotation and length of support for versions other than LTS mean you have to update at least once between LTS releases, which might be confusing until you learn the ropes.

Cheers!

---

### Post by deadflowr on 2013-08-31
First off, any reason to be running the development release of Ubuntu?(Saucy Salamander)

Secondly, of the releases still supported for which you can add the deluge-team ppa are as of now two
Quantal, or Precise.
Whether it is an oversight on launchpad for why raring isn't listed, I don't know.

[https://launchpad.net/~deluge-team/+archive/ppa](https://launchpad.net/~deluge-team/+archive/ppa)

Personally, I'd recommend Precise, Version 12.04(Now 12.04.3)
It'll be supported for close to three and a half years, as opposed to Quantal which support ends next April.

And I don't ever recommend beta/development release.
If you want to run one, I won't stop you, I'll even help you figure out how to install it.
 but I try not to push people into periodic breakages, which development release can cause.

---

### Post by carmonacr75 on 2013-08-31
Thank you guys, I guess the pioneering spirit got the best of me this time!  Here is a nice website explaining the 13.10 in case they are interested. 
[http://www.webupd8.org/2013/05/possible-changes-in-ubunu-1310-saucy.html](http://www.webupd8.org/2013/05/possible-changes-in-ubunu-1310-saucy.html)
The OS runs and looks great its just the updating that I will either look for a work around or go to 12.04.3!  This is exciting though I might stay!  I'll have a look around the forum to see if there are any pros testing 13.10 Saucy Salamander right now.

---

### Post by deadflowr on 2013-08-31
This entire sub-forum is dedicated to the development cycle

[http://ubuntuforums.org/forumdisplay.php?f=427](http://ubuntuforums.org/forumdisplay.php?f=427)

---

### Post by Impavidus on 2013-08-31
Concerning the 64-bit version: With an Intel 64-bit CPU you can run the AMD64 version of Ubuntu. With more than about 3GB RAM it is recommended to use 64-bit. The name AMD is there for historical reasons: AMD started producing this processor design first, but the AMD and Intel processors are compatible.

---

### Post by newb85 on 2013-08-31
> **QIII said:**
> 
... the release rotation and length of support for versions other than LTS mean you have to update at least once between LTS releases...


Actually, since the support for other-than-LTS releases has been cut from 18 to 9 months (as of 13.04), using non-LTS releases means you now have to update with every new release.

---

### Post by ibjsb4 on 2013-08-31
> **QIII said:**
> Hello!

Saucy Salamander (Ubuntu 13.10) is still in development and testing.  It has not made it to final release yet and can be expected to break.

I might recommend that you install Precise Pangolin (Ubuntu 12.04) instead.

Precise was a Long Term Support (LTS) release, which will be supported until April 2017.  If you are new to Ubuntu, I would recommend staying with the biennial LTS releases (which come out in April of even-numbered years, like 12.04) because the release rotation and length of support for versions other than LTS mean you have to update at least once between LTS releases, which might be confusing until you learn the ropes.

Cheers!

Yes, 12o4 would be a good choice.

---

