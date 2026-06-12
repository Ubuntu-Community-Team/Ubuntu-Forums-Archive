---
title: "Need help getting java 6 into firefox 3"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by camino3701 on 2008-08-01
I need help getting java to work in firefox I was able to download java and open it so that it shows in "applications/internet/sun java 6 web start" also java web site test shows that it is installed but "about: plugins" does not show it and when I try to use a web site that needs java it won't work.

Thanks for any help,
RLB

---

### Post by tuxxy on 2008-08-01
I use the GCJ java, works great for me.  If you want to install sun java 6 you need to install the java web plugin usually into your /usr/lib/mozilla dir

Once you done that run this command in the terminal to select the new java to be used

```
sudo update-alternatives --config java
```

---

### Post by camino3701 on 2008-08-01
1. I am really new at this so need alot of help.
2. where do I find GCJ java.
3. what is the procedure for installing the java plugin, where is or what is the command for /usr/lib/mozilla dir (how do I do that)

RLB

---

### Post by exsapientiasalus on 2008-08-01
If you also want support for mp3s, movie codecs,flash, etc., you can get java working by installing ubuntu-restricted-extras. From the command line (in gnome-terminal), type: sudo apt-get install ubuntu-restricted-extras. You may need to enable repositories in advance. Run synaptic and edit your repositories or find software repositories (I'm using SUSE now, so not sure where it is) in your system or preferences menu and enable all of your repositories. You don't need to install all of the other extras if you don't want (though they are helpful). If you just want java 6, issue the command from the command line: sudo apt-get install sun-java6-plugin or search for it in synaptic. It will download java-bin and java-jre I think as well. That will get you going.

---

### Post by camino3701 on 2008-08-01
I tried to follow your instructions and I don't know what I realy did but java is now working in firefox.

Thanks again,
RLB

---

### Post by meitetsuman on 2008-08-11
I had a lot of trouble getting Java to download from the Java website, but finally, I went to "Applications" "Add/Remove Applications" and chose "All Open Source Applications".  Then I downloaded "Icedtea Java Plugin".  I had some trouble resolving a dpkg error message before I could do it, but then it went really smoothly and I could finally use Java in Firefox.

---

### Post by Snave88 on 2008-08-11
meitetsuman - how did you resolve the dpkg error?

---

### Post by silkstone on 2008-08-11
The way I install java 6 and the FF3 plugin is like this...

sudo apt-get remove icedtea-gcjwebplugin openjdk-6-jre && sudo apt-get install sun-java6-fonts sun-java6-jre sun-java6-plugin

That has worked fine on two machines.

---

