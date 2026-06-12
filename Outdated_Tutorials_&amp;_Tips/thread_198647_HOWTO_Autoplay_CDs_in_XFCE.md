---
title: "HOWTO: Autoplay CDs in XFCE"
date: 2006-06-17
forum: Outdated Tutorials &amp; Tips
---

### Post by picpak on 2006-06-17
One feature I miss in Gnome is autoplaying CDs. Here's how to get it back:

1) Install ivman (a program which manages automounting/autoplaying devices):
```
sudo apt-get install ivman
```

2) Edit ivman's actions config file:
```
mousepad .ivman/IvmConfigActions.xml
```

3) Paste the following in this file:
```
<?xml version="1.0" encoding="UTF-8"?> 
<ivm:ActionsConfig version="0.2" xmlns:ivm="http://www.eikke.com/ivm">
   <ivm:Match name="hal.volume.disc.has_audio" value="true"> 
      <ivm:Option name="exec" value="**beep-media-player** -p /media/cdrom0" /> 
   </ivm:Match> 

    <!-- Read the IvmConfigActions.xml man page for details on how to edit this file. -->

    <!-- mount everything we can -->
    <ivm:Match name="ivm.mountable" value="true">
        <ivm:Option name="mount" value="true" />
    </ivm:Match>

    <!-- rip CDs with audio tracks and no data tracks -->
    <!--
    <ivm:Match name="hal.volume.disc.type" value="cd_rom">
        <ivm:Match name="hal.volume.disc.has_audio" value="true">
            <ivm:Match name="hal.volume.disc.has_data" value="false">
                <ivm:Option name="exec" value="kaudiocreator" />
            </ivm:Match>
        </ivm:Match>
    </ivm:Match>
    -->

    <!-- When attaching a wireless card, if we connect to network with Nickname 'QUT-Wireless',
         start 'vpnc-connect' to connect to VPN; when we remove wireless card, disconnect
         from the VPN. Replace the 'NETID' with your own wireless network Nickname.
		 As you can see, this script, being fairly big, is probably a good candidate to put into
		 a separate little scriptlet. -->
    <!--
    <ivm:Match name="hal.info.category" value="net.80211">
        <ivm:Option name="exec" value="NETID=&apos;QUT-Wireless&apos;; i=0; while ! { /sbin/ifconfig $hal.net.interface$ | grep 'inet addr' &amp;>/dev/null || [ $i -gt 45 ]; }; do sleep 1; i=`expr $i + 1`; done; ps aux | grep -v grep | grep vpnc &amp;> /dev/null || { c=0; while ! { [ &quot;`/usr/sbin/iwconfig $hal.net.interface$ 2>&amp;1 | sed -n -r -e 's/.*Nickname:\&quot;([^\&quot;]+)\&quot;.*/\1/ p'`&quot; = &quot;${NETID}&quot;] || [ $c -ge 10 ]; }; do sleep 1; c=`expr $c + 1`; done; [ $c -lt 10 ] &amp;&amp; sudo vpnc-connect; }" />
        <ivm:Option name="execun" value="sudo vpnc-disconnect" />
    </ivm:Match>
   -->

    <!-- autoplay video DVDs in Xine (change PLAYER and PLAYEROPT to use a different media player -->
    <!--
    <ivm:Match name="hal.volume.disc.is_videodvd" value="true">
        <ivm:Option name="exec" value="PLAYER='xine'; PLAYEROPT='-f dvd://'; pumount '$hal.volume.mount_point$' &amp;&amp; ${PLAYER} ${PLAYEROPT}$hal.block.device$" />
    </ivm:Match>
    -->

   <!-- ======================= KDE notifications ========================== -->
   <!-- If you would like a little box to pop-up in KDE and notify when a new
        device is detected, Windows-style, uncomment this entire block.  
        Feel free to add entries for devices which aren't handled yet... -->
   <!--
   <ivm:Match name="hal.info.category" value="storage">
       <ivm:Match name="hal.storage.bus" value="usb">
           <ivm:Option name="exec" value="kdialog --passivepopup 'USB storage device detected: $hal.info.vendor$ $hal.info.product$' 4" />
       </ivm:Match>
   </ivm:Match>
   <ivm:Match name="hal.info.category" value="scanner">
       <ivm:Match name="hal.storage.bus" value="usb">
           <ivm:Option name="exec" value="kdialog --passivepopup 'USB scanner detected: $hal.info.vendor$ $hal.info.product$' 4" />
       </ivm:Match>
   </ivm:Match>
   <ivm:Match name="hal.info.category" value="printer">
        <ivm:Match name="hal.info.bus" value="usb">
           <ivm:Option name="exec" value="kdialog --passivepopup 'USB printer detected: $hal.info.vendor$ $hal.info.product$' 4" />
        </ivm:Match>
   </ivm:Match>
   -->
   <!-- ======================= end of KDE notifications =================== -->

</ivm:ActionsConfig>
 
```
(Replace beep-media-player with whichever media player you prefer.) Save the file and exit.

4) Load ivman when you log in:
```
sudo mousepad /etc/xdg/xfce4/xinitrc
```

After the first line (the line that says, #!/bin/sh), paste the following:

```
ivman-launch &
```

Save the file, and log out and in. Now you can automatically play your CDs when you put them in!

---

### Post by CronoDekar on 2006-06-17
This is pretty cool.  I'll be sure to bookmark this and try it out sometime (too lazy right now).  Thanks!

---

### Post by redcharlie on 2007-07-18
After installing the gnome removeable media manager, I discovered that xfce has this capability already built in.  The file manager, thunar, has a module for this that comes installed with xubuntu by default.

It's not very obvious
see:[http://thunar.xfce.org/documentation/C/using-removable-media.html]("http://thunar.xfce.org/documentation/C/using-removable-media.html")

---

### Post by picpak on 2007-07-19
Yeah, this guide is outdated...now you can set it up in Thunar > Edit > Preferences > Advanced > Volume Management. (why isn't this under Settings? It'd make a lot more sense...)

---

