---
title: "Java Swing GUI not showing?"
date: 2007-05-18
forum: Programming Talk
---

### Post by fbradyirl on 2007-05-18
Hi,

I have being programming in Java for a couple of years but have just moved to Ubuntu (7.04). I am trying to launch a swing GUI I have created but the GUI doesn't show (see screenshot)

[IMG]http://meteorjsms.googlepages.com/jsms.jpg[/IMG]

I have tried to recompile using suns 1.5 JDK using Eclipse & Netbeans but the GUI still doesnt show! Anyone any ideas? I think it might be a GNOME problem. I have searched all over but can't find any fix.

PS - the GUI runs fine under Solaris, Win32, & Mac OS X

Thanks for any tips

---

### Post by DC@DR on 2007-05-18
That problem must be on your side, since my Java Swing works just fine here. Please make sure that you compiled the code and/or Eclipse running with Sun Java, not GCJ. If you're not sure what to do, just run sudo update-java-alternatives -s sun_java_version_you_installed (i.e in my case, I'd issue this command:
```

sudo update-java-alternatives -s java-1.5.0-sun

```
G'luck :-)
P/S: If this still doesnt help, you could, if possible, post your code up here, so we can test for you.

---

### Post by fbradyirl on 2007-05-18
Thanks a lot. I have tried that earlier today & as you suggested I have been compiling & running with suns JDK (1.5). I also tried 1.6 but no joy. The source code is here:

[http://meteorjsms.googlepages.com/src.zip]("http://meteorjsms.googlepages.com/src.zip")

The main method is in com.googlepages.meteorjsms.gui.MeteorJSMSGUI.java
The GUI should look something like this-
[IMG]http://uk.geocities.com/finbrady/JSMS/Features/Features_files/screen1-full.png[/IMG]

Thanks.

---

### Post by Vert on 2007-05-18
I haven't looked at the source code just yet, but make sure you don't have Compiz or Beryl running.  Some Java applications which use the Swing API (If I remember correctly) have trouble displaying.

---

### Post by fbradyirl on 2007-05-18
> **Vert said:**
> I haven't looked at the source code just yet, but make sure you don't have Compiz or Beryl running.  Some Java applications which use the Swing API (If I remember correctly) have trouble displaying.

Yes that is probably it I hadn't thought of that. I have 'Desktop Effects' enabled in preferences. Is there any workaround for this yet? Thanks.

---

### Post by srt4play on 2007-05-18
> **fbradyirl said:**
> Yes that is probably it I hadn't thought of that. I have 'Desktop Effects' enabled in preferences. Is there any workaround for this yet? Thanks.

Yes there is, check this thread:

[http://ubuntuforums.org/showthread.php?t=362821](http://ubuntuforums.org/showthread.php?t=362821)

Which shows the fix being to add:

```
export AWT_TOOLKIT="MToolkit"
```

to the end of the file /etc/profile

---

### Post by fbradyirl on 2007-05-18
> **srt4play said:**
> Yes there is, check this thread:

[http://ubuntuforums.org/showthread.php?t=362821](http://ubuntuforums.org/showthread.php?t=362821)

Which shows the fix being to add:

```
export AWT_TOOLKIT="MToolkit"
```

to the end of the file /etc/profile

Thanks a lot. I have been searching for days for this. I will try this out on Monday when I get back into work!!
Cheers.

---

