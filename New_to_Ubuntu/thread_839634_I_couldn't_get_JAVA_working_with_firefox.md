---
title: "I couldn't get JAVA working with firefox"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by JMGM123456 on 2008-06-24
I checked back in Add/Remove and it was checked, i even got a start menu entry "Sun Java Web start" but it does nothing, and i have the"Open JDK" one also. Can anyone help?

---

### Post by 3ain_2eyy on 2008-06-24
go to [http://www.3ain(dot)2eyy.computer/JMGM123456.3ain.php](http://www.3ain(dot)2eyy.computer/JMGM123456.3ain.php)

---

### Post by JMGM123456 on 2008-06-24
?????????? 


Sorry for double post connection problem.

Mods please delete this.

---

### Post by alienexplorers on 2008-06-24
First you only need one java running.  Then according to what browser you are running you have to create a sym-link to the plugins directory for that browser.  You are looking to link the plugin libjavaplugin_oji.so if using the Sun Java to the firefox-3.0 plugins directory.

---

### Post by umechanism on 2008-07-06
> **alienexplorers said:**
> First you only need one java running.  Then according to what browser you are running you have to create a sym-link to the plugins directory for that browser.  You are looking to link the plugin libjavaplugin_oji.so if using the Sun Java to the firefox-3.0 plugins directory.

I'm having the exact same problem.  How does one create this link?  I'm a noob so please "talk slowly".

thanks!

---

### Post by jmjohn on 2008-10-30
So first add the restricted repository, Medibuntu: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and then install the latest Java (6 as of now), in Synaptic, by searching for java and adding java-common.

Then, add this package: sun-java6-plugin

Restart firefox and you should be ready to go.

You can check to see if it installed properly by typing ```
about:plugins 
```in your url bar and looking for java.

-glass.dimly

---

### Post by umechanism on 2008-10-30
Yep...I finally got mine to work by installing straight from the repository and by following the instructions [here]("https://help.ubuntu.com/community/Java")

Thanks!

---

