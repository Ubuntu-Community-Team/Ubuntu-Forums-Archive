---
title: "2 questions about .deb and adobe flash."
date: 2008-04-26
forum: New to Ubuntu
---

### Post by rhc on 2008-04-26
1) I'm using Kde 4 Remix in Hardy.

I want to install flash player but when i opened the file that i downloaded from Adobe site(install_flash_player_9_linux.tar.gz),
i unrar it,then write

xxx@ubuntu:~/&#304;ndirilenler$ sudo ./flashplayer-installer
[sudo] password for xxx:
sudo: ./flashplayer-installer: command not found

What can be my problem about this flash thing. I can't install it.

2) I can't use deb files in Kubuntu :) Easy question
I think Ark don't open them. (i installed unrar-free)
How can i make it?

---

### Post by nebu on 2008-04-26
1 > just type ---->>> chmod +x flashplayer-installer

2> deb files.... just type  ------>>> sudo dpkg -i package_file.deb

---

### Post by rhc on 2008-04-26
I did what you say and it solved problems but now i have 2 questions again.

1) What is the use of chmod +x ?

2) How can i open deb files without using terminal?

---

### Post by nebu on 2008-04-26
1. chmod +x [I]filename
[/I]gives you acess to execute the file specified..... just type *man chmod *for a better idea

2. right click on the .deb file and tehn choose kubuntu package menu > install package

---

### Post by rhc on 2008-04-26
Thanks a lot.
I said it solved the problem,but it didn't. when i go to youtube(or youtube like sites),it doesn't say "turn on" java(cause it's installed) but there is a grey background in the place of video,but no video there.

Like this;

[http://imaj.at/39665-582c](http://imaj.at/39665-582c)

---

### Post by Google Spider on 2008-04-26
hmmm..so are you sure flash **was** installed by running those commands?

Another way of installing flash, java and all other codecs is
```
sudo apt-get install ubuntu-restricted-extras
```

EDIT: Oh, sorry if you know that already. Just saw your number of posts.

---

