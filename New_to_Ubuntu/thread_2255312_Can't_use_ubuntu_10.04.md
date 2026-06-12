---
title: "Can't use ubuntu 10.04"
date: 2014-12-04
forum: New to Ubuntu
---

### Post by newbie13 on 2014-12-04
First let me tell you my system condition
I have windows 8 preinstalled then I have installed ubuntu 14.04 on it with help of this forum and now I am trying to install ubuntu 10.04, where I need help again.

What I have done is this
1. Downloaded .iso image of ubuntu 10.04 64 bit desktop version
2. Used unetbootin to burn the image on pendrive
3. Turned on legacy mode because my pendrive was not showing up while choosing where to boot from
4. Switched from usb 3.0 port to 2.0 because when selected ' Try without installing' it said 'could not find media etc.' But using usb 2.0 port solved it
5. There was 20 gb free space so gave that space to 'ext4 /' but did not give any space for swap because I have already given 4 gb for swap while installing ubuntu 14.04
6. Completed the installation process and restarted laptop

Everything was going as expected till this step

7. In the boot menu there was no option added to boot into ubduntu 10.04 so I selected an option from where I start ubuntu 14.04 but no luck there too
8. So, I selected 'boot from hard drive'. There I found all the options for booting like ubuntu 14.04, 10.04, windows vista( don't know why) with their recovery options
9. After selecting ubuntu 10.04 black screen appeared with text which I can't understand( the only thing I could 'understand' was 'child_rip' lol...) and nothing happened after this
10. And if I select ubuntu 10.04 recovery mode, I could use the terminal but could not do much with it

Please help

---

### Post by coffeecat on 2014-12-04
Please do not even try to install Ubuntu 10.04. The desktop version has long passed end-of-life and is no longer supported.

[http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

Also - you refer to Ubuntu in your post but you have used the Lubuntu prefix in your thread title. Is there a reason for this?

---

### Post by coffeecat on 2014-12-04
Re-reading your post again, it appears that you have indeed installed 10.04. And from your description, it sounds as though you have a UEFI system. I can't remember whether 10.04 supports booting from UEFI but I doubt it.

You will probably need help removing 10.04 from your system. In order to get that help, apart from answering the questions in my previous post, I suggest you get the boot info summary as described in the link below and post it:

[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Gordonbp531 on 2014-12-04
> **coffeecat said:**
> Re-reading your post again, it appears that you have indeed installed 10.04. And from your description, it sounds as though you have a UEFI system. I can't remember whether 10.04 supports booting from UEFI but I doubt it.



No it doesn't. 12.04 did but was a bit hit and miss AFAIR - the first version to install on UEFI with no problems was 13.04 AFAIK...

---

### Post by newbie13 on 2014-12-04
Sorry, there is no reason for selecting lubuntu but I can't find a way to change it to ubuntu.. 
It doesn't matter to me if there are vulnerabilities in it, there is no important stuff on this laptop
The reason why I am trying to use 10.04 is because I want to use 2.6 kernel version which is not there in 14.04 or is very difficult for me to downgrade

About UEIF, when I turn off legacy mode, the option to select usb for booting disappers but when I turn it on, it comes back(only when 10.04's image is in pendrive)
Andeverything is perfectly fine when I select "try without installing' but after restarting nothing works
Tried reinstalling it but no luck

---

### Post by sudodus on 2014-12-04
Maybe you can try ***Wary Puppy 5.5***, which is a current (updated) system with a 2.6 kernel. See this link

[http://distro.ibiblio.org/quirky/wary-5.5/release-Wary-5.5.htm](http://distro.ibiblio.org/quirky/wary-5.5/release-Wary-5.5.htm)

> Wary 5.5 has the same old 2.6.32.59 kernel

You can download it from this link [http://distro.ibiblio.org/quirky/wary-5.5/](http://distro.ibiblio.org/quirky/wary-5.5/)

and read more about it at the following link [http://puppylinux.org/main/Long-Term-Supported%20WaryPuppy.htm](http://puppylinux.org/main/Long-Term-Supported%20WaryPuppy.htm)

-o-

If you understand and can manage the risk with program packages, that do not receive security updates, you can run Ubuntu or Lubuntu 10.04 LTS. But we have warned you.

You will also have problems installing packages. The desktop related packages are already beyond end of life. The server related packages will reach end of life in April 2015, and after that it will not be easy to maintain the system.

---

### Post by newbie13 on 2014-12-04
I will give Wary 5.5 a shot but isn't there any way to make 10.04 work? Because I have wasted too many days to make it work without success.. And don't worry, I won't blame ubuntu if anything happens to my laptop. In case something goes wrong I have option to format the hard disc and reinstall the os

---

### Post by mörgæs on 2014-12-04
Why do you want to run an old kernel?

---

### Post by newbie13 on 2014-12-04
To use reaver to crack my own and my friends wpa2 wifi router who has challenged me.. I have tried everything within ubuntu 14.04 and the last option is to use older kernel, which I thought, would be easy if I use 10.04
I think I'm gonna use kali linux for this purpose.. I have already uninstalled ubuntu 10.04 and will post other questions regarding 14.04 later after researching them first, mostly they are driver issues..

Thank you all for as always quick responses..

---

### Post by coffeecat on 2014-12-04
> **newbie13 said:**
> To use reaver to crack my own and my friends wpa2 wifi router who has challenged me.. 

We don't support cracking. Thread closed.

---

