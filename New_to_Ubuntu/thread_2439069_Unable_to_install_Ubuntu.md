---
title: "Unable to install Ubuntu"
date: 2020-03-22
forum: New to Ubuntu
---

### Post by esquire64 on 2020-03-22
Hello!

I wanted to install Ubuntu on an old Windows tablet that I had. The tablet in question is a Winbook TW802, and I had previously installed Fedora on it.

However, at this point, I'm unable to boot into a USB stick. I don't know if this is the correct place to post asking for help with this, but if I get kicked around to another forum, so be it. Just want to start on getting this solved.

For the record, I've already created a bootable USB using etcher (and Ubuntu 18.04).

Here's what happens:
1) I turn on the tablet and boot into the BIOS
2) I move the boot order around so that it tries to boot into the USB stick first
3) I restart the tablet
4) It boots into Fedora

If I boot back into the BIOS, it shows that the boot order is unchanged, even though I've tried every combination of "Save" and "Save and Exit".

if anyone has any ideas on how to get this working, I would definitely appreciate it.

Thanks!

---

### Post by dino99 on 2020-03-22
Do you get usefull info from journalctl after the usb boot failure ?

[https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-windows#1-overview)

---

### Post by yancek on 2020-03-22
I'm not familiar with the table you are using.  Is Fedora the only OS installed?  How old is this hardware and which version of Fedora are you using?  Does the BIOS show options under the hard drive as many computers will show the usb under the hard drive option listed by manufacturer of the usb.  Make sure after making the chanage in the BIOS that you save the change.  How did you install Fedora?  Did you use a CD/DVD/flash drive.  Didn't keep any notes on the process?

---

### Post by esquire64 on 2020-03-22
So I did a little reading about journalctl (of which I frankly still  know very little). I was able to figure out how to capture the logs  since I attempted booting into the USB drive. It was around 15:25 that  it happened so I captured the logs with:

```
journalctl --since  "2020-03-22 15:20:00" &> log
```

I'm  a relatively new and inexperienced user, so don't expect this kind of  magic from me again (assuming, of course, that I actually got something  useful to begin with). 

I guess the logs are too long to attach (and I don't know if it's worthwhile pasting the contents here). If it helps, the first instance I can find of Ubuntu is: "Mar 22 15:28:50 localhost.localdomain udisksd[816]: Mounted /dev/sda1 at /run/media/glenbanks/Ubuntu 18.04.4 LTS amd64 on behalf of uid 1000".

Not sure if that means anything, but can we assume that it didn't try booting into the device (only mounting it after Fedora started)?

Also worth noting, I've tried putting the USB stick in another computer, and it works to boot from it just fine.

Thank you for your help.

---

### Post by esquire64 on 2020-03-22
Hello yancek. I'll try to answer all your questions.

Q: Is Fedora the only OS installed?
A: Yes.

Q: How old is this hardware and which version of Fedora are you using?
A: I don't recall exactly how old it is, but the BIOS firmware is from 2014. I have Fedora 31 installed.

Q: Does the BIOS show options under the hard drive?
A: It doesn't show any additional options for booting from flash drive, although it's very clear which drive is the flash drive I want to boot from (it's called "SanDisk").

Not really a question, but I'll respond to the fact that you mentioned to save changes in the BIOS. I can promise you I both saved the changes as well as chose the option "Save changes and Exit" when I was done.

Q: How did you install Fedora?
A: I used the live media that was created from Fedora's website. I went to this site and downloaded the Windows version of the "Fedora Media Writer": [https://getfedora.org/en/workstation/download/](https://getfedora.org/en/workstation/download/)

Q: Did you use a CD/DVD/flash drive?
A: I used a SanDisk flash drive.

Q: Did you keep any notes on the process?
A: Unfortunately I didn't. I thought I was going to stick with it, but I'm having enough issues with it that I figured I'd go to something slightly more familiar (i.e. Ubuntu).

---

