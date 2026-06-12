---
title: "HOWTO: Stop hal from IDE polling of CD-Rom drives"
date: 2005-10-17
forum: Outdated Tutorials &amp; Tips
---

### Post by skoal on 2005-10-17
**Problem**:

[LIST]
[*]*Nothing really*.  
[*]I just hate seeing my IDE light flickering off _constantly_.  And I mean constantly!
[*]I detest automounting anything with a passion.  I prefer the CLI and mounting my CD-Roms that way.
[/LIST]
**Notes**:

As best I understand the hal *demon*, the dbus runlevel init script fires off hal to check for events, such as polling your IDE channel for possible events (like a CD-Rom insert, for example).  Then, it's passed up the food chain: hal > system dbus > (application) message dbus.  From the message bus, KDE or Gnome applications will then give it some loving and suckle off it's teat.

**Solution**:
[LIST]
[*]Create your own .fdi file.  *Name it whatever you want*, and place it in the following path (in maroon).

skoal@morpheus:///[COLOR="DarkRed"]etc/hal/fdi/preprobe[/COLOR] $ cat cdromnoa.fdi 
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
        <device>
                <match key="block.device" string="[COLOR="DarkRed"]/dev/hdc[/COLOR]">
                        <merge key="storage.media_check_enabled" type="bool">false</merge>
                </match>
        </device>
        <device>
                <match key="block.device" string="[COLOR="DarkRed"]/dev/hdd[/COLOR]">
                        <merge key="storage.media_check_enabled" type="bool">false</merge>
                </match>
        </device>
</deviceinfo>
```
[*]...*notice that I have two CD-Roms* (/dev/hdc and /dev/hdd).  Just replace those with your actual devices.  If you only have one, well, just don't include the other entry between (and including) the tags (<device> [...] </device>).
[*]Restart the hal demon.
```
skoal@morpheus://~ $ sudo /etc/init.d/dbus restart
Password:
 * Stopping Hardware abstraction layer: 
   ...done.
 * Stopping system message bus...
   ...done.
 * Starting system message bus...
   ...done.
 * Starting Hardware abstraction layer: 
   ...done.
```
[*]Stop the Desktop service which checks for CD-Roms and automatically mounts them.  

**Gnome**

*I dunno*.

**KDE**
[LIST=1]
[*]System Settings > KDE Components > Service Manager
[*]Hilight 'KDED Media Manager', click STOP. (optionally) Uncheck USE (for subsequent logins)
[/LIST]
[/LIST]
**Addendum**:

If you ever want to restore your previous polling and automounting behaviour, just remove that .fdi file from that path, restart dbus, and recheck the Gnome/KDE automount feature.

**Conclusion**:

R.I.P. (Rest In Peaces) hal.  I will defeat you yet! Enjoy your flicker free [K]Ubuntu box!

\\//_

---

