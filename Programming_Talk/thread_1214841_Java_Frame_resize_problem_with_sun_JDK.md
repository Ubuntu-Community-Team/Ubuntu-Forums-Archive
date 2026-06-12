---
title: "Java Frame resize problem with sun JDK"
date: 2009-07-16
forum: Programming Talk
---

### Post by nguillot on 2009-07-16
Hi everybody, 

I explain my problem with a sample application:
```
import java.awt.event.ComponentAdapter;
import java.awt.event.ComponentEvent;

import javax.swing.JFrame;

import org.apache.log4j.Logger;

public class ResizingJFrame extends ComponentAdapter {
    /** logger */
    protected static final Logger LOGGER = Logger
            .getLogger(ResizingJFrame.class);

    public void componentResized(final ComponentEvent p_e) {
        LOGGER.debug("resize detected!");
    }

    public static void main(String[] args) {
        JFrame frame = new JFrame("test app");
        frame.setSize(300, 300);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.addComponentListener(new ResizingJFrame());
        frame.validate();
        frame.setVisible(true);
    }
}
```As you can see the application should display a message when the frame is resized.

With java-6-openjdk all goes right, but with java-1.5.0-sun I can't see any message.

You can read the log here:
```
[jdur - /tmp > sudo update-alternatives --config java

Il y a 5 alternatives fournissant « java ».

  Sélection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
          2    /usr/bin/gij-4.3
          3    /usr/lib/jvm/java-gcj/jre/bin/java
 +        4    /usr/lib/jvm/java-6-openjdk/jre/bin/java
*         5    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Appuyez sur Entrée pour conserver la valeur par défaut
[*] ou choisissez le numéro sélectionné :4
Utilisation de « /usr/lib/jvm/java-6-openjdk/jre/bin/java » pour fournir « java ».
[jdur - /tmp > java -jar AppTest-0.0.1-SNAPSHOT-jar-with-dependencies.jar 
DEBUG [ResizingJFrame.java:14]: resize detected!
DEBUG [ResizingJFrame.java:14]: resize detected!
DEBUG [ResizingJFrame.java:14]: resize detected!
DEBUG [ResizingJFrame.java:14]: resize detected!
[jdur - /tmp > sudo update-alternatives --config java

Il y a 5 alternatives fournissant « java ».

  Sélection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
          2    /usr/bin/gij-4.3
          3    /usr/lib/jvm/java-gcj/jre/bin/java
*+        4    /usr/lib/jvm/java-6-openjdk/jre/bin/java
          5    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Appuyez sur Entrée pour conserver la valeur par défaut
[*] ou choisissez le numéro sélectionné :5
Utilisation de « /usr/lib/jvm/java-1.5.0-sun/jre/bin/java » pour fournir « java ».
[jdur - /tmp > java -jar AppTest-0.0.1-SNAPSHOT-jar-with-dependencies.jar 
[jdur - /tmp > java -version
java version "1.5.0_16"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_16-b02)
Java HotSpot(TM) Client VM (build 1.5.0_16-b02, mixed mode, sharing)
```

Anyone know how to fix it with sun JDK?

Thanks for any response and sorry for my poor english.

---

