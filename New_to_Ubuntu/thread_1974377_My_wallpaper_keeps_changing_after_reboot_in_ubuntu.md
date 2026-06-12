---
title: "My wallpaper keeps changing after reboot in ubuntu 12.04"
date: 2012-05-06
forum: New to Ubuntu
---

### Post by soumoks on 2012-05-06
i added a custom wallpaper by right clickin and using the change desktop background option but after reboot i only find a black wallpaper..,thats not the only thing,the custom wallpaper does not even appear in the lightDM,what do i do about it?

---

### Post by Perfect Storm on 2012-05-06
Is the wallpaper on an external HDD or another partition?

---

### Post by soumoks on 2012-05-06
> **Artificial Intelligence said:**
> Is the wallpaper on an external HDD or another partition?its on an another partition,is that the problem?

---

### Post by Perfect Storm on 2012-05-06
> **soumoks said:**
> its on an another partition,is that the problem?

It's an observation I made that wallpapers used from external or custom partition doesn't load properly.

Solution move your wallpaper(s) to your hone directory or copy them into /usr/share/backgrounds

---

### Post by Shadius on 2012-05-06
> **soumoks said:**
> its on an another partition,is that the problem?

I think it has to do with the path of the file. The wallpapers are in /usr/share/backgrounds so maybe if you move it in there...? Sorry for the limited answer, hope it helps.

---

### Post by soumoks on 2012-05-09
> **Shadius said:**
> I think it has to do with the path of the file. The wallpapers are in /usr/share/backgrounds so maybe if you move it in there...? Sorry for the limited answer, hope it helps.thanks bro helped a lot..:)

---

### Post by Shadius on 2012-05-09
> **soumoks said:**
> thanks bro helped a lot..:)

Glad to help. :)

---

