---
title: "Java is not working"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by EleFlameMax on 2008-06-12
I'm on a site that requires the Java applet, and it shows me the loading screen, but after that there is nothing.

---

### Post by Biggy on 2008-06-12
what version of java do you have installed ?

in terminal type :
> java -version

---

### Post by Biggy on 2008-06-12
check "Enable Java" from firefox

Edit>Preferences>Content>Enable java

---

### Post by wolfen69 on 2008-06-12
did you install the sun-java6-plugin from synaptic?

---

### Post by Ash1984 on 2008-06-12
I have noticed that in synaptic there is no sun-java6-plugin. Why would this be?

---

### Post by Nepherte on 2008-06-12
Are you using 64 bit? Sun does not have a browser plugin for java. Fortunate for us, there is openjdk that has a plugin icedtea-gcjwebplugin. That requires installing openjdk. Search for it in synaptic to install.

---

### Post by Ash1984 on 2008-06-12
Hi I tried Icedtea and it works. Thanks

---

