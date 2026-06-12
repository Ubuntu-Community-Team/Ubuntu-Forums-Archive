---
title: "[SOLVED] How to (manually) install the latest version of Java"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by ktrnka on 2008-07-31
Not sure if this is the correct spot to post a How-To but here it goes:

This is the manual way to install java.(also not using the sudo update-alternatives --config java) 
Download the latest version of java from [http://www.java.com/en/download/index.jsp](http://www.java.com/en/download/index.jsp)

Click on "Free Java Download"

If you are on (x86) then select the (usually) second line (just below the RPM).

Then move it to /usr/lib/jvm
 	```
sudo mv jre*version-number*.bin /usr/lib/jvm
```

If the directory does not exist, then create it.
        ```
sudo mkdir jvm
```

Change directory to /usr/lib/jvm
	```
cd /usr/lib/jvm
```

Then make it executable if it isn't already.
	```
sudo chmod +x jre*version-number*.bin
```

Run the bin
	```
sudo ./jre*version-number*.bin
```

Remove the current java symlink in /etc/alternatives
	```
sudo rm /etc/alternatives/java
```

(Using version jre1.6.0_07 as an example)
Create a new symlink
	```
sudo ln -s /usr/lib/jvm/jre1.6.0_07/bin/java /etc/alternatives/java
```

Check what version of Java you're using
	```
java -verson
```

It should read something like:
java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)


"Adding Firefox 3 plugin"
If there's a java plugin in /usr/lib/firefox-3.0.1/plugins  then remove it otherwise
we will create a symlink to the new version of Java.

	```
sudo ln -s /usr/lib/jvm/jre1.6.0_07/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox-3.0.1/plugins/libjavaplugin_oji.so
```

Restart firefox and you should be running the latest version of Java!

(Please let me know if any corrections are needed)

---

### Post by daimaru on 2008-07-31
if you don't have the right java version running you might have to change it manually by typing:
```
sudo update-alternatives --config java
```

select the java version you want to use and you should be good to go. 
cheers

---

### Post by ktrnka on 2008-07-31
I ran into a problem where sudo update-alternatives --config java did not pick up the new version that had been extracted, which is why I wrote this.

Thanks though

---

### Post by daimaru on 2008-07-31
> **ktrnka said:**
> I ran into a problem where sudo update-alternatives --config java did not pick up the new version that had been extracted, which is why I wrote this.

Thanks though
sorry to hear that, am at a loss too on the subject now.

---

### Post by ktrnka on 2008-07-31
Yea but I was able to get it to work finally.

(BTW I like your avatar)

---

### Post by daimaru on 2008-07-31
> **ktrnka said:**
> Yea but I was able to get it to work finally.

(BTW I like your avatar)
Would you mind sharing how you got it to work. just in case somebody else has the same problem. I'm just saying this since I searched forums before and came across the same problem i had and then i read that the original poster solved it, but he didn't say how so i was no smarter than before:) 

So if you have time it would be great if you could post your fix, thx mate.

---

### Post by ktrnka on 2008-07-31
My Thread wasn't actually a problem, it was a how-to. I didn't know exactly where to put it. I hope one of the Admins can move it to it's proper location. The way I finally got it to work is from my Post. Those are the steps I went through to get 1.6.0_07 to install properly. Not sure what else you're asking.

---

