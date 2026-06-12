---
title: "making eclipose to use sun JVM"
date: 2007-04-26
forum: Programming Talk
---

### Post by mohtasham1983 on 2007-04-26
Hello everybody,
I have installed eclipse from the source. I have installed JVM using get-apt and tried to make eclipse to use Sun's JVM according to the wiki for edgy. But when I reached to the point where it says that i have to edit /etc/eclipse/java_home I cannot find such file. I have searched for it everywhere but still cannot find it out.

I cannot find ~/.eclipse/eclipserc either.

I really appreciate if you help me configuring this, since eclipse runs very slowly sometimes.

---

### Post by ssodhi on 2007-04-26
Hi,
I'd recommend that you install the Java SDK as I outlined in [this]("http://ubuntuforums.org/showthread.php?t=423253") thread. That is the same thing that I did when I was installing Oracle JDeveloper, and my setup has not failed as of yet. You may wish to simply refuse to provide a Java SDK to Eclipse at first, and then to manually input it via the Preferences panel. You would simply point Eclipse to the name of the folder that you installed the Java SDK to.

I am installing Eclipse now to verify that it works.

Edit: Disregard the above, I misread your question.You had a JVM issue.

```

sanjay@sanjay-desktop:~$ sudo apt-get install eclipse
...
sanjay@sanjay-desktop:~$ eclipse
searching for compatible vm...
  testing /usr/lib/jvm/java-gcj...found
sanjay@sanjay-desktop:~$

```

Eclipse runs fine for me. I did not change a single thing with regard to my JVM. Can you try and rollback the changes that you made?
Please verify the integrity of your install by using the GCJ JVM before trying to use the one provided by Sun Microsystems

---

### Post by hod139 on 2007-04-26
How did you install eclipse and java, from the repository or downloading and installing manually?  If you used the repository, [my howto for dapper]("http://ubuntuforums.org/showthread.php?t=201378") should still work.  If you did a manual install, check out [phossal's guide]("http://ubuntuforums.org/showthread.php?t=332674#1").

---

### Post by jespdj on 2007-04-26
There's a bug in the Feisty packages that causes the Eclipse package to (indirectly) depend on GNU Java: [https://answers.launchpad.net/ubuntu/+question/5383](https://answers.launchpad.net/ubuntu/+question/5383)

I uninstalled gij and gcj (GNU Java) and installed the Sun JDK 6 via the package manager, and manually downloaded Eclipse from eclipse.org.

Unfortunately there is also a bug in Eclipse 3.2.2, see this for a description and a fix: [https://eclipse.org/bugs/show_bug.cgi?id=174547](https://eclipse.org/bugs/show_bug.cgi?id=174547)

Eclipse 3.2.2 now works perfectly on my 64-bit Feisty Fawn with Sun Java 6 and I don't have the GNU Java junk on my system.

---

### Post by phossal on 2007-04-26
The important part is that the bug is 64-bit specific. For most Ubuntu users - even those running 64-bit platforms (as I do) - 32bit Ubuntu/eclipse is still the best path. There isn't any 64bit plugin support.

---

### Post by jespdj on 2007-04-27
> **phossal said:**
> The important part is that the bug is 64-bit specific. For most Ubuntu users - even those running 64-bit platforms (as I do) - 32bit Ubuntu/eclipse is still the best path. There isn't any 64bit plugin support.
Which bug, do you mean the Eclipse bug? It's very easy to fix by installing the patch that's in the bug report that I provided a link to.

Eclipse runs fine on 64-bit Ubuntu. You don't need 32-bit Eclipse.

What do you mean with "there isn't any 64-bit plugin support"? Indeed, there is no 64-bit Java plugin from Sun for browsers, which you need when you want to run applets. But this does not have anything to do with whether you are using 64-bit or 32-bit Eclipse.

---

### Post by phossal on 2007-04-27
> **jespdj said:**
> Which bug, do you mean the Eclipse bug? It's very easy to fix by installing the patch that's in the bug report that I provided a link to.

Eclipse runs fine on 64-bit Ubuntu. You don't need 32-bit Eclipse.

What do you mean with "there isn't any 64-bit plugin support"? Indeed, there is no 64-bit Java plugin from Sun for browsers, which you need when you want to run applets. But this does not have anything to do with whether you are using 64-bit or 32-bit Eclipse.

Right, I mean the eclipse bug. And, yes, I know 64bit eclipse "runs fine" on Ubuntu, assuming you patch the *bug*, and don't intend to use it for browser support. I don't consider that fine, personally. As for matching the versions of eclipse and the JDK, I have always noticed significant improvement when I do so.

---

### Post by jespdj on 2007-04-27
> **phossal said:**
> Right, I mean the eclipse bug. And, yes, I know 64bit eclipse "runs fine" on Ubuntu, assuming you patch the *bug*, and don't intend to use it for browser support. I don't consider that fine, personally. As for matching the versions of eclipse and the JDK, I have always noticed significant improvement when I do so.
I am personally not very interested in programming applets - I'm using Java for server side development and for desktop apps.

The problem is that Sun doesn't see the need to develop a 64-bit Java browser plugin, they think that 64-bit is only interesting for servers... :(

The good news is that Sun's Java is going to be open source very soon (see the [OpenJDK project](https://jdk.dev.java.net/)) so I hope that when the source is completely available someone will be able to compile a 64-bit browser plugin. We'll see... :)

---

### Post by phossal on 2007-04-27
I don't enjoy programming applets either. I mainly use Java for desktop applications, too. I prefer 32bit Java for that. I brought up the plugin because a lot of Ubuntu users want to *use* applets without installing multiple JDK's.

---

### Post by jespdj on 2007-04-28
Ok, so why do you prefer 32-bit Java for desktop apps :confused: Note that there is no difference at all in your compiled class files between the 32-bit and 64-bit version - the Java byte code will be exactly the same. The only difference between the 32-bit and 64-bit version is the native code in the JVM itself.

---

