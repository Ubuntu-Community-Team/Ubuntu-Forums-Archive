---
title: "MP3 player gets dismounted abruptly"
date: 2018-02-17
forum: New to Ubuntu
---

### Post by wrongusername2 on 2018-02-17
I connect KLANGTOP MP3 player to transfer files. As soon as it is connected, drive appears in File Manager but gets unmounted within few seconds. I have never seen this happen on Win7 so I am thinking MP3 player is good enough.  Help me diagnize this issue. I am interested in **Mounted /dev/sdc1 at /media/afterwindows/K-183**

Here is the SYS.log

```

 Feb 17 18:56:14 afterwindowsZBook kernel: [27742.131061]  sdd: sdd1
Feb 17 18:56:14 afterwindowsZBook kernel: [27742.131998]**  sdc: sdc1**
Feb 17 18:56:14 afterwindowsZBook kernel: [27742.134018] sd 6:0:0:1: [sdd] Attached SCSI removable disk
Feb 17 18:56:14 afterwindowsZBook kernel: [27742.134639] sd 6:0:0:0: [sdc] Attached SCSI removable disk
Feb 17 18:56:15 afterwindowsZBook kernel: [27743.069645] FAT-fs (sdc1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
Feb 17 18:56:15 afterwindowsZBook udisksd[2135]: **Mounted /dev/sdc1 at /media/afterwindows/K-183 on behalf of uid 1000**
Feb 17 18:56:15 afterwindowsZBook systemd[1566]: dev-disk-by\x2did-usb\x2dACTIONS_HS_USB_FlashDisk_4512482ADF0FEEEE\x2dpart1.device: Dev dev-disk-by\x2did-usb\x2dACTIONS_HS_USB_FlashDisk_4512482ADF0FEEEE\x2dpart1.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10:1.0/host6/target6:0:0/6:0:0:0/block/sdc/sdc1 and /sys/devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10:1.0/host6/target6:0:0/6:0:0:1/block/sdd/sdd1
Feb 17 18:56:15 afterwindowsZBook systemd[1]: dev-disk-by\x2did-usb\x2dACTIONS_HS_USB_FlashDisk_4512482ADF0FEEEE\x2dpart1.device: Dev dev-disk-by\x2did-usb\x2dACTIONS_HS_USB_FlashDisk_4512482ADF0FEEEE\x2dpart1.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10:1.0/host6/target6:0:0/6:0:0:0/block/sdc/sdc1 and /sys/devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10:1.0/host6/target6:0:0/6:0:0:1/block/sdd/sdd1
Feb 17 18:56:15 afterwindowsZBook kernel: [27743.266905] **FAT-fs (sdd1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.**
Feb 17 18:56:15 afterwindowsZBook udisksd[2135]: **Mounted /dev/sdd1 at /media/afterwindows/K-1 on behalf of uid 1000**
Feb 17 18:56:15 afterwindowsZBook gnome-session[1783]: (nautilus:12510): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed
Feb 17 18:56:15 afterwindowsZBook gnome-session[1783]: (nautilus:12510): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed
Feb 17 18:56:15 afterwindowsZBook gnome-session[1783]: (nautilus:12518): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed
Feb 17 18:56:15 afterwindowsZBook gnome-session[1783]: (nautilus:12518): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed
Feb 17 18:56:15 afterwindowsZBook gnome-session[1783]: (nautilus:12510): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed
Feb 17 18:56:15 afterwindowsZBook gnome-session[1783]: (nautilus:12510): GLib-GObject-WARNING **: invalid (NULL) pointer instance
Feb 17 18:56:15 afterwindowsZBook gnome-session[1783]: (nautilus:12510): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed
Feb 17 18:56:15 afterwindowsZBook gnome-session[1783]: (nautilus:12518): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed
Feb 17 18:56:15 afterwindowsZBook gnome-session[1783]: (nautilus:12518): GLib-GObject-WARNING **: invalid (NULL) pointer instance
Feb 17 18:56:15 afterwindowsZBook gnome-session[1783]: (nautilus:12518): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed
Feb 17 18:56:15 afterwindowsZBook dbus[983]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
Feb 17 18:56:15 afterwindowsZBook systemd[1]: Starting Hostname Service...
Feb 17 18:56:16 afterwindowsZBook dbus[983]: [system] Successfully activated service 'org.freedesktop.hostname1'
Feb 17 18:56:16 afterwindowsZBook systemd[1]: Started Hostname Service.
Feb 17 18:56:17 afterwindowsZBook colord-sane: io/hpmud/pp.c 627: unable to read device-id ret=-1
Feb 17 18:56:19 afterwindowsZBook org.gtk.vfs.Daemon[1653]: ** (process:2236): WARNING **: send_infos_cb: No such interface 'org.gtk.vfs.Enumerator' on object at path /org/gtk/vfs/client/enumerator/445 (g-dbus-error-quark, 19)
Feb 17 18:56:19 afterwindowsZBook org.gtk.vfs.Daemon[1653]: message repeated 6 times: [ ** (process:2236): WARNING **: send_infos_cb: No such interface 'org.gtk.vfs.Enumerator' on object at path /org/gtk/vfs/client/enumerator/445 (g-dbus-error-quark, 19)]
Feb 17 18:56:19 afterwindowsZBook org.gtk.vfs.Daemon[1653]: ** (process:2236): WARNING **: send_done_cb: No such interface 'org.gtk.vfs.Enumerator' on object at path /org/gtk/vfs/client/enumerator/445 (g-dbus-error-quark, 19)
Feb 17 18:56:19 afterwindowsZBook org.gtk.vfs.Daemon[1653]: ** (process:2236): WARNING **: send_infos_cb: No such interface 'org.gtk.vfs.Enumerator' on object at path /org/gtk/vfs/client/enumerator/448 (g-dbus-error-quark, 19)
Feb 17 18:56:19 afterwindowsZBook org.gtk.vfs.Daemon[1653]: message repeated 3 times: [ ** (process:2236): WARNING **: send_infos_cb: No such interface 'org.gtk.vfs.Enumerator' on object at path /org/gtk/vfs/client/enumerator/448 (g-dbus-error-quark, 19)]
Feb 17 18:56:19 afterwindowsZBook org.gtk.vfs.Daemon[1653]: ** (process:2236): WARNING **: send_done_cb: No such interface 'org.gtk.vfs.Enumerator' on object at path /org/gtk/vfs/client/enumerator/448 (g-dbus-error-quark, 19)
Feb 17 18:56:37 afterwindowsZBook kernel: [27765.155733] usb 3-10: USB disconnect, device number 15
Feb 17 18:56:37 afterwindowsZBook udisksd[2135]:** Cleaning up mount point /media/afterwindows/K-183 (device 8:33 no longer exist)**
Feb 17 18:56:37 afterwindowsZBook udisksd[2135]: Cleaning up mount point /media/afterwindows/K-1 (device 8:49 no longer exist)
Feb 17 18:56:37 afterwindowsZBook systemd-udevd[12556]: inotify_add_watch(9, /dev/sdd, 10) failed: No such file or directory

```

---

