---
title: "Trouble installing a Sh file"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by Ameades on 2008-07-31
Hey guys, I'm trying to install a program called Talkhouse and it comes in .sh format and the install stalls just after the JRE launches.  I think I have a java problem but no idea how I would fix it.  

Here is a screenshot of where it stalls.  

[[IMG]http://img516.imageshack.us/img516/3509/setupproblemhe0.th.png[/IMG]](http://img516.imageshack.us/my.php?image=setupproblemhe0.png)

Thanks

---

### Post by Pro-reason on 2008-08-01
You have unfortunately left the window covering most of the error messages, so we can't see the last thing that went wrong.

In any case, this is probably something to take up with the Talkhouse people.

I'm now downloading it myself to have a look.

---

### Post by Pro-reason on 2008-08-01
When I try to run it, I get a blank window as you did.  The terminal output seems similar to yours.

Their installer looks like crap to me.  Is it too hard to make a .deb package?  Even I know how to.

Complain to them.

---

### Post by tinny on 2008-08-01
What Ubuntu version are you running?

i guess you have a defult setup when it comes to your Java setup. (E.g. You haven't touched it since installing Ubuntu)

When it comes to Java on Ubuntu you really want to use the Sun version not the default GNU Java version.

To install the Sun Java environment...
```

sudo apt-get clean
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin

```

Then to check your install
```

java -version

```

If it all worked you should see something like this
```

java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)

```

---

### Post by forger on 2008-08-01
What's the link? [www.talkhouse.com](www.talkhouse.com) ? Isn't it for mobile phones?

---

### Post by tinny on 2008-08-01
> **forger said:**
> What's the link? [www.talkhouse.com](www.talkhouse.com) ? Isn't it for mobile phones?

Doesnt look like a mobile app to me :)

[http://www.talkhouse.com/screenshots.html](http://www.talkhouse.com/screenshots.html)

---

### Post by Pro-reason on 2008-08-01
> **tinny said:**
> What Ubuntu version are you running?

i guess you have a defult setup when it comes to your Java setup. (E.g. You haven't touched it since installing Ubuntu)

When it comes to Java on Ubuntu you really want to use the Sun version not the default GNU Java version.
I for one have that already, and yet it didn't work. Try it yourself.

> **forger said:**
> What's the link? [www.talkhouse.com](www.talkhouse.com) ? Isn't it for mobile phones?
Here is the link to the software: [https://www.talkhouse.com/ThankYou.html](https://www.talkhouse.com/ThankYou.html)

It is for Windows, Macs and Linux.  I think it is a program that you install on your desktop computer in order to manage stuff on a media device that you attach.

---

### Post by tinny on 2008-08-01
> **Pro-reason said:**
> I for one have that already, and yet it didn't work. Try it yourself.

Are you saying that Sun Java 6 doesnt work correctly for you?

I write Java software for a living and use it all the time on my Ubuntu machine.

I have Ubuntu Hardy and Java 6.

If you give details of how its not working perhaps we could try and help you fix it?

---

### Post by Pro-reason on 2008-08-01
> **tinny said:**
> Are you saying that Sun Java 6 doesnt work correctly for you?
The .sh installer failed for me in the same way it failed for the original poster.

I have Sun Java 6, which works for other things.  I tried the installer as user and as root, and with and without the "xset r off" that the site recommends.

If you are sure that it works, then install it yourself!

---

### Post by tinny on 2008-08-01
> **Pro-reason said:**
> The .sh installer failed for me in the same way it failed for the original poster.

I have Sun Java 6, which works for other things.  I tried the installer as user and as root, and with and without the "xset r off" that the site recommends.

If you are sure that it works, then install it yourself!

Oh, I thought you meant that Java 6 didn't work for you in "general".

I believe you, this application doesnt work. I have a slow internet connection so I really dont want to download 80MB+ :) 

Whats the output of...
```

java -version

```

Sometimes you can have Sun Java 6 installed but it is not set as your system default Java runtime.

BTW: Have you turned off keyboard repeat?

```

xset r off

```

---

### Post by Pro-reason on 2008-08-01
```

java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)

```

---

### Post by tinny on 2008-08-01
> **Pro-reason said:**
> ```

java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)

```

Ok, so that looks all good.

Have you tried "xset r off" (I edited my last post #10).

Also, can you post back the output to the terminal. (the output that we couldnt see correctly from the OP's attached screen shot)

---

### Post by Pro-reason on 2008-08-01
> **tinny said:**
> 
Also, can you post back the output to the terminal. (the output that we couldnt see correctly from the OP's attached screen shot)

OK, I did this: ```
sh talkhouse_unix.sh 1> talkhouse.stdout 2> talkhouse.stderr
```

It dumped this to standard output:
```

Unpacking JRE ...
Preparing JRE ...
Starting Installer ...

```

... and this to standard error:

```

Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xad615767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xad6158b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xad2eb29d]
#3 ~/Desktop/talkhouse_unix.sh.14286.dir/jre/lib/i386/xawt/libmawt.so [0xad67622e]
#4 ~/Desktop/talkhouse_unix.sh.14286.dir/jre/lib/i386/xawt/libmawt.so [0xad654ed7]
#5 ~/Desktop/talkhouse_unix.sh.14286.dir/jre/lib/i386/xawt/libmawt.so [0xad655188]
#6 ~/Desktop/talkhouse_unix.sh.14286.dir/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x2f) [0xad65548f]
#7 [0xb5d5568e]
#8 [0xb5d4de9d]
#9 [0xb5d4de9d]
#10 [0xb5d4b207]
#11 ~/Desktop/talkhouse_unix.sh.14286.dir/jre/lib/i386/client/libjvm.so [0x620967d]
#12 ~/Desktop/talkhouse_unix.sh.14286.dir/jre/lib/i386/client/libjvm.so [0x63057d8]
#13 ~/Desktop/talkhouse_unix.sh.14286.dir/jre/lib/i386/client/libjvm.so [0x6209510]
#14 ~/Desktop/talkhouse_unix.sh.14286.dir/jre/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x34b) [0x625f38b]
#15 ~/Desktop/talkhouse_unix.sh.14286.dir/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb7d6696d]
#16 [0xb5d5568e]
#17 [0xb5d4dd37]
#18 [0xb5d4b207]
#19 ~/Desktop/talkhouse_unix.sh.14286.dir/jre/lib/i386/client/libjvm.so [0x620967d]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xad615767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xad61581e]
#2 /usr/lib/libX11.so.6 [0xad2ea5f8]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x26) [0xad2e1186]
#4 ~/Desktop/talkhouse_unix.sh.14286.dir/jre/lib/i386/xawt/libmawt.so [0xad654189]
#5 ~/Desktop/talkhouse_unix.sh.14286.dir/jre/lib/i386/xawt/libmawt.so [0xad6543d5]
#6 ~/Desktop/talkhouse_unix.sh.14286.dir/jre/lib/i386/xawt/libmawt.so [0xad655239]
#7 ~/Desktop/talkhouse_unix.sh.14286.dir/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x2f) [0xad65548f]
#8 [0xb5d5568e]
#9 [0xb5d4de9d]
#10 [0xb5d4de9d]
#11 [0xb5d4b207]
#12 ~/Desktop/talkhouse_unix.sh.14286.dir/jre/lib/i386/client/libjvm.so [0x620967d]
#13 ~/Desktop/talkhouse_unix.sh.14286.dir/jre/lib/i386/client/libjvm.so [0x63057d8]
#14 ~/Desktop/talkhouse_unix.sh.14286.dir/jre/lib/i386/client/libjvm.so [0x6209510]
#15 ~/Desktop/talkhouse_unix.sh.14286.dir/jre/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x34b) [0x625f38b]
#16 ~/Desktop/talkhouse_unix.sh.14286.dir/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb7d6696d]
#17 [0xb5d5568e]
#18 [0xb5d4dd37]
#19 [0xb5d4b207]

```

I've substituted "~" for my home directory.

---

### Post by tinny on 2008-08-01
Looks to me as though its bundled with its own Java runtime environment. This means your not using your systems Java 6 runtime but the bundled version.

Im getting more interested now, looks like ill have to download it after all.

---

### Post by Pro-reason on 2008-08-01
> **tinny said:**
> Looks to me as though its bundled with its own Java runtime environment. This means your not using your systems Java 6 runtime but the bundled version.


Ah yes, so it seems.

That just goes to show what terrible programmers they are.  The proper Unix way of doing this would be to make .deb or .rpm packages that depend upon an appropriate form of Java.  I already have Java on this machine, and those fools have made me download it again for no reason.  Sigh.

---

### Post by Ameades on 2008-08-01
First off thanks for your help guys, I've been asleep for the last little while which is why I haven't responded.

Sorry for the poor setup of the screenshot, I had figured that this was something simple which is usually the case when I run into problems.

I have the latest version of Sun Java and are running Hardy as well.  

Is there any other information you guys need in order to try and find a solution?

---

### Post by Ameades on 2008-08-01
I should also mention I have tried the windows version through wine and it does not work as well.

---

### Post by Pro-reason on 2008-08-01
> **Ameades said:**
> I should also mention I have tried the windows version through wine and it does not work as well.

I think you should give up on this pile of poo.

---

### Post by tinny on 2008-08-01
Just a quick thought, have you tried running the talkhouse_unix.sh file as "sudo"?

```

sudo ./talkhouse_unix.sh

```

---

### Post by Ameades on 2008-08-02
Does not work :(  Oh well, I guess I shall have to wait until another program like this comes out.  Thanks for the help though.

---

### Post by tinny on 2008-08-02
> **Ameades said:**
> Does not work :(  Oh well, I guess I shall have to wait until another program like this comes out.  Thanks for the help though.

Have you tried Amarok?

Its available in the Ubuntu repositories

---

### Post by Ameades on 2008-08-04
Does amarok have a speech retrieval feature?  I cannot seem to find it.

---

### Post by tinny on 2008-08-04
> **Ameades said:**
> Does amarok have a speech retrieval feature?  I cannot seem to find it.

No speech.

"Add /Remove Applications" > Search > amarok

---

