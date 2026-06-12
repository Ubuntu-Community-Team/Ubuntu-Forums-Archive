---
title: "Medibuntu question- what is GPG Key"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by Unreal223linux on 2008-05-04
In the steps to install the stuff from medibuntu:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

It says you need to add it to your gpg key after you add it to your sources list. What exactly is a gpg key/what does it mean? The command says something about medibuntu keyring? I kinda just want to know what the command is actually doing more than anything. 

I understand that the first part is to just add the repository to the list that synaptic will download from. But what exactly does that other do?

Also am I correct in assuming that w32codecs is not installed with ubuntu-restricted-extras?

---

### Post by SunnyRabbiera on 2008-05-04
its kind of like a insurance policy, to make sure you are using trusted sources.
GPG keys are usually used when people feel the need to verify their sources, especially third parties.
I would not worry about it as I use medibuntu, it will do you no harm to do as they say on the page.

---

### Post by zvacet on 2008-05-04
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by Unreal223linux on 2008-05-04
Thanks, I wasn't worried about it being harmful I just wanted to know exactly what it does.

---

