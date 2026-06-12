---
title: "Help with Limewire (Not connecting)"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by aflatun on 2008-05-10
I just installed Limewire on Ubuntu 8.04. Any help would be welcome. Thanks.

I get the following message in the terminal:

Starting LimeWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_06]
Configuring environment...
Loading LimeWire:

(<unknown>:13848): Gtk-WARNING **: Attempting to add a widget with type GtkButton to a GtkComboBoxEntry (need an instance of GtkEntry or of a subclass)

(<unknown>:13848): Gtk-CRITICAL **: gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(<unknown>:13848): Gtk-CRITICAL **: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(<unknown>:13848): Gtk-CRITICAL **: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

******************************************************************
Something went wrong with LimeWire.
Maybe you're using the wrong version of Java?
(LimeWire is tested against and works best with with Sun's JRE, Java 1.5+)
The version of Java in your PATH is:
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)

---

### Post by barbedsaber on 2008-05-10
try [http://www.frostwire.com/](http://www.frostwire.com/)

its not limewire, but it is just as good (better)

---

### Post by dRock1286 on 2008-05-10
```
sudo update-alternatives --config java
```

Try that.  That's what got Frostwire working for me with the same error codes.

---

### Post by aflatun on 2008-05-10
Tried that but it didn't work.

:~$ sudo update-alternatives --config java

There is only 1 program which provides java
(/usr/lib/jvm/java-6-sun/jre/bin/java). Nothing to configure.

---

### Post by barbedsaber on 2008-05-10
are you trying limewire or frostwire?

---

### Post by aflatun on 2008-05-10
Trying for limewire but will consider frostwire as well. Tried installing frostwire but get the same problem i.e. it doesn't connect.

---

### Post by barbedsaber on 2008-05-10
I dont have a clue, sorry mate

---

### Post by aflatun on 2008-05-10
Here is what I get with Frostwire:

Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_06]
Configuring environment...
Loading FrostWire:
Warning: Cannot convert string "-b&h-luxi sans-medium-r-normal--*-140-*-*-p-*-iso8859-1" to type FontStruct
Warning: Cannot convert string "-wenquanyi-wenquanyi zenhei-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct
Warning: Cannot convert string "-sazanami-gothic-medium-r-normal--*-140-*-*-c-*-jisx0208.1983-0" to type FontStruct
Warning: Cannot convert string "-baekmuk-gulim-medium-r-normal--*-140-*-*-c-*-ksc5601.1987-0" to type FontStruct
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@69a4cb
current thread is Thread[Thread-6,5,main]
please submit a bug report to [email]bugs@frostwire.com[/email] with the following information :
java.lang.Exception: Stack trace
	at java.lang.Thread.dumpStack(Thread.java:1206)
	at irc.EventDispatcher.dispatchEventSyncEx(EventDispatcher.java:293)
	at irc.ListenerGroup.sendEventEx(ListenerGroup.java:169)
	at irc.ListenerGroup.sendEvent(ListenerGroup.java:143)
	at irc.ListenerGroup.sendEvent(ListenerGroup.java:211)
	at irc.gui.pixx.PixxTaskBar.enter(PixxTaskBar.java:152)
	at irc.gui.pixx.PixxTaskBar.addStatus(PixxTaskBar.java:207)
	at irc.gui.pixx.PixxMDIInterface.statusCreated(PixxMDIInterface.java:250)
	at irc.gui.pixx.PixxMDIInterface.sourceCreated(PixxMDIInterface.java:330)
	at irc.IRCApplication.sourceCreated(IRCApplication.java:325)
	at irc.IRCServer.enumerateSourcesAsCreated(IRCServer.java:301)
	at irc.IRCApplication.newServer(IRCApplication.java:166)
	at irc.IRCApplication.init(IRCApplication.java:133)
	at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:149)
	at com.limegroup.gnutella.gui.chat.ChatMediator$1.run(ChatMediator.java:107)
	at java.lang.Thread.run(Thread.java:619)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@69a4cb
current thread is Thread[Thread-6,5,main]
please submit a bug report to [email]bugs@frostwire.com[/email] with the following information :
java.lang.Exception: Stack trace
	at java.lang.Thread.dumpStack(Thread.java:1206)
	at irc.EventDispatcher.dispatchEventSyncEx(EventDispatcher.java:293)
	at irc.ListenerGroup.sendEventEx(ListenerGroup.java:169)
	at irc.ListenerGroup.sendEvent(ListenerGroup.java:143)
	at irc.ListenerGroup.sendEvent(ListenerGroup.java:211)
	at irc.gui.pixx.PixxTaskBar.activate(PixxTaskBar.java:398)
	at irc.gui.pixx.PixxTaskBar.enter(PixxTaskBar.java:153)
	at irc.gui.pixx.PixxTaskBar.addStatus(PixxTaskBar.java:207)
	at irc.gui.pixx.PixxMDIInterface.statusCreated(PixxMDIInterface.java:250)
	at irc.gui.pixx.PixxMDIInterface.sourceCreated(PixxMDIInterface.java:330)
	at irc.IRCApplication.sourceCreated(IRCApplication.java:325)
	at irc.IRCServer.enumerateSourcesAsCreated(IRCServer.java:301)
	at irc.IRCApplication.newServer(IRCApplication.java:166)
	at irc.IRCApplication.init(IRCApplication.java:133)
	at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:149)
	at com.limegroup.gnutella.gui.chat.ChatMediator$1.run(ChatMediator.java:107)
	at java.lang.Thread.run(Thread.java:619)
Smileys should be ACTIVE!
SponsorLoader.startElement -> Detected a custom refreshrate -> 0
SponsorLoader.startElement -> Killing Banner Refresh Tasks
BannerContainer.setupBannerRefreshTask() - No banner refresh for me.
Discarding message - 
UpdateMessage @21337813{_hashCode : 1469, 
_message : There's a new Windows version of FrostWire Available.
We highly recommend you update it now, 
_url : [http://www.frostwire.com](http://www.frostwire.com), 
_messageType : update, 
_version : 4.13.5, 
_expiration : null, 
_torrent : null, 
_os : windows, 
_showOnce : false, 
}

Discarding message - 
UpdateMessage @28415827{_hashCode : 1233, 
_message : There's a new MacOSX version of FrostWire Available.
We highly recommend you update it now, 
_url : [http://www.frostwire.com](http://www.frostwire.com), 
_messageType : update, 
_version : 4.13.5, 
_expiration : null, 
_torrent : null, 
_os : mac, 
_showOnce : false, 
}

ABOUT TO SHOW SOME ANNOUNCEMENTS

---

### Post by barbedsaber on 2008-05-10
> **aflatun said:**
> Here is what I get with Frostwire:

Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_06]
Configuring environment...
Loading FrostWire:
Warning: Cannot convert string "-b&h-luxi sans-medium-r-normal--*-140-*-*-p-*-iso8859-1" to type FontStruct
Warning: Cannot convert string "-wenquanyi-wenquanyi zenhei-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct
Warning: Cannot convert string "-sazanami-gothic-medium-r-normal--*-140-*-*-c-*-jisx0208.1983-0" to type FontStruct
Warning: Cannot convert string "-baekmuk-gulim-medium-r-normal--*-140-*-*-c-*-ksc5601.1987-0" to type FontStruct
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@69a4cb
current thread is Thread[Thread-6,5,main]
please submit a bug report to [email]bugs@frostwire.com[/email] with the following information :
java.lang.Exception: Stack trace
	at java.lang.Thread.dumpStack(Thread.java:1206)
	at irc.EventDispatcher.dispatchEventSyncEx(EventDispatcher.java:293)
	at irc.ListenerGroup.sendEventEx(ListenerGroup.java:169)
	at irc.ListenerGroup.sendEvent(ListenerGroup.java:143)
	at irc.ListenerGroup.sendEvent(ListenerGroup.java:211)
	at irc.gui.pixx.PixxTaskBar.enter(PixxTaskBar.java:152)
	at irc.gui.pixx.PixxTaskBar.addStatus(PixxTaskBar.java:207)
	at irc.gui.pixx.PixxMDIInterface.statusCreated(PixxMDIInterface.java:250)
	at irc.gui.pixx.PixxMDIInterface.sourceCreated(PixxMDIInterface.java:330)
	at irc.IRCApplication.sourceCreated(IRCApplication.java:325)
	at irc.IRCServer.enumerateSourcesAsCreated(IRCServer.java:301)
	at irc.IRCApplication.newServer(IRCApplication.java:166)
	at irc.IRCApplication.init(IRCApplication.java:133)
	at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:149)
	at com.limegroup.gnutella.gui.chat.ChatMediator$1.run(ChatMediator.java:107)
	at java.lang.Thread.run(Thread.java:619)
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@69a4cb
current thread is Thread[Thread-6,5,main]
please submit a bug report to [email]bugs@frostwire.com[/email] with the following information :
java.lang.Exception: Stack trace
	at java.lang.Thread.dumpStack(Thread.java:1206)
	at irc.EventDispatcher.dispatchEventSyncEx(EventDispatcher.java:293)
	at irc.ListenerGroup.sendEventEx(ListenerGroup.java:169)
	at irc.ListenerGroup.sendEvent(ListenerGroup.java:143)
	at irc.ListenerGroup.sendEvent(ListenerGroup.java:211)
	at irc.gui.pixx.PixxTaskBar.activate(PixxTaskBar.java:398)
	at irc.gui.pixx.PixxTaskBar.enter(PixxTaskBar.java:153)
	at irc.gui.pixx.PixxTaskBar.addStatus(PixxTaskBar.java:207)
	at irc.gui.pixx.PixxMDIInterface.statusCreated(PixxMDIInterface.java:250)
	at irc.gui.pixx.PixxMDIInterface.sourceCreated(PixxMDIInterface.java:330)
	at irc.IRCApplication.sourceCreated(IRCApplication.java:325)
	at irc.IRCServer.enumerateSourcesAsCreated(IRCServer.java:301)
	at irc.IRCApplication.newServer(IRCApplication.java:166)
	at irc.IRCApplication.init(IRCApplication.java:133)
	at com.limegroup.gnutella.gui.chat.ChatMediator.tryToStartAndAddChat(ChatMediator.java:149)
	at com.limegroup.gnutella.gui.chat.ChatMediator$1.run(ChatMediator.java:107)
	at java.lang.Thread.run(Thread.java:619)
Smileys should be ACTIVE!
SponsorLoader.startElement -> Detected a custom refreshrate -> 0
SponsorLoader.startElement -> Killing Banner Refresh Tasks
BannerContainer.setupBannerRefreshTask() - No banner refresh for me.
Discarding message - 
UpdateMessage @21337813{_hashCode : 1469, 
_message : There's a new Windows version of FrostWire Available.
We highly recommend you update it now, 
_url : [http://www.frostwire.com](http://www.frostwire.com), 
_messageType : update, 
_version : 4.13.5, 
_expiration : null, 
_torrent : null, 
_os : windows, 
_showOnce : false, 
}

Discarding message - 
UpdateMessage @28415827{_hashCode : 1233, 
_message : There's a new MacOSX version of FrostWire Available.
We highly recommend you update it now, 
_url : [http://www.frostwire.com](http://www.frostwire.com), 
_messageType : update, 
_version : 4.13.5, 
_expiration : null, 
_torrent : null, 
_os : mac, 
_showOnce : false, 
}

ABOUT TO SHOW SOME ANNOUNCEMENTS

GAH!  :o:o:o:shock::shock:

/run away from computer in mad confused state and bash head against wall. ](*,)

---

