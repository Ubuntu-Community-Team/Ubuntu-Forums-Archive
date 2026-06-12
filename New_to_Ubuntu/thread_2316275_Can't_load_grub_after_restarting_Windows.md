---
title: "Can't load grub after restarting Windows"
date: 2016-03-06
forum: New to Ubuntu
---

### Post by cristobal.abarca95 on 2016-03-06
Hello
i've just made a dual boot with Windows 8.1 and Ubuntu 15.04. Grub loader works fine until i need to boot Windows for any reason. The problem comes when i want to change to Ubuntu, grub loader doesn't load and Windows starts loading. 
I've searched a lot for a answer. 
Hope you guys can help !

---

### Post by oldfred on 2016-03-06
What Brand  & model system.
Many Windows want to reset Windows to default boot in UEFI on updates in Windows.

Does Ubuntu still boot from one time boot key like f10 or f12.
And then what does this show as default boot or first in UEFI boot order?
sudo efibootmgr -v

---

### Post by cristobal.abarca95 on 2016-03-06
Oh thank you for the quick answer. I'm going to spend time looking for the answer in the forum!

---

