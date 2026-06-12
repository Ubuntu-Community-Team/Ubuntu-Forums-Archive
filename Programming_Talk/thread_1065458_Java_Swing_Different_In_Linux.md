---
title: "Java Swing Different In Linux?"
date: 2009-02-09
forum: Programming Talk
---

### Post by konqueror7 on 2009-02-09
this what i got, i have a java project shared between xp and ubuntu, i'm using netbeans 6.5 as my default ide creating both the design and code of my application.

the problem is, i noticed that some of my frame renders differently compared in xp, though they came from the same template that i made in netbeans. now i'm using netbeans inside vbox just to fix it again. 

is it a bug? as far as i know that java is a cross-platform environment, and also that xp and ubuntu (gnome) got different window managers (so i expect some minor alterations/rendering of the frames), but they came from the same template, only one of them is rendered incorrectly.

can you give me an opinion or details about this issue?

---

### Post by Imaginationac on 2009-02-10
If you're using OpenJDK (which is the one Ubuntu has by default), this is where your problem most likely lies.

You can confirm this by installing the Sun JDK (either from the repository, or from the Sun website). You'll have to either change the preferred JDK in the netbeans.conf file, or pass the directory path as runtime argument.

This was the case for me. For the longest time, I couldn't figure out why the editor in NetBeans did odd spacing for no apparent reason.

---

### Post by jespdj on 2009-02-10
Also, which Swing look-and-feel are you using?

If you use the native look-and-feel, then ofcourse things are going to look different (because Swing will in that case make everything look like the native GUI on the platform that you're running your program on).

Also, what text looks like depends on what fonts you have installed on your system.

---

### Post by konqueror7 on 2009-02-10
thanks for the response...

by the way i'm using the one from the restricted extras, so its the standard sun jdk, right?

also about the look-and-feel, yes it is set to native, but the difference is that it there are two windows that are exactly the same, but only one renders differently...

maybe my version of jdk has a problem or bug,,,here my jdk version ```
java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Client VM (build 10.0-b23, mixed mode, sharing)

```

---

### Post by jespdj on 2009-02-10
It looks like you are using the standard Sun JDK.

Can you attach a screenshot of how it looks on Windows and on Linux? And as I said, it's to be expected that it looks different if you use the native look-and-feel.

---

### Post by Zugzwang on 2009-02-10
Ok, so you are using the Sun JDK, but are you also using the Sun JRE?

```

sudo update-alternatives --config java

```

---

### Post by konqueror7 on 2009-02-10
yes, my jre is still from sun...

and also about the screenshot, i cannot release it because its a project for a local corporation here, and it is confidential as said in our contract...

yes, i expected it to look different, but then one frame looks the same (all the margins an spacing) as in winxp...

but anyway, thanks for all the help and suggestions, i'll just be sticking to using vbox in my dev't since the client's os is windows...

i have a dual-boot winxp, but i try to refrain from using it, i am trying to migrate to full linux usage...:P (only some games of mine gives me the reason to login to xp)

---

### Post by Zugzwang on 2009-02-10
Note that if it is really a problem that the frame renders a little bit differently, then you are doing something wrong, i.e. you don't use the Layouts correctly.

My general advice (especially in Netbeans) is to use GridBadLayouts whenever possible. In fact, there was never a necessity for me to use something else. You can have sub-layouts by adding a panel in which you add components again, etc. Never ever use the NullLayout except for first screenshots for the customer to give them a little impression on how it will roughly look like. Then by customizing the GridBagLayouts correctly, you get nice layouts on every platform. Finally, for cases in which this is necessary, you tell Netbeans to write resize() code and choose some safe values (i.e. a little bit larger than actually needed).

---

### Post by konqueror7 on 2009-02-10
thanks for the tip...though i usually use the GridLayout and the FlowLayout...but anyway, thanks again to all of you...

---

