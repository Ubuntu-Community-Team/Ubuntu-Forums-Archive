---
title: "Google earth"
date: 2012-12-06
forum: New to Ubuntu
---

### Post by roster on 2012-12-06
Can run google earth, its begins with the image but doesnt runs the program

---

### Post by levlaz on 2012-12-06
Can you please provide some more information? 

1. What kind of computer are you using, what are the specs. 

2. What version of Ubuntu are you using? 

3. How did you install Google Earth? 

Thanks!

---

### Post by roster on 2012-12-06
Im using the latest ubuntu (64 bits think so)
in a laptop dell
I used de installation package in the page of google earth

---

### Post by levlaz on 2012-12-06
Are you sure you are using 64bit? And if so did you install the 64bit version of google earth?

A quick way to check is to go to System Settings and then "Details" 

Under OS Type it will say either 32bit or 64 bit. Make sure that you are running the correct version of google earth that matches your OS - and we will go from there! :)

---

### Post by BlinkinCat on 2012-12-06
Hi,

Additionally, did you install it as per this guide ?

[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

Cheers - :)

---

### Post by kostkon on 2012-12-06
It doesn't work at the moment in Ubuntu, although a fix is coming soon.

Check the following blog post for more info
[http://www.omgubuntu.co.uk/2012/12/google-earth-for-linux-signal-11-fix-coming]("http://www.omgubuntu.co.uk/2012/12/google-earth-for-linux-signal-11-fix-coming")

---

### Post by alphacrucis2 on 2012-12-06
> **kostkon said:**
> It doesn't work at the moment in Ubuntu, although a fix is coming soon.

Check the following blog post for more info
[http://www.omgubuntu.co.uk/2012/12/google-earth-for-linux-signal-11-fix-coming]("http://www.omgubuntu.co.uk/2012/12/google-earth-for-linux-signal-11-fix-coming")

Be aware that not everyone is getting that signal 11 problem. GE 7 worked for me on 12.10 as soon as it was released.

---

### Post by roster on 2012-12-06
[attach]228316[/attach]

---

### Post by roster on 2012-12-06
that is de SS from details of the system

---

### Post by levlaz on 2012-12-06
> **roster said:**
> that is de SS from details of the system

Great, so you are running the 64 bit version. Just make sure that you downlaoded and instaleld the 64 bit version of Google Earth. If you did - then perhaps you are suffering from the same bug that was mentioned previously. 

If that is the case, I think our only option is to wait until there is a fix, or maybe try using an older version?

---

### Post by roster on 2012-12-07
I have al ready installed the 64 bit version

---

### Post by roster on 2012-12-07
I have al ready installed de 64 bit version

---

### Post by levlaz on 2012-12-07
It seems the latest version "7" is still in beta, why don't you try installing the previous version "6.2" 

Click on advanced setup on the download page and select the previous version.

---

### Post by roster on 2012-12-07
How i install the .bin file?

---

### Post by levlaz on 2012-12-07
Download the .bin file to the desktop 

Open a terminal 

```
cd /home/username/Desktop 
```* Make sure to replace username with your actual username 

```
 sh GoogleEarthLinux.bin 
```It should now install and you can use it.

---

### Post by roster on 2012-12-07
=( im too bad, Cant install

roster@roster-Inspiron-1464:~/Descargas$ sh GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 5.2.1.1588..............................................................
setup.data/bin/Linux/amd64/setup.gtk2: error while loading shared libraries: libxml2.so.2: cannot open shared object file: No such file or directory
setup.data/bin/Linux/amd64/setup.gtk: error while loading shared libraries: libSM.so.6: cannot open shared object file: No such file or directory
The setup program seems to have failed on amd64

Fatal error, installer failed to run at all!
roster@roster-Inspiron-1464:~/Descargas$

---

### Post by levlaz on 2012-12-07
Do not run this from the Downloads directory (Discargas means downloads, correct?) Move it to the desktop first, then change your directory to the desktop, and then run the file. 

I just did it and it worked just fine. 

Follow these steps: 

1. Open the Downloads (Discargas) directory and drag the file right onto the Desktop. 

2. Open a terminal and change the active directory to the desktop 

```
 cd ~/Desktop 
``` (escritorio???) 

then 

```
 sh GoogleEarthLinux.bin 
``` 

It will work as long as you are running this from the desktop and NOT the downloads folder.

---

### Post by kostkon on 2012-12-07
Why .bin? Where did you find it?

If you try to [download google earth]("www.google.com/earth/download-earth.html") while being logged in ubuntu, it will offer you the option to download a 32bit or 64bit .deb file.

---

### Post by levlaz on 2012-12-07
> **kostkon said:**
> Why .bin? Where did you find it?

If you try to [download google earth]("http://www.google.com/earth/download-earth.html") while being logged in ubuntu, it will offer you the option to download a 32bit or 64bit .deb file.

He is having trouble getting Google Earth 7 to work (which is what google earth gives you when you download the ubuntu link) the .bin is for the stable version 6.2 

The .bin is easy to install you just have to do it from the Desktop and not from the Downloads folder.

---

### Post by rburkartjo on 2012-12-07
yup sure will be nice when they fix. having the same problem for a while.

---

### Post by monkeybrain2012 on 2012-12-07
> **levlaz said:**
> He is having trouble getting Google Earth 7 to work (which is what google earth gives you when you download the ubuntu link) the .bin is for the stable version 6.2 

The .bin is easy to install you just have to do it from the Desktop and not from the Downloads folder.

Why not from Downloads? You can cd into it just like you cd into the Desktop (by the way "cd Desktop" is fine, you don't need "cd ~/Desktop" if you start the terminal normally so you are in your home directory)

---

### Post by roster on 2012-12-09
setup.data/bin/Linux/amd64/setup.gtk2: error while loading shared libraries: libxml2.so.2: cannot open shared object file: No such file or directory
setup.data/bin/Linux/amd64/setup.gtk: error while loading shared libraries: libSM.so.6: cannot open shared object file: No such file or directory
The setup program seems to have failed on amd64

Fatal error, installer failed to run at all!
roster@roster-Inspiron-1464:~/Escritorio$

---

### Post by rburkartjo on 2012-12-09
here is a link the new version of google-earth that is suppose to fix the problem. it did not work for me .same error. but maybe it will for someone else. good luck.

[http://www.webupd8.org/2012/12/download-google-earth-7-with-fixed.html](http://www.webupd8.org/2012/12/download-google-earth-7-with-fixed.html)

---

### Post by roster on 2012-12-09
ok, i will try

---

### Post by rburkartjo on 2012-12-18
bump-has anyone who has been experiencing the same problem found a fix yet?

---

### Post by SuperFreak on 2012-12-18
I have Google earth 6 working after not being able to open the program (got a brief flicker of program starting then it disappeared off the screen). I found this thread and it worked perfectly [http://ubuntuforums.org/showthread.php?t=2085529]("http://ubuntuforums.org/showthread.php?t=2085529")

I don't know if this will work for Google Earth 7 though

---

