---
title: "i have no clue what i am doing"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by armyman82 on 2008-08-09
i am new to the hole linex opp system and i am not that good on a computer but i need hepl with getting my system loaded up so that i can play movies and also so i can play games. my system will paly a cd but i need a decryptor so that i can play movies and i have no clue how to go about and get the decryptor can i plz get some help

---

### Post by nothingspecial on 2008-08-09
This should help.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by starcannon on 2008-08-09
first off your going to need add some repositories(places where Ubuntu Programs are stored on the internet) in order to use some proprietary codecs and softwares:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then your going to need to go through your menu's (upper left hand corner) to:

System->Administration->Synaptic Package Manager (tons of FREE software in here)

Click on "Search"

for DVD's you'll likely need dvdcss (search for it and install it)

You'd also likely like to have:

ubuntu-restricted-extras (search ubuntu-restricted)

might as well get a GREAT mp3 ripper while your at it:
search: ripperx

There are more Free games than you can shake a stick at, browse the package manager, if you have a "must have" windows only title you can try:
wine(search synaptic package manager)
or:
Cedega: [http://www.cedega.com/](http://www.cedega.com/)

either way you'll find an incredible amount of win for lin games that way.

it takes a bit of getting used to, but if you don't give up, and don't be impatient with yourself, you'll soon find that the Synaptic Package Manager is the greatest thing since sliced bread and ribbed condominiums.

GL and most importantly have fun out there.

---

### Post by billgoldberg on 2008-08-09
Go to "applications -> accessories -> terminal" and copy/paste this.

You will now be able to play all your videos and music.
```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
```

---

### Post by adamogardner on 2008-08-09
> **starcannon said:**
> for DVD's you'll likely need dvdcss (search for it and install it)

why don't I have dvdcss in synaptic?  all I have is a libdvdread3 already installed and a libdvdread-dev that's not installed.

---

### Post by billgoldberg on 2008-08-09
> **adamogardner said:**
> why don't I have dvdcss in synaptic?  all I have is a libdvdread3 already installed and a libdvdread-dev that's not installed.

You need the medibuntu repo.

The package you need is called, libdvdcss2.

If you use the command in my previous post, you'll have all the codecs including dvd support installed.

---

