---
title: "Updating to Java 5.0"
date: 2006-02-20
forum: Programming Talk
---

### Post by Plank117 on 2006-02-20
I'd like to use 5.0's new, funky-fresh features in Eclipse. Enlighten me, as my introductory CS course is using 5.0.

---

### Post by haocheng on 2006-02-20
SO what's the problem???

---

### Post by Plank117 on 2006-02-20
Well, how do I do it? I'm sorry about my first post - I'm usually pretty good about keeping them coherent. The problem is that in this class I have earned the nickname "The Sultan of Swing" because of my ability when it comes to coding, but I'm noob when it comes to Eclipse. Once I venture out beyond coding I'm pretty clueless. Go figure.

---

### Post by Keffin on 2006-02-20
To install java 1.5 follow this link and scroll down to "Sun Java":
[https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=AddingJavaSupport](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=AddingJavaSupport)

You'll need to follow the "Selecting the default Java version" section too.
Then fire up eclipse, and go to the Window->Preferences dialogue. Expand the "Java" branch of the tree on the left and click "Compiler", then flip "Compiler compliance level" to 5.0. Done. You can also set it on a per project basis via the Project menu.

---

### Post by Plank117 on 2006-02-20
Success! I've apparently reached new lows of idiocy, but it works now.

---

### Post by hod139 on 2006-02-20
An even easier way to get the sun 1.5 SDK is to add the [plf repositories]("http://doc.ubuntu-fr.org/doc/plf") to /etc/apt/sources.list ```

## http 100mbit/s mirror provided thanks to OVH http://ovh.com
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

``` 
then
```

sudo apt-get update

``` 
Lastly
```

sudo apt-get install sun-j2sdk1.5

```

edit:  Oops, looks like I was 5 minutes too late.

---

### Post by Plank117 on 2006-02-20
Not at all! I spoke a bit too soon. I'll try your method.

---

### Post by Plank117 on 2006-02-20
Okay, it's downloading right now. Just thought I'd mention that, when I set my default compiler in Eclipse to a v 1.5 RE in /usr/proc I can't run anything. I get a dialog box proclaiming that an exception occured while executing command line. What gives?

EDIT: This is probably the stupidest possible question, but will the SDK serve my purposes? I just want to run crap in Eclipse with the compiler compliance set to 5.0 and not have problems.

---

### Post by hod139 on 2006-02-20
[quote=Plank117]Okay, it's downloading right now. Just thought I'd mention that, when I set my default compiler in Eclipse to a v 1.5 RE in /usr/proc I can't run anything. I get a dialog box proclaiming that an exception occured while executing command line. What gives?
[/quote] Why are you editing anything in /usr/proc? To set the compliance level in Eclipse just do what Keffin said "Window->Preferences dialogue. Expand the "Java" branch of the tree on the left and click "Compiler", then flip "Compiler compliance level" to 5.0."
[quote=Plank117]
EDIT: This is probably the stupidest possible question, but will the SDK serve my purposes? I just want to run crap in Eclipse with the compiler compliance set to 5.0 and not have problems.[/quote]
Eclipse needs to find a SDK that supports the 5.0 features before it lets you set the compliance to 5.0. So yes, you need the SDK. You will have to tell Eclipse to use the new version of Java. To do this go to "Window->Preferences dialogue. Expand the "Java" branch of the tree on the left and click "Installed JREs". There you can add the new SUN JRE, which is part of the SDK.

---

### Post by Plank117 on 2006-02-21
Yeah. I figured out why I was having these bizarre problems. It was because I told Eclipse to search my entire /usr directory for a RE, and it would say it had found 32; I'd then stop it and try to use one of those, but the RE I had gotten by apt-getting was in /usr/lib, and Eclipse never found it because I kept stopping its search before it ever got out of /usr/proc. That probably made no sense whatsoever, since it's late and I'm having trouble forming coherent thoughts. Basically, I just hadn't looked around enough for a JRE that I'd already installed. Everything works fabulous now, and I even wrote my first GUIed Java program! Hooray! \\:D/

---

