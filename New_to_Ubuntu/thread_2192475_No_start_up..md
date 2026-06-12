---
title: "No start up."
date: 2013-12-08
forum: New to Ubuntu
---

### Post by harmony2 on 2013-12-08
I inserted the disc and clicked boot up with disc in tray.

Nothing happened.

Max

---

### Post by claracc on 2013-12-08
In order to get help, you have to add information about your hardware and give explanations about what do you want to do: See [https://help.ubuntu.com/community/GettingAnswers](https://help.ubuntu.com/community/GettingAnswers)

What ubuntu do you want to try?, what way have you burnt the iso you want to run?, what are your hardware specifications?, is it a live CD what you are trying?, is it your bios ready to boot from CD ?

---

### Post by harmony2 on 2013-12-08
I bought a CD from Ubuntu.

I put it into the laptop and I've tried all of the options - it's telling me that I have to uninstall, but there is noting loaded.

I have an acer laptop with a 25 Gb SSD

Very disappointing.

---

### Post by claracc on 2013-12-08
Here, [https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD) you have information about the problems you can encounter to boot ubuntu from CD, read it carefully and try the fixes propossed

---

### Post by harmony2 on 2013-12-08
I've tried everything I can read here, but Ubuntu won't load.

I'm going to have to format the drive and reinstall Windows 7 Ultimate.

I was warned not to mess with this stuff,  Serves me right.

Thanks, anyway.

Max

---

### Post by claracc on 2013-12-08
I think your ptoblem is in your win 7 ultimate OS, it has a secure booting named UEFI that I think you had to disable in order to boot from live ubuntu CD. 

This link can give you a real idea of the problem:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by harmony2 on 2013-12-08
Thanks all the same.

Don't waste any more time on me.

Max

---

### Post by claracc on 2013-12-08
You are welcome. Not a waste of time for me.

---

### Post by harmony2 on 2013-12-08
I can't get to the BIOS as the partial Ubuntu install is blocking me.

Tried a System Restore - no good.

Looks like formatting the SSD is the only answer.

---

### Post by kulen19 on 2013-12-09
> **harmony2 said:**
> I can't get to the BIOS as the partial Ubuntu install is blocking me.

Tried a System Restore - no good.

Looks like formatting the SSD is the only answer.

I don't think Ubuntu will restrict you from entering the BIOS. Different mother board manufacturers have different methods of accessing the BIOS(it can be F1, F2, F8, F12, Delete etc. Google(or DuckDuckGo :)) your mother boards name, along with "enter bios" and you should find it quick enough.

As for your initial problem, I can't really understand what went wrong. Try to be as specific as possible when asking a question, i.e. 
1) First i entered BIOS and set the boot order correctly.
2) Then the welcome screen from Ubuntu showed up
3) I then choose "try Ubuntu"(or something similar) to ensure that this is was I wanted(you should always do this, so ensure everything works as it should)
4) Then I rebooted and installed Ubuntu ...
    4.1 On a HDD with Windows already installed, and therefore overwriting the windows files.
    4.2 On the same HDD as Windows installed, but on a different partition(not overwriting the Windows files.)
    4.3 On a separate HDD.

How much of this did you do, before you encountered the problem?

Best of luck.

---

### Post by buzzingrobot on 2013-12-09
> **harmony2 said:**
> I can't get to the BIOS as the partial Ubuntu install is blocking me.



Ubuntu, or Windows, or any other operating system, will not block access to the BIOS.  The BIOS is embedded in hardware and runs before the OS loads.  Different machines use different BIOSes from different vendors, and each has a different way of enabling access to the BIOS configuration screen during bootup.  Typically, this access is accomplished with a specific keystroke.

If you have a newer UEFI machine with Microsoft's "Secure Boot" enabled, then you need to follow guidance specific to that hardware. 

We really need more specific information.  You imply that the Ubuntu image did not boot, which strongly suggests that either the image is bad or that the BIOS is not configured to boot first from that device.  But, you also mention a "partial Ubuntu install", which is impossible if the installation image didn't boot.

[The OP says the install CD was "bought" from Canonical.  If so, only 12.04 desktop and server and 12.10 server are available st the online store.]

---

### Post by codenine75a on 2013-12-09
> **harmony2 said:**
> I can't get to the BIOS as the partial Ubuntu install is blocking me.

Tried a System Restore - no good.

Looks like formatting the SSD is the only answer.

Buzzz!  Not the right answer.  It should be one of the function buttons or the ESC key or DEL.  Don't worry.  I used to frantically tap them not knowing which one gets me into BIOS because I did not have a manual available.  Oh harmony2, I assume you are trying to install Ubuntu on an internet laptop (what do they call them?) An internet only computer.  Ok it is called a chromeOS laptop I guess.  I makes sense with a 25gb SSD

---

### Post by harmony2 on 2013-12-11
OK.  So I took the laptop back to the technician who installed the SSD.

We completely wiped the drive and inserted the CD.

It got to the screen where I insert my name and stopped.

It will run off the CD, but it won't install it to the drive.

I've left it with him.

Max

---

### Post by harmony2 on 2013-12-11
I just had a text.  You MUST enter a password.

No message.  No warning.  It just stops.

Max

---

### Post by kulen19 on 2013-12-11
Ok, so the installation progress went fine. When you try to boot up Ubuntu, you get some indication that Ubuntu has started(a logo or something), and then you are prompted for a password. Is this right, so far?  This sounds pretty normal to me. Do you see the username you chose when you installed Ubuntu? What happens when you enter the password you made when installing Ubuntu? Can you take a picture of the screen causing you trouble?

---

### Post by buzzingrobot on 2013-12-11
> **harmony2 said:**
> I just had a text.  You MUST enter a password.

No message.  No warning.  It just stops.

Max

What's requesting a password? Perhaps the BIOS is password protected.

---

### Post by harmony2 on 2013-12-11
There is no trouble now.  It stopped halfway through the installation process and wouldn't go on until we agreed to use a password.

Once the password was selected, the installation process proceeded to the end.

Other users on other forums have complained to me that Ubuntu will not allow a non-password protected log in.

That will be annoying, given the number of re-starts I will be doing.

For the time being I will use the password nn to save time.

Cheers
Max

---

### Post by buzzingrobot on 2013-12-11
Creation of a password during installation is, in my experience, universal in Linux. Ditto Windows and OS X.  What you saw was the installer functioning normally, not throwing an error.

At that point in the install, you should have been able to opt for automatic login.  This eliminates the need to log in unless you manually log out.

User passwords are mandatory in the Unix multi-user configuration that Linux has adopted.  This allows multiple users to use a single system simultaneously.  Users are assigned certain rights to certain files and directories, and not others.  Arguably, few Linux systems are multi-user these days. But, passwords remain central to its security, and only a complete redesign of the OS and its security architecture would change that.

---

### Post by harmony2 on 2013-12-11
Aahh!  Automatic login.  That's the ticket!

Thank you.   :cool:

---

### Post by harmony2 on 2013-12-13
Thanks to you guys for your patience.

It's a neat little system.  Now to try something really tricky.

Downloading software - Railroad & Co from freiwald.com

No doubt I'll be back.

Thanks again
Max

---

