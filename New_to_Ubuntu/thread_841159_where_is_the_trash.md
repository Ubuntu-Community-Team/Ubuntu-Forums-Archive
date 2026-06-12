---
title: "where is the trash?"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by cencorot_91 on 2008-06-26
hello,
im using ubuntu 8.04 with lxde coz gnome is to slow for my PC. But when i delete a file, i dont know where it goes. Can anybody tell me?

---

### Post by Nepherte on 2008-06-26
The trash bin in Hardy Heron is located in ~/.local/share/Trash (files/)

If you remove something as root, I believe it's gone forever.

---

### Post by iaculallad on 2008-06-26
> **cencorot_91 said:**
> hello,
im using ubuntu 8.04 with lxde coz gnome is to slow for my PC. But when i delete a file, i dont know where it goes. Can anybody tell me?

Look in: 

User's Trash:
> /home/your_user_name/.local/share/Trash

or

Root:
> ~/.local/share/Trash/files

---

### Post by Elfy on 2008-06-26
> If you remove something as root, I believe it's gone forever.
If you remove something using rm in the terminal it's likely gone - regardless of whether you are root or not.

---

### Post by Nepherte on 2008-06-26
Just as I thought. I never bothered to check it since I don't delete anything vital anyways :p

---

### Post by Elfy on 2008-06-26
> **Nepherte said:**
> Just as I thought. I never bothered to check it since I don't delete anything vital anyways :p

Always best :lol:

---

### Post by PCMan on 2008-06-26
> **cencorot_91 said:**
> hello,
im using ubuntu 8.04 with lxde coz gnome is to slow for my PC. But when i delete a file, i dont know where it goes. Can anybody tell me?
It goes no where. If you delete a file, it's deleted. In the next major release, we'll try to support trash.

---

### Post by cencorot_91 on 2008-06-28
> **PCMan said:**
> It goes no where. If you delete a file, it's deleted. In the next major release, we'll try to support trash.

thanx for that. :)
i think you've solve my problem...

---

