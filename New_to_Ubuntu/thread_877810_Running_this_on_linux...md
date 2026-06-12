---
title: "Running this on linux..?"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by ikick on 2008-08-02
Hey there guys.

I am totally new to ubuntu and linux. The reason i decided to switch was so my game server could run a little better.

Now, i was wondering how to run a java game on linux (instead of using .bat files on windows). 

I took a screen shot as i am not understandable because i don't even know what i am talking about half the time :o

Basically, i need to run a bunch of .java (aka .class) files.

[http://i37.tinypic.com/vzvmo6.jpg](http://i37.tinypic.com/vzvmo6.jpg)

In the image on the right; thats what i need to change.

Any ideas?

Regards,

ikick

---

### Post by howlingmadhowie on 2008-08-02
the first thing you need to do is install java.

system->administration->Synaptic Package Manager.

search for openjdk and select the jdk.

then you may well be able to start the server.

============== edit ================

if the game folder doesn't include a jython.jar, you can install jython through synaptic as well.

---

### Post by ikick on 2008-08-02
thank you very much for that.

What if i wanted to run this on a dedicated server (ubuntu) and only had access to ssh or command line?

---

### Post by kpkeerthi on 2008-08-02
I suggest you stick with Sun's JDK

Type this in a terminal (for command-line only/server systems):

```
sudo aptitude install sun-java6-bin 
```

You can, however, have multiple JDK implementations in your box. To choose the default active Java, run this command

```
sudo update-alternatives --config java
```
and select Sun's as your preferred Java.

More info here [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by howlingmadhowie on 2008-08-02
then you'd do this to install a jre and jdk:

sudo apt-get install openjdk-6-jdk

---

### Post by ikick on 2008-08-02
Thanks again.

One more baby question,

Do i keep what is in run.bat the same? or should i chage it to something else?

Thanks very much

---

### Post by howlingmadhowie on 2008-08-02
no, the bat file is windows specific. you'll have to start the application using a valid command for the unix command line. try:

java  -Xmx1024m server

if that doesn't work, maybe somebody will answer who knows something about bat files :)

---

