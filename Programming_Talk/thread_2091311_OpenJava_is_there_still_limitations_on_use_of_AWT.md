---
title: "OpenJava is there still limitations on use of AWT ?"
date: 2012-12-04
forum: Programming Talk
---

### Post by jaho22 on 2012-12-04
I remember someone told a well ago, that there is limitations what AWT classes there is freely in use on OpenJDK, like bilinear and cubic images and some other AWT classes ?

Is this still so, or is the entire OpenJDK now at today allready an open source class pack, and ok to use to every one who likes it ?

---

### Post by slickymaster on 2012-12-05
Are you specifically refering to AWT versus Swing? If that's the case in my point of view, Swing has much richer controls than AWT. 
It's 100% java and do not depend on the Peer Classes (each AWT component has a peer class, representing the native component), hence light weight.
You can use the Look and Feel using swing, icons and borders can be used for almost all components, it provides inbuilt double buffering.
Swing components follow the MVC paradigm and provides Tree and Table components which are not avaliable in AWT.

---

### Post by Jason80513 on 2012-12-05
OpenJDK 6 and OpenJDK 7 are nearly identical to Sun Java 6 and 7, down to the last detail. And OpenJDK is fully open-sourced, and has been for a few years.  The only API difference I have been able to find (that affected my own code) is in the browser plugin. The way Sun documents you should talk to the browser DOM uses a Sun-specific API, and it was not donated for some reason. So OpenJDK is a very, very complete implementation of Java SE.

The previous poster was correct. Don't use AWT. Swing is somewhat better, but can result in some "interesting" LAF issues on Linux systems, where Swing can't pick up the skinning of the desktop. The best cross-platform GUI library for Java I know of is SWT. SWT uses native OS widgets and supports integration with Swing and LWJGL. 

There is also a Gnome-specific Java library that looks promising, but I have not worked with it.

---

