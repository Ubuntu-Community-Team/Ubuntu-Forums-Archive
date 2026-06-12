---
title: "How to remove a badly installed file"
date: 2022-07-09
forum: New to Ubuntu
---

### Post by jd1237285 on 2022-07-09
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290701&stc=1[/IMG]

every time i put sudo apt update this is what i get

---

### Post by mIk3_08 on 2022-07-09
> **jd1237285 said:**
> every time i put sudo apt update this is what i get
If you are about to remove the steam. Here are the commands below, Hope this can still help.

```

sudo dpkg --remove --force-remove-reinstreq <packagename>
sudo apt-get remove <packagename>
sudo apt purge <packagename>


sudo apt purge <packagename>
sudo apt-get remove --purge <packagename>
sudo apt-get autoremove && sudo apt-get autoclean
sudo apt autoremove && sudo apt autoclean

```
Regards and cheers.

---

### Post by Impavidus on 2022-07-09
Please post text, not a screenshot of text. I can't copy parts of it to my own post. And could you change language to English by temporarily changing the LANG environment variable?```
LANG=C_LANG sudo apt update
```

I don't get the details, but it seems that apt is complaining about the l386 architecture, with a lower case ell. There used to be an i386 architecture, but on Ubuntu that's no longer supported. Could you show the contents of your /etc/apt/sources.list?

---

