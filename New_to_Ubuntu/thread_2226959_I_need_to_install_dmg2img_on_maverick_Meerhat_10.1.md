---
title: "I need to install dmg2img on maverick Meerhat 10.10"
date: 2014-05-29
forum: New to Ubuntu
---

### Post by Louise_Avon on 2014-05-29
I am told that the reason my terminal can not locate dmg2img package is because its an old release and is now archived. I don't want to upgrade my operating System, but would like to use the package dmg2img in my linux 10.10. Where and how do I get and download the dmg2img software for the version I am using as on my VC.

---

### Post by Frogs Hair on 2014-05-29
There are old repositories for end of life upgrades , but I don't know what they include and the sources have to added manually. If at all possible and your hardware supports a newer version it would be wise to install just for security reasons. 

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by kansasnoob on 2014-05-29
[http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release](http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release)

---

### Post by Louise_Avon on 2014-05-29
Does anyone know where these old repositories are because i want to use that specific 10.10 dmg2img version without upgrading?

---

### Post by Louise_Avon on 2014-05-29
Do you know the exact name of the package...so i can search for it?

---

### Post by QIII on 2014-05-29
Hello!

kansasnoob included a link with the instructions you need.

Cheers!

---

### Post by Frogs Hair on 2014-05-29
Where it says code name you would enter the name of the release . Read through the posted links.
Ubuntu package search no longer includes 10.10 packages.[http://packages.ubuntu.com/search?keywords=search](http://packages.ubuntu.com/search?keywords=search)   

## EOL upgrade sources list.
# Requiredhttp://packages.
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME-security main restricted universe multiverse

# Optional
#deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME-backports main restricted universe multiverse

---

