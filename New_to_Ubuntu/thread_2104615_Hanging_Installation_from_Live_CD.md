---
title: "Hanging Installation from Live CD"
date: 2013-01-13
forum: New to Ubuntu
---

### Post by ConCla on 2013-01-13
Hello. Thank you in advance for any help you can offer me. I am somewhat at the end of my rope here.

The situation is this: I have some fairly serious problems with Windows 7, the exact nature of which eludes me (though it seems to be something to with the .NET framework), and in any case would probably be beyond my limited technical expertise to solve. I would have considered doing a fresh install, except that Windows came pre-loaded on the machine when I bought it, and I now can't find any recovery disc that may have come packaged with it.

I decided that perhaps it was time to try Ubuntu (12.04.1). So, I burned a live CD. Good thing I did, as Windows decided to stop booting altogether shortly after.

So, now I'm running Ubuntu off the live CD. Except I don't seem to be able to install it. The process starts, but then once I click past the first step of the installation wizard it just loads and loads, without ever progressing.

I decide to download a Windows 7 ISO, burn that to a disc, and see if I had more luck. Unfortunately, I only have the one drive. Which I am using to run Ubuntu from the Live CD. So, I take a risk and try taking the live CD out in order to burn the DVD. But I get the same problem as with the installation. It just hangs and hangs on the preparation to write the disc without ever progressing.

I have searched the forums for solutions to both of these problems, and tried a couple of the fixes suggested, but I don't seem to be able to get either process working.

Any advice you have to offer would be gratefully received.

- ConCla

---

### Post by audiomick on 2013-01-13
Given that both the Linux installer and the Windows installer exhibit the same behaviour, I would be worried that the drive is having trouble.

Can you access the drive from the live environment?

In the Ubuntu live environment, look for the drive manager utility. I think you should find it if you type "hard drive" into the dash. In there, you would need to point it at the internal drive of the machine. There is a button to the right of the window that lets you see the SMART values of the drive. See what that says.


Have you got the files on the machine backed up? If not, you should do this. If the drive has problems, it could become unreadable. If you do an install over the windows install, you will lose anything that is on that partition. If you have a separate data partition, you can leave that intact during the install, but you should back it up anyway. Something could go wrong.

Another thing that might be useful is a screenshot of gparted showing the drive. Are you aiming for a dual boot? Win7 installs often have 4 primary partitions. If you want to do a dual boot, you would have to remove one of them and replace it with an extended partition inside of which you can make logical partitions for the Ubuntu partitions.

---

### Post by ConCla on 2013-01-13
Such a rapid response!

It seems you got it in one. There are some 'bad sectors'. Which sounds ominous. The detailed assessment reads 'Good' or 'Not Applicable' for all variables except 'Reallocated Sector Count' and 'Current Pending Sector Count', which are both displaying warnings.

Fortunately, when I switched from my old computer to this one, I backed up all of my important files to an external hard drive. When I first started having problems I copied anything newly added that I couldn't afford to lose over to that drive as well. So I am well protected on that front, at least.

I am not particularly fussed about dual-booting at this stage (maybe once I've resolved these issues), or preserving anything saved locally since everything important is backed up externally. 

In other words, feel free to make suggestions that over-write/reset/otherwise nuke the drive if you feel it will help.

---

### Post by tlhIngan on 2013-01-13
Try reformating the drive.
Not a quick format, but a thorough format that will write zeros to the drive.
Sometimes bad sectors are just logical errors, and those get "fixed" by a thorough format.
It this doesn't fix it, it's physical damage, and I don't trust a drive after it gets it's first bad sector due to physical damage.
Time to upgrade, you may wish to consider an SSD rather than a spin-drive.

---

### Post by drawkcab on 2013-01-13
A couple things:

1.  You can use a utility called fsck to try to repair the drive.  It works wonders although someone more technically proficient will have to help you through the procedure.  If you drive is failing, however, fsck can't really do much.

2.  If you have another computer you can actually download install images of Windows 7 from microsoft's website.  See this wiki article:

[http://en.community.dell.com/support-forums/software-os/w/microsoft_os/3316.2-1-microsoft-windows-7-official-iso-download-links-digital-river.aspx]("Article")

This is to say if you have a valid key (these days you can usually find them located on a sticker somewhere on your computer) you can prepare an install disk and use your key to activate it.

3.  If your hdd has failed, you can get by via installing ubuntu to a 8gb+ usb device with a persistent install.  In fact you can probably do this with the live cd!  This will allow you to boot ubuntu from the usb and save your changes and data so that you are not without a computer while you wait for your new hdd to arrive!

Good luck with your troubles and, though it's misfortune which brings you to ubuntu, I'm glad that you have the opportunity to discover the usefulness of linux whether it be a livecd, persistent usb install or a complete conversion to ubuntu.

---

### Post by ConCla on 2013-01-13
Well, that did it. Ubuntu installed successfully, thank you kindly for your assistance, both of you!

Final question:

I formatted the drive with Disk Utility, but is that what you would call a "thorough" format? Or is there another method?

I guess if these bad sectors persist I'll have to look into a new HDD. Google informs me that bad sectors tend to multiply?

EDIT:

Just saw drawkcab's post, which pretty much addressed my last question.

Thanks again everyone!

---

### Post by drawkcab on 2013-01-13
In terms of managing the problem for now you can keep running fsck from a live cd as needed.

If your system is irrecoverable or you just want peace of mind, you can consider using another command line program called dd to zero out the drive (i.e. write all zeros across the drive) and then repartition and reinstall.  I was able to recover my ssd this way when I was having similar problems.

At any rate, be sure to constantly back up important data until you're reasonably sure your drive is stable.

---

