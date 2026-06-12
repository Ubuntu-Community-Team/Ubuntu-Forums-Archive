---
title: "Problem with &#273;elete"
date: 2018-07-29
forum: New to Ubuntu
---

### Post by winterswan127 on 2018-07-29
Hello,

Very new to Linux, so I'd need an explanation step-by-step, preferably a safe solution as well :razz:.

Basically, this is the problem:

Installed Ubuntu on both laptop and desktop. On laptop it works fine,  can delete everything and when I right-click a file, I can check 'Run as  program' and such. Something I needed to do when following certain  instructions to install f.e. Netbeans.
On the laptop it's installed on a singular SSD, with nothing else on it.

On desktop, I can't do the things above, even though there is only 1  account, which is the administrator (= same as root, right?).  Desktop-Ubuntu is a dualboot with Windows 10. Windows installed on a  SSD, Ubuntu on a seperate HDD (which is used by Windows to install  programs that don't need to fill up the SSD).

More details:
-Never had another account on (n?)either laptop or desktop.
-Both are fresh installs (laptop few days ago, desktop today).
-Both installs from exact same physical USB-install, no installer-software changes at all.

I googled some solutions, and figured out it probaly has something to do  with permissions. But the solutions were different and overall too  confusing for me as a new user.


Hope you can help!

---

### Post by #&amp;thj^% on 2018-07-29
This would be the problem 
> Desktop-Ubuntu is a dualboot with Windows 10. Windows installed on a SSD, Ubuntu on a seperate HDD (which is used by Windows to install programs that don't need to fill up the SSD).
Windows is taking over the permissions sounds to me.
Check if  fast startup is causing your problems: [https://askubuntu.com/questions/917695/read-only-partition-dual-boot-win10](https://askubuntu.com/questions/917695/read-only-partition-dual-boot-win10)

---

### Post by monkeybrain20122 on 2018-07-29
> **winterswan127 said:**
> Hello,


On desktop, I can't do the things above, even though there is only 1  account, which is the administrator (= same as root, right?).  Desktop-Ubuntu is a dualboot with Windows 10. Windows installed on a  SSD, Ubuntu on a seperate HDD (which is used by Windows to install  programs that don't need to fill up the SSD).


You don't need sudo to do these things. How do you format your second hard drive? I am asking because Windows cannot see anything other than ntfs while Ubuntu should be installed in a Linux file system. Did you partition your hdd into separate ntfs and ext4 partitions?? Also I think the whole idea of having two drives is to keep the OSes separate to avoid problems arising from usual dualboot setups (I could be wrong about this since I have no use for Windows) So better keep Windows to itself instead of reaching out into Ubuntu's drive.

---

