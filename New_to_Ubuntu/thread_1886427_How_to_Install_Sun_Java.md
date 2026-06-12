---
title: "How to Install Sun Java"
date: 2011-11-24
forum: New to Ubuntu
---

### Post by vincej on 2011-11-24
Hi - I have succeeded in installing Sun Java. However, using a Microsoft metaphor, do you need to "associate" an existing application sing Open JDK to now use Sun Java, or is it likely that the app. would simply find Sun Java is I deleted the Open JDK version ? 

Many Many Thanks

---

### Post by ExileAmongYou on 2011-11-24
You need to run the command "update-java-alternatives" in a terminal. 
First you run:
```
sudo update-java-alternatives --list
```

And you'll see a list of the installed java versions, which in my case looks like this:
```
java-1.6.0-openjdk 1061 /usr/lib/jvm/java-1.6.0-openjdk
java-1.7.0-openjdk-amd64 1051 /usr/lib/jvm/java-1.7.0-openjdk-amd64

``` 

Copy the first little name string next to the one you want (e.g. "java-1.7.0-openjdk-amd64"), and paste it after --set in the next command like this:
```
sudo update-java-alternatives --set java-1.7.0-openjdk-amd64

```

---

### Post by wolfen69 on 2011-11-24
If you deleted openjdk, the app *should* automatically use java.

---

### Post by Immolatus on 2011-11-25
Is this for programming?
If so you need to set the bash path variable in .bashrc.

---

### Post by vincej on 2011-11-25
It's not for programming as such - I have an app. which is currently using the default - Open JDK. I am getting some performance problems, and allegedly, I will get better performance with Sun Java.  

I'm new to Ubuntu, so it's all a bit of a struggle. 

Many thanks !

---

### Post by Immolatus on 2011-11-25
ok, then just remove open JDK using Synaptic if you like and install Sun JDK. should be fine.

---

