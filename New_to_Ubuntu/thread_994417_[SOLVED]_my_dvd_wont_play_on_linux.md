---
title: "[SOLVED] my dvd wont play on linux"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by aszxcv on 2008-11-26
totem movie player wont play my dvd movies

---

### Post by sstusick on 2008-11-26
You'll need to install the codecs. Go into Applications > add/remove and install Ubuntu-restricted extras. That should have everything you'll need.

---

### Post by aszxcv on 2008-11-26
i installed it still doesnt play my dvd

---

### Post by sirjoebob on 2008-11-26
I use VLC to play all DVDs and video files in general

---

### Post by doas777 on 2008-11-26
go to [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and follow the repository how-to. that should do it.

ubuntu can't legally distribute libdvdcss2, the DVD copy protection decoder.

sirjobob is right, VLC will play almost anything. I just wish their UI wasn't such crap.
good luck,
franklin

---

### Post by oldos2er on 2008-11-26
You'll need to enable the Medibuntu repository (see [http://medibuntu.org/](http://medibuntu.org/)), and install libdvdcss2.

---

### Post by aszxcv on 2008-11-26
i dont know what gives i install  by following [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) instructions

> sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) --output-document=/etc/apt/sources.list.d/medibuntu.list


then
> sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

then

> sudo apt-get install libdvdcss2

> wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb

then
> sudo apt-get install w32codecs

stilll dvd wont play

---

### Post by doas777 on 2008-11-26
I noticed you marked the post solved. are you good on DVDs?

---

### Post by aszxcv on 2008-11-26
somewhat good?

i got one of them to play

but another one the content is scramble i can barely see the scenes

but none of them can i get the main menu you normal get when you play dvd's

---

### Post by doas777 on 2008-11-26
well, I noticed that you did some weird steps with the mediubuntu install. you don;t have to follow the instructions for installing the packages individually, so if you use 
```
sudo apt-get install libdvdcss2
```

you do not need to do:
```

wget -c http://packages.medibuntu.org/pool/f...untu4_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb 

```

I'm really not sure what if any harm would come from double installing it, but that is one potential reason you could be having trouble.

there also may be some newer DVDs that don;t completely follow the CSS spec, so that they can keep people from ripping. as a general rule, if you can;t rip it with a tool like dvd decryptor, then you prolly won;t be able to play it in linux. 

good luck,
franklin

---

### Post by aszxcv on 2008-11-26
thanks is there anyway to delete the double package

---

### Post by doas777 on 2008-11-26
I don't use dpkg often, but according to [http://en.wikipedia.org/wiki/Dpkg](http://en.wikipedia.org/wiki/Dpkg), if you repeat the same command with a -r instead of -i it will uninstall.

I would try
```

sudo dpkg -r libdvdcss2_1.2.9-2medibuntu4_i386.deb
sudo apt-get update
sudo apt-get purge libdvdcss2 
sudo apt-get autoremove
sudo apt-get install libdvdcss2

```

---

### Post by aszxcv on 2008-11-26
i get this error when i run

> sudo dpkg -r libdvdcss2_1.2.9-2medibuntu4_i386.deb


> Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !


---

### Post by doas777 on 2008-11-26
ok, try
```

sudo apt-get purge libdvdcss2 
sudo apt-get update
sudo apt-get autoremove
sudo apt-get install libdvdcss2

```

I gotta go offline for a while (and we're getting to the end of the advice I can provide), but I'll be back tommorow.

good luck,
franklin

---

### Post by aszxcv on 2008-11-26
sorry for my constant posting but why the reinstall of > sudo apt-get install libdvdcss2

after > sudo apt-get purge libdvdcss2 


noob to linux  me

---

### Post by doas777 on 2008-11-27
since you do need libdvdcss2, I'm suggesting that you remove it, and then reinstall.
the error message you recieved when we tried to use dpkg -r suggested that we use aptitude or apt to remove it.

give it a try. if you want, you can remove it with apt-get purge and then test to see if it works as is. my guess is that you will not have the lib anymore after running purge, so my thought is that it won't work, but hey, we're just shooting in the dark anyway. don't be afraid to try stuff.

let us know how it works out

---

