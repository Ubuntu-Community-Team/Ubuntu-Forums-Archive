---
title: "Cannot seem to be able to adjust brightness on Lubuntu"
date: 2014-08-10
forum: New to Ubuntu
---

### Post by babyblue on 2014-08-10
I have just installed Lubuntu 14.04.1 on my Acer Aspire 5733 series and I cannot seem to be able to adjust my brightness. It's stuck on maximum brightness and it's hurting my eyes quite a bit. The Fn keys appear to do nothing at all. I've tried a couple of the things I've seen mentioned on the forum, such as, adding the acpi_backlight=vendor parameter to the grub and downloading xbacklight, but neither seem to have done anything at all.

---

### Post by Jonathan Precise on 2014-08-10
If you go into the settings, isn't there an option for brightness?

Could be that Lubuntu is somewhat new and somewhat buggy. Xubuntu is just a bit heavier, but still runs fast, and is much more mature, which means there are less bugs here and there.

---

### Post by walterorlin on 2014-08-14
If you already have xbacklight installed then do the keys controlf10 or control f11 work as keybinding to work with xbacklight to decrase brightness which will be the control f10 key.

---

### Post by Rob Sayer on 2014-08-16
When you added the acpi_backlight=vendor string to your grub config file did you run

```
sudo update-grub
```

afterwards?  if not the change won't be persistent when you reboot.

This is from a similar thread on an Acer 5733.  Do the steps there to make sure it's the same video card:

[http://ubuntuforums.org/showthread.php?t=2200860](http://ubuntuforums.org/showthread.php?t=2200860)

---

