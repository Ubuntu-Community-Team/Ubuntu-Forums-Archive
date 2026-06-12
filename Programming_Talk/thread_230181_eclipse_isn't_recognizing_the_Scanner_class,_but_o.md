---
title: "eclipse isn't recognizing the Scanner class, but only in ubuntu."
date: 2006-08-05
forum: Programming Talk
---

### Post by Amablue on 2006-08-05
When I switch to windows and open the same file, eclipse has no problem. I don't know why Ubuntu's eclipse isn't recognizing it.

---

### Post by mlind on 2006-08-05
Are you using Sun's JDK 1.5 ?

---

### Post by mikeoh on 2006-08-05
What JDK are you using?  Eclipse out of the repositories using the GNU java compiler, libraries and interpreter and these are different then the standard Sun Java JDK.  So it would I would guess not being able to open a standard class is because of this.

---

### Post by rko618 on 2006-08-06
I believe the Scanner class is new to Java 1.5.  Check to make sure you have Sun's 1.5 SDK installed.

---

### Post by Amablue on 2006-08-06
> **mlind said:**
> Are you using Sun's JDK 1.5 ?

I jsut double checked. According to synaptic, I have sun-java5-jre, sun-java5-bin, and sun-java5-plugin all installed. That's the one I need, right? Also, eclipse is set to use 5.0 in the compiler settings.

---

### Post by bieber on 2006-08-06
You need the JDK, still.

---

### Post by jeff_ on 2006-08-06
I had this problem even after I installed 1.5. In eclipse go to Window > Preferences > Java > Installed JRE's and make sure that you have java 1.5 there and set as default. Also make sure that java -version returns 1.5 and if it doesn't use update-alternatives --config java to make 1.5 the default. 

Tell me if you need clarification or if this doesn't work.

---

### Post by mlind on 2006-08-07
You probably haven't set Sun's java as default ?

```

sudo update-alternatives --config **java**

```
You may have to do same for **javac** too.

---

### Post by hod139 on 2006-08-07
This howto explains the process of setting up eclipse and Sun's java. [http://ubuntuforums.org/showthread.php?t=201378](http://ubuntuforums.org/showthread.php?t=201378)

[quote=mlind]
You probably haven't set Sun's java as default ?

     Code:
     [LEFT]sudo update-alternatives --config **java**[/LEFT]
  
 You may have to do same for **javac** too.
[/quote]
You should use ```

sudo update-java-alternatives -s java-1.5.0-sun
``` to update all of java-common.  Do not use ```

update-alternatives

``` as that will miss some stuff.

---

