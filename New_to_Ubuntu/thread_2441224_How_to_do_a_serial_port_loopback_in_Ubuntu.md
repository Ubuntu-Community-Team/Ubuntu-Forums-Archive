---
title: "How to do a serial port loopback in Ubuntu?"
date: 2020-04-20
forum: New to Ubuntu
---

### Post by jeremymok on 2020-04-20
Hi,
I'm new to Ubuntu, I have a PC running on Ubuntu 18.04, it has 02 RS232 serial port.
How can I do a loopback test on the serial port?

I had tried dmesg | grep tty
It returns:
[    0.141242] printk: console [tty0] enabled
[    1.593150] printk: console [ttyS2] enabled
[    6.095807] serial8250: ttyS2 at I/O 0x3e8 (irq = 4, base_baud = 115200) is a 16550A
[    6.125392] serial8250: ttyS3 at I/O 0x2e8 (irq = 3, base_baud = 115200) is a 16550A

I had tried cat /dev/ttyS2 in one terminal.
Then I tried echo "hi" > /dev/ttyS2 in another terminal.
But it doesn't seems to be working.

I had tried putty.
Then I tried echo "hi" > /dev/ttyS2 in one terminal.
But there is no reply in putty too.

Is there any thing that I had missed out?
Please kindly advice.

Thank you

---

### Post by Holger_Gehrke on 2020-04-21
You do have a loopback plug connected to the serial port ? Otherwise you're just sending data into the void. This [page at National Instruments]("http://www.ni.com/tutorial/3450/en/") describes what pins need to be connected to each other when performing a loopback test.

Holger

---

### Post by jeremymok on 2020-04-21
> **Holger_Gehrke said:**
> You do have a loopback plug connected to the serial port ? Otherwise you're just sending data into the void. This [page at National Instruments]("http://www.ni.com/tutorial/3450/en/") describes what pins need to be connected to each other when performing a loopback test.

Holger


Hi Holger,
Thank you for your reply.
I have a loopback connector with Pin 2 & 3 short together.

---

### Post by Holger_Gehrke on 2020-04-22
You might want to try it also with ttyS3 since the dmesg output you posted mentions starting a console on ttyS2 (so if you connected another computer to ttyS2 you should get a linux console on that ...).

Holger

---

### Post by jeremymok on 2020-04-23
> **Holger_Gehrke said:**
> You might want to try it also with ttyS3 since the dmesg output you posted mentions starting a console on ttyS2 (so if you connected another computer to ttyS2 you should get a linux console on that ...).

Holger

Hi Holger,
I had tried ttyS3 too, it fails.
For the past 1 day, I had used Windows to test the serial port and it is working.
I had also used a fresh installed Ubuntu to test the serial port and it is working too.
I also found out that the new dmesg display is different from my old dmesg display.

 [ATTACH=CONFIG]285589[/ATTACH]

Is there a way to repair my system without reinstalling new Ubuntu?

---

