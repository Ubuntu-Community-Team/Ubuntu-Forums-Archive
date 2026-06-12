---
title: "modem firmware"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by Kalawala on 2008-06-27
well im back once again with more modem issues since i havent been able to fix the last few but trying something different how exactly do i install firmware for a modem i downloaded it from the companies website placed it on my desktop now how do i use it through the command terminal since it wont let me just open it???

---

### Post by Journeyman on 2008-06-27
what kind of file is it? Does it have any documentation? if so post the link for it

---

### Post by Kalawala on 2008-06-29
its a xmf file and it comes with a text file that says this 

******   U.S. Robotics Courier V.Everything V.92 update  ******



**************************************

*****   Manual Firmware update   *****

*****  (All Operating Systems)  *****

**************************************



To send the new code to your modem, all you need is a terminal program that can send files

using the XMODEM protocol. 



Start your terminal program. Adjust the settings, if necessary, so you can send AT to your

modem and get an OK response.

Enter ATXMODEM. The modem should respond as follows:



atxmodem

Firmware Update

---------------

Options:

(1) Read firmware

(2) Write firmware

ESCape Exits

>



Select "2" to begin updating the code. The modem will respond with:



Ready to receive firmware update





Send the "xmf" file to your modem using either the XMODEM-Checksum or XMODEM-CRC protocol. 

After the transfer is complete, you will see a *TRANSFER SUCCESSFUL* message. 

Press ESC. Modem will automatically reset. Firmware update is complete.




but i have no idea how to use this info

---

