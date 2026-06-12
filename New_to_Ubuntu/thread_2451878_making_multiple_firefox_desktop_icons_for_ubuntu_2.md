---
title: "making multiple firefox desktop icons for ubuntu 20.04"
date: 2020-10-12
forum: New to Ubuntu
---

### Post by thehappybilly on 2020-10-12
MY SPECS
i am running Ubuntu 20.04.1 LTS x86_64 on a Lenovo ThinkPad E590 15.6 laptop. 

MY PROBLEM
hello, i am new to Ubuntu and downloaded and installed it 3 days ago, my previous operating system was Linux Mint 19.3, and on Linux mint i had a lot of mozzila firefox account on my desktop, and i would make a new desktop icon for each of my firefox accounts

in this video i show how i made my firefox icons

[https://www.bitchute.com/video/babRboVoDinK/](https://www.bitchute.com/video/babRboVoDinK/)

i would like to ask if there is a way for me to make new firefox profile icons onto my desktop, and if so, how, thank you!

---

### Post by yapidumoac on 2020-10-13
Depends on what Desktop you are using.

[How to run two different Firefox profiles at once on Linux]("https://www.techrepublic.com/article/how-to-run-two-different-firefox-profiles-at-once-on-linux/")

---

### Post by ActionParsnip on 2020-10-13
You'll want a launcher that runs:
```

firefox -P profilenamehere

```

Source
[https://linux.die.net/man/1/firefox](https://linux.die.net/man/1/firefox)

---

### Post by thehappybilly on 2020-10-14
how do i know which desktop i am using?

---

### Post by walts48 on 2020-10-15
> **thehappybilly said:**
> MY SPECS
i am running Ubuntu 20.04.1 LTS x86_64 on a Lenovo ThinkPad E590 15.6 laptop. 

MY PROBLEM
hello, i am new to Ubuntu and downloaded and installed it 3 days ago, my previous operating system was Linux Mint 19.3, and on Linux mint i had a lot of mozzila firefox account on my desktop, and i would make a new desktop icon for each of my firefox accounts

in this video i show how i made my firefox icons

[https://www.bitchute.com/video/babRboVoDinK/](https://www.bitchute.com/video/babRboVoDinK/)

i would like to ask if there is a way for me to make new firefox profile icons onto my desktop, and if so, how, thank you!

I used the manual method from the link below to add Firefox and Thunderbird icons to my Gnome desktop on 20.04.

[https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-20-04-focal-fossa-linux)

If I were to add icons for other profiles of the same or beta versions I would add a -p switch to the Exec command as ActionParsnip suggests.

I chose to select the profile from the Profile Manager instead of adding it to the Exec command.

---

### Post by metacell on 2020-10-16
Right-click your desktop, select "Create program launcher", and fill in "[FONT=courier new]firefox -P ProfileName[/FONT]", like you did before.

Also, if you want a simpler way to create new profiles, make an icon that only runs "[FONT=courier new]firefox -P[/FONT]". That will bring up the dialog för creating/deleting profiles directly.

---

