---
title: "New install questions."
date: 2014-10-14
forum: New to Ubuntu
---

### Post by OpenFerret on 2014-10-14
Hi all,
I've got a Dell XPS 13 (9333) that I'm looking to install Kubuntu / Xubuntu on.  I have a few questions before I begin my install.


1.     UEFI or not?  I don't intend to dual boot at all and this will be a  Linux only system.  Does installing with UEFI incur any distinct  advantages or is it more secure?  

2.    If UEFI  is a yes... Secure Boot or not?  If I leave secure boot enabled in the  BIOS will the system  actually run with secure boot functionality, or am I better with it off?

3.     To TRIM or not to-TRIM?  I intend to use LUKS encryption to protect  my SSD, which will be separated into a swap partition of 12GB (1.5 x RAM  - for hibernation / suspend to disk) and the remainder will be the root  partition.  I'm aware that TRIM will potentially allow an attacker to  see what parts of the disk are in use, but I'm not expecting any attacks  from a sophisticated attacker.  Does not using TRIM incur any serious  disadvantages to me?
4.    Has anyone used / got to work a  TPM-LUKS combination?  That is, stored LUKS keys in the TPM using  something like trousers or tpm-luks from GitHub?  If they have, can any  advice be given on its set-up?

Many thanks for your time all!  Apologies for all of the questions.

---

### Post by Vladlenin5000 on 2014-10-14
1. Ubuntu should be fine with or without EFI. It has no advantage I'm aware of, *at the moment* and definitely isn't more secure. That's just marketing. UEFI is about control, not security.

2. Currently you don't need to disable secure boot. Again, nothing particularly secure about "secure boot".

3. TRIM triggered by a weekly cron job should be enough and is the Ubuntu's default.

4. No, and I don't see the point of dealing with the TPM but leave this as an open question and wait for other opinions.

---

### Post by OpenFerret on 2014-10-14
Loving the Hitch avatar my friend!!!

Thanks for the reply.  I will wait and see about Question 4.

---

