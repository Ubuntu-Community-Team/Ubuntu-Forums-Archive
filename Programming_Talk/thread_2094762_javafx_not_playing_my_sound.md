---
title: "javafx not playing my sound"
date: 2012-12-14
forum: Programming Talk
---

### Post by 3v3rgr33n on 2012-12-14
Hi

I've been playing around with javafx today trying to make a music player.
I keep getting the following Exception, I don't even understand what this "ibavformat.so.52" file is

```
** (process:11801): WARNING **: Failed to load plugin '/usr/local/java/jre1.7.0_07/lib/i386/fxavcodecplugin-52.so': libavformat.so.52: cannot open shared object file: No such file or directory
Exception in thread "AWT-EventQueue-0" java.lang.IllegalStateException: Toolkit not initialized
    at com.sun.javafx.application.PlatformImpl.runLater(PlatformImpl.java:153)
    at com.sun.javafx.application.PlatformImpl.runLater(PlatformImpl.java:148)
    at javafx.application.Platform.runLater(Platform.java:52)
    at javafx.scene.media.MediaPlayer.init(MediaPlayer.java:450)
    at javafx.scene.media.MediaPlayer.<init>(MediaPlayer.java:365)
    at zola.uct.Sax.BlueSax.play(BlueSax.java:129)
    at zola.uct.Sax.BlueSax.actionPerformed(BlueSax.java:121)
    at javax.swing.AbstractButton.fireActionPerformed(Unknown Source)
    at javax.swing.AbstractButton$Handler.actionPerformed(Unknown Source)
    at javax.swing.DefaultButtonModel.fireActionPerformed(Unknown Source)
    at javax.swing.DefaultButtonModel.setPressed(Unknown Source)
    at javax.swing.AbstractButton.doClick(Unknown Source)
    at javax.swing.plaf.basic.BasicMenuItemUI.doClick(Unknown Source)
    at javax.swing.plaf.basic.BasicMenuItemUI$Handler.mouseReleased(Unknown Source)
    at java.awt.Component.processMouseEvent(Unknown Source)
    at javax.swing.JComponent.processMouseEvent(Unknown Source)
    at java.awt.Component.processEvent(Unknown Source)
    at java.awt.Container.processEvent(Unknown Source)
    at java.awt.Component.dispatchEventImpl(Unknown Source)
    at java.awt.Container.dispatchEventImpl(Unknown Source)
    at java.awt.Component.dispatchEvent(Unknown Source)
    at java.awt.LightweightDispatcher.retargetMouseEvent(Unknown Source)
    at java.awt.LightweightDispatcher.processMouseEvent(Unknown Source)
    at java.awt.LightweightDispatcher.dispatchEvent(Unknown Source)
    at java.awt.Container.dispatchEventImpl(Unknown Source)
    at java.awt.Window.dispatchEventImpl(Unknown Source)
    at java.awt.Component.dispatchEvent(Unknown Source)
    at java.awt.EventQueue.dispatchEventImpl(Unknown Source)
    at java.awt.EventQueue.access$200(Unknown Source)
    at java.awt.EventQueue$3.run(Unknown Source)
    at java.awt.EventQueue$3.run(Unknown Source)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.security.ProtectionDomain$1.doIntersectionPrivilege(Unknown Source)
    at java.security.ProtectionDomain$1.doIntersectionPrivilege(Unknown Source)
    at java.awt.EventQueue$4.run(Unknown Source)
    at java.awt.EventQueue$4.run(Unknown Source)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.security.ProtectionDomain$1.doIntersectionPrivilege(Unknown Source)
    at java.awt.EventQueue.dispatchEvent(Unknown Source)
    at java.awt.EventDispatchThread.pumpOneEventForFilters(Unknown Source)
    at java.awt.EventDispatchThread.pumpEventsForFilter(Unknown Source)
    at java.awt.EventDispatchThread.pumpEventsForHierarchy(Unknown Source)
    at java.awt.EventDispatchThread.pumpEvents(Unknown Source)
    at java.awt.EventDispatchThread.pumpEvents(Unknown Source)
    at java.awt.EventDispatchThread.run(Unknown Source)
```

I was just trying to play a ".wav" file. Here's my play method
```

@args The path of the sound file
public void play(String path){
              File sound = new File(path);
              Media song = new Media(sound.toURI().toString());
              MediaPlayer player = new MediaPlayer(song);
              player.play();
}

```

---

### Post by Unterseeboot_234 on 2012-12-17
Your snippet code's method looks OK. 

What I have learned in JavaFX 2.2 is _ALL, ANY and EVERY_ JRE plug-in must be deleted from your current hard drive to use the beta FX 2.2.

The new JRE has the package path inside the jars for FXSDK 2.2 beta
```
com.oracle.*
```

The original JRE has the package path inside FXSDK 2.1.0
```
com.sun.*
```

The new 2.2 stops all code from execution with FX version < 2.2 and logs out to Terminal with warnings to edit your code. Thus, any textbook about JavaFX has deprecated code, but not in Media / MediaPlayer.

So, check your JRE plug-in.

---

### Post by 3v3rgr33n on 2012-12-19
Thanx for the reply, I resorted to using JLayer instead of javafx for mp3 playback.

---

