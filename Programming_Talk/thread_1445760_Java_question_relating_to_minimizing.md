---
title: "Java question relating to minimizing"
date: 2010-04-03
forum: Programming Talk
---

### Post by travmanx on 2010-04-03
Ok, I have hit a slight problem in my newest project. 
I am trying to get it so the program will minimize and be placed in the tray. 
I have tried a few ways on doing so but I always end up with this error on running:

```
Exception in thread "main" java.lang.UnsupportedOperationException
        at java.awt.TrayIcon.<init>(TrayIcon.java:112)
        at java.awt.TrayIcon.<init>(TrayIcon.java:136)
        at java.awt.TrayIcon.<init>(TrayIcon.java:165)
        at java.awt.TrayIcon.<init>(TrayIcon.java:195)
        at TwatUI.main(TwatUI.java:450)

```

In Suns trayIcon.java most of these errors relate to
```
SystemTray.isSupported()) {
```

Is it because I am Ubuntu and have to work around a different way for this, or am I just doing something wrong.

From a tut I followed...
```
import java.awt.HeadlessException;import java.awt.Image;

import java.awt.MenuItem;

import java.awt.Panel;

import java.awt.PopupMenu;

import java.awt.SystemTray;

import java.awt.TrayIcon;

import java.awt.event.ActionEvent;

import java.awt.event.ActionListener;

import java.awt.image.BufferedImage;

import javax.swing.Icon;

import javax.swing.JOptionPane;

import javax.swing.plaf.metal.MetalIconFactory;

 

public class SysTray {

private static Image getImage() throws HeadlessException {

        Icon defaultIcon = MetalIconFactory.getTreeComputerIcon();

        Image img = new BufferedImage(defaultIcon.getIconWidth(),

                defaultIcon.getIconHeight(),

                BufferedImage.TYPE_4BYTE_ABGR);

        defaultIcon.paintIcon(new Panel(), img.getGraphics(), 0, 0);

return img;

    }

private static PopupMenu createPopupMenu() throws

                                                 HeadlessException {

        PopupMenu menu = new PopupMenu();

MenuItem exit = new MenuItem("Exit");

        exit.addActionListener(new ActionListener() {

           public void actionPerformed(ActionEvent e) {

               System.exit(0);

           }

        });

        menu.add(exit);

return menu;

    }

public static void main(String[] args) throws Exception {

        TrayIcon icon = new TrayIcon(getImage(),

                "This is a Java Tray Icon", createPopupMenu());

        icon.addActionListener(new ActionListener() {

           public void actionPerformed(ActionEvent e) {

               JOptionPane.showMessageDialog(null,

                       "Bring Java to the Desktop app");

           }

        });

        SystemTray.getSystemTray().add(icon);

        while(true) {

            Thread.sleep(10000);

            icon.displayMessage("Warning", "Click me! =)",

                TrayIcon.MessageType.WARNING);

        }

    }

}
```

---

### Post by Reiger on 2010-04-03
What you are doing wrong is simple: you fail to check if your environment supports the tray icon.

IOW you must check the return value of SystemTray.isSupported() using a construct like this in your main():

```

public static void main(String[] args) {
  if(SystemTray.isSupported()) {
    // create image and popup menu and make a tray item from it
  }
  else {
    // fall back logic in case the JVM has no access to the tray.
  }
}

```

---

