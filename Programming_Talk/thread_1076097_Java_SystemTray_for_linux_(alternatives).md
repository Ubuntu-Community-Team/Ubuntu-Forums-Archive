---
title: "Java SystemTray for linux (alternatives?)"
date: 2009-02-21
forum: Programming Talk
---

### Post by DocForbin on 2009-02-21
I've just started playing with SystemTray in Ubuntu, and although it seems mostly functional, it's pretty disappointing. There are bugs I've already stumbled onto (I think) such as mouseClicked not firing from the TrayIcon when right clicking more than once, and ActionEvent not firing on CheckboxMenuItem.

It also looks ugly, and aside from setting fonts on PopupMenu, I don't see any way to make menus and  tray icon messages look decent.

Is SystemTray even worth using? If not, what are the alternatives?

---

### Post by drubin on 2009-02-21
What Java version are you using?
How are you creating the system try. Have you tried changing your look and feel to the systems native one?

---

### Post by DocForbin on 2009-02-21
running the sun jvm 1.6.0_10.

I'm creating it using SystemTray, TrayIcon, and PopupMenu. Just like the example here:

[http://java.sun.com/developer/technicalArticles/J2SE/Desktop/javase6/systemtray/](http://java.sun.com/developer/technicalArticles/J2SE/Desktop/javase6/systemtray/)

Hopefully I'm wrong, but I don't think the look and feel stuff comes into play with SystemTray since it doesn't use swing (it's just awt). UIManager.getSystemLookAndFeelClassName() shows its using the GTKLookAndFeel which looks best to me in Ubuntu with swing apps. Changing it to any of the 5 or so UIManager.getInstalledLookAndFeels()) shows on my system doesn't seem to have any effect on the tray.

---

### Post by drubin on 2009-02-21
> **DocForbin said:**
> running the sun jvm 1.6.0_10.

I'm creating it using SystemTray, TrayIcon, and PopupMenu. Just like the example here:

[http://java.sun.com/developer/technicalArticles/J2SE/Desktop/javase6/systemtray/](http://java.sun.com/developer/technicalArticles/J2SE/Desktop/javase6/systemtray/)

Hopefully I'm wrong, but I don't think the look and feel stuff comes into play with SystemTray since it doesn't use swing (it's just awt). UIManager.getSystemLookAndFeelClassName() shows its using the GTKLookAndFeel which looks best to me in Ubuntu with swing apps. Changing it to any of the 5 or so UIManager.getInstalledLookAndFeels()) shows on my system doesn't seem to have any effect on the tray.


No you are correct awt components don't change with look and feel.

I haven't worked with java6's native tray icon before but with [this]("https://jdic.dev.java.net/documentation/incubator/tray/") this seems to be what they bassed the java6 api on but instead of using swing java chose to use awt :(.

You should be able to try this component and use this instead. 

**NOTE:** This is not native Java and *might* not work on all os environments that native Java would.

---

### Post by DocForbin on 2009-02-21
Thanks for the link, I'll check that out. The java 6 tray stuff is real easy to use, here's a quick example I just made if anyone wants to experiment with it:
[PHP]
package playground;

import java.awt.AWTException;
import java.awt.Image;
import java.awt.MenuItem;
import java.awt.PopupMenu;
import java.awt.SystemTray;
import java.awt.Toolkit;
import java.awt.TrayIcon;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class Tray {

    private static final String TOOLTIP = "tray test";
    private static final String IMAGE = "/usr/share/pixmaps/gnome-gmush.png";
    private static PopupMenu menu;

    public static void main(String[] args) {
        new Tray().start();
    }

    private void start() {
        if (SystemTray.isSupported()) {
            SystemTray tray = SystemTray.getSystemTray();
            Image trayImage = Toolkit.getDefaultToolkit().getImage(IMAGE);
            createMenu();
            TrayIcon trayIcon = new TrayIcon(trayImage, TOOLTIP, menu);
            trayIcon.setImageAutoSize(true);
            try {
                tray.add(trayIcon);
                trayIcon.displayMessage("caption", "howdy", TrayIcon.MessageType.INFO);
            } catch (AWTException e) {
                System.err.println("Error starting tray: " + e);
            }

        } else {
            System.err.println("SystemTray not supported");
        }
    }

    private void createMenu() {
        menu = new PopupMenu();
        MenuItem foo = new MenuItem("foo");
        MenuItem exit = new MenuItem("exit");
        exit.addActionListener(new exitListener());
        menu.add(foo);
        menu.addSeparator();
        menu.add(exit);
    }

    class exitListener implements ActionListener {

        public void actionPerformed(ActionEvent e) {
            System.out.println("exiting...");
            System.exit(0);
        }
    }
}
[/PHP]

---

### Post by drubin on 2009-02-21
> **DocForbin said:**
> Thanks for the link, I'll check that out. The java 6 tray stuff is real easy to use, here's a quick example I just made if anyone wants to experiment with it:


The API for the example I gave is 90% the same only it uses JMenu and JPopupMenu so the examples would be much more styleable and would allow changing the look and feel. Let us know what you find. :)

---

### Post by DocForbin on 2009-02-21
the jdic Tray Icon doesn't appear to be supported in Ubuntu, or at least I can't seem to get the demo to work. I installed jdic-java, and when I run the demo with

java -classpath ../../tray.jar:. -Djava.library.path=../../ IconDemo

I get

Error: Couldn't find per display information

edit: maybe the jdic version in the repository is too old?

---

### Post by DocForbin on 2009-02-21
Found this hack for jusing JPopupMenu with the native TrayIcon.

[http://weblogs.java.net/blog/ixmal/archive/2006/05/using_jpopupmen.html](http://weblogs.java.net/blog/ixmal/archive/2006/05/using_jpopupmen.html)

Unfortunately, using this approach the menu doesn't close when clicking outside it like system tray menus normally do. arggh

---

### Post by DocForbin on 2009-02-21
In case anyone else is actually interested <g>...

Last year Alexander Potochkin wrote a JXTrayIcon that extends TrayIcon to support JPopupMenu. It is based on the same idea as his original blog post I linked above, but fixes the problem with the menu not closing when clicking outside it by using a hidden JDialog.

[http://weblogs.java.net/blog/alexfromsun/archive/2008/02/jtrayicon_updat.html](http://weblogs.java.net/blog/alexfromsun/archive/2008/02/jtrayicon_updat.html)

BUT, as he mentions at the bottom of the comments, the JDialog hack causes problems in Linux. On my system it makes the title bar of  apps flicker/change color.

This workaround  by Michael Bien is based on JXTrayIcon and addresses the Linux problems by using a JWindow for non-windows:

[https://fishfarm.dev.java.net/source/browse/fishfarm/trunk/FishFarm/src/net/java/fishfarm/ui/JPopupTrayIcon.java?rev=198&view=markup](https://fishfarm.dev.java.net/source/browse/fishfarm/trunk/FishFarm/src/net/java/fishfarm/ui/JPopupTrayIcon.java?rev=198&view=markup)

It seems to work fine, at least on my laptop running Ubuntu 8.10.

It's a shame there isn't swing support for TrayIcon to begin with.

---

### Post by DocForbin on 2009-02-21
So with the above workaround, here's a TrayIcon example using JPopupMenu on Ubuntu :) It's using nimbus look and feel,
 
[[IMG]http://img222.imageshack.us/img222/556/swingtray.th.png[/IMG]](http://img222.imageshack.us/my.php?image=swingtray.png)

This is a tiny MPD tray client, btw

---

### Post by drubin on 2009-02-21
> **DocForbin said:**
> In case anyone else is actually interested <g>...

Last year Alexander Potochkin wrote a JXTrayIcon that extends TrayIcon to support JPopupMenu. It is based on the same idea as his original blog post I linked above, but fixes the problem with the menu not closing when clicking outside it by using a hidden JDialog.

Thanks for sharing great to know.

---

### Post by HotCupOfJava on 2009-02-21
Wow. Doc - you've really gotten into this......Educational thread, I like it.

---

### Post by drubin on 2009-02-22
> **HotCupOfJava said:**
> Wow. Doc - you've really gotten into this......Educational thread, I like it.

Ye. Thread started with the OP asking for help and ended with the OP writing a basic tut on how to do it.

If only all threads answered them selves:)

---

### Post by DocForbin on 2009-02-23
> **drubin said:**
> Ye. Thread started with the OP asking for help and ended with the OP writing a basic tut on how to do it.

If only all threads answered them selves:)

That's how I roll, yo :)

I've tested these hacks fairly extensively and have a few more notes. If anyone is interested I'll post a summary.

I'm afraid I spent way too much time thinking I could fix the shortcomings of these workarounds. Argg, I hope Sun adds proper try support in 7.

---

### Post by drubin on 2009-02-23
> **DocForbin said:**
> That's how I roll, yo :)

I've tested these hacks fairly extensively and have a few more notes. If anyone is interested I'll post a summary.

I'm afraid I spent way too much time thinking I could fix the shortcomings of these workarounds. Argg, I hope Sun adds proper try support in 7.

Great post away. I think this thread is going in the right direction for helping others.

I would definitely come back here should I ever need the system try icon thing going on in java :)

---

### Post by DocForbin on 2009-02-23
Right on, if you don't hear from me in the next couple days, please someone bump this to remind me.

---

### Post by loteq on 2010-05-05
> **DocForbin said:**
> Right on, if you don't hear from me in the next couple days, please someone bump this to remind me.

Bump?

I know this is an old thread but is is 2010 and the linux system tray still looks like crap.

I am really interested in what workarounds are out there.

---

