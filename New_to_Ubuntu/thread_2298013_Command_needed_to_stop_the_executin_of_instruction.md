---
title: "Command needed to stop the executin of instructions in Gtkterm"
date: 2015-10-08
forum: New to Ubuntu
---

### Post by Danial_Rana on 2015-10-08
In Ubuntu whenever a command is running indefinitely, pressing clrl+c stops that command and the system is stabilized. I am using Gtkterm for serial communication, to stop execution of instructions in Gtkterm cltrl+c does not work. kindly tell me the command which will stop the execution of instructions in Gtkterm.

---

### Post by sotiris2 on 2015-10-08
Try Ctrl+Shift+C

---

### Post by Danial_Rana on 2015-10-08
Ctrl+Shift+C is for copy

---

### Post by tgalati4 on 2015-10-08
With serial communication, you typically kill the terminal.  In this case "reset" and "reset and clear" are your commands.  You can assign keyboard shortcuts for them in "Edit"-->"Keyboard Shortcuts".  There are several different methods for flow control with serial communication.  Hardware and software-based.  If you are having a communication issue that is not handled with flow control, then your only recourse is to reset the terminal and then send a reset command to the serial device.

---

### Post by Danial_Rana on 2015-10-08
In the menu of gtkterm edit doesn't shows any option for keyboard shortcuts, kindly tell me how can i reset the Gtkterm terminal.

---

### Post by tgalati4 on 2015-10-08
You are correct.  I use *mate-terminal* which is a fork of *gnome-terminal*.  These are text consoles, not serial consoles.  If you are trying to send a Control-C to an embedded device (as in your other thread), then you need to attach a keyboard device on that device (somehow) and issue the Control-C through that.

What happens when you send a Control-B (Break) to the device?

---

