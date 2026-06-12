---
title: "Java best look and feel for Swing."
date: 2011-07-11
forum: Programming Talk
---

### Post by stchman on 2011-07-11
Hello.  I was wondering what everyone thinks is the best look and feel for a Java application.

I used to use the System look and feel, however I have really started to like the Nimbus look and feel.

UIManager.setLookAndFeel("com.sun.java.swing.plaf.nimbus.NimbusLookAndFeel");

Anyone else have any good look and feel for Swing.

---

### Post by PaulM1985 on 2011-07-11
I always use:
            UIManager.setLookAndFeel(UIManager.getSystemLookAndFeelClassName());

That way it always looks *like* native programs on the users system.

Paul

---

### Post by Simian Man on 2011-07-11
Debating the best look and feel for Swing is like debating what kind of terminal disease you'd most like to have :).  If you have to program in Java, at least use SWT.

---

### Post by stchman on 2011-07-11
> **Simian Man said:**
> Debating the best look and feel for Swing is like debating what kind of terminal disease you'd most like to have :).  If you have to program in Java, at least use SWT.

Everyone has an opinion FWIW.

---

### Post by t1497f35 on 2011-07-11
> **Simian Man said:**
> Debating the best look and feel for Swing is like debating what kind of terminal disease you'd most like to have :).  If you have to program in Java, at least use SWT.
Oh boy, SWT is deader than dead. Eclipse and Azureus use it cause back then it was the only reasonable Java toolkit, since then Swing has become a lot better, unlike SWT - Swing is native to Java, more flexible, less bugs and is hw accelerated on windows. Starting with Java 7 (to be launched this month btw!) Swing will be hw accelerated on Linux too! - through the XRender extension. Not to mention that with SWT you have to ship your app + a copy of SWT for each OS and bit resolution (32 or 64 bit) and write/keep around scripts for each platform to be able to use SWT.. it's such a headache compared to pure and built-in Swing.

As to what L&F to use - I prefer Nimbus - it's way more professional than the default one, but since a lot of apps  don't work perfectly with Nimbus (including NetBeans) it's not used in Java by default (yet). My Java apps always use Nimbus.

That said, if Oracle ships "prism" (see [this]("http://javamagic.wordpress.com/2010/10/21/whats-next-for-java-at-oracle/") and [this]("http://weblogs.java.net/blog/opinali/archive/2010/05/03/first-long-look-javafx-13-and-prism")) in a reasonable time frame it could (easily) put an end to Swing and SWT (and AWT for that matter) altogether, but imo it would be worth it. By the looks  - it's exactly what I (and many others) have been thinking about lately, and given the 2D/3D hw advancements and market share penetration in recent years - it's actually doable and worth it.

---

