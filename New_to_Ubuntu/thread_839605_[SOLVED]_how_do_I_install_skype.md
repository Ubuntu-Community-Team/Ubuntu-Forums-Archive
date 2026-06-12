---
title: "[SOLVED] how do I install skype?"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by bmann11 on 2008-06-24
Tried searching through previous threads but didn't come up with anything.

I'm running Hardy on a dell laptop with an intel pentium.  Thanks

By the way, I, of course, found the web page to download the linux version of skype, but in my limited experience with ubuntu, downloading from a web site has never happened, thus the question.

---

### Post by isaacj87 on 2008-06-24
Just head over the the Skype website and download a copy (a deb).

Here's the direct link: [http://www.skype.com/download/skype/linux/choose/]("http://www.skype.com/download/skype/linux/choose/")

Choose the selection "Ubuntu 7.04+"

Then when the file is downloaded, just run the deb.

---

### Post by drunkardivan on 2008-06-24
Go to skype.com, click on "Downloads", and choose Ubuntu.

It's self-explanatory from there.

---

### Post by webofunni on 2008-06-24
You can get the ubuntu binary package from skype website. 

Usually following steps will work : 

```

#wget http://www.skype.com/go/getskype-linux-ubuntu
#dpkg -i skype-debian_2.0.0.72-1_i386.deb

```

---

### Post by bmann11 on 2008-06-24
Wow, that was easy.  Thanks.

---

### Post by ChompTheMan on 2008-06-24
Skype is also available in the Medibuntu repositories.  Once you add their repository then Skype is as simple to install as any other program in the official repositories(add/remove, synaptic, command line install), plus it will be updated for you, as opposed to grabbing the .deb manually everytime.  To add the medibuntu repository:
[URL="https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f"]
https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f[/URL]

There are also other packages in the medibuntu repo(like Google Earth).  To see their list of packages go to:

[http://www.medibuntu.org/packages.php]("http://www.medibuntu.org/packages.php")

---

### Post by rafaelrc on 2008-06-24
Or you can add this repository to your sources list:

deb [http://download.skype.com/linux/repos/debian](http://download.skype.com/linux/repos/debian) stable non-free

---

