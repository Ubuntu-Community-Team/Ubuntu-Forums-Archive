---
title: "Install ubuntu-studio"
date: 2018-01-26
forum: New to Ubuntu
---

### Post by onesixtyfourth on 2018-01-26
Hi. I have been away for a while and just completed a 17.10 install of Ubuntu (just checked and my old laptop has 13.04 on it ) onto my new hardware. Great to have a Linux machine back but I am struggling to remember where things are and how to do certain things. I used to have all the ubuntu-studio applications installed through meta packages and I have searched to see if I can still do this but all info I can find seems to be old. I have found reference to:

[audio meta-package]("http://packages.ubuntu.com/search?searchon=names&keywords=ubuntustudio-audio")
[video meta-package]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=ubuntustudio-video")
[graphics meta-package]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=ubuntustudio-graphics")[COLOR=#333333][FONT=Ubuntu] 
[/FONT][/COLOR][desktop meta-package]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=ubuntustudio-desktop")

but that page references 12.04 which is older than my last install. I searched for the audio package from the Activities screen and I found what appears to be the meta package but I refrained from installing further as I wasn't sure if it was right. 

I don't want to install the full ubuntu-studio desktop as I want to keep the ubuntu one. I use Blender a little, play guitar and everyone should have good graphics apps for photos etc. So a little guidance please preferably to some up to date documentation so I can get back into the swing of things.

Thanks

---

### Post by Frogs Hair on 2018-01-26
Hello and Welcome !

You can install the Ubuntu Studio applications without using any U Studio meta packages and drawing unneeded dependencies . I've been using Arduor and Hydrogen drum machine from 17.10. Blender, audacity, and various guitar applications are also available from the repository. As for codecs use the following command . Be sure to enable the Canonical Partners repository from software and updates. ```
sudo apt install ubuntu-restricted-extras    
```

---

### Post by onesixtyfourth on 2018-01-26
Good point and I was thinking that when looking through their docs. I already have the restricted-extras package. Thanks.

---

