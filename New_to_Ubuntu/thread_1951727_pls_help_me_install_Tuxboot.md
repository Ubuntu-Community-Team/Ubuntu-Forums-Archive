---
title: "pls help me install Tuxboot"
date: 2012-04-03
forum: New to Ubuntu
---

### Post by hanzj on 2012-04-03
I've downloaded tuxboot_0.2ubuntu1.tar.gz from [http://tuxboot.org/download/files-on-sf.php](http://tuxboot.org/download/files-on-sf.php). I read Tuxboot's installation instructions  ([http://tuxboot.org/installation-screenshots.php](http://tuxboot.org/installation-screenshots.php)) but it is hard to understand, because they don't specify the exact command to run in Terminal. 

Please help. All I was able to do is unpack/extract the tarball.

Thanks.

---

### Post by raja.genupula on 2012-04-03
- click at the folder , extract it .
 - now open your terminal 
  - cd to that directory what you have extracted 
- now there in the terminal do as ```
chmod +x ./tuxboot-linux*
```- then do this also```
 sudo ./tuxboot-linux*
```NOTE: Remember in the place of star , place your file name .

so after doing that you will get main dialog window from there you can move on and if help needed make a look at the screen shots in the installation link given by you . 


if you need more help on running it , provide me the file contents list .   

all the best .

---

### Post by hanzj on 2012-04-03
> **raja.genupula said:**
> - click at the folder , extract it .
 - now open your terminal 
  - cd to that directory what you have extracted 
- now there in the terminal do as ```
chmod +x ./tuxboot-linux*
```- then do this also```
 sudo ./tuxboot-linux*
```NOTE: Remember in the place of star , place your file name .


if you need more help on running it , provide me the file contents list .   

all the best .

I have not found any file inside that starts with tuxboot-linux.

Could you kindly try it yourself? Why don't you go ahead and download the small 3.8 MB tarball?

---

### Post by Elfy on 2012-04-03
There's an Install script in the one I just downloaded, there's also a deb at the download site.

Have a look in the readme in the extracted folder.

> Why don't you go ahead and download the small 3.8 MB tarball?Not everyone has broadband ;)

---

### Post by hanzj on 2012-04-03
there is an install file in the one I downloaded, too. What did you do to install it?

---

### Post by jerome1232 on 2012-04-03
Make this easy on yourself, use the debian package

64-bit
[http://sourceforge.net/projects/tuxboot/files/0.2/ubuntu-oneiric-amd64/tuxboot_0.2ubuntu1_amd64.deb/download](http://sourceforge.net/projects/tuxboot/files/0.2/ubuntu-oneiric-amd64/tuxboot_0.2ubuntu1_amd64.deb/download)


32-bit
[http://sourceforge.net/projects/tuxboot/files/0.2/ubuntu-oneiric-x86/tuxboot_0.2ubuntu1_i386.deb/download](http://sourceforge.net/projects/tuxboot/files/0.2/ubuntu-oneiric-x86/tuxboot_0.2ubuntu1_i386.deb/download)

---

### Post by Elfy on 2012-04-03
> **hanzj said:**
> there is an install file in the one I downloaded, too. What did you do to install it?I didn't go much further as I didn't want to be installing extra packages. But if you want to then navigate to the folder and

./INSTALL

it'll tell you what you need to install.

> **jerome1232 said:**
> Make this easy on yourself, use the debian package

64-bit
[http://sourceforge.net/projects/tuxboot/files/0.2/ubuntu-oneiric-amd64/tuxboot_0.2ubuntu1_amd64.deb/download](http://sourceforge.net/projects/tuxboot/files/0.2/ubuntu-oneiric-amd64/tuxboot_0.2ubuntu1_amd64.deb/download)


32-bit
[http://sourceforge.net/projects/tuxboot/files/0.2/ubuntu-oneiric-x86/tuxboot_0.2ubuntu1_i386.deb/download](http://sourceforge.net/projects/tuxboot/files/0.2/ubuntu-oneiric-x86/tuxboot_0.2ubuntu1_i386.deb/download)
I agree - mentioned them earlier :)

---

### Post by hanzj on 2012-04-03
Oh thanks. That makes it so much easier. Thanks, I've installed it now.

---

