---
title: "Installing Graphic Card drivers from terminal"
date: 2012-03-03
forum: New to Ubuntu
---

### Post by Rekhytz on 2012-03-03
So I just got a new low end laptop, and I was hoping to squeeze some more performance out of it by running Ubuntu on it.

I installed 11.04 via CD, and booted it up, I quickly figured out that the machine doesn't boot into a GUI, it hangs on either a black screen or a blank screen with blinking cursor, I can alt f4 into terminal and log in but not much else. After some searching, I think the problem is it can't find a driver for my video card.

I had some trouble like this during installing where I had to use a modeset command from this link [http://journalxtra.com/linuxsanity/ubuntu-fixing-the-blank-screen-on-installation-bug-2532/](http://journalxtra.com/linuxsanity/ubuntu-fixing-the-blank-screen-on-installation-bug-2532/) and it booted up a gui to allow installation of ubuntu, I guess it still has trouble booting with the video card. So I went in search of a driver for my card, and found the driver here [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

So finally here is my question, I need to install this driver via terminal, and I don't know the command to do so, google search didn't really help so I have to ask myself.

I have an external usb driver I can put it on if that makes things easier, but I'll need to be walked through the entire process because I am really new to linux.

Thank you in advance for any help~

---

### Post by TeoBigusGeekus on 2012-03-03
Navigate to the folder where the file is
```
cd /path/to/folder
```
Make the file executable
```
chmod +x name_of_file.ext
```
Execute the file as root
```
sudo ./name_of_file.ext
```

---

### Post by Mark Phelps on 2012-03-03
Please post the specs of the "low-end" laptop.  It could be that you're getting no desktop because it's too "low-end".

---

