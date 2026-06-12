---
title: "Winusb USB formatting trouble with terminal"
date: 2016-11-23
forum: New to Ubuntu
---

### Post by joelsmith on 2016-11-23
Hi everyone! I'm having trouble using Winusb with the terminal. (When I tried using Winusb without the terminal, it just kept crashing.)  When I've selected my directories and the ISO I want to copy and hit ENTER, I get this message:

[FONT=monospace][COLOR=#000000]Formating device...[/COLOR]
Warning: Partition /dev/sdc1 is being used. Are you sure you want to continue?
[FONT=arial]

The trouble is that I don't know how to answer "do you want to continue?" I tried entering "Y", "y", and "SPACE" without anything happening.  I even tried "yes" and you can guess what happened! I want to continue with the format but I don't know how to tell it.
It doesn't tell you what your options are.
[/FONT]
[/FONT]

---

### Post by sudodus on 2016-11-23
Welcome to the Ubuntu Forums :-)

There are some problems with Winusb in the new Ubuntu releases.

- If yoo can stand a text mode interface, you can try ***mkusb-nox***.

- If you are willing to try a new version with a graphical interface, that works for me and some other people but is not tested enough to be released officially, you can try ***dus*** with the interface ***guidus***. 

See the following links,

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[Installation](https://help.ubuntu.com/community/mkusb/gui#Installation)

[Making a USB drive to install Windows](https://help.ubuntu.com/community/mkusb/v7#Making_a_USB_drive_to_install_Windows)

[dus - a revamped interface of mkusb and mkusb-nox](https://help.ubuntu.com/community/mkusb/gui#dus_-_a_revamped_interface_of_mkusb_and_mkusb-nox)

---

### Post by HermanAB on 2016-11-23
Well, the answer is right there in front of you actually:
"Warning: Partition /dev/sdc1 is being used."

You have to umount /dev/sdc1 otherwise the script won't work, since sdc1 is in use.

---

