---
title: "can't install java"
date: 2015-08-24
forum: New to Ubuntu
---

### Post by Edric_Megan on 2015-08-24
I just started using linux ubuntu 14.04 a few days ago and now I'm trying to install the essential stuff. one of them being java, I checked the website, downloaded the suitable file for linux 64bit, and can't seem to understand the instruction, ( please understand I'm still a noob at this)

I'm referring to this instruction : [https://java.com/en/download/help/linux_x64_install.xm](https://java.com/en/download/help/linux_x64_install.xm)

whenever I inserted the directory path through the terminal, it would say that there is no such file or directory

---

### Post by Alex_Kittenz on 2015-08-24
Hi,

You can install Java from the Ubuntu Software Center, it is called OpenJDK. It is of course, unless you explicitly need to use Java provided by the Orace Corproation, then you may install it from a guide located here ([https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java))

---

### Post by Edric_Megan on 2015-08-24
well this is embarassing, I've downloaded both the open JDK runtime 6 and 7, but I don't know how to install them

tried to tinker with the sudo apt-get command, but can't get it to work

---

### Post by Alex_Kittenz on 2015-08-24
Try this command

```
sudo apt-get install openjdk-7-jre 
```

This should install OpenJDK java runtime environment.

---

### Post by slickymaster on 2015-08-24
Why don't you do it the easiest and comfortable way. The WebUpd8 Oracle Java PPA is a script that automatically downloads and install Oracle Java 8. Everything is done automatically so you'll get updates through the update manager for JDK8 which includes JRE8 and the Java browser plugin. All you have to do is to run the followings commands in a terminal window```

sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
```
And you're good to go.

---

### Post by Edric_Megan on 2015-08-25
I've entered the commands and it was installed just fine, but when I open some sites, a heads up display would come up and say that:  java (TM) is required to display some elements on this page

---

### Post by slickymaster on 2015-08-25
What browser are you using?

---

### Post by Edric_Megan on 2015-08-25
firefox and chromium

---

### Post by monkeybrain20122 on 2015-08-25
You need to install the java web plugin. Search for icedtea-plugin in the software centre and install.

java is blocked by default on Firefox, you need to click allow for it to work.


P.S. For future use install the synpatic packages manager and it will be so much easier to search for and install packages (basically to replace the software centre) I don't like to give command line instructions to install packages like sudo apt-get install blah blah because it is a mystery to new users how does one know the exact name of the packages. But I will do it once here. :)
```
sudo apt-get install synaptic
``` Now you can search for java and try to locate the web plugin, you should find icedtea-plugin.

---

### Post by monkeybrain20122 on 2015-08-25
BTW, unless you have some applications (mostly Oracle apps) that explicitly require Oracle java I suggest you just use OpenJDK from the repository (and if needed can add ppa for OpenJdk8) I see no need or advantage of using Oracle Java otherwise.

---

### Post by Edric_Megan on 2015-08-25
> **monkeybrain20122 said:**
> You need to install the java web plugin. Search for icedtea-plugin in the software centre and install.

java is blocked by default on Firefox, you need to click allow for it to work.


P.S. For future use install the synpatic packages manager and it will make it so much easier to search and install packages (basically to replace the software centre) I don't like to give command line instructions to install packages like sudo apt-get install blah blah because it is a mystery to new users how does one know the exact name of the packages. But I will do it once here. :)
```
sudo apt-get install synaptic
``` Now you can search for java and try to locate the web plugin, you should find icedtea-plugin.

yeah I already allowed java to work on firefox, but the yellow pop ups saying it requires java are still there

anyway I'll give synaptic a try

---

### Post by monkeybrain20122 on 2015-08-25
> **Edric_Megan said:**
> yeah I already allowed java to work on firefox, but the yellow pop ups saying it requires java are still there

anyway I'll give synaptic a try

What site is that?

---

### Post by Edric_Megan on 2015-08-26
thanks for the replies guys

seems to be working now

---

