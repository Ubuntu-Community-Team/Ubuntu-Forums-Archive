---
title: "fail install ubuntu gnome 16.04"
date: 2016-05-12
forum: New to Ubuntu
---

### Post by KangTaHu on 2016-05-12
when i install ubuntu gnome 16.04 on my laptop, and it's error like this,, and i don't know how to fix it, -_-'   

i've try to fix it with many way from google, -_- may be i should learn more..,, :confused:

[IMG]https://scontent-sin1-1.xx.fbcdn.net/v/t1.0-9/13220824_10204578820350640_7000714122569414585_n.jpg?oh=346f219c1a5c78139cb08f9f133d6b02&oe=57E0F37E[/IMG][IMG]https://scontent-sin1-1.xx.fbcdn.net/v/t1.0-9/13221651_10204578820310639_1874131936564027385_n.jpg?oh=2d8be876b2856ae2982de0e4836bc321&oe=579FD3CB[/IMG][IMG]https://scontent-sin1-1.xx.fbcdn.net/v/t1.0-9/13230063_10204578822670698_356042204012733866_n.jpg?oh=746245a341f41be68f344983a29a483e&oe=57A1AB49[/IMG]

---

### Post by Bucky Ball on 2016-05-12
Welcome. Ok. You have the boot order set to boot from the UEFI OS boot manager, not your install USB/disk. Not sure if that is the problem.

You are attempting to install in UEFI? You don't say, nor do you mention whether you are dual-booting with Windows, or are wanting to be. If the latter is the case, you need to boot into Windows and switch off hibernation. 

If Windows is installed in UEFI, Ubuntu needs to be installed in UEFI. Therefore, you need to boot from 'internal cd/dvd' or either of the entries 'USB diskette' under the UEFI boot section, depending on what you are trying to install from.

If Win is installed in UEFI and you are attempting to install Ubuntu in 'legacy' mode, you will end up with a mess.

---

### Post by KangTaHu on 2016-05-12
oh hallo, ^_^'  ohya i didn't say, i dont have any os on my laptop,,  i just want to install ubuntu on my laptop,,  just single os,,  and when i try with 14.04 it's fine, no error report..

---

### Post by KangTaHu on 2016-05-12
i will try the usb diskette,  thaks for suggestion sir ^_^

---

