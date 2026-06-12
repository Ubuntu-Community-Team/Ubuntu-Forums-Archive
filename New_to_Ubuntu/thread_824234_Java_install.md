---
title: "Java install"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by bluzepher on 2008-06-09
I tried to install Java and it will not install.

 sh j2re-1_4_2_06-linux-i586-rpm.bin   is the file I downloaded to my desktop then used this command, error, cant open file..

any ideas ?


very new to Ubuntu

thanks in advance for your help..

---

### Post by jon8105 on 2008-06-09
Your best option, IMO, would be to get java from the repositories.  Go to System>Administration>Synaptic Package Manager, click on search and type in Openjdk (this is the Java runtime I installed).  Check the file that says "openjdk-6-jre" and it will also mark all of the other necessary files.  Then click "Apply" and let it do the rest.

Hope that helps!

---

### Post by RealPSL on 2008-06-09
```
chmod u+x j2re-1_4_2_06-linux-i586-rpm.bin; ./j2re-1_4_2_06-linux-i586-rpm.bin
```

Will solve your problem however I agree with the previous poster in that you should install it from synaptic whenever possible as it is so must cleaner. I also read today that 1.4.2 will be end of life soon so you should look at Java 5 and 6.

---

### Post by superzorro on 2008-06-09
Or you could also just go to Applications > Add/Remove and search for Java, select it and then click Apply changes, and that should install Java.

Good luck

---

