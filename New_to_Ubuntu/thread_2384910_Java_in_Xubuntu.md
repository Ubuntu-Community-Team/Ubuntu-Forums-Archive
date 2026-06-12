---
title: "Java in Xubuntu"
date: 2018-02-14
forum: New to Ubuntu
---

### Post by awachens on 2018-02-14
Good morning i need some help to understand how to install Java in Xubuntu... I download .tar.gz... I want to install with this way. I decompress the archive in /usr/java with root permission.
But id don't know what i have to do now. Have I now installed Java ? How can i use or configure ?
I want to use with IDE Eclipse. Some help?

Thank you !
[COLOR=#212121][FONT=arial]I do not know what I have to do[/FONT][/COLOR][COLOR=#212121][FONT=arial]I do not know what I have to do[/FONT][/COLOR][COLOR=#212121][FONT=arial]I do not know what I have to do[/FONT][/COLOR][COLOR=#212121][FONT=arial]I do not know what I have to do[/FONT][/COLOR][COLOR=#212121][FONT=arial]I do not know what I have to do[/FONT][/COLOR][COLOR=#212121][FONT=arial]I do not know what I have to do[/FONT][/COLOR][COLOR=#212121][FONT=arial]I do not know what I have to do[/FONT][/COLOR]

---

### Post by augussee on 2018-02-14
Hi! ):P

There is always an easy way to install Java on Xubuntu using apt-get.

Assuming that you have Xubuntu 16.04 or latest version, IDE Eclipse requires Java 8, so you can install it using apt-get like this:

```
sudo apt-get install default-jre
```

Now, if you are on Xubuntu 14.04 or you want the official Oracle Java, you can add a PPA to install Java 8 easily:

```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
```

To install Java 8 use:

```
sudo apt-get install oracle-java8-installer
```

Also, to install Java 9 use:

```
sudo apt-get install oracle-java9-installer
```

You can learn more about this commands in this post: [https://thelinuxcode.com/install-java-apt-get-ubuntu-16-04/](https://thelinuxcode.com/install-java-apt-get-ubuntu-16-04/)

---

