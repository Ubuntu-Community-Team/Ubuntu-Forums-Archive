---
title: "error 'BrokenCount&gt;0'"
date: 2012-12-26
forum: New to Ubuntu
---

### Post by jtnath on 2012-12-26
i tried to install furiusisomount using software center.it gave me errors so i downloaded furiusisomount deb files and install it via terminal .gave me problems saying files like fuseiso, python-glade n several others were not installed n included certain unmet dependecies.
i downloaded above files and tried installing furuiusisomount again.but now it seems ive trashed something withing my ubuntu an dthe software center does not allow me to download any files . software manager gives me error stating it requires installations from untrusted packages. and to download any other software i get errors stating tht to download tht application i have to remove furiusisomount , fusiso , fuseiso9660.
[B]how do i do this ????
[/B]and on the top ryt corner of my screen i have a **RED alert **sign tht tells me an error occured and to run package manager or in terminal apt-get to see wots wrong.. the error message is **error 'BrokenCount>0**'. Somebody please get me out of this error..!!!

---

### Post by ibjsb4 on 2012-12-26
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get update
```

Get any errors?

---

