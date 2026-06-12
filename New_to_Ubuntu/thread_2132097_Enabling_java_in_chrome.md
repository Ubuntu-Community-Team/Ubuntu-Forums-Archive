---
title: "Enabling java in chrome"
date: 2013-04-03
forum: New to Ubuntu
---

### Post by SchrodingerCat on 2013-04-03
Hi, i need to enable Java in my Chrome browser. Unfortunately the way i found
on the java website didn t work (create a folder, then a link ). How can i fix it?
thanks

---

### Post by slickymaster on 2013-04-03
Easy to follow instructions: [How do I enable Java in a web browser on Ubuntu Linux?]("http://java.com/en/download/help/enable_browser_ubuntu.xml")

Let us know how it went.

---

### Post by SchrodingerCat on 2013-04-03
I did it but not working yet :(

---

### Post by slickymaster on 2013-04-03
Did you make sure you were in **/opt/google/chrome/plugins** directory before you made the symbolic link from the Java **libnpjp2.so** to Chrome?

Another thing, did you received any message stating ```
ln: creating symbolic link `./libnpjp2.so': File exists
```

---

### Post by SchrodingerCat on 2013-04-03
Yes i get the right directory and i also get the message you wrote..

---

### Post by slickymaster on 2013-04-03
Alright, if you got that message, that means that there was a problem with the symbolic link.

To correct this issue simply remove the previous symbolic link using the following commands, but [COLOR=#ff0000]make sure you are in the **/opt/google/chrome/plugins** directory before you issue the last command[/COLOR]:
```
sudo -s
cd /opt/google/chrome/plugins
rm -rf libnpjp2.so
```

Restart your web browser and go to [Java Tester]("http://java.com/en/download/testjava.jsp") to test if it is functioning in your web browser.

---

### Post by SchrodingerCat on 2013-04-03
done..but still not working..

---

### Post by end33thousand on 2013-04-03
are you sure you have java installed because i had a similar problem once i had to reinstall it to get it to work

---

### Post by slickymaster on 2013-04-04
> **end33thousand said:**
> are you sure you have java installed because i had a similar problem once i had to reinstall it to get it to work

The OP already has Java installed on his system: [http://ubuntuforums.org/showthread.php?t=2132079](http://ubuntuforums.org/showthread.php?t=2132079)

> **SchrodingerCat said:**
> done..but still not working..

Can you please post the output of:
```
locate libnpjp2.so
```

---

### Post by SchrodingerCat on 2013-04-04
Here it is:
/opt/google/chrome/plugins/libnpjp2.so
/usr/local/java/jdk1.7.0_12/jre/lib/amd64/libnpjp2.so
/usr/local/java/jre1.7.0_12/lib/amd64/libnpjp2.so

---

### Post by slickymaster on 2013-04-04
Alright, let's restart.

Run these at terminal, one at a time, please:
```
sudo -s
cd /opt/google/chrome/plugins/
rm -rf libnpjp2.so
ln -s /usr/local/java/jre1.7.0_12/lib/amd64/libnpjp2.so

```

Restart the browser to check if it worked.

---

