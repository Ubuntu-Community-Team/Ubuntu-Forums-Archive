---
title: "Of nautilus and files!!!"
date: 2013-10-31
forum: New to Ubuntu
---

### Post by Luc_Lacombe on 2013-10-31
Hello

When I try to move a folder and/or files from one folder to another one , it pops"Error moving file permission denied".
I know perfectly  it's about security.
But I want to have _full... absolute...undeniable control_ of my folders/files activity as I'm the only one on this computer.
How can In set FULL permissions everywhere and everytimes for everybody even if I'm the only one on this computer?
I feel claustrophobic when this happens!!![IMG]http://ubuntuforums.org/images/icons/icon11.png[/IMG]

Thanks

Luc

---

### Post by merlyn2748 on 2013-10-31
You should have FULL permissions for the files in your home folder /home/*username*.  What are you trying to change that is outside there?  Most often there really is no reason for you to make changes outside of that folder, since 99% of your personal settings and customizations are stored in hidden folders in your home directory.  Changing FULL permissions for files outside your home folder runs a serious risk of damaging the OS and making your machine unusable.  Most programs and services run themselves under their own usernames and if this is changed things like printing etc may stop working.  This is also the reason their are practically no viruses for Linux/Unix systems.

Let me know
Justin

---

### Post by Dennis N on 2013-10-31
To have a stable system, your personal files should remain within your home folder. And there, you have the control you seek. Linux has a carefully thought out design that you don't want to mess with. Otherwise, sooner or later, you would have an unstable, unusable system.

---

### Post by Impavidus on 2013-10-31
You already have full, absolute, undeniable control over your files. Just use sudo. It gives you more control than using some better known operating systems. However, keep in mind that if you use sudo when you are sleepy, drunk or confused* you'll probably break your system. The security system also protects you from yourself.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

* I don't know whether you're ever drunk, but most people sometimes are sleepy or confused.

---

### Post by merlyn2748 on 2013-10-31
> **Impavidus said:**
> You already have full, absolute, undeniable control over your files. Just use sudo. It gives you more control than using some better known operating systems. However, keep in mind that if you use sudo when you are sleepy, drunk or confused* you'll probably break your system. The security system also protects you from yourself.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

* I don't know whether you're ever drunk, but most people sometimes are sleepy or confused.

I completely agree with this.  If you are newer to Ubuntu and Linux in general please, please do your research before you start trying to change things outside of your home folder.  But as Impavidus said if you truly need to make changes sudo has you covered.

---

### Post by coffeecat on 2013-10-31
> **Luc_Lacombe said:**
> But I want to have _full... absolute...undeniable control_ of my folders/files activity as I'm the only one on this computer.
How can In set FULL permissions everywhere and everytimes for everybody even if I'm the only one on this computer?

There is a simple command that will give you full permission everywhere and always for everybody. Why am I not telling it to you? It's because it will break your system totally, utterly and irrevocably. With monotonous regularity, people who have run this command start threads asking how they can repair their system. The answer is always the same: you can't. Reinstall.

As others have said, you have permission to move stuff around within your home folder. Outside of your home folder are system files which you should leave alone unless you know what you are doing.

---

### Post by ajgreeny on 2013-10-31
There you are; you have seen all the warnings which I fully agree with!

Now to try to be more helpful.

Please tell me what you are trying to move and from where to where.  This may give us all some way to figure out if there is a good reason for not being able to move the folders/files.

---

### Post by Luc_Lacombe on 2013-10-31
Hello you all

Thanks for helping me.
Ok Guys...I understand your point! Legit arguments.
What caused this...
I recently installed Variety, a background pictures manager.
And I tried to copy personnal pictures to a folder in : /File System/USR/share/backgrounds.
So I decided to put these pictures in /Home/Pictures instead.
Everything's fine right now.
Thanks very much!

Luc Lacombe

---

