---
title: "Encrypted C-drive in Windows (with Veracrypt) and Installing Ubuntu"
date: 2023-07-26
forum: New to Ubuntu
---

### Post by h9c34-et on 2023-07-26
Hi all,

I am seriously considering leaving Windows once and for all and starting up with Linux through Ubuntu. While I explore Ubuntu to decide whether it's the right choice, I want to encrypt my C-drive. I know that if I choose to install Ubuntu alongside Windows I will need to disable Bitlocker encryption before Ubuntu installation. I am wondering whether the same is true of Veracrypt if I choose to implement system encryption with it instead of Bitlocker. Has anyone had experience with this?

Thanks!

---

### Post by aljames2 on 2023-07-26
> **h9c34-et said:**
> Hi all,

I am seriously considering leaving Windows once and for all and starting up with Linux through Ubuntu.

Good move!  and welcome!

Regarding encrypting your Windows, I am not familiar with Windows encryption methods.  However, have you considered just installing Ubuntu desktop in a Virtualbox VM.  A great way to use any flavour you like, for as long as you want.  Your OS doesn’t have to live on bare metal thanks to virtualization.

---

### Post by MAFoElffen on 2023-07-26
I am confused. 

You can have both OS'es encryted, but it comes a lot of manual work to do, which you posted in the "New To Ubuntu" section... So, first, a warning. There is no automated solution to doing it = lots of typing ad manual work, with some skills to back that up with. Have very good backups.

RE: [https://www.mikekasberg.com/blog/2020/04/08/dual-boot-ubuntu-and-windows-with-encryption.html](https://www.mikekasberg.com/blog/2020/04/08/dual-boot-ubuntu-and-windows-with-encryption.html)

I have some recipes for this, but I am hesitant to share them with someone I know is new, as they are not experience with problems that may come up, and you would need to understand what is being done / when, or risk wiping your system. This recipe is much more detailed and much more than you would need for the Ubuntu Side...
RE: [https://ubuntuforums.org/showthread.php?t=2488075&p=14148569#post14148569](https://ubuntuforums.org/showthread.php?t=2488075&p=14148569#post14148569)

My confusion above come from your opening statement, where you said you were leaving Windows... If you were leaving Widows, and goig full bored with Ubuntu, the why would keeping Windows, and bit-locker be a factor at all? I do dual-boot's and some crazily complex configurations of both Linux, and Windows systems...

My dual-boot consideration for myself is being on physical hardware. But my considerations for those have been less and less as time passes. Having said that, since you have already said your plans are to leave Windows... If you installed Windows as a VM, on KVM as a VM Guest, and your Linux system was encrypted, then everything in your Windows VM would be encrypted within that already, without having to worry about anything further. Right?

---

### Post by Quarkrad on 2023-07-28
One option you could consider is to:

a) Backup everything you current have in your Windows environment in terms of personal data/important to you
b) Start with a fresh install of ubuntu with the installation encrypted hard disk option (linux does not have lettered drive name like 'c drive' or 'd drive' - but thats another matter).  This will give you your encrypted hard disk with the ubuntu OS installed on it
c) Create a virtual machine within ubuntu and run Windows in it.  (The fact that the whole disk in encrypted mean both ubuntu and Windows are encrypted).

I think this will cover your needs.

As MAFoElffen says, there are other options such as dual booting but, as he points out,  with individual OS encryption things will get difficult to set up.  If you go the 'Windows in a vm' route via. an encrypted HD, there are many people on this site that can help you.

---

