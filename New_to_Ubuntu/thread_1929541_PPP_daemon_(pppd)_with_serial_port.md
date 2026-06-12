---
title: "PPP daemon (pppd) with serial port"
date: 2012-02-22
forum: New to Ubuntu
---

### Post by snare91 on 2012-02-22
I want to use the PPP Daemon pppd to set up a Point to Point link between a laptop and a Desktop (for simple data transfer using Point to Point Protocol [PPP]). How can I use pppd to set up the link and check if it is working fine?

On the desktop, I ran the following command:

**dmesg | grep tty**

which told me that I have 2 serial ports on the hardware - ttyS0 and ttyS1 on ports 0x3f8 and 0x2f8 respectively. They both use the UART 16550A. 

I ran the same command on the laptop, and this told me that I have 1 serial port on the hardware - ttyS0 on port 0x3f8 and it uses the UART 16550A.

Now, with this information, I checked the datasheet of the UART. 9600 bps is a valid baud rate for the UART, so I decided to use that (even though its not the highest rate, but for testing I thought that this would suffice).

Then, I connected the Desktop and the Laptop with a crossover RS232 serial cable (to make a null modem connection).

Then, I ran the following command in both the devices simultaneously

**sudo pppd /dev/ttyS0 9600 noauth logfile log**

Then, I checked if pppd was running by typing in ps -e | grep pppd on both the Desktop and the Laptop separately. It gave me a valid PID. But when I checked my log file, it showed "ttyS0 locked by PID ####". This was the same PID number as of pppd.

After fumbling with the pppd man page, I typed in this command on both the terminals -

**sudo pppd /dev/ttyS0 9600 noauth nolock logfile log**

Then I repeated the above procedure again.  This time the log file was empty, and the pppd process was running. 

Now, how can I check if the PPP link is running properly if at all it is running? Even though the pppd has a valid PID, I don't know if what I did was in the same direction as my purpose!

ANY help with this will be greatly appreciated! 
Hoping for a quick reply!

---

