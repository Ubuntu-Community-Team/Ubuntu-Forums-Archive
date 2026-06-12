---
title: "Cannot access GUI after update"
date: 2013-09-29
forum: New to Ubuntu
---

### Post by Skilbride on 2013-09-29
[COLOR=#333333][FONT=UbuntuRegular]I just updated Ubuntu 12.04.3 and when I rebooted the computer it only boots into a text only mode. A black screen that asks for my login details. When I login it stays in a text only mode, like a giant terminal window. I cant access the gui at all. I think it may be a problem with graphics card drivers? Please help meas I'm wondering if i have to a total reinstall and lose all of my data.[/FONT][/COLOR]

---

### Post by magfoor on 2013-09-29
I am sure you won't have to reinstall. Login in to that black screen and then try to reconfigure your display manager with the following command (given that you are using ubuntu's default GUI) 
[B]sudo dpkg-reconfigure lightdm

[/B]Then you chose lightdm as your display manager and reboot your machine to see the changes.

Hope that helps.

---

