---
title: "i2c bus using the serial com port?"
date: 2006-02-02
forum: Programming Talk
---

### Post by Barre on 2006-02-02
Hi.
I’m quite new to linux (have the basic administration skills but completely new when it comes to programming)

I’m in the progress of replacing windows on all my computers at home and currently I’m running one fedora and two ubuntu but one windows machine is still going strong and is hard to shutdown.

I have created a temperature sensor using the DS1621 IC (uses i2c for communication) and attached that to my serial port on my windows machine, I’ve created a small VB program that communicates with the i2c devices and logs the temperatures in a text file.

In order for me to completely remove windows from home I need to replace that program so my questions is:

•	can I use lm_sensors and configure it to use the com port and run i2c? (I know I should read the man pages, but maybe some kind soul already knows the answer…)
•	Can anyone point me to a source where I can learn how to create a program/script to emulate i2c through the com port, or do I need to create a device driver in order to get the com port to use i2c instead of rs232?

never mind that the rs232 uses 12V (or atleast I think it's 12V), My device fixes the signal to 5V according to i2c spec...

I have some programming knowledge in c, (c++), php, VB and just starting to dive into perl.

Cheers…

---

### Post by toojays on 2006-02-02
If you can do it in VB using standard Windows API calls, then you should be able to get it working in GNU/Linux using serial port ioctls. However, I've never done it myself, and I didn't find anything with a quick google, so it may be harder than I think.

Bitbanging over RS232 is really pretty evil. It's much nicer to have some kind of USB<->parallel device instead. Where I work, we did I2C over serial port for years, but some serial ports (especially on laptops) just can't drive it properly. Thankfully we now have a USB<->I2C module, and it's a hellavula lot nicer to work with. It's also much faster. Also it seems that with each new release of Windows, bitbanging on the serial port becomes a lot more difficult. Of course I understand that you don't have to worry about all these issues since it's just a personal project for you.

Also I don't know if lm_sensors can do what you want. So not a terribly informative reply, sorry. :(

---

### Post by Barre on 2006-02-02
Thanks for a quick reply...

I've done some reading up on lm_sensors, and it seems like it's the thing for me although not with the serial com port but rather using the parallel port instead :D 

there's a "primitive parallel port driver", not really much extra work for me..
[http://www2.lm-sensors.nu/~lm78/cvs/i2c/doc/i2c-pport](http://www2.lm-sensors.nu/~lm78/cvs/i2c/doc/i2c-pport)

Although I create the +5V from the serial port today so my device doesn't need a extra power source thats one thing I have to fix (thinking of using the USB just for power the device, it doesn't use amny mAmps :))

again, thanks for a quick reply...

cheers

---

### Post by toojays on 2006-02-02
Oh, by the way, I remembered where it's documented how to set the serial control lines: [http://www.easysw.com/~mike/serial/serial.html#5_1_2](http://www.easysw.com/~mike/serial/serial.html#5_1_2)

---

