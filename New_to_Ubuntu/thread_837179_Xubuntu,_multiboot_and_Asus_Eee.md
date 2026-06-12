---
title: "Xubuntu, multiboot and Asus Eee"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by Mylorharbour on 2008-06-22
I have a multiboot setup running quite happily on my PC (WinXP, Kubuntu, Gutsy and Hardy) but wanted to test Xubuntu as this may be an alternative OS for my daughter's Asus Eee PC 900, which currently runs an Asus version of Zandros. When trying to add Xubuntu Hardy to the PC setup the installer fails at the 'Configuring boot loader' stage. The installer window just closes. The system still boots up ok as normal so the Grub bootup is unaffected. 

Can I assume Xubuntu is only usable where it's the only OS on the system or do you guys have another explanation?

By way of a bit of background for you, the Asus works well with it's installed apps, it's just that the repository doesn't have any additional games and she can't download Evolution nor Komposer. In fact the only apps in the repository are those that come pre-loaded. It's early days for the Eee 900 but the feeling on their forums is that you have to jump through hoops to get apps not in the Asus repository, that such apps can break the system and that Xubuntu may be the way to go. So few have tried it yet and they don't seem to be sure that the 'reset factory settings' getout key combination would still work after Xubuntu had done it's thing.

---

### Post by Mylorharbour on 2008-06-22
Bump

---

### Post by atomkarinca on 2008-06-22
You can try [Ubuntu Eee]("http://www.ubuntu-eee.com/index.php5?title=Get_Ubuntu_Eee"). 1 gb of ram should be more than enough.

---

### Post by CrimsonEclipse on 2008-06-27
Has anyone successfully installed it on a 2G?

CE

---

### Post by snowpine on 2008-06-27
Check out the forums at eeeuser.com; they have a lot of info on how to get different distros working on the eee. There's even a distro called eeeXubuntu that is Xubuntu optimized for the eee.

To answer the original question, no, Xubuntu will work just fine as a dual (or triple, etc) boot. I speak from experience. Perhaps it is just a problem with that particular disk? 

You can also add Xubuntu to an existing Ubuntu (or Kubuntu) install by using 'sudo aptitude install xubuntu-desktop'. Then, you can choose Xfce from the Sessions menu at login. The problem with this is you'll get a lot of apps that duplicate the functions of your existing Ubuntu apps.

Good luck!

---

### Post by kansasnoob on 2008-06-27
This is probably a foolish question so don't throw stones, eh?

Do you know that you can only have four primary partitions on a hard drive?

Like I said it's foolish and maybe downright stupid, but I had to ask):P

---

### Post by SuperStuff on 2008-06-27
> **kansasnoob said:**
> This is probably a foolish question so don't throw stones, eh?

Do you know that you can only have four primary partitions on a hard drive?

Like I said it's foolish and maybe downright stupid, but I had to ask):P

Is that true? I did not know that. Thanks for the tip.

---

### Post by kansasnoob on 2008-06-27
> **SuperStuff said:**
> Is that true? I did not know that. Thanks for the tip.

Yes, thank goodness for the Virtual Boot option!

---

