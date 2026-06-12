---
title: "JRE 1.3.1 parallel to 1.6"
date: 2010-02-05
forum: Programming Talk
---

### Post by 4thfloorstudios on 2010-02-05
Hi,
I need to use the 1.3.1 JRE.

Therefore I downloaded and installed the RPM file from Sun and tried to configure the 1.3.1 as default JRE via 

```
sudo update-alternatives --config java
```but the 1.3.1 JRE is not shown there. Is there any other way to set the default JRE in Ubuntu 9.10? I really did not find any other explanation than the one I tried.

---

### Post by kahumba on 2010-02-05
1) Ubuntu doesn't support RPMs (unless you transcoded it with alien).
2) Download the non-RPM self extracting JRE/JDK, point your IDE to this JRE/JDK and you're done.
but what exactly do you need the JRE 1.3.1 for (?)

---

### Post by 4thfloorstudios on 2010-02-05
I need it for a webstart application which only works with JRE 1.3.1, so pointing my IDE does not help unfortunately.

---

### Post by kahumba on 2010-02-05
Well, as I said you gotta download the non-RPM version (see screenshot), unpack it, go to the /bin folder and try using the "java" executable (from either subfolder) to open your webstart app.

---

### Post by 4thfloorstudios on 2010-02-05
As i wrote I have already installed the RPM file (converted it before to .deb of course). That is not my problem :)

If I can use the 1.3.1 javaws binary to open the webstart app with 1.3.1, then I am fine (can not test right now...) and do not need to switch the JRE in general.

Although I really would like to know why the configuration via update-alternatives is not possible in my case or what the alternatives for setting the JRE globally are.

Thanks for your help!

---

### Post by doas777 on 2010-02-05
the update alternatives line you used, does not specify which java version to use, so it is unlikely that it will work correctly for you. 
I would recomend just calling the 1.3 runtime explicitly when you execute your java applet.

---

### Post by 4thfloorstudios on 2010-02-05
Yes, I know that. The command line I posted should show me the JREs known as installed (I think it is kind of the same as "update-java-alternatives --list") but it only shows 1.6 and no 1.5 or 1.3 (both are installed).

---

