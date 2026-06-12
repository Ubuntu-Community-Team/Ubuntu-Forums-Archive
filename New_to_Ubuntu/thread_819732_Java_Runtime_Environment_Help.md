---
title: "Java Runtime Environment Help"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by redfox1160 on 2008-06-05
I need help installing the Java Runtime Environment. I went to [http://www.java.com/en/download/help/5000010500.xml#rpm]("http://www.java.com/en/download/help/5000010500.xml#rpm") and tried to use the guide, but it said I needed the root password. I don't know what this is, can someone tell me how to find it out?Thanks.

---

### Post by The Cog on 2008-06-05
Unless you have a very good reason to do otherwise, I suggest you install the JRE that comes with Ubuntu:
```
sudo apt-get install sun-java6-jre
```

---

### Post by redfox1160 on 2008-06-05
It says I still need to install a plugin. when i try to run a online java program. can i just do it the way the website said? if so, how to i find the root password.

---

### Post by Pepperoni on 2008-06-05
> **redfox1160 said:**
> It says I still need to install a plugin. when i try to run a online java program. can i just do it the way the website said? if so, how to i find the root password.

Right there with ya.  I'm having Java issues as well.  I've tried downloading installing Java from java.com, but it didn't help.  

The root password is disabled.  You'd have to use the sudo command to elevate your priviledges and install it.

---

### Post by stchman on 2008-06-05
> **redfox1160 said:**
> I need help installing the Java Runtime Environment. I went to [http://www.java.com/en/download/help/5000010500.xml#rpm]("http://www.java.com/en/download/help/5000010500.xml#rpm") and tried to use the guide, but it said I needed the root password. I don't know what this is, can someone tell me how to find it out?Thanks.

As long as you have your account set up to administer the system just use your password.  If you are running 32 bit and want Java use this line in a terminal:

```

sudo apt-get -y install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin
```

In Ubuntu root does not have a password.

---

### Post by The Cog on 2008-06-06
OK, if ou insist. 

I installed my java JDK from a Sun download (I wanted a later version than Ubuntu provided). I did it this way:

Download the binary fron Sun's web site. Get the self-extracter, nit the RPM.

Get a root prompt by using the command **sudo -i**.

Change the the /opt directory: **cd /opt**

Execute the download: **sh whatever-it-was.bin**
and agree to the terms etc. It should create a directory under /opt.

Link to the java executable by making a symlink in /usr/local/bin:
[B]cd /usr/local/bin
ln -s /opt/jdk1.6.0_06/jre/bin/java java[/B]

Link the plugin to Firefox. cd to your fireox plugins directory and from there make a symlink to the java plugin like this:
[B]cd /wherever-firefox-is/plugins
ln -s /opt/jdk1.6.0_06/jre/plugin/i386/ns7/libjavaplugin_oji.so libjavaplugin_oji.so[/B]

---

### Post by redfox1160 on 2008-06-06
> **stchman said:**
> As long as you have your account set up to administer the system just use your password.  If you are running 32 bit and want Java use this line in a terminal:

```

sudo apt-get -y install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin
```

In Ubuntu root does not have a password.

Thanks so much, this worked.

---

