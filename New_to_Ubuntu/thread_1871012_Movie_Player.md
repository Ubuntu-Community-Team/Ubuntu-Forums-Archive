---
title: "Movie Player"
date: 2011-10-28
forum: New to Ubuntu
---

### Post by ashu_tears on 2011-10-28
Hi,

My movie player is not working. It can't play the media files and says some package is missing... I don't know what that is... Is there any thing else that I can do to solve this problem? Or is the formats of the media files not matching to what the Movie Player requires...?? 

Please give me some ideas...

thanks

---

### Post by azkraja on 2011-10-28
Install VLC or SM Player through Software center. they both play almost everything. This trick works for me, other wise you have to search and install extra codices for movie player to run all media formats.
Second option open terminal and input command "sudo apt-get install vlc " to install VLC player








                    Download: [www.eType1.com/e1.php?ElbTVt](www.eType1.com/e1.php?ElbTVt)

---

### Post by Paqman on 2011-10-28
> **ashu_tears said:**
> It can't play the media files and says some package is missing... I don't know what that is...

If it's offering to install the required packages (which it should), go ahead and let it do that.

Otherwise installing the package [ubuntu-restricted-extras (click to install)](apt:ubuntu-restricted-extras) will install all the codecs you need for any kind of media. The you should be able to use whatever media player you like most. Installing VLC like azkraja suggests is also an option, as that can handle pretty much any format on it's own.

---

### Post by BlinkinCat on 2011-10-28
For what it is worth, I have always found movie player O.K. provided you download Ubuntu Restricted Extras - :)

---

