---
title: "Ubuntu 16.04 : Networking GUI : How to find out which files are changed"
date: 2016-10-19
forum: New to Ubuntu
---

### Post by andimethia on 2016-10-19
Hi All, 

The short question version : When going (via Unity GUI) to system settings -> network, selecting the network,-> then hitting settings for that network -> Updating the Wi-Fi Security tab with the password, my connection sprung into life. Are you able to tell me which files it would have populated with this information? 

I checked /etc/network/interfaces and it just has :

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

I am hoping to find out what the files were that got changed and learn how to make changes via command line should I ever need to. 

Thanks for your help. 

System : Lenovo G580
OS : Ubuntu 16.04 64 bit
Network Card : 02:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
Ubuntu experience : about 20 hours, though I am keen and willing to learn.

Kind Regards


Kevin

---

### Post by howefield on 2016-10-19
Have a look at the files in..

```
/etc/NetworkManager/system-connections
```

---

### Post by Zero_Bytes on 2016-10-19
Try having a terminal open with        ```
sudo tail -f /var/log/syslog  
```  When you change settings in the GUI, it should report this in the terminal.

---

### Post by andimethia on 2016-10-19
Thanks guys! You were right about the location. It created two files "ssidname" and "ssidname 1", the first contains the WPA2 key. 

From the log, well this was from yesterday, but I managed to find the log for that (it got zipped). When I was attempting to connect via the signal icon on top right of the screen, I was getting disconnected every time. Now I know it says reason code "none". I am so glad the other method worked! 

Oct 17 15:59:25 paycek-Lenovo-G580 NetworkManager[937]: <info>  [1476716365.6743] device (wlp2s0): state change: config -> need-auth (reason 'none') [50 60 0]
Oct 17 15:59:25 paycek-Lenovo-G580 gnome-session[1720]: nm-applet-Message: No keyring secrets found for windsor2/802-11-wireless-security; asking user.
Oct 17 15:59:26 paycek-Lenovo-G580 gnome-session[1720]: Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Oct 17 15:59:26 paycek-Lenovo-G580 gnome-session[1720]: (nm-applet:1860): Gtk-WARNING **: Can't show Caps Lock warning, since secondary icon is set
Oct 17 15:59:50 paycek-Lenovo-G580 NetworkManager[937]: <warn>  [1476716390.6890] device (wlp2s0): No agents were available for this request.
Oct 17 15:59:50 paycek-Lenovo-G580 NetworkManager[937]: <info>  [1476716390.6891] device (wlp2s0): state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Oct 17 15:59:50 paycek-Lenovo-G580 NetworkManager[937]: <info>  [1476716390.6897] manager: NetworkManager state is now DISCONNECTED
Oct 17 15:59:50 paycek-Lenovo-G580 NetworkManager[937]: <warn>  [1476716390.6906] device (wlp2s0): Activation: failed for connection 'windsor2'
Oct 17 15:59:50 paycek-Lenovo-G580 NetworkManager[937]: <info>  [1476716390.6919] device (wlp2s0): state change: failed -> disconnected (reason 'none') [120 30 0]
Oct 17 15:59:50 paycek-Lenovo-G580 kernel: [  221.059477] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready

---

### Post by dxvargas on 2017-05-25
@andimethia where did you place the file "ssidname"? It was really only the WPA2 key in it?

---

### Post by christianc123 on 2017-05-27
[COLOR=#000000][FONT=&quot]
File is /etc/NetworkManager/system-connections[COLOR=#111111][FONT=Ubuntu] .[/FONT][/COLOR]

NetworkManager tries to read and write your distribution's normal network configuration files through plugins called "system settings plugins". These plugins allow you to use the file formats you're already comfortable with and the tools you already know how to use to manage your network configuration. You can use NetworkManager's D-Bus interface too.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]A generic plugin called 'keyfile' is also provided to read and write configuration that your distro's native file format cannot handle.


Regards
Christian
Network Admin
[/FONT][/COLOR]
[http://cloudappsportal.com/](http://cloudappsportal.com/)
[COLOR=#000000][FONT=&quot]
[/FONT][/COLOR]

---

