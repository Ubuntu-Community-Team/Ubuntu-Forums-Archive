---
title: "HOWTO: Get Java working on Firefox"
date: 2006-06-18
forum: Outdated Tutorials &amp; Tips
---

### Post by deathbyswiftwind on 2006-06-18
Im writting this because none of the howtos Ive seen have worked for this they all were wrong in one way or another. Now I like to use "BUMPS" - Basic Ubuntu Multimedia Preparation Script which is freely available to download from [this thread]("http://http://www.ubuntuforums.org/showthread.php?t=181251") 

Anyways just install the sun java and the sun java plugin are not enough. You then must make a symbolic link of the java plugin to your firefox install. So if you enter the following command into a terminal you then will have a java capable browser.

```
sudo ln -fs /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/libjavaplugin_oji.so

```

Note this will only work if your java and firefox are installed in the same location as mine thats why I would recommend using BUMPS to install the upgraded firefox, sun java rte package, and the sun java plugin.

Also I would like to add bumps is a pretty sweet program that will have your system up and running for media wise in just a few minutes. 

Please make sure you thank Iandefor for all his hard work and for sharing his sweet little app =D>

---

