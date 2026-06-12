---
title: "Changes made as su in terminal gone after reboot"
date: 2015-12-06
forum: New to Ubuntu
---

### Post by tud17750 on 2015-12-06
I just installed ubuntu 14.04 and had problems getting the ethernet, and the backlight on my keyboard to work.  I can fix the ethernet by entering
```
modprobe alx
echo 1969 e0a1 > /sys/bus/pci/drivers/alx/new_id
```

and I can get the backlight working with
```
sudo xmodmap -e 'add mod3 = Scroll_Lock'
```

both while logged in as the super user, or with sudo, but when i restart my computer the changes are lost, and I need to reenter them.  Any ideas on how to make them permanent?  Thanks.

---

### Post by egeezer on 2015-12-06
Add them to Settings > Session > Autostart

---

### Post by jeremy31 on 2015-12-07
There is a better way to get the ethernet working.  I can make a dkms module that will provide support for your card.  Post the result of ```
lspci -nnk | grep -iA2 net; uname -a
```

---

