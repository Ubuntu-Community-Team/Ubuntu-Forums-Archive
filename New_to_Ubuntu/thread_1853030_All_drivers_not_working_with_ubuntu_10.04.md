---
title: "All drivers not working with ubuntu 10.04"
date: 2011-10-01
forum: New to Ubuntu
---

### Post by pillowslap on 2011-10-01
Recently I split my partition with Wins 7 and Ubuntu. I got Ndiswrapper downloaded but none of my drivers will install. I look for the correct .inf file but nothing is working. The linux computer has no internet but I have my desktop. The laptop is a Toshiba Satellite L665D-S5159. I've read every web page and article on this issue and nothing has worked. Any clues?

---

### Post by westie457 on 2011-10-01
Hi, the easiest way is to plug a cable in to the laptop (ethernet should work out of the box). If it does not we will have to use the more difficult way.
With the laptop running open a terminal using Ctrl+Alt+t type in ```
lspci -vnn
``` copy the output and paste the output between code tags (clicking the # at the top of the message pane.

The above should be done with a cable connection, if that is not possible then save the output to a text file on a USB stick and drag it to your desktop pc and attach the text file using the paperclip also in the top of the message pane.

Thank you.

---

### Post by gandaran on 2011-10-01
first we need more info on the hardware and what drivers do you need.

---

