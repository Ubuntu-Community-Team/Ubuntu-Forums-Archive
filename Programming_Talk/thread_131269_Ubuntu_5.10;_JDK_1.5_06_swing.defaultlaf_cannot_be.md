---
title: "Ubuntu 5.10; JDK 1.5_06: swing.defaultlaf cannot be changed?"
date: 2006-02-16
forum: Programming Talk
---

### Post by Poldi on 2006-02-16
hi, all.

since JRE/JDK 1.5 the default LnF on Linux Java installations is the Gtk-LnF. as of 1.5 there are not many Gtk-engines supported by the LnF beyond Pixmap so the result is quite ugly on most systems. I am aware that this will change with 1.6.

now my problem is that I could normally adjust this by specifying swing.defaultlnf in swing.properties (in $JRE7lib) or by passing the same parameter to my java binary on application start.

this does not work in Ubuntu 5.10. no matter what I try (swing.defaullnf=javax.swing.plaf.metal.MetalLookAndFeel or any of the JGoodies Looks LnFs [yes, they are in $classpath]) it still defaults to Gtk.

what makes this worse is that I develop Swing applications in Netbeans 5.0 and while Netbeans itself starts with Metal (programatically set by NetBeans), the developed applications that are started from Netbeans again follew the seemingly unchangable default: Gtk. and they break with any modern Gtk-Theme-engine. when I say break, I mean: they cannot be started from within NetBenas at all, as opposed to defaulting to the simple-Theme like Swing-apps do that I start from the desktop.

I have no other Linux distributions to test right now. can anybody confirm unchangable default Lnf==GtkLookAndFeel on Linux 2.6 with JDK 1.5.0_06? or does anybody know how to change this in a Ubuntu/Debian distribution other that with swing.properties?

I installed the JDK with
fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin
sudo dpkg -i sun-j2re1.5_1.5.0+update06_i386.deb

in /usr/lib/

the problem is reproducable on different machines with fresh installs.

suggestions?
kind regards,
Carsten

---

### Post by pertti on 2006-02-16
I'm using Sun's JDK 1.5.0_06 on Breezy, and Java applications default to Metal LaF for me. I've tried running apps from the command line with the -Dswing.defaultlaf property, setting the GTK+ LaF, and it works. NetBeans also launches my apps with Metal, but I haven't tried to change this with -Dswing.defaultlaf: I can't find where to put the command line options :*).

I've always used UIManager to set the LaF programmatically, and to change it at runtime.

---

### Post by Poldi on 2006-02-16
how have you installed the JDK on Ubuntu? perhabs the 'make-jpkg' machanism does something worng - my dpkg-knowledge is rather limited...

the problem with Netbeans for me is that yes, Netbeans sets its LnF to Metal with UIManager, but Swing applications I deveop and start from within Netbeans again use the Gtk-LnF that seems to be my default.

did you install the JDK globally (via sudo) or as user? from a .deb, a self-mde .de (like me) or from the .bin (thud ignoring Ubuntu-dependancies)?

kind regards,
Carsten

---

### Post by pertti on 2006-02-16
[QUOTE=Poldi]how have you installed the JDK on Ubuntu? perhabs the 'make-jpkg' machanism does something worng - my dpkg-knowledge is rather limited...

the problem with Netbeans for me is that yes, Netbeans sets its LnF to Metal with UIManager, but Swing applications I deveop and start from within Netbeans again use the Gtk-LnF that seems to be my default.

did you install the JDK globally (via sudo) or as user? from a .deb, a self-mde .de (like me) or from the .bin (thud ignoring Ubuntu-dependancies)?

kind regards,
Carsten[/QUOTE]

I installed the JDK globally with a self-made .deb, made with make-jpkg, following the instructions in the Ubuntu Wiki. I don't know what's wrong here... :(

---

