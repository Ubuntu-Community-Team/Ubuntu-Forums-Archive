---
title: "UUSB wireless dondle problem."
date: 2008-09-12
forum: New to Ubuntu
---

### Post by markloudon on 2008-09-12
Hi, very new to linux and unbuntu. 
Couldn't get my old wireless card to work after converting laptop to edubuntu.
Bought an edimax usb dongle claimed to work out of the box with hardy heron.
Nothing.
Won't let me activate wireless networking, that remains greyed out.

Someone suggested I try this command :  tail -f /var/log/syslog

and watch what happened when I plugged in the device. It generated the following:


Sep 10 20:29:04 marks-laptop NetworkManager: <info>  wlan1: Device is fully-supported using driver 'rt73usb'. 
Sep 10 20:29:04 marks-laptop NetworkManager: <info>  wlan1: driver supports SSID scans (scan_capa 0x01). 
Sep 10 20:29:04 marks-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Sep 10 20:29:04 marks-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Sep 10 20:29:04 marks-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'wlan1'. 
Sep 10 20:29:04 marks-laptop NetworkManager: <info>  Deactivating device wlan1. 

Anyone know why it is doing that, what it means and what I can do to correct it?

Mark Loudon

---

