---
title: "Why does SWT exist anymore?"
date: 2007-03-05
forum: Programming Talk
---

### Post by laxmanb on 2007-03-05
Really, why does SWT exist anymore?? IBM came up with SWT because Swing didn't provide a native look and feel, but since Java 6, the native look and feel of Swing apps is a lot better than SWT apps... Should IBM just port Eclipse to Swing??

---

### Post by hod139 on 2007-03-05
Why does cobol still exist?  SWT will always be around now.  I doubt IBM will spend any effort changing the GUI for eclipse, but who knows what their plans are.

---

### Post by laxmanb on 2007-03-05
IBM should do that,,, It would be better if IBM puts energy into Swing rather than SWT... SWT has never exceeded 3-4% of all desktop UI apps, and is only marginally better than AWT in usage... Isn't it better that IBM's work goes into Swing, which is the de facto standard??

---

### Post by pmasiar on 2007-03-05
> **laxmanb said:**
> IBM should do that,,, It would be better if IBM puts energy into Swing rather than SWT... SWT has never exceeded 3-4% of all desktop UI apps, and is only marginally better than AWT in usage... Isn't it better that IBM's work goes into Swing, which is the de facto standard??

Better for whom? If IBM wanted Sun to join Eclipse project, they would pick some other name, don't you think? :-)

For companies, creating incompatibilities is a way to keep customers in created lock-in. Microsoft is creating  incompatible nonstandard features in IE, so users of other, standard compliant browsers(like Opera or Firefox) will have bad experience on websites optimized for IE bugs. Java could  used some GNU libraries under LGPL - Sun wanted to create platform competing with Window (in mobile devices and such), so Sun designed all this incompatible platform with different tools for everything not to make sharing with Unix/Linux/Windows easier - just the opposite, to prevent java users to switch to Windows.  But they failed, and Linux is energing as future mobile platform. Slowly of course. If you supply free products, you don't have millions to pay for marketing hype :-)

Companies are in business of *making money for stockholders*. If they have to solve customer's problems to make them fork cash, they will do it. If they can make a customer to pay up by other means - like MS uses MS Office upgrade treadmill - why would they bother to solve customer's problems? Do you know anyone who *needs* new features of old office suite (or for that matter, who at least knows and uses them)? And yet everobody upgrades to new version, with even more unused features - because everybody else upgraded. Companies do not stop lemmings - they will charge them for transportation :-)

The only software genuinely concerned about needs of users is free software. Free software developer gains nothing from technology lock-in, just the opposite - she will strand herself on incompatible island. That's why we have free documentation -  writing FAQ and sharing knowledge gains you good karma, siloing knowledge and non-sharing makes your project pariah and someone else's project will be used as alternative. 

IMHO, IANAL, YMMV.

---

### Post by MadMan2k on 2007-03-05
> **laxmanb said:**
>  the native look and feel of Swing apps is a lot better than SWT apps
no, it is NOT

---

### Post by laxmanb on 2007-03-05
Have you had a look at Netbeans with Java 6(perhaps even Java 5)?? IMHO it is more native looking than Eclipse...

---

### Post by MadMan2k on 2007-03-05
> **laxmanb said:**
> Have you had a look at Netbeans with Java 6(perhaps even Java 5)?? IMHO it is more native looking than Eclipse...
I've just written a small sum-up about that:
[http://www.madman2k.net/article/71#part5](http://www.madman2k.net/article/71#part5)

perhaps you got your impression because the netbeans icons look more like the other desktop icons in comparison with eclipse.

---

### Post by fabian.vogler on 2007-03-05
> **MadMan2k said:**
> no, it is NOT

Yeah I also think so ... we've seen an pretty good improvement with Java 6 but Swing still isn't there where it IMHO should be. I'm a big fan of SWT and would like to see Swing providing the same feeling - but Java 6 isn't yet perfect.

btw: [http://weblogs.java.net/blog/campbell/archive/2007/02/swing_and_gtk_w_1.html](http://weblogs.java.net/blog/campbell/archive/2007/02/swing_and_gtk_w_1.html)

---

### Post by G Morgan on 2007-03-06
SWT uses GTK on Linux (or usually does so). How can you get more native looking than native. Even if Swing does manage to look more like GTK than GTK you can even use Swing with SWT.

---

