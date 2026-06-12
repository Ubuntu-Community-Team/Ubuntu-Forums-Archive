---
title: "Java Runtime not working"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by prenger745 on 2008-05-10
I installed Sun Java 6 Runtime and Sun Java 6.0 Plugin from the add/remove programs.  It installed fine and everything but when I got to java.com to check for Java it says I have missing plugins.  When I click on it it says the Java Runtime Environment is available...but have to manually install.  But I already installed it?

Any help?

Thanks,
Dan

---

### Post by tjwoosta on 2008-05-10
what does it say when you type this in the terminal
```

java -version

```

Edit:
i know for a fact that i have java and its working fine but when i go to java.com and take the test i also fail

(i dont think the test works right, because i use java all the time and it works fine)

---

### Post by prenger745 on 2008-05-11
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)



Thats what it spits out.  Any ideas?

---

### Post by y-lee on 2008-05-11
> **tjwoosta said:**
> i know for a fact that i have java and its working fine but when i go to java.com and take the test i also fail

(i dont think the test works right, because i use java all the time and it works fine)

Same here that test has never worked for me in Linux, but java works fine. I wouldn't worry about it unless java is not working.

---

### Post by prenger745 on 2008-05-11
Ok here is a website I am trying to use and I get the 'missing plugin' error.

[http://www.norma.cc/#](http://www.norma.cc/#)

Once there go to the "ballistik" tab then select "ballistik US"

A window will pop up and that is where i get the "missing plugin" error.

Does it work for you?

Can you give me a page that works for you that I can go to?

Thanks,
Dan

---

### Post by philinux on 2008-05-11
Try this one.

[http://www.thinkbroadband.com/speedtest.html](http://www.thinkbroadband.com/speedtest.html)

---

### Post by prenger745 on 2008-05-11
Same error.  Missing plugins.  :(

---

### Post by Yannick Le Saint kyncani on 2008-05-11
> **prenger745 said:**
> Ok here is a website I am trying to use and I get the 'missing plugin' error.

[http://www.norma.cc/#](http://www.norma.cc/#)

It works for me, i have the icedtea-gcjwebplugin package (using konqueror).

---

### Post by gandaran on 2008-05-11
> **prenger745 said:**
> Ok here is a website I am trying to use and I get the 'missing plugin' error.

[http://www.norma.cc/#](http://www.norma.cc/#)

Once there go to the "ballistik" tab then select "ballistik US"

A window will pop up and that is where i get the "missing plugin" error.

Does it work for you?

Can you give me a page that works for you that I can go to?

Thanks,
Dan

works fine for me, I can only think do you really have the sun-java6-plugin installed? do you have another java installed like open java?
check in synaptic for what is installed.
also which firefox you using ff2 or ff3?

---

### Post by y-lee on 2008-05-11
> **prenger745 said:**
> Ok here is a website I am trying to use and I get the 'missing plugin' error.

[http://www.norma.cc/#](http://www.norma.cc/#)

Once there go to the "ballistik" tab then select "ballistik US"

A window will pop up and that is where i get the "missing plugin" error.

Does it work for you?

Can you give me a page that works for you that I can go to?

Thanks,
Dan


Hmm works fine for me.

---

### Post by alzie on 2008-05-11
Try looking in synaptic to see if you have ubuntu-restricted-extras enabled.

I was having problems with the games at Pogo.com,  enabling this helped me.

Maybe it will help you?

---

### Post by dstin1 on 2008-05-11
Type **about: plugins** (without the space) in the address bar of fire fox to see if java is installed.

I have had a lot of problems with icedtea some sites would work some wouldn't removed the icedtea package now everything works great.

---

### Post by philinux on 2008-05-11
Run this to choose which to run and see which works best.

sudo update-alternatives --config java

---

### Post by alzie on 2008-05-11
I was still having problems with java at pogo.  It would work but it was freezing completely.  Following the instructions here: [http://ubuntuforums.org/showthread.php?p=4934350#post4934350](http://ubuntuforums.org/showthread.php?p=4934350#post4934350)
I removed java 1.6 and replaced it with 1.5 and now it seems to be working fine. (or as well as it used to anyway ;) )

---

### Post by claris on 2010-04-07
> **philinux said:**
> Try this one.

thinkbroadband/speedtest

 [FONT=&quot]oh lord, that's a good one! can we trust this [speed test]("http://www.myspeedtestonline.com/")? i heard they are not accurate. is it true?[/FONT]

---

