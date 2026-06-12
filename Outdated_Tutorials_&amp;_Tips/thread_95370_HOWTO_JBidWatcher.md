---
title: "HOWTO: JBidWatcher"
date: 2005-11-26
forum: Outdated Tutorials &amp; Tips
---

### Post by foxy123 on 2005-11-26
JBidWatcher is a nice eBay tool for searching, bidding and snipping on eBay, which I came across after some frustration with bidwatcher, availabe from repositories. As the author describes it:
> A Java-based application allowing you to monitor auctions you're not part of, submit bids, snipe (bid at the last moment), and otherwise track your auction-site experience. It includes adult-auction management, MANY currencies (yen, pound, dollar (US, Canada, Australian, and New Taiwanese), Swiss Francs, and euro, presently), drag-and-drop of auction URLs, a unique and powerful 'multisniping' feature, a relatively nice UI, and is known to work cleanly under Linux, Windows, Solaris, and MacOSX from the same binary.

**Official Website:** [http://www.jbidwatcher.com/](http://www.jbidwatcher.com/)

Requirements: you have to have Sun version of Java.

1. Download the latest version  [here]("http://www.jbidwatcher.com/download/JBidWatcher-0.9.9.jar")

2. You may have it anywhere. However I crated a directory /usr/local/share/java and copied it there. It's up to you though.

```
sudo mkdir /usr/local/share/java
sudo cp JBidWatcher-0.9.9.jar /usr/local/share/java
```

3. Make a bash script to run it.
```
sudo gedit /usr/local/bin/jbidwatcher
```

and paste the following:
```
#!/bin/sh
java -jar /usr/local/share/java/JBidWatcher-0.9.9.jar
```

Make the script executable:
```
sudo chmod +x /usr/local/bin/jbidwatcher
```

You are almost set. Just run from command line
```
jbidwatcher
``` and enter your ebay user name and password.

4. You can make a .desktop file for JBidWatcher to have it in your menu:

```
sudo gedit /usr/local/share/applications/jbidwatcher.desktop
```
and insert the following text:
```
[Desktop Entry]
Encoding=UTF-8
Name=JBidWatcher
Comment=Ebay watching and bidding tool
Exec=jbidwatcher
Icon=jbidwatch.xpm
Terminal=false
Type=Application
Categories=Utility
GenericName=JBidWatcher

```
I use xfce and I've got menu entry in menu as soon as I created it. I am not sure if it will work in Gnome without activating it in some way.

Overall it is up to you where to store jar file. The author suggests your home dir, but I like to keep it clean and tidy.

The site has a Quick Start Guide, available [here]("http://www.jbidwatcher.com/help/jb_quickstart.shtml")

It is my first HOWTO here, so let me know if anything is wrong or unclear. Enjoy your bidding!

---

### Post by shane.reid on 2006-05-19
This was very helpful.. thank you.  Excellent program and very perfect How-to

---

### Post by TomH on 2006-06-10
I get the following errors any help :confused: 


tom@tomnix:~/Desktop$ sudo jbidwatcher
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   at java.awt.Font.tk(libgcj.so.7)
   at java.awt.Font.getPeerFromToolkit(libgcj.so.7)
   at java.awt.Font.<init>(libgcj.so.7)
   at javax.swing.plaf.FontUIResource.<init>(libgcj.so.7)
   at javax.swing.plaf.metal.DefaultMetalTheme.<clinit>(libgcj.so.7)
   at java.lang.Class.initializeClass(libgcj.so.7)
   at javax.swing.plaf.metal.MetalLookAndFeel.createDefaultTheme(libgcj.so.7)
   at javax.swing.plaf.metal.MetalLookAndFeel.<init>(libgcj.so.7)
   at javax.swing.UIManager.<clinit>(libgcj.so.7)
   at java.lang.Class.initializeClass(libgcj.so.7)
   at JBidWatch.main(JBidWatch.java:594)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit
   at java.lang.Class.forName(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   ...11 more

---

### Post by TomH on 2006-06-10
Curiously though if i right click on it and choose, open with Sun Java 5.0 Runtime it works ?

---

### Post by foxy123 on 2006-06-10
[QUOTE=TomH]Curiously though if i right click on it and choose, open with Sun Java 5.0 Runtime it works ?[/QUOTE]
why would you like to run it with sudo?

---

### Post by TomH on 2006-06-11
sorry just put sudo in a a trial, if i just run jbidwatcher it gives the same errors. 

Have managed to fit it now anyways by telling ubuntu which java its using :) 

Tom

---

### Post by stani on 2006-06-30
I installed sun java, but bidwatcher refuses to run:
> 
Exception in thread "main" java.lang.ExceptionInInitializerError
   at java.lang.Class.initializeClass(libgcj.so.7)
   at FilterManager$AuctionListHolder.<init>(FilterManager.java:67)
   at FilterManager.loadFilters(FilterManager.java:89)
   at JBidWatch.<init>(JBidWatch.java:1021)
   at JBidWatch.main(JBidWatch.java:636)
Caused by: java.lang.IllegalArgumentException: classname: java.io.InputStream;
   at java.awt.datatransfer.DataFlavor.getRepresentationClassFromMime(libgcj.so.7)
   at java.awt.datatransfer.DataFlavor.<init>(libgcj.so.7)
   at java.awt.datatransfer.DataFlavor.<init>(libgcj.so.7)
   at JDropListener.getDataFlavor(JDropListener.java:72)
   at JDropListener.setupFlavors(JDropListener.java:98)
   at JDropListener.<init>(JDropListener.java:60)
   at JBidMouse.<init>(JBidMouse.java:74)
   at AuctionsUIModel.<clinit>(AuctionsUIModel.java:48)
   at java.lang.Class.initializeClass(libgcj.so.7)
   ...4 more

Any idea what is causing this?

---

### Post by foxy123 on 2006-06-30
[QUOTE=stani]I installed sun java, but bidwatcher refuses to run:

Any idea what is causing this?[/QUOTE]
it looks like Jbidwatcher is trying to use a open-source Java alternative rather then Sun's Java (see a post above). There is a command something like 'java alternative' or else, I do not remember, frankly speaking. It allows you to choose what Java to use. Try to search the forum for that. Sorry that I cannot be more of help. 

BTW, if you find the solution, could you post it here as well, so other people could use it in future?

---

### Post by stani on 2006-06-30
Thanks!

The code is:
>  sudo update-alternatives --config java

---

### Post by Endolith on 2008-01-02
In GNOME, just add a menu entry for "java -jar /home/username/Programs/jBidWatcher".  Easy.

(Though double-clicking a .jar file should ideally launch the program without any additional effort, and GNOME popping up a balloon notification asking you if you'd like a launcher to be automatically created would be even easier.)  ;-)

---

### Post by MrGrey1 on 2009-09-13
> **Endolith said:**
> In GNOME, just add a menu entry for "java -jar /home/username/Programs/jBidWatcher".  Easy.

(Though double-clicking a .jar file should ideally launch the program without any additional effort, and GNOME popping up a balloon notification asking you if you'd like a launcher to be automatically created would be even easier.)  ;-)

This worked very well, thanks.

Found the pretty icon here:

[http://g.imagehost.org/download/0415/jb.svg](http://g.imagehost.org/download/0415/jb.svg)

place into: 

/usr/share/icons/hicolor/scalable/apps/

And don't forget to change the ownership of the jb.svg file:

chown root:root /usr/share/icons/hicolor/scalable/apps/jb.svg

---

### Post by amillionsheep on 2010-01-25
When is the last time this was updated? Do these intructions still work? What's the best way to get this program?

---

### Post by divers3 on 2011-06-27
I haven't been having luck installing on anything from 9.10 on up; luckily I have prior installs that I've been able to update, though I still have to launch it from konsole.
This application really needs the benefit of a "no-brainer" type installer for us poor geeklings with memory problems...:(

:popcorn:

On another note; the most recent install attempt on a 10.x machine resulted in a failed sun java install that really tossed a wrench into things.
The dang "_OK_" input on the release acknowledgement was non-responsive, resulting in opening a real can of worms.:mad:

---

