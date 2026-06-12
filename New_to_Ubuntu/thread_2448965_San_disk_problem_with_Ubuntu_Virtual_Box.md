---
title: "San disk problem with Ubuntu Virtual Box"
date: 2020-08-17
forum: New to Ubuntu
---

### Post by cody1970 on 2020-08-17
I am very new here, and new to Ubuntu. I have been trying for 4 days to get this to work, searched the web for all info and found nothing. I want to use my sandisk 2.0 flash drive in the ubuntu virtual box. I followed ALL directions on how to do it and set up, everything works except when I click on "64GB  Volume" then I click "SanDiskSecureAccessV3.1_win.exe"   ,  I get this error: "And Error Occurred While Loading The Device" I cant open the usb flash drive at all in linux. It opens fine in Windows.

Is sandisk not supported by linux? I run all other usb devices, camera, seagate hard drive, and no problem, i am able to read all files in seagate. Any help would be appreciated, thanks.

---

### Post by ajgreeny on 2020-08-17
You do not make this clear, but are you running a virtual install of Windows in VBox, and is it using this Windows VM that the sandisk fails?

Do you have the Guest Additions extension pack installed in VBox which you can download from [https://download.virtualbox.org/virtualbox/6.1.12/Oracle_VM_VirtualBox_Extension_Pack-6.1.12.vbox-extpack](https://download.virtualbox.org/virtualbox/6.1.12/Oracle_VM_VirtualBox_Extension_Pack-6.1.12.vbox-extpack) and then double click to install it in VBox.  You will also have to boot to and then install the guest additions in your VMs.

---

### Post by cody1970 on 2020-08-17
Hello, thank you for replying. I have I guess what you call the windows host. I have a pc with windows 10, and I downloaded the virtual box which has Linux Ubuntu.  I have the Ubuntu virtual box, oracle I think its called? Yes , I have that extension, l I double checked, its installed. I dont understand why I cant get this usb flash to open. I tried every port on my computer, it opens in windows fine, but I get that same error in Ubuntu, "And Error Occurred While Loading The Device" after I click "SanDiskSecureAccessV3.1_win.exe" My friend has the exact same sandisk, and same virtual box, and his works fine.  My san disk flash works perfect in windows, not ubuntu.

---

### Post by Holger_Gehrke on 2020-08-17
SanDiskSecureAccess is a Windows program to transparently encrypt data on the USB drive. Since it works at a rather low level in Windows it's quite probably interfering with Virtual Box and it's drivers. If you've encrypted the whole drive using this tool, then you've made the data on it impossible to access from Ubuntu. Ask your friend whether he's using this encryption tool. He probably doesn't.

Holger

---

### Post by SeijiSensei on 2020-08-17
Can you mount the SD card with that "SecureAccess" program and assign the device a drive letter? If so, you should be able to use the "Shared Folders" feature in VirtualBox to make the device visible inside the virtual machine.  You'll need to install the [Extension Pack]("https://download.virtualbox.org/virtualbox/6.1.12/Oracle_VM_VirtualBox_Extension_Pack-6.1.12.vbox-extpack") if you have not yet done so. You can access the feature by opening the VirtualBox manager and clicking on a virtual machine. Hit Settings, and you'll see the Shared Folders option.

If the device is encrypted using this SecureAccess feature, and the steps above don't work, I'm not sure you'll be able to use it at all. Any reason you need this feature? Worried about the security of your files?

---

