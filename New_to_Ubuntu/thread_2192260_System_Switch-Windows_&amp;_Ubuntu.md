---
title: "System Switch-Windows &amp; Ubuntu"
date: 2013-12-06
forum: New to Ubuntu
---

### Post by ocar23 on 2013-12-06
New to Linux and have just installed Ubuntu 12.10 LTS and LAMP, running on a dedicated HD with Win7 64bit OS.

Is there a Program or Method of Switching between Ubuntu and Windows and Back again.

One of my reasons is: If I am working in Ubuntu, and say, go into a Forum, which returns me an Email, I have to Shutdown Ubuntu, then Open Windows and Outlook, to read my Email. When I finish, I have to Reverse the Shutdown and Restart Ubuntu.

Rather annoying and I am sure there is someone who would have the skills to solve this problem.

---

### Post by QIII on 2013-12-06
Hello!

Other than running one or the other in a virtual machine, no.  For most users, VirtualBox (which is free to use) seems to suit the need pretty well.

Your computer will only run one OS at a time on bare metal.

Cheers!

---

### Post by DuckHook on 2013-12-06
If your e-mail is IMAP then you can open an e-mail reader in Ubuntu. Anything you do in your Linux e-mail client will be synchronized with your server and will be properly updated in your Windows client the moment you open it (and vice versa).

But I understand your issue and e-mail is just one example. If your HW is powerful enough, then what you are looking for is a technology called Virtual Machines (VM). There are many VMs around and some of them have their cores already built in to the Linux kernel. Two such are KVM and Xen, but they are rather involved and not very beginner-friendly. A better choice for beginners is either VirtualBox or VMWare. Explanation of a VM is [here]("https://help.ubuntu.com/community/VirtualMachines"), which in turn contains a link to a very informative Wikipedia article.

---

### Post by oldfred on 2013-12-06
Back when I was running XP before Ubuntu I switched everything to Firefox, Thunderbird & OpenOffice. Then when I changed to Ubuntu it was just the operating system for my main applications.

And then I found I could move my Firefox & Thunderbird profiles to a shared NTFS partition and use the same bookmarks & email in both systems.
I still have the NTFS partition as I do not have a lot of room in my Linux shared data but do not use XP any more.

       [http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)
Firefox
[http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox](http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox)

---

### Post by electrohandyman501 on 2013-12-06
If your mail provider has a web access portal, you could just go there too to read it.....Or your smartphone......

Just extra options...

---

### Post by ocar23 on 2013-12-08
Thank you for your replies.
I had a nasty feeling that it may not be possible to switch OS.

---

### Post by amjjawad on 2013-12-08
> **ocar23 said:**
> Thank you for your replies.
I had a nasty feeling that it may not be possible to switch OS.

You 'definitely' do NOT need to switch Operating Systems just to 'read emails' :)

If your Email Provider does not have Web Interface like MSN/Hotmail, Yahoo and/or Gmail then depends on the settings of your email server, you can use many programs like Thunderbirds to read your emails :)

If your Email Provider has Web Interface (like Gmail), then you just need to open a new tab, login to your email and that is all :)

When I was Dual-booting/Multi-Booting with Windows 3 years ago, I had to switch back and forth 'only' when there is a very specific program that I need to work on. Now, typing this from Xubuntu 12.04.3, I don't need to switch to any other system :)

Don't worry, once you learn how to make your first steps in Linux World, you will learn how to run and start to help others with their issues so don't give up ;)

---

### Post by bigmonmulgrew on 2013-12-09
Personally I try to get into the habbit of using the same program in Windows and Linux wherever possible. Many people will tell you the pros and cons but often systems are functionally the same.

I've used Firefox for some time. I use web for my email but you can use thunderbird in both Windows and Linux. I use GIMP for image editing. Open office for office documents. You can make the learning curve for Linux much easier if you get used to using Open source software since the interface is typically the same regardless of OS.

I still need to dual boot due to the fact I use Microsoft Visual Studio but for most things you should be able to find a cross platform alternative.

---

