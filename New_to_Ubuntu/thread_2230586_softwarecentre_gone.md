---
title: "softwarecentre gone"
date: 2014-06-20
forum: New to Ubuntu
---

### Post by Ruerd_Visser on 2014-06-20
Hello, i am new to ubuntu 14.04. Last week i freshly installed ubuntu 14.04. But i did a clean install again. After the softwarecentre was damaged. And yesterday the softwarecentre and sound button where suddenly gone again. It could have to do with the installment of the wrong version of crossover. i386 instead of the amd 64 version. Anyway there is no way i can get access to the software centre and sound anymore. It's completely gone since the buttons are no longer there. Also i can't find them back in unity. Could anyone help me out restoring the softwarecentre and sound?

---

### Post by sudodus on 2014-06-20
Welcome to the Ubuntu Forums :-)

Try with 

```
sudo apt-get install software-center
```

I don't know what is wrong with your sound. Is it only the 'sound button'? Is there sound, if you play an audio file or video file?

---

### Post by amborsdorfer on 2014-06-20
What exactly happened to the Software Center that made you reinstall Ubuntu? Is it gone from the application menu on the left?

[IMG]http://i.imgur.com/zCjEHQU.png[/IMG]

Try checking whether the file "software-center-gtk3" is present in your file system (type this in a terminal):

```
ls /usr/bin/software-center-gtk3
```

If it's not, you might want to install it using:

```
sudo aptitude install software-center
```

I am not sure what your issue with your sound is, maybe you could describe it in more detail?


Edit: Dammit, sudodus was faster.

---

