---
title: "Where can I find &quot;pam.unix.so&quot;"
date: 2011-10-27
forum: New to Ubuntu
---

### Post by imckinley on 2011-10-27
I am trying to install mcafee v1.7 on ubuntu 11.10 64 bit. The first step is to copy the file pam.unix.so into the temporary folder. I cannot find this file. I have tried the command dpkg -s pam.unix.so in terminal and it says "pam.unix.so is not installed and info is unavailable". Help! I'm brand new to ubuntu...

---

### Post by Mustard on 2011-10-27
My first question would be why are you trying to install McAfee on Ubuntu?

Firstly I have never heard of such a thing.  If you wanted virus detection on linux I would think Clamav would be the best option.

Secondly, where are you getting your information on installing McAfee on Ubuntu?

Do you realise that windows viruses don't work on Linux?  I have never found a need for virus detection on Linux in the 6 years I have been using Linux.

---

### Post by Rubi1200 on 2011-10-27
Hi and welcome to the forums imckinley :)

As Mustard asked and pointed out, why do you think you need an antivirus program for Ubuntu?

If you explain your needs, we can offer a more comprehensive answer.

Thanks.

---

### Post by egalvan on 2011-10-27
> **Mustard said:**
> 

Do you realise that windows viruses don't work on Linux?  I have never found a need for virus detection on Linux in the 6 years I have been using Linux.

It may not be the OP's reason to install anti-virus on Linux,
but MY reason is to clean infected MS Windows machines,
or more exactly, their hard drives and memory cards.

Since, as you state, Windows virii don't run on Linux, I don't have to worry about my washing machine getting infected.. :D

(my "washing machine" is a ThinkPad T60P for the road, and 
an HP desktop for the lab in my workshop.
they each have multiple I/O adapters to allow just about ANY drive/card to be connected)


In regular situations, It works when accessing email, or accessing a flash drive off a camera or other computer.
 It helps ensure that any Windows baddies will NOT propagate  beyond the Linux user's machine.
One more way that Linux users can make the world better and safer for our Windows Brothers :lolflag:

---

### Post by imckinley on 2011-10-27
> **Rubi1200 said:**
> Hi and welcome to the forums imckinley :)

As Mustard asked and pointed out, why do you think you need an antivirus program for Ubuntu?

If you explain your needs, we can offer a more comprehensive answer.

Thanks.
First of all, thanks for the replies...
 
The version of mcafee I was trying to install was specifically made for Linux. I figured if they make antivirus software for this OS then there must be *some* sort of threat.. maybe just paranoid. 
 
I am getting the information on how to install it directly from a .txt file that comes with the software. The first step is to put the specified file into /temporary, only I'm not sure if this file exists on 64-bit ubuntu 11.10; this step is not needed for the 32-bit version.
 
Perhaps I should just use clamav, as mustard suggested.

---

### Post by imckinley on 2011-10-28
bump

---

### Post by decoherence on 2011-10-28
Antivirus for linux generally scans for Windows viruses and is used for the reasons egalvan stated. To prevent infected files on your Linux machine from getting to a Windows machine where they can do damage.

Is it really asking for pam.unix.so or does it want pam_unix.so? On my system this file lives in /lib/security/pam_unix.so but I don't use Ubuntu so I can't promise it's in the same place for you.

If Ubuntu still includes the locate command, you could type 'locate pam_unix.so' in to the terminal to see where it is.

---

### Post by imckinley on 2011-10-28
Thank you very much, decoherence. First of all, you were correct; I was looking for pam_unix.so. Secondly, the locate command worked perfectly. In 64 bit ubuntu 11.10, pam_unix.so is located in "/lib/x86_64-linux-gnu/security".

---

### Post by atomicslave on 2012-02-29
Hi just wondering if you got this working, I have mine all installed but the password I set doesnt work even when i change it and try again, are there permissions that need to be changed?

---

