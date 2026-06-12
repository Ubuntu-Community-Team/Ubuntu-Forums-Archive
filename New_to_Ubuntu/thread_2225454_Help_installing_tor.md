---
title: "Help installing tor"
date: 2014-05-21
forum: New to Ubuntu
---

### Post by anon-t417 on 2014-05-21
I recently upgraded to 14.04 and trying to download the tor browser but when i do this is what i get:

W: Failed to fetch cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)/dists/trusty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)/dists/trusty/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)/dists/trusty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)/dists/trusty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch http://deb.torproject.org/torproject.org/dists/<trusty>/main/binary-amd64/Packages  404  Not Found [IP: 82.195.75.101 80]

W: Failed to fetch http://deb.torproject.org/torproject.org/dists/<trusty>/main/binary-i386/Packages  404  Not Found [IP: 82.195.75.101 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

dont really know what im missing though. any help is greatly appreciated.

---

### Post by oldos2er on 2014-05-21
Moved to Absolute Beginners.

The < > marks need to be removed from the torproject URL. Can you run the following commands and copy/paste all their output here? ```
cat /etc/apt/sources.list

ls /etc/apt/sources.list.d/
```

---

### Post by Rana_Muhammad_Waqas_ on 2014-05-25
I am having the same problem but i didnt upgrade i installed 14.04 LTS directly from USB 
here is the output of the comands you said 

```
cat /etc/apt/sources.list
```
```
deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)]/ trusty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://stingray.cyber.net.pk/pub/ubuntu/](http://stingray.cyber.net.pk/pub/ubuntu/) trusty main restricted
deb-src [http://stingray.cyber.net.pk/pub/ubuntu/](http://stingray.cyber.net.pk/pub/ubuntu/) trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://stingray.cyber.net.pk/pub/ubuntu/](http://stingray.cyber.net.pk/pub/ubuntu/) trusty-updates main restricted
deb-src [http://stingray.cyber.net.pk/pub/ubuntu/](http://stingray.cyber.net.pk/pub/ubuntu/) trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://stingray.cyber.net.pk/pub/ubuntu/](http://stingray.cyber.net.pk/pub/ubuntu/) trusty universe
deb-src [http://stingray.cyber.net.pk/pub/ubuntu/](http://stingray.cyber.net.pk/pub/ubuntu/) trusty universe
deb [http://stingray.cyber.net.pk/pub/ubuntu/](http://stingray.cyber.net.pk/pub/ubuntu/) trusty-updates universe
deb-src [http://stingray.cyber.net.pk/pub/ubuntu/](http://stingray.cyber.net.pk/pub/ubuntu/) trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://stingray.cyber.net.pk/pub/ubuntu/](http://stingray.cyber.net.pk/pub/ubuntu/) trusty multiverse
deb-src [http://stingray.cyber.net.pk/pub/ubuntu/](http://stingray.cyber.net.pk/pub/ubuntu/) trusty multiverse
deb [http://stingray.cyber.net.pk/pub/ubuntu/](http://stingray.cyber.net.pk/pub/ubuntu/) trusty-updates multiverse
deb-src [http://stingray.cyber.net.pk/pub/ubuntu/](http://stingray.cyber.net.pk/pub/ubuntu/) trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://stingray.cyber.net.pk/pub/ubuntu/](http://stingray.cyber.net.pk/pub/ubuntu/) trusty-backports main restricted universe multiverse
deb-src [http://stingray.cyber.net.pk/pub/ubuntu/](http://stingray.cyber.net.pk/pub/ubuntu/) trusty-backports main restricted universe multiverse

deb [http://stingray.cyber.net.pk/pub/ubuntu/](http://stingray.cyber.net.pk/pub/ubuntu/) trusty-security main restricted
deb-src [http://stingray.cyber.net.pk/pub/ubuntu/](http://stingray.cyber.net.pk/pub/ubuntu/) trusty-security main restricted
deb [http://stingray.cyber.net.pk/pub/ubuntu/](http://stingray.cyber.net.pk/pub/ubuntu/) trusty-security universe
deb-src [http://stingray.cyber.net.pk/pub/ubuntu/](http://stingray.cyber.net.pk/pub/ubuntu/) trusty-security universe
deb [http://stingray.cyber.net.pk/pub/ubuntu/](http://stingray.cyber.net.pk/pub/ubuntu/) trusty-security multiverse
deb-src [http://stingray.cyber.net.pk/pub/ubuntu/](http://stingray.cyber.net.pk/pub/ubuntu/) trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner
# deb-src [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner
```

and 
```
ls /etc/apt/sources.list.d/
```
```

chris-lea-node_js-trusty.list                       google-chrome.list
chris-lea-node_js-trusty.list.save                  google-chrome.list.save
danielrichter2007-grub-customizer-trusty.list       google-talkplugin.list
danielrichter2007-grub-customizer-trusty.list.save  google-talkplugin.list.save
```

---

### Post by Nobody Nessie on 2014-06-19
The TorProject recommends itself to use directly the full Tor Bundle Browser package. It is updated as soon as a bug or a vulnerability is discovered, plus some improvements (you can direcly select an obfs3 bridge from your torbutton only since the 3.6.0 version I beleive).

Choose your version here : [https://www.torproject.org/download/download-easy.html.en](https://www.torproject.org/download/download-easy.html.en)
Download and extract it where you want and it's done ! You just have to click the "start-tor-browser" file in the /tor-browser_en-US/ directory. Just be very careful to block all scripts globally / javascript for the first time with Noscript, until you get more familiar with it. 

My point view about Tor, it is a fantastic tool (technically), and it can provides valuable communication channels in some countries where it is difficult or forbidden. I even made a donation as I find this project really important, but I also find that the darknet is really dirty and the exit nodes too much insecure (I personnally avoid them). And it is still a real question for me : keep using Tor, or not ?! There is still Jondonym as a very interesting alternative : cleaner and safer, and much more faster, but with a very smaller users base.

---

