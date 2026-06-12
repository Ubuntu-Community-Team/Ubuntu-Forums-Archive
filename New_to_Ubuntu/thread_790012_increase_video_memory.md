---
title: "increase video memory"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by sharks on 2008-05-11
i have a system with 1gb ddr2 ram ,intel 915 mobo but no graphics card.the maximum video memory allocated in BIOS is 128MB.is there a way to increase video memory (ie)allocate a part from my ram.

---

### Post by thisiam on 2008-05-11
when you were in the BIOS, did you see any option to change it there?

---

### Post by sharks on 2008-05-11
maximum shown in the drop down list is 128mb

---

### Post by sharks on 2008-05-11
[http://www.anandtech.com/video/showdoc.aspx?i=2143&p=2](http://www.anandtech.com/video/showdoc.aspx?i=2143&p=2)
check this link,it shows a max memory of 224mb but i am getting a max of 128mb.should i update my bios.

---

### Post by thisiam on 2008-05-11
probably as much as you can give it then. using your ram i don't really see working, but i may be wrong on that. getting a video card would give you better results all around so thats a better choice than the onboard card.
updating the BIOS is worth a shot, always good to have it up to date aswell.
i just got [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814130341") and works great.

---

### Post by sdennie on 2008-05-11
Is there a specific reason you want to increase the amount of video RAM?  Every increase will take away from your main system RAM and, unless you are gaming, it's kind of a waste.

---

### Post by sharks on 2008-05-11
i just wanna know is there a way to do it.i'll be adding another gig of ram in a week or two.then it might be helpul

---

### Post by sdennie on 2008-05-11
The BIOS may be the limiting factor.  But, I wouldn't worry about it too much.  I don't have an intel gpu around at the moment, but, it used to be the case that the intel (i810) driver would choose a very conservative value for your video RAM (like 64M) unless you explicitly set it to a higher value in /etc/X11/xorg.conf.  For regular desktop usage (even with compiz) I'm not sure if it really makes much of difference how high you set that value.

---

### Post by cubeist on 2008-05-11
The bios is the only place to allocate ram for an onboard card.  But 128 should be fine... I just went in to my bios last week and downgraded from 256mb to 128mb and did not see any difference in games.  In fact I gained some advantage in graphics processing because now the system has (slightly) more memory.

---

### Post by daengbo on 2008-05-11
The Intel driver can re-allocate RAM, but it doesn't really matter since it's all shared anyway. If you're using Hardy with no xorg.conf, it will allocate as much as it thinks you need.

---

### Post by sharks on 2008-05-11
is there a way to increase it using xorg

---

