---
title: "Trendmicro, JRE Installation and FF2"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by stevezygote on 2008-07-01
My system in the last few days has been acting strangely. I am running a dual boot with Windows XP SP3 and Kubuntu split on a 60GIG HDD with a 2.2Ghz Celeron and 512MBs of RAM. It was working fine. I'm not running any virus software on the Linux partition because everyone said it's so secure. I've been accepting email on the Linux partition. On the Windows partition about a month ago I got the virumod virus (or something) and my internet browser (FF and IE7 - when I absolutely have to) and file browser were being hijacked. So I says to myself, maybe the same has happened with the Kubuntu partition. 

Hence I am attempting to run Trendmicro's free on-line scan on my Linux partition. Trendmicro wants JRE. I installed the JRE from the repository, assuming that would do it. But it hasn't. Trendmicro's site keeps prompting me for JRE. It sends me to the Java site. When I run the verifier on the Java site to determine whether my JRE is installed correctly, it tries to install the JRE, so I assume the repository install hasn't taken. So...we try it manually. 

That's where I've hit a snag. I downloaded Java's instruction and a bin file to install the JRE. When I follow there instructions, and invoke the following command....

chmod a+x jre-6u<version>-linux-i586.bin

I get a ch command not found. Can someone please help me resolve this issue? It's totally beyond me. 

I'm starting to wonder whether I have to reboot, so that's going to be my next move.

---

### Post by Dark_Stang on 2008-07-01
Linux doesn't really get viruses. Software for windows will not work on Linux. So trend's scanner is not going to work for you. If you're really paranoid you can install clamAV and it's graphical front end from your add/remove programs tool.

You probably have virtumonde on the Windows side, I'd recommend spyware doctor to remove it.

---

### Post by stevezygote on 2008-07-01
> **Dark_Stang said:**
> Linux doesn't really get viruses. Software for windows will not work on Linux. So trend's scanner is not going to work for you. If you're really paranoid you can install clamAV and it's graphical front end from your add/remove programs tool.

You probably have virtumonde on the Windows side, I'd recommend spyware doctor to remove it.

Had. I got rid of it, finally. Long story. But what I'm noticing with Kubuntu and FF is that I can clink incessantly on a link and it just won't respond until I use foul language and pound the you know what out of it. Any ideas?

---

### Post by stchman on 2008-07-01
> **stevezygote said:**
> My system in the last few days has been acting strangely. I am running a dual boot with Windows XP SP3 and Kubuntu split on a 60GIG HDD with a 2.2Ghz Celeron and 512MBs of RAM. It was working fine. I'm not running any virus software on the Linux partition because everyone said it's so secure. I've been accepting email on the Linux partition. On the Windows partition about a month ago I got the virumod virus (or something) and my internet browser (FF and IE7 - when I absolutely have to) and file browser were being hijacked. So I says to myself, maybe the same has happened with the Kubuntu partition. 

Hence I am attempting to run Trendmicro's free on-line scan on my Linux partition. Trendmicro wants JRE. I installed the JRE from the repository, assuming that would do it. But it hasn't. Trendmicro's site keeps prompting me for JRE. It sends me to the Java site. When I run the verifier on the Java site to determine whether my JRE is installed correctly, it tries to install the JRE, so I assume the repository install hasn't taken. So...we try it manually. 

That's where I've hit a snag. I downloaded Java's instruction and a bin file to install the JRE. When I follow there instructions, and invoke the following command....

chmod a+x jre-6u<version>-linux-i586.bin

I get a ch command not found. Can someone please help me resolve this issue? It's totally beyond me. 

I'm starting to wonder whether I have to reboot, so that's going to be my next move.

You don't need to run Trendmicro's free scan.  It is BS.

To install Java on 32 bit Ubuntu do this.

```
sudo apt-get -y install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin
```

For 64 bit Ubuntu install this:

```
sudo apt-get -y install icedtea-java7-jdk icedtea-java7-jre icedtea-java7-plugin
```

The SUN java will most assuredly work with the site, the openJDK may or may not.

---

### Post by stevezygote on 2008-07-02
> **stchman said:**
> You don't need to run Trendmicro's free scan.  It is BS.

To install Java on 32 bit Ubuntu do this.

```
sudo apt-get -y install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin
```



Well I've done two things since I asked and you so kindly replied. I installed ClamAV and it found four brokens which it quarantined. Then, having followed your advice about Trendmicro, I went to the java site ([www.java.com](www.java.com)) and tested to see whether my java is installed correctly. But the java site wants to install a plug in again (the jre) and firefox blocks it. It never gets installed so I don't know if my java is working. How do I check or fix this?

---

