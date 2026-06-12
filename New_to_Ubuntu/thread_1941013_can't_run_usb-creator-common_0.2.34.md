---
title: "can't run usb-creator-common 0.2.34"
date: 2012-03-14
forum: New to Ubuntu
---

### Post by Kevin McCready on 2012-03-14
I used Advanced Search in the forums to search titles for this but found nothing.

I've installed the program with

```
sudo apt-get install usb-creator-common
```

but when I try to run the installed program, the terminal tells me 'command not found'. I also can't find the program in the LXDE desktop menu.

```
Setting up usb-creator-common (0.2.34) ...
k@k-TECRA-A5:~$ usb-creator-common
usb-creator-common: command not found
k@k-TECRA-A5:~$ info usb-creator-common
k@k-TECRA-A5:~$ info usb-creator
k@k-TECRA-A5:~$ usb-creator
usb-creator: command not found
```

I'm trying to create a bootable USB of my system with all the changes I've made to all the packages (I've learned it's called persistence and that's what I need - droll)

Thanks to anyone who can help.

---

### Post by ptn107 on 2012-03-14
```
sudo apt-get install usb-creator-gtk
```
then go under System Tools -> Startup Disk Creator

---

### Post by HeroOfCanton on 2012-03-15
Not sure about why that won't run (never used it), but there are a lot of other tools you can try.

[UNetbootin]("http://unetbootin.sourceforge.net/") is popular.

Or check out [this list]("http://en.wikipedia.org/wiki/List_of_tools_to_create_Live_USB_systems") of other options.

---

### Post by teh603 on 2012-06-22
You have to invoke usb-creator-gtk from the command prompt for some reason. It doesn't show up under system tools.

---

