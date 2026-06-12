---
title: "Frustrated with my first experience"
date: 2013-02-15
forum: New to Ubuntu
---

### Post by Zarukei on 2013-02-15
I am really upset at how hard it is to get Ubuntu going. At first it was  GPU locking at the login screen and looped while it tried to switch to  software mode. Then I had to search for a solution which was hard to  find alone. I finally get to the Desktop where I had to google for  information to install the Drivers and get updates as well. This took  about an hour and after it was done, it stayed software mode graphics. I  logged in also to find that only the background showed and I could only  make folders and stuff and had no access to the menu button.

Could someone please help me? I would like to try to fix what is happening right now instead of redoing it all again.

Extra Information:
  Using Ubuntu 12.10 installed from windows.
  GTX 580 with i7-930

---

### Post by HermanAB on 2013-02-15
Well, Ubuntu is probably the worst desktop Linux around these days.  You would be better off using Xubuntu, Lubuntu, Mint, Mageia, PCLinuxOS, Fedora KDE/XFCE spins - pretty much any non-Gnome3 based version of desktop Linux is much better.  

Plus, by the sounds of it, you did a Wubi install, which is an emulator on Windows and which is only meant for demonstrations, not serious use.

Soooo, you did pretty much everything wrong!

---

### Post by Nebelhom on 2013-02-15
@HermanAB: I am sure that is exactly what he wanted to hear. Well done ;) I started off with Ubuntu, too, and had serious teething problems a couple of years ago. It's probably better to tell him where to start and not what s/he's done "wrong" (if s/he actually has...)

@Zarukei: I am definitely not an expert and after this comment, I will leave it to them.

It is best to tell people what you tried, so that they know where to start. Secondly, I would try the [nvidia website]("http://www.nvidia.com/Download/index.aspx?lang=en-us") for drivers if all things fail.

All the best for the future. I hope you get there eventually. It may be a bit of an upward struggle sometimes, but I think the rewards are worth it.

---

### Post by lisati on 2013-02-15
> **HermanAB said:**
>  
Plus, by the sounds of it, you did a Wubi install, which is an emulator on Windows and which is only meant for demonstrations, not serious use.

A relatively minor correction might be in order here. Wubi isn't exactly an emulator. The main difference between a Wubi installation and a regular installation is that instead of installing Ubuntu into its own partition, it installs it into what might be thought of as a "virtual partition" that is really a file within the Windows file system. Wubi also provides an entry in the "Add/Remove software" utility on the Windows control panel.

---

### Post by sudodus on 2013-02-15
> **Nebelhom said:**
> @HermanAB: I am sure that is exactly what he wanted to hear. Well done ;) I started off with Ubuntu, too, and had serious teething problems a couple of years ago. It's probably better to tell him where to start and not what s/he's done "wrong" (if s/he actually has...)

@Zarukei: I am definitely not an expert and after this comment, I will leave it to them.

It is best to tell people what you tried, so that they know where to start. Secondly, I would try the [nvidia website]("http://www.nvidia.com/Download/index.aspx?lang=en-us") for drivers if all things fail.

All the best for the future. I hope you get there eventually. It may be a bit of an upward struggle sometimes, but I think the rewards are worth it.
+1
@Zarukei,

Welcome to the Ubuntu Forums :-)

Please tell us more details about your computer, at least brand name, model, and wifi chip/card, we'll add that to the specs you provided (Ubuntu 12.10 installed from windows.  GTX 580 with i7-930). Then it will be much easier for us to help you find a good way to get it working.

Unless you have a brand new computer, it is probably better to download the iso file of some flavour of Ubuntu 12.04 LTS with long time support. This version has been debugged 6 months longer than 12.10, and is more likely to work (except with brand new hardware). And as Herman AB described, there are several flavours, Lubuntu, Xubuntu and Kubuntu except [vanilla] Ubuntu with different desktop environments, but the engines behind are basically the same.

---

### Post by grahammechanical on 2013-02-15
I would like to point out that during the development of Ubuntu 12.10 there were serious problems (bugs) with Nvidia video drivers. Unfortunately they are proprietary code and Ubuntu developers can not modify them. We just have to wait for Nvidia to correct the faults.

Because of this bad experience that I have had with Nvidia drivers I never install Ubuntu with the option to install third part software ticked.

That way I do get the Nvidia driver but the Open source Nouveau driver and I get to a Desktop. If I want to use the proprietary driver then I can activate it very easily by going (in 12.10) to Software  Sources>Additional Drivers tag. Ubuntu does all the work.

Ubuntu also has some very useful help documentation that explains the Ubuntu Desktop.

I have no experience with Wubi installs. And I am wondering if this machine has Nvidia Optimus technology. Nvidia has only just started to develop a Linux driver for its Optimus technology. Failure of hardware makers to provide drivers or cooperate with Linux developers is often a reason why there are problems installing Linux.

You would have had much the same problems with those other recommended Linux distributions. Simply because they are issues outside the control of Linux developers.

May I suggest that you go into Additional Drivers and try the Nouveau driver? Or a different Nvidia driver?

If you do have Optimus technology then you need this web site

[http://bumblebee-project.org/]("http://bumblebee-project.org/")

You can often get to a desktop by selecting Recovery Mode>Resume.

Other than that I do not understand what you mean by 'software mode.' Fail Safe mode, perhaps?

Oh, and I vigorously disagree with that comment about the Ubuntu desktop. 

Regards.

---

### Post by snowpine on 2013-02-15
Welcome to the forums!

If you purchase a computer with Ubuntu preinstalled from a vendor such as System76 or Dell, you will have no problems.

If you are tech-savvy and feel confident with your abilities to install an operating system yourself, here is a list of Ubuntu-certified hardware that is extensively tested to run Ubuntu flawlessly: [http://www.ubuntu.com/certification/](http://www.ubuntu.com/certification/)

The third tier of support would be a self-install on non-certified hardware. Obviously this will be the most difficult and frustrating of the three options.

Here is a suggestion to take hardware support out of the equation: Since you have a powerful new computer, you can run Ubuntu "inside of" Windows. In this case, Windows does the low-level hardware and driver support, and Ubuntu "thinks" it is running inside generic, well-supported hardware with no driver issues. Here are easy instructions to accomplish this: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

(please note that when using Virtualbox, many users report better results with Xubuntu or Lubuntu than with Ubuntu.)

---

### Post by Mark Phelps on 2013-02-15
> **Zarukei said:**
> I am really upset at how hard it is to get Ubuntu going. At first it was  GPU locking at the login screen and looped while it tried to switch to  software mode. Then I had to search for a solution which was hard to  find alone. I finally get to the Desktop where I had to google for  information to install the Drivers and get updates as well. This took  about an hour and after it was done, it stayed software mode graphics. I  logged in also to find that only the background showed and I could only  make folders and stuff and had no access to the menu button.

Yes, it CAN be very frustrating starting out in the Linux world, largely because you are used to thinking in "Windows terms" and haven't let learned how the Linux world is different.

One major difference, is that in general, you do NOT start out in Ubuntu by manually installing drivers; instead, the setup process scans the hardware, and downloads and installs the proper drivers -- for you.

Unless something is actually NOT working, it is not advisable to go out and start downloading and installing drivers.

Video drivers are a good example of this -- the default drivers generally work quite well, and when a new Ubuntu release comes out, there is often the case where the "restricted" drivers haven't yet caught up.

So, unless you have stuff you really need to keep, my suggestion would be to REMOVE the Wubi installation, reinstall it -- and do NOT go installing any drivers.  Just see what works and what does not.

And, in the case of stuff not working, just post here with the problems.

---

