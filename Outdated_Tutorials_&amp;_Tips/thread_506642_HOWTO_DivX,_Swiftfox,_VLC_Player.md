---
title: "HOWTO: DivX, Swiftfox, VLC Player"
date: 2007-07-21
forum: Outdated Tutorials &amp; Tips
---

### Post by VileTimes on 2007-07-21
This howto assumes that you have [Swiftfox]("http://getswiftfox.com/") already installed. If you don't, what's keeping you? ;)

**Step 1 - Install VLC**

Follow the instructions for your particular version of Ubuntu according to the [_VLC Media Player's website_]("http://www.videolan.org/vlc/download-ubuntu.html").

The problem is, if you do: ```
about:plugins
``` ... in Swiftfox's address bar, nothing even remotely VLC-ish pops up. Let's fix that now.


**Step 2 - Hunt down the mozilla plug-in files**

This is the most important part of this howto. For some reason, the mozilla-plugin-vlc package does not install the plugin where Swiftfox can access them. We need to find the .so and .xpt files and soft link them to our Swiftfox plugins directory.

First let's drill-down to the Swiftfox plugins directory.

```
cd ~/.mozilla/plugins
```

Next, we create the links to the plugin...

```
ln -s /usr/lib/mozilla-firefox/components/vlcintf.xpt vlcintf.xpt
```
```
ln -s /usr/lib/mozilla-firefox/plugins/libvlcplugin.so libvlcplugin.so
```

Restarting Swiftfox and typing "about plugins" in the address bar will now display a long list of VLC goodies, but we aren't done yet.


**Step 3 - Install and configure the Media Connectivity Add-On**

You can scoop this up [_here_]("https://addons.mozilla.org/en-US/firefox/downloads/file/2285/mediaplayerconnectivity-0.8.3-fx+fl+mz+ns+zm.xpi"). Restart Swiftfox and let the installation wizard run as it searches for your media players (you only really need VLC for everything). Once it's done, you'll be presented with a list of media formats and which application the Add-On should launch. Scroll down and look for the entry marked "DivX". Make sure the checkbox is ticked and enter this line as the default player: /usr/bin/X11/vlc

Done!

This howto won't help if you absolutely want to watch stuff off of stage6's website, but it works fabulously at [_tv-links.co.uk_]("http://tv-links.co.uk/"), even though a lot of their material is hosted at stage6.com. Simply click on the...

[IMG]http://img382.imageshack.us/img382/6219/mcpvl7.gif[/IMG]

Enjoy!

---

