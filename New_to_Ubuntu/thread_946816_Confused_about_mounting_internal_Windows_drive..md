---
title: "Confused about mounting internal Windows drive."
date: 2008-10-13
forum: New to Ubuntu
---

### Post by RedMartin on 2008-10-13
Our desktop PC has one drive with XP on it and another with 8.04 64-bit.

My partner has been getting to grips with Ubuntu and is now moving across all of her personal files, pictures etc.

She was doing this by clicking on the 160gb volume that is the old XP drive. Inititally Ubuntu asked for the su password but has now stopped. In fact, it appears that Ubuntu now mounts the drive automatically.

Is this supposed to happen? If so, and indeed, if not, then how do we get it back to asking for the password before mounting the XP drive?

Many thanks.

---

### Post by jbrown96 on 2008-10-13
It's up to the administrator (you, I suppose) whether your partner should have access. You can change the permissions by doing two things. Go to System-->Administration-->Users and Groups. Select your partner's account and go to properties, go to the second tab. There are two options which need to be disabled: Automatically mount external storage (will prompt for password when mounting) and administer the system (so he/she can't reenable automatic mounting). There's no reason to do this unless he/she shouldn't have access.

---

### Post by RedMartin on 2008-10-13
She doesn't have an account of her own. She basically inherited my old set-up when I got a new laptop. She is the administrator in effect.

It's not really a question of her not being allowed access, more a case of why isn't she baing asked for the password any longer and is the reason for this any cause for concern?

---

### Post by jbrown96 on 2008-10-13
Check the permissions that I put in my last post. Is automatically mount external devices checked? There could be another cause as well. I know that when I have Windows on another partition (NTFS) and I try to mount it, it asks for my password. Does the computer think that the drive is internal? Try booting with and without the drive connected; that may make a difference on what Ubuntu thinks it is. The ownership of the drive might have also changed.

---

### Post by gandaran on 2008-10-13
the password is only asked the first time you access a windows drive, if you want to change permissions do it in system » administration » permissions

---

### Post by RedMartin on 2008-10-13
> **jbrown96 said:**
> Check the permissions that I put in my last post. Is automatically mount external devices checked? There could be another cause as well. I know that when I have Windows on another partition (NTFS) and I try to mount it, it asks for my password. Does the computer think that the drive is internal? Try booting with and without the drive connected; that may make a difference on what Ubuntu thinks it is. The ownership of the drive might have also changed.

We've checked the permissions and automatically mount ext drives WAS/IS checked. However, the drive itself is an internal drive.

Is this anything to do with automount? I was hoping that Ubuntu had kind of thought that as the drive is used a lot it'd just leave it easily accessible.

---

### Post by RedMartin on 2008-10-13
> **gandaran said:**
> the password is only asked the first time you access a windows drive, if you want to change permissions do it in system » administration » permissions

Hmm.. is that the first time ever or the first time each time you use the PC?

---

### Post by gandaran on 2008-10-13
first time ever, thats how it works in my computer and another friends computer I installed ubuntu

---

### Post by RedMartin on 2008-10-13
> **gandaran said:**
> first time ever, thats how it works in my computer and another friends computer I installed ubuntu

According to my partner she is convinced that she was asked for the password many times.

---

### Post by gandaran on 2008-10-13
> **RedMartin said:**
> According to my partner she is convinced that she was asked for the password many times.

then I just don't know why it's deferent!

---

### Post by RedMartin on 2008-10-13
Solved it. 

In authorizations / storage / mount file systems from internal drives the explicit section had the su listed. I revoked it and now get asked for the password when mounting. It appears that she ticked the always remember type option.

Simple solutions. Why do they always get overlooked?

---

