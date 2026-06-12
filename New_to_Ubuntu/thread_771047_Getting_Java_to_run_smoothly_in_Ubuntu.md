---
title: "Getting Java to run smoothly in Ubuntu"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by SPsPrincess on 2008-04-27
My husband just installed the newest version of Ubuntu(version 8.04lts), and I am trying to install Java so that I can play the games on pogo.com  What is the easiest way to install and run Java.
Thanks for all your help.
SPsPrincess:

---

### Post by riven0 on 2008-04-27
You can do it through Add/Remove, but I think it's easier through the terminal. So fire up the terminal, (Applications > Accessories > Terminal), and copy and paste this command:

**sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin**

---

### Post by SPsPrincess on 2008-04-27
It says that it is already the newest version, and I am trying to load pogo.com in the firefox 2 browser.  When I try to load it it tells me that the plug in is missing(it does the same in opera) and the instructions that they give me are hard for me to follow.  I am fairly new to Ubuntu and I think that I need step by step instructions in how to load it.  Is there another browser that already has Java installed so that I can skip this step.  My husband had it working before he installed the newest version of Ubuntu.  Thanks for your help.
SPsPrincess:)

---

### Post by rockerphil on 2008-04-27
here's what i'd do. open up your terminal and like said before run this.

sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin

then restart your browser. that should do the trick. if that doesn't work open up your update manager and see if anything needs updating
oh, afterwards try running this

sudo apt-get update

along with 

sudo apt-get autoremove

---

### Post by riven0 on 2008-04-27
Good suggestion to restart the browser. I forgot about that. If for some reason it still doesn't work, try download Java manually and re-installing it through the terminal. I've posted instructions below. Copy and paste commands one by one:

Download the java:

wget [http://javadl.sun.com/webapps/download/AutoDL?BundleId=18705](http://javadl.sun.com/webapps/download/AutoDL?BundleId=18705)

Set permissions:

sudo chmod a+x jre-6u5-linux-i586.bin

Start installation:

./jre-6u5-linux-i586.bin

Follow the instructions. Hopefully, it'll work.

---

### Post by kelean on 2008-04-27
I have just set up java on two machines today.  I am running 8.04 and firefox 3b5.  I have it working very well.  I am able to play pogo and yahoo games.  If you had java installed and your hubby did an upgrade it might have been broken.  I would start synaptic and remove the installed java.  Then I would install sun-java6-jre, sun-java6-plugin, and sun-java6-fonts.  After install make sure you restart firefox and you should be good to go.

Kelean.

---

### Post by ChompTheMan on 2008-04-30
Open up your file manager and go to */usr/lib/firefox/plugins/* and check if *libjavaplugin_ijo.so* is there.  If it isn't, then you need to open up your terminal and type:

```
cd /usr/lib/firefox/plugins/

sudo ln -s /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_ijo.so
```

Now restart Firefox and Java should work.  Hope this helped.

---

