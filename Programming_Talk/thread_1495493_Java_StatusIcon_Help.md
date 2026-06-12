---
title: "Java StatusIcon Help"
date: 2010-05-28
forum: Programming Talk
---

### Post by neothedm on 2010-05-28
Hey guys, I'm new here. I need some help with something that I couldn't solve on my own, see I am a java programmer and I am working on a small project. The problem that I have is not being able to get StatusIcon to work using java-gnome library ([java-gnome.sourceforge.net]("http://java-gnome.sourceforge.net")), I googled it many times to come up with nothing useful, I know how to use AWT TrayIcon but I don't want to use it, because it looks so old and I really need something that looks native in gnome.

To explain my problem a little more:
I want to add an icon to the gnome system tray(which java-gnome is suppose to be able to do that)
I can display notifications but there is really no icon in the tray
When the code is executed I see that something took a little space in the system tray but its empty.


simply this is the portion of my code that I using to make this:

```
...
...
...
...
            StatusIcon xx = new StatusIcon();
            xx.setFromFile("./ir.png");
            xx.setTooltip("Lama_Lirc");
            xx.setVisible(true);
            Notification x = new Notification("Lama_Lirc", "Started", "", xx);
            x.show();

...
...
...
...

```
Please I need help to do this.

Thanks

---

### Post by lykeion on 2010-05-28
I haven't tested this myself but I found an example showing a status icon using java-gnome:

[http://java-gnome.sourcearchive.com/documentation/4.0.14/ExampleLowBattery_8java-source.html](http://java-gnome.sourcearchive.com/documentation/4.0.14/ExampleLowBattery_8java-source.html)

Hope that helps...

---

