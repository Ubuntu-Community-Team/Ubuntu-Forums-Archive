---
title: "Newbie can't get 8.10 to detect monitor and resolution"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by davefaulkner on 2008-10-30
I've just started running 8.10 inside the Sun VirtualBox 2.0.4 (having failed to get a dual-boot setup via wubi.exe). However, I can only get 800x600 resolution at 61Hz. My monitor is not detected, and the only other resolution available is 640x480. I'm using a 19-inch monitor, and so want 1280x1024, or at very least 1024x768.

My monitor is a Dell 1907FP (Digital). The card is an nVidia Geforece 7900 GS.

If anyone has any ideas, I'm all ears. Many thanks.

---

### Post by jbrown96 on 2008-10-30
Very common problem. You need to install the Guest Editions. When running the VM, go to the Vbox menu bar and there should be some sort of option about installing the additions. It will download a very CD image; I think it automounts it as well, but perhaps not. Open the folder and execute the linux version for your version (x86 or AMD64_86)

Try the seamless mode. It's under file when running the VM. It's awesome

---

### Post by davefaulkner on 2008-10-31
Sorry, struggling here. The Guest Additions appear to be installed - not least on the grounds of your help with my sound problem. But beyond that, no luck, and I'm nowhere near having anything enabled that would get me into seamless mode. I can't even find something appropriate to click in the main VirtualBox window under the Details tab for my guest OS, in the way I clicked 'Audio' for the sound problem. 

If you have any further thoughts, or anyone else can help, I'd be most grateful. Thanks.

---

### Post by redbob on 2008-10-31
To get out Seamless mode, you could press RightCtrl-F. I have a similar problem when I upgraded my VirtualBox from 2.0.2 to 2.0.4, I installed a Kubuntu box and my screen gone white. All I had to do was reinstall VirtualBox with the same version 2.0.4

---

### Post by davefaulkner on 2008-11-02
@redbob: Thank you for your kind reply, unfortunately Seamless Mode is a tangent to the original question (although what you mention works). I'm still struggling to change my resolution higher than 800x600, with Guest Additions apparently installed for Sun VirtualBox 2.0.4. If anyone can walk me through what I do so that higher resolutions are available at System>Screen Resolution, I'd be very grateful.

---

### Post by jbrown96 on 2008-11-02
When you choose to install the guest additions, a Cdrom should appear on the desktop. In that there are several executables. You need to execute the linux version for you system (x86 or amd64). Unless you install those, there will not be any other resolution options. Once you install them, you don't change the resolution, just make the window bigger.

---

