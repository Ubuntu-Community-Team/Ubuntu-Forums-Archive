---
title: "Cannot mount any usb flash drive after upgrade to Hardy"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by concite on 2008-08-20
I was running Gutsy for some time.  I could take one of my USB flash drives (I have several) and plug it in.  Ubuntu would recognize the drive, I could read and write to it, I could transfer the drive to an XP system, transfer files there.  In short, it just worked.

Then I upgraded to Hardy using the Synaptic package manager.

Now, when I plug in a usb flash, drive, the machine thinks, and then the rive shows up in the File Browser as "STORE'N'GO" or similar.  When I double click on it, nothing happens.  No error, nothing.  When I right click and select "Open", nothing. When I right click and select "Open in a new window", nothing. When I right click and select "Mount", nothing.

Very frustrating as everything used to just work.  Any thoughts?

---

### Post by falcon61102 on 2008-08-20
Is it possible that while in Windows, you accidently removed them prior to hitting the Safely Remove Hardware button and that's what's causing your problem.  Have you been able to go back into windows and access any of them?

---

### Post by decoherence on 2008-08-20
first, unplug the device. then open up a terminal and type ```
sudo udevmonitor | tee udevout.txt
``` then plug the device in. give it a few seconds to settle then press Ctrl C to exit udevmonitor. Post the contents of udevout.txt here (it should be in your home folder)

---

### Post by timcredible on 2008-08-20
you upgraded to hardy via synaptic?  that's probably the problem.  try running the hardy live cd and see if the usb drive works then.  if so, i would recommend you back up your stuff and install hardy from scratch.

---

### Post by concite on 2008-08-20
OK - responding to all three suggestions:

1) The drive works fine in XP. I don't think this is my problem.
2) UDEV output as follows:

> udevmonitor will print the received events for:
UDEV the event which udev sends out after rule processing
UEVENT the kernel uevent

UEVENT[1219246102.523116] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-7 (usb)
UEVENT[1219246102.523651] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-7/usb_endpoint/usbdev5.6_ep00 (usb_endpoint)
UDEV  [1219246102.525311] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-7 (usb)
UEVENT[1219246102.525334] add      /class/scsi_host/host5 (scsi_host)
UEVENT[1219246102.525343] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-7/5-7:1.0/usb_endpoint/usbdev5.6_ep81 (usb_endpoint)
UEVENT[1219246102.525351] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-7/5-7:1.0/usb_endpoint/usbdev5.6_ep02 (usb_endpoint)
UDEV  [1219246102.527132] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-7/usb_endpoint/usbdev5.6_ep00 (usb_endpoint)
UDEV  [1219246102.625932] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-7/5-7:1.0 (usb)
UDEV  [1219246102.627238] add      /class/scsi_host/host5 (scsi_host)
UDEV  [1219246102.629552] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-7/5-7:1.0/usb_endpoint/usbdev5.6_ep81 (usb_endpoint)
UDEV  [1219246102.631496] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-7/5-7:1.0/usb_endpoint/usbdev5.6_ep02 (usb_endpoint)
UEVENT[1219246107.525336] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-7/5-7:1.0/host5/target5:0:0/5:0:0:0 (scsi)
UEVENT[1219246107.525372] add      /class/scsi_disk/5:0:0:0 (scsi_disk)
UDEV  [1219246107.643963] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-7/5-7:1.0/host5/target5:0:0/5:0:0:0 (scsi)
UDEV  [1219246107.643990] add      /class/scsi_disk/5:0:0:0 (scsi_disk)
UEVENT[1219246107.824951] add      /block/sdd (block)
UEVENT[1219246107.824968] add      /block/sdd/sdd1 (block)
UEVENT[1219246107.824976] add      /class/scsi_device/5:0:0:0 (scsi_device)
UEVENT[1219246107.824983] add      /class/scsi_generic/sg4 (scsi_generic)
UDEV  [1219246107.828649] add      /class/scsi_device/5:0:0:0 (scsi_device)
UDEV  [1219246107.833013] add      /class/scsi_g

All gibberish to me.  Sorry.  

3) OK - downloaded burned a live CD.  USB drives work fine with the live CD.  As anecdotal evidence, I have other issues with Hardy that appear to have to do with the upgrade.  i.e. - the "unlock" buttons are greyed out, VNC performance is very slow, and a few other issues that appear to be upgrade problems.

Looks like backing up and installing from scratch, although painful, is the way to go.

Thanks for the help.

---

