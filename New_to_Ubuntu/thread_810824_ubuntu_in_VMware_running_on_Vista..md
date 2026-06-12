---
title: "ubuntu in VMware running on Vista."
date: 2008-05-28
forum: New to Ubuntu
---

### Post by Roen hayden on 2008-05-28
Ok I have VMware installed on windows vista.  I have a WIFI usb device, I&#8217;m running ubuntu 8.04 in the VMware server but I cannot get it use the wifi usb device. The VMware server sees the usb device but does not let i run in ubuntu and there is no check in the menu. And I have VMware tools installed on the ubuntu os. Any ideas?

---

### Post by quelx on 2008-05-28
Why not just let Windows manage the network and bridge the Windows network with VMware.  Ubuntu will treat the bridge as a plain ole Ethernet conneciton.

---

### Post by Roen hayden on 2008-05-28
I dont want to i want to use the wifiusb device not the bridge.

---

### Post by Roen hayden on 2008-05-28
any ideas on geting ubuntu to use the usb device and i have tested it with other usb devices and it does not pick them up.

---

### Post by Bananas21ca on 2008-05-28
This might be of some use to you

[http://www.vmware.com/support/ws45/doc/devices_usb_ws.html](http://www.vmware.com/support/ws45/doc/devices_usb_ws.html)

---

### Post by Roen hayden on 2008-05-28
Installing USB Devices as a Non-Administrator 

Any user on a Windows host can connect USB devices for use in a virtual machine. You no longer need administrative privileges on the host to connect a USB device to a virtual machine. 

This functionality is not enabled by default. To enable it, you must use a text editor such as Notepad to add one line to the global configuration file. This file is
C:\Documents and Settings\<username>\Application Data\VMware\config.ini 

Add the following line anywhere in the file: 

usb.EnablePnpMgr = TRUE 

Note: A user with administrative privileges on the host operating system must install a USB device on the host before it can be connected by users who do not have administrative privileges. 


^ that might be my problem but i'm the only user that uses the computer shouldnt i automatically be admin.

---

### Post by Roen hayden on 2008-05-28
as i said about that might be my problem but is there anything in ubuntu that would cause this problem?

---

### Post by ajane on 2009-12-02
Hi everyone,

My host OS is Linux 9.04 and I tried to install windows server as guest host.

I installed VMware and I have got this message:

Operating system not found!

I don't know what I have to do and no good tutorial on that subject, do you any good link(even I didn't find any troubleshooting in VMware website?)

I don't understand also the process of VMware how it cannot find a boot file if by default I configured the installation?

And What does mean the virtual cd boot?

Many questions and no answer in any forums!

Does anyone can understand VMware?

Ajane.

---

### Post by Mark Phelps on 2009-12-02
> **ajane said:**
> Hi everyone,

My host OS is Linux 9.04 and I tried to install windows server as guest host.

I installed VMware and I have got this message:

Operating system not found!

I don't know what I have to do and no good tutorial on that subject, do you any good link(even I didn't find any troubleshooting in VMware website?)

I don't understand also the process of VMware how it cannot find a boot file if by default I configured the installation?

And What does mean the virtual cd boot?

Many questions and no answer in any forums!

Does anyone can understand VMware?

Ajane.

The folks that can answer your question will most likely NOT read this thread -- because your problem is totally different from the thread title.

You would do best to start your own thread and NOT hijack this one.  That way, folks with experience with Windows Server and Ubuntu 9.04 will see the thread.

---

