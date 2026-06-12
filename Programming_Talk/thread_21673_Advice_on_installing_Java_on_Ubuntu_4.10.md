---
title: "Advice on installing Java on Ubuntu 4.10"
date: 2005-03-23
forum: Programming Talk
---

### Post by Ron W on 2005-03-23
I'm looking for advice on installing Java on Ubuntu 4.10 so that I can start getting some experience with Java.

I have decided to go for Sun's Java 5 SDK and Eclipse 3.1M5a.

I've tried looking through the forums and am getting very confused as some people say that Sun's Java 5 and Eclipse are easy to install whereas others are having problems. As I am new to Linux (having only used Windows before) I don't understand some of the terminally used and this will be my first attempt at installing programmes to Ubuntu, so I'm looking for clear instructions on how to go about installing these two.

Thanks

Ron

---

### Post by kirk on 2005-03-23
For Java, have a look here: [http://www.ubuntuguide.org/#jre](http://www.ubuntuguide.org/#jre) (should be the same, just that you download the SDK, not the JRE)
Regarding Eclipse this should be the correct download: [Milestone Build: 3.1M5a Linux (x86/GTK 2)](http://www.eclipse.org/downloads/download.php?file=/eclipse/downloads/drops/S-3.1M5a-200502191500/eclipse-SDK-3.1M5a-linux-gtk.tar.gz)
I guess there will be an INSTALL file included containing all the necessary instructions. Otherwise have a look at the [Eclipse FAQ](http://www.eclipse.org/eclipse/faq/eclipse-faq.html)

---

### Post by bonifacio on 2005-03-23
AFAIK, there is no install file for Eclipse.  The binary that you'll get from their download site should be extracted from your $HOME dir (less painful without permission issues to deal with).

The SDK go ahead and follow the ubuntuguide.  Be careful with the variation on names and versions.

---

### Post by defkewl on 2005-03-25
Where did you downloaded the JDK from? Get the ones from java.sun.com
Download the .bin ones

And run it from your shell:
$ ./the_jdk_file.bin

---

### Post by sri7777 on 2006-07-29
I want to thank all you guys to get me going on Eclipse development. Here were my steps:
1. Followed defkewl's advise on downloading Linux jdk installation (*.bin) from Sun's java site. 
2. Run the .bin file (had to prefix it with sudo to get the right permissions).
3. Downloaded Eclipse 3.2 and extracted it (no installation here). Thanks bonifacio!
4. Forced eclipse to use the newly installed Sun's JVM by running the command:
eclipse -vm /path/to/jdk-install-dir*/bin/java*. Note the -vm option requires the complete (absolute) path for java executable. You may also add the -vm to eclipse.ini file.

cheers,
Sri

---

### Post by agger on 2006-07-30
I'm glad it worked for you.

If you're new to Linux and if it's at all possible, you might want to consider switching to Ubuntu 6.06 instead:

In 6.06, you can download eclipse directly from Synaptic if you enable the universe, multiverse and commercial repositories. That way, you wouldn't have to download things directly from Eclipse.org.

Also, I believe Ubuntu 4.10 is no longer serviced with security updates, whereas 6.06 will get them for the next three years.

Just my two cents :-)

---

