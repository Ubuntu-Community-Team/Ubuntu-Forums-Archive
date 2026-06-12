---
title: "Eclipse CDT, so slow it's driving me crazy..."
date: 2007-07-05
forum: Programming Talk
---

### Post by ishaqmalik on 2007-07-05
Hi,

        a few weeks ago I had made a post here about which IDE to choose from Eclipse CDT, KDevelop, Anjuta and Code::Blocks for C/C++ development. and I had decided to go with Eclipse's CDT. However, I recently started some real programming and it's running too slow (may be on the intellisense feature). i.e. like if I enter 

```
std::
```

it would keep me stuck there for about 2 Minutes and then (after opening the intellisense suggestions) let me proceed.

My laptop is a Core 2 Duo 2.0 GHz and 1Gig RAM so hardware limitation cannot be an issue...

Can any one suggest me something here. Even if it means going to explore some other IDE. Or do I need to go back to my Window's Visual Studio. (I had shifted to open source technologies in March and I have been a huge fan of every software I found, but for me, nothing beats VC++ for C/C++ development till now. do correct me if I am wrong.)

Regards,
MI

---

### Post by {spitFire} on 2007-07-05
Try running eclipse as root, and that might solve your problem. From more details peruse through the discussion @ [http://ubuntuforums.org/showthread.php?t=281080](http://ubuntuforums.org/showthread.php?t=281080)

---

### Post by jespdj on 2007-07-06
Also, make sure you install Sun Java and that Eclipse runs on Sun Java instead of on the default GNU Java which is included with Ubuntu. GNU Java is horribly slow.

Did you install Eclipse 3.2 from the Ubuntu repository? Since a few days, Eclipse 3.3 is out, and it contains a new and improved version of CDT. Eclipse 3.3 isn't in the Ubuntu repositories as far as I know so you'll have to download and install it yourself from [http://www.eclipse.org](http://www.eclipse.org)

---

### Post by ishaqmalik on 2007-07-06
Thank you both, yes I have Eclipse 3.2 but I had installed it a few weeks ago. in the mean time I have verified both that:

- I am running Sun's Java 6
- I tried to run it through root
- I have set the Heap size to 256MB (initial) and 512MB (max) which is enough


but it's still slow... I'll sure upgrade to version 3.3 myself because I work use it extensively for Java. but I am planning to switch to Code Blocks for C/C++. Specially I like features like wxWidgets Application, and RAD UI builders in Code Blocks which are absent in Eclipse. Eclipse's CDT is immature and needs time to become a fully featured IDE for C/C++.

What do you suggest gentlemen?

---

### Post by DC@DR on 2007-07-06
A quick search shows me this: 
[http://ubuntuforums.org/showthread.php?t=332674&highlight=eclipse+java](http://ubuntuforums.org/showthread.php?t=332674&highlight=eclipse+java)
[http://ubuntuforums.org/showthread.php?t=201378&highlight=eclipse+java](http://ubuntuforums.org/showthread.php?t=201378&highlight=eclipse+java)
I'm pretty sure your problem is with Eclipse and Java setup, since I'm using Eclipse CDT, it works like a charm for me (I follow those instructions in those links above). And one more note, I'd recommend using the Eclipse SDK downloaded from [www.eclipse.org](www.eclipse.org) rather than the one in repository :-)

---

### Post by daniel of sarnia on 2007-07-06
You could also try to install netbeans, It's similar but I think the UI is a little nicer and it Definitely faster.  It also has a C/C++ plug in.

I have had the same problems with Eclipse, I have a 3.6 ghz due core with 4 gigs of ram and Eclipse chokes. There is no reason for it but the latency is so bad it's unusable. I first thought it was java, but I installed netbeans that is also written in java and it was much faster. So I don't know what's wrong with Eclipse.

---

### Post by ishaqmalik on 2007-07-07
I had already followed the second link you mentioned in response to jespdj. So, it's no use...

I am planning to download Eclipse Europa on Monday. However, this is definitely a fact that Eclipse runs quiet slow than the other IDEs.

Installing NetBeans is totally out of question since I am already used to Eclipse for Java Development and installing NetBeans would mean that I install a new IDE only for C/C++ in which case I had prefer a pure C/C++ IDE e.g. CodeBlocks.

Let's hope Eclipse 3.3's CDT is better since I come from a VC++ background and I must say VC++ is a marvelous IDE to work with. DC@DR do you know any plugins for Eclipse that could improve its intellisense...

---

### Post by sam1948 on 2008-06-23
After some digging here is what worked for me
remove these packages
java-gcj java-gcj-dev eclipse-gcj
and all the packages that starts with "eclipse"
then install sun java downloaded from their site
and finaly download eclipse from the oficial site
unzip it
it is ready,
now all u have to do is to ask google how to install cdt

i haven't checked the eclipse from the official site with the java-gcj . it might work but up here is worked for me

enjoy u pepole

---

