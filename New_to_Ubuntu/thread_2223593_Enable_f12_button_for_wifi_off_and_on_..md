---
title: "Enable f12 button for wifi off and on ."
date: 2014-05-11
forum: New to Ubuntu
---

### Post by Bipin_Paudel on 2014-05-11
Hello
I installed Ubuntu 12.04 lts on my hp envy 15t - j100. My f12 button is not working to make wifi off and on. Can someone help on this? All my network is fine but just the f12 button is not working.

---

### Post by tfrue on 2014-05-12
Make sure that rfkill has not blocked the button. You can type:
```
sudo rfkill list
```
That will show you if you have a hard block or soft block for your wifi button and if there is a block, you could type:
```
sudo rfkill unblock wifi
or to make sure that you unblock the right one, type:
sudo rfkill unblock all
```
Hope that helps!
Chris

---

### Post by aathi on 2014-05-27
In my HP Envy m6, installed ubuntu 12.04, wifi is not working. F12 button is always red. I can connect using LAN cable only. Can anyone help?

sudo rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by jeremy31 on 2014-05-27
Do you get any response from the keypress using xev or acpi_listen in terminal?

---

