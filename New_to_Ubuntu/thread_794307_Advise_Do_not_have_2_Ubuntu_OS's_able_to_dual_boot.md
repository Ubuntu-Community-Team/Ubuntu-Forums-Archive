---
title: "Advise: Do not have 2 Ubuntu OS's able to dual boot."
date: 2008-05-14
forum: New to Ubuntu
---

### Post by Tex786 on 2008-05-14
Hi Everyone,

Well the last couple of days I was checking out xubuntu after I installed it from an ISO I put on CD.

If anyone is thinking about trying out the other kinds of Ubuntu with the existing install of Ubuntu you already have, think again! Today i reinstalled my primary Ubuntu partion after having  several problems.

After Installing Xubuntu the boot loader gave me like 5 things to boot. All but 2 of them were named ubuntu 8.04. I did not like that. If i am going to Dual boot I want ubuntu or xubuntu, not six other things in my bootloader.

After I wanted to get rid of Xubuntu (I did not care for it) I tryed to get rid of the partion witch I had xubuntu on. long story short my hard drive was not giving me the amount of space my regular ubuntu install had. I ended up just dumping everything on the harddrive.

So just stick to the Ubuntu install you already have.

Just wanted to contribute...

P.S. I do not have any sort of problem with my hardwre or OS.

---

### Post by Paqman on 2008-05-14
> **Tex786 said:**
> 
After Installing Xubuntu the boot loader gave me like 5 things to boot. All but 2 of them were named ubuntu 8.04. I did not like that. If i am going to Dual boot I want ubuntu or xubuntu, not six other things in my bootloader.

You can edit the list that shows up on Grub. It's located at /boot/grub/menu.lst, just comment out any lines you don't wat to see by putting # at the start

---

### Post by Tex786 on 2008-05-14
Thanks for the Info.

---

### Post by ch_123 on 2008-05-14
> **Tex786 said:**
> 
After I wanted to get rid of Xubuntu (I did not care for it) I tryed to get rid of the partion witch I had xubuntu on. long story short my hard drive was not giving me the amount of space my regular ubuntu install had. I ended up just dumping everything on the harddrive.

I'm not sure if I'm reading your problem correctly, but did you make sure to expand the old partition to cover the partition you just deleted?

---

### Post by Tex786 on 2008-05-14
> **ch_123 said:**
> I'm not sure if I'm reading your problem correctly, but did you make sure to expand the old partition to cover the partition you just deleted?

Yes I did.

Everything is fine now.

---

### Post by ntrgc89 on 2008-05-14
If you want to experiment with other display managers, you don't have to choose between them when you boot up, changing them is as simple as logging out.

When you install another interface like KDE or Xfce it's listed as an option under "session type" when you're at the login screen.

So there's no need to go through the hassle of setting up two partitions for ubuntu, it'll work on one!

---

### Post by Tex786 on 2008-05-14
> **ntrgc89 said:**
> If you want to experiment with other display managers, you don't have to choose between them when you boot up, changing them is as simple as logging out.

When you install another interface like KDE or Xfce it's listed as an option under "session type" when you're at the login screen.

So there's no need to go through the hassle of setting up two partitions for ubuntu, it'll work on one!

yeah i know but i was having package problems + I like to make things harder on myself lol..

I installed the xubuntu package and all but all i got from xubuntu was the login screen.

How do i fix that?

---

### Post by KOTAPAKA on 2008-05-14
I hate when unprepared guys try to give advice. As I can see you are not very knowledgeable using linux, are you? So you try to warn us about a possible mistake that you've done? Here are 2 thing you should have had in mind before posting:
1. It might be a mistake I did or I messed up something which other people will not mess up.
2. It might be my system or configuration that cause the problem - perhaps they were not set up correctly.
Did you think about those 2 things before posting or did you just think "Oh, it can't be my mistake - it must come from Ubuntu."? There is no logic in what you are saying and further more it is not true.

---

### Post by joel_gil on 2008-05-14
well i dont see the need of the sarcastic and/or offended people...

dont take it as a complaint of ubuntu or the community, i think he is just expressing is not as simple as he thought it would be.

it is true he should've researched about this a bit further, that way he would have realized that although is not as easy as point and click, it is possible, unlike on windows...

..aaaand... ubuntu still rules! ^.^

---

### Post by ch_123 on 2008-05-14
> **Tex786 said:**
> Everything is fine now.

I think you misunderstood me - I read that when you uninstalled Xubuntu that you had less space than normal. I was suggesting that this was because you didn't properly extend your original parition to cover the deleted space. If you did this, then sorry for misunderstanding you again :)

I agree to an extent with the sentiments of KOTAPAKA, Linux is a rather complicated thing, I have been using it for about 2 years and I wouldn't even pretend to know half of the things I need to. My rule of thumb is that if it doesnt work, I assume that it was something I did wrong until proven otherwise. I suggest that this be your motto too :) If you have problems with something new, then read up on it. If you posted your problems here they would have been solved very quickly. Undoing all your work then telling everybody that something cant be done because you dont know how to do it is somewhat stupid tbh.

---

### Post by lazyart on 2008-05-14
from ubuntu you should simply:```
sudo apt-get install xubuntu-desktop
```Then from the login screen change the session from gnome to xfce.  Tada, you're in xubuntu.  Save the dual booting for different OSes, such as linux & windows, or different distros, like Ubuntu and Fedora.

---

### Post by ace007 on 2008-05-14
This is a case of not enough knowledge/patience.  Please change the thread title or delete it.  Everything you had problems with is easily managed with a little searching.

---

### Post by KOTAPAKA on 2008-05-14
> **joel_gil said:**
> well i dont see the need of the sarcastic and/or offended people...

dont take it as a complaint of ubuntu or the community, i think he is just expressing is not as simple as he thought it would be.

it is true he should've researched about this a bit further, that way he would have realized that although is not as easy as point and click, it is possible, unlike on windows...

..aaaand... ubuntu still rules! ^.^

This is not true either. I've had them both when I was a newbie and didn't even know what ext3 was. Did I experience any problems? No. They ran smoothly. As I said this tread is misleading. If I was new to linux and I wanted to install those 2 on the same computer and I read this thread I might not do it. People should think what they write. It's just like a person who can't swim telling you that you will drawn if you try to swim. Is this true? Now - it might happen but generally it is not true.

---

