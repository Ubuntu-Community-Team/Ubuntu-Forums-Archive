---
title: "Chrubutu root password recovery options?"
date: 2013-05-18
forum: New to Ubuntu
---

### Post by Scrufdog on 2013-05-18
So, my kid forgot his password on his C7 with Chrubuntu 12.04 on it. Since there is no grub for recovery, and I can't get a usb drive to boot, what options do I have to recover his password?

---

### Post by Redmouse on 2013-05-29
Please clarify. Did your son forget the password to the root account? If so.... I must ask, why let a kid do anything(including serious harm) to your/his computer with accsess to the root account? I'm not much help, sorry, but I don't think there are any more options...
Edit:([http://ubuntuforums.org/showthread.php?t=2098507](http://ubuntuforums.org/showthread.php?t=2098507))

---

### Post by Scrufdog on 2013-06-01
> **Redmouse said:**
> Please clarify. Did your son forget the password to the root account? If so.... I must ask, why let a kid do anything(including serious harm) to your/his computer with accsess to the root account? I'm not much help, sorry, but I don't think there are any more options...
Edit:([http://ubuntuforums.org/showthread.php?t=2098507](http://ubuntuforums.org/showthread.php?t=2098507))

He is 14 and wants to learn about linux, and wants to learn personal responsibility. I spoke with him and about before I gave him the laptop and he assured me it wouldnt be a problem, and that he would consult with me before doing anything to change the laptop.

I recovered it by removing the hard drive and editting the shadow file with BT5r3.

---

### Post by MG&amp;TL on 2013-06-01
> **Scrufdog said:**
> He is 14 and wants to learn about linux, and wants to learn personal responsibility. I spoke with him and about before I gave him the laptop and he assured me it wouldnt be a problem, and that he would consult with me before doing anything to change the laptop.

I recovered it by removing the hard drive and editting the shadow file with BT5r3.

For future reference, if Chrubuntu is the same as other *buntus, you can recover a password (root or otherwise) using this method: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by oldrocker99 on 2013-06-05
Unfortunately, at present, Chrubuntu does not use GRUB; as an experienced user but someone who remains a bit mystified about how the beastie actually boots, I would (in your situation) try backing up what you can, and do a fresh installation (putting ChromeOS back on, etc). The Chrubuntu installation script now allows 13.04 to be installed, for what it's worth.

---

