---
title: "totem not playing css dvds"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by ecrivain5 on 2008-05-09
Although this is listed as a new thread. The forums are littered with this problem. Yet all the solutions offered seem not to cure the problem
Totom player puts out the folliwing error when attempting to play css disks. "Error...cannot read from source." It is fine when running other dvds. I have tried installing all the suggested fixes but to no avail. Is there anyone out there who knows the fix for this problem please. (me hairs falling out).[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
:confused: 
I really want to use ONLY ubuntu but have been forced to reinstall windows to play my css dvds.
My thanks in advance if you can bring about a good solution.
Brian

---

### Post by mlentink on 2008-05-09
Have you installed libdvdcss2?

See e.g.: [http://www.ubuntugeek.com/playing-encrypted-dvds-in-ubuntu.html](http://www.ubuntugeek.com/playing-encrypted-dvds-in-ubuntu.html)

or: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by szymon_g on 2008-05-09
sudo aptitude install libdvdcss2 :>

---

### Post by bumanie on 2008-05-09
You need to add medibuntu to your /etc/apt/sources.list and then download css package.
> sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
 Then > sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update > sudo apt-get install libdvdcss2
 That should work

---

### Post by por100pre1 on 2008-05-09
You can also download it directly from here:

[http://packages.medibuntu.org/pool/free/libd/libdvdcss/](http://packages.medibuntu.org/pool/free/libd/libdvdcss/)

---

### Post by ecrivain5 on 2008-05-10
Thanks to you all. I will print off these replies and try them when I reinstall kbuntu later.
My thanks to you all for your suggestions.
Brian

---

