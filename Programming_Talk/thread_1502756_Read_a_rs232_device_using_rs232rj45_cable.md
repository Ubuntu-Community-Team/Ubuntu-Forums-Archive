---
title: "Read a rs232 device using rs232/rj45 cable"
date: 2010-06-06
forum: Programming Talk
---

### Post by frankabel on 2010-06-06
Hi all

I have a device with a rs232 port. That device connect to PCs (using a normal rs232 cable) to be managed for a old software. I want use the device on  new PCs that don't have a rs232 interface even I must reprogrammer the soft.

I have on my hand a rs232-rj45 cable, how can I read the data sent from the device? Is that possible using such cable?

Cheers
Frank Abel

---

### Post by McRat on 2010-06-06
> **frankabel said:**
> Hi all

I have a device with a rs232 port. That device connect to PCs (using a normal rs232 cable) to be managed for a old software. I want use the device on  new PCs that don't have a rs232 interface even I must reprogrammer the soft.

I have on my hand a rs232-rj45 cable, how can I read the data sent from the device? Is that possible using such cable?

Cheers
Frank Abel

You have a legacy RS-232 device that you want to use on a modern PC that does not have a RS-232 port?

You need a USB/RS232 converter, which are cheap and plentiful at most computer stores.  

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=123071&CatId=464](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=123071&CatId=464)

---

### Post by dwhitney67 on 2010-06-06
There's also RS-232 to RJ-45 (Ethernet) converters.

Here's one site that discusses it:
[http://www.lammertbies.nl/comm/cable/yost-serial-rj45.html](http://www.lammertbies.nl/comm/cable/yost-serial-rj45.html)

Here's a place where you can actually go to procure the h/w:
[http://www.sealevel.com/store/serial/asynchronous-serial/ethernet/4101-ethernet-to-1-port-rs-232-serial-server.html](http://www.sealevel.com/store/serial/asynchronous-serial/ethernet/4101-ethernet-to-1-port-rs-232-serial-server.html)

Here's the kernel driver and configuration applications that SeaLevel provides for the product mentioned above:
[http://www.sealevel.com/support/article/AA-00108](http://www.sealevel.com/support/article/AA-00108)

---

### Post by frankabel on 2010-06-06
Thanks to all for the replies...

I already have a cable with a rs-232 connector in a side and a rj-45 on the other side, that cable don't will fill the bill?

I'm trying to avoid any device and not open free software, so, my question is, with the rs232-rj45 cable I have can't solve the problem? Will the problem get solved with the rs232-usb cable? How I read from a PC the info?

Cheers
Frank Abel

---

### Post by dwhitney67 on 2010-06-06
> **frankabel said:**
>  How I read from a PC the info?

Cheers
Frank Abel

I personally have never developed the low-level s/w you are attempting, however I do know it is possible.  I have used a device in the past (under Windoze) that *somehow* setup a TCP port that was used to communicate to the RS-232 device.

Take a look at the link I provided earlier with the open-source s/w.  Maybe some clues will be revealed to you there.

---

### Post by frankabel on 2010-06-06
Thanks again...
Using a converter device or just a cable with rj45-rs232 connector?

---

### Post by dwhitney67 on 2010-06-06
> **frankabel said:**
> Thanks again...
Using a converter device or just a cable with rj45-rs232 connector?
I did not have either; all I had was a 'virtual' connector.

The folks who paid me to do a job, wanted me to revamp their existing application to not only support serial communication, but also RJ-45 communications (sigh, using UDP, not TCP!)

Anyhow, there was a lot of revamp of the application, which forced me to have to test not only the new UDP interface, but also whether it was still capable of receiving data via the serial port (COM1?).  I downloaded a third-party application that bound the serial port to a TCP port. From there I was able to develop test programs which could send data to a TCP socket on the Windows machine, and magically the data would be received by the serial socket being used by the application.  Had I had a serial cable to connect to the laptop, this data would have been sent to the external device.

In conclusion, this 3rd-party application I used is eerily similar to what you require.  The application I used was closed-source; thus I haven't a clue how it was implemented; all I know is that it worked.

EDIT: Scratch my thoughts below; it slipped my mind that you do not have a serial port.  Perhaps you should consider using the USB port as someone mentioned earlier.

[COLOR="White"]If I had to guess how to do this task, I would think that what you require is a "bridge" between the serial port and the ethernet port.  Forget the cable thingy; I'm sure what you have is fine.

Create a daemon application that opens a (specified) serial port AND a TCP socket, and bind said socket to a (specified) port.  The daemon will wait for an application to connect, and then serve as the broker, forwarding TCP data to the serial interface, and vice versa.

When I think more about this, it is probably not that difficult to develop this daemon.  But it will require knowledge of setting up a serial port and setting up a non-blocking TCP socket.[/COLOR]

---

### Post by xblong on 2010-06-06
Ubuntu has a driver which will work with most USB-Serial adapters that you can buy online or in a computer store. Ubuntu has had this driver for a few releases.

See this link:

"How to enable USB-Serial Port Adapter (RS-232) in Ubuntu Linux"

[http://blog.mypapit.net/2008/05/how-to-use-usb-serial-port-converter-in-ubuntu.html](http://blog.mypapit.net/2008/05/how-to-use-usb-serial-port-converter-in-ubuntu.html)

Windows drivers for for these adapters are also available. Some of these adapters even have DOS drivers (TSR's).

If you built your own adapter you will probably have to write your own driver to support it.

With the driver loaded the adapter looks like a serial port. It will show up as the next unused COM port (COM1). Any application that uses a serial port can use the adapter. If you are writing an application you can use the same calls just as if it is a serial port.

---

### Post by frankabel on 2010-06-08
Thanks a lot, I will find a usb-rs232 cable then.

---

