---
title: "Best language for serial coms/enet coms"
date: 2011-01-31
forum: Programming Talk
---

### Post by eeprom on 2011-01-31
Hello,
I have been programming for many years in C, visual basic, and ladder logic.  I am adequate at programming; I can usually accomplish what I need to accomplish.  I would like to start developing graphical user interfaces which can be used to communicate with serial and ethernet devices (such as a microprocessor and/or a programmable logic controller).  There will be database requirements as well for use as a data historian.

So my question is what would be the best language for doing this?

thanks,
EE

---

### Post by lavinog on 2011-02-01
Python should be adequate for this.
install python-serial for communicating with serial devices.

---

### Post by eeprom on 2011-02-02
Lavinog,
Thanks for your reply.  It sounds as if Python and Python-serial are two different downloads.  Is this correct?

thanks,
EE

---

### Post by lavinog on 2011-02-03
> **eeprom said:**
> Lavinog,
Thanks for your reply.  It sounds as if Python and Python-serial are two different downloads.  Is this correct?

thanks,
EE

Python is installed by default in ubuntu.

You can use the following to install python-serial
```

sudo apt-get install python-serial
```

---

### Post by eeprom on 2011-02-03
Thank you.  Yes, I have already found the python, and I've run a few versions of "hello world."  It reminds me of Matlab.  I will try the serial upload.

thanks again,
EE

---

### Post by lavinog on 2011-02-04
Here are some examples on how to use python-serial
[http://pyserial.sourceforge.net/examples.html](http://pyserial.sourceforge.net/examples.html)

---

