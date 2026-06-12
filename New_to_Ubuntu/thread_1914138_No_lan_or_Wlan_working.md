---
title: "No lan or Wlan working"
date: 2012-01-23
forum: New to Ubuntu
---

### Post by jithinj26 on 2012-01-23
Hi

I am new to ubuntu 10.04 . I already love it a lot but Im facing a problem which I cant find a solution.
My laptop is Toshiba L755-S5256.
I am not being able to connect to wifi or lan . I think its because I have no drivers. Finally I tethered my mobile and got internet connection and tried to see if there are any drivers available to make my network adapters work but I couldnt find any.

Pleaseeeeee Helpppppppp

---

### Post by Nick_Kats on 2012-01-23
Why don't you check this thread: [http://ubuntuforums.org/showthread.php?t=1661489](http://ubuntuforums.org/showthread.php?t=1661489)
It helped me fix my Realtek Ethernet controller.
Also, could you post more information on your hardware?
To do that execute lspci and them lsmod on terminal.

---

### Post by varunendra on 2012-01-24
Hi jithinj26, welcome to the forums!

To provide proper details about your system, please follow these instructions:

[LIST]
[*]Open a terminal (goto **Applications > Accessories > Terminal**, or simply press **Ctrl+Alt+T**)
[*]Enter the following commands and copy-paste their outputs in your new post (*or in a blank file if you are not connected to internet while running the commands. You can then copy the file to a computer which is connected to internet, and copy-paste its contents in your new post*):
[/LIST]
```
uname -rm
lspci -nnk | grep -iA2 net
lsmod

```

While posting the results, click on # symbol at the top of the edit box to automatically generate [ code]..[ /code] tags. Paste (only) the output of the commands between the tags.

---

