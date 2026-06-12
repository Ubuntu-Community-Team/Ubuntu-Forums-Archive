---
title: "Python and bluetooth hacker needed"
date: 2007-08-18
forum: Programming Talk
---

### Post by highno on 2007-08-18
Hi there,

I need some assistance for my project ([http://blueproximity.sourceforge.net](http://blueproximity.sourceforge.net)) where I am using python as the programming language together with pybluez for accessing bluetooth devices.

I am trying to get the rssi value of a connection to do some distance approximation (which is running well but I keep using hcitool rssi which is what I want to throw out as an external dependance).

I want to support Bluetooth 1.1 so Inquiry-with-rssi is no option here. I think I partly know the answer but don't know how to get there from python.
I know I can send an hci command getting the rssi value of a given connection but it requires to send the handle of that connection. I can get the connection from the Bluetooth socket together with a special ioctl call which is exactly the problem. I don't know how to call that one.

This comes from hcitool's source:
```

        if (ioctl(dd, HCIGETCONNINFO, (unsigned long) cr) < 0) {
                perror("Get connection info failed");
                exit(1);
        }

        if (hci_read_rssi(dd, htobs(cr->conn_info->handle), &rssi, 1000) < 0) {
                perror("Read RSSI failed");
                exit(1);
        }

```

That's already the problem - the first ioctl (HCIGETCONNINFO = -2147202860) I don't know how to call that. fcntl doesn't help me as it seems only few ioctl's are supported, HCIGETCONNINFO is definitely not among these.

Can anybody help me or at least point to the right direction?

Thanks
Lars

---

### Post by pmasiar on 2007-08-18
IMHO this is too specific question for hackers here, you might have more luck asking for help in pybluez mailing list.

---

### Post by tombott on 2007-08-20
I just want to say that I am using BlueProximity and it's a cracking application.
Sorry I cannot answer your query but I just wanted to thank you for writing BlueProximity!

Tom.

---

### Post by maxinbjohn on 2008-03-19
Dear Lars,

 IMHO, We python guys can move (almost) in the same direction as Perl guys did in [http://perl.jonallen.info/pub/Main/BluetoothProximityDetection/xscreensaver.pl](http://perl.jonallen.info/pub/Main/BluetoothProximityDetection/xscreensaver.pl). 
They have used inline C code to measure RSSI. So for python, we can use swig to create wrapper code for C and use it as such. 

I have done that and the code is available at [http://pysportslive.googlecode.com/svn/trunk/pyrssi/](http://pysportslive.googlecode.com/svn/trunk/pyrssi/). Using this module , we can measure rssi values using python. It will be like

import bluessid
help(bluessid)
bluessid.read_rssi('xxxx')

Though, I couldn't test it due to the unavailability of bluetooth dongle (will get one and do the testing when I am back at home). 

Regards,

Maxin B. John
[http://maxinbjohn.blog.com/2894178/](http://maxinbjohn.blog.com/2894178/)

---

### Post by highno on 2008-03-19
Hi Maxin,

thanks for your work. I will check it hopefully tonight. Would this way be working on windows too? Since people keep asking me for a windows version this would be a breakthrough since everything else should already work...

Bye and thanks again,
Lars

---

### Post by imdano on 2008-03-19
> **highno said:**
> ```

        if (ioctl(dd, HCIGETCONNINFO, (unsigned long) cr) < 0) {
                perror("Get connection info failed");
                exit(1);
        }

        if (hci_read_rssi(dd, htobs(cr->conn_info->handle), &rssi, 1000) < 0) {
                perror("Read RSSI failed");
                exit(1);
        }

```

That's already the problem - the first ioctl (HCIGETCONNINFO = -2147202860) I don't know how to call that. fcntl doesn't help me as it seems only few ioctl's are supported, HCIGETCONNINFO is definitely not among these.

Can anybody help me or at least point to the right direction?I think that the python fcntl module supports any ioctl call you give it.  You just have to manually add the constants into your code. The tricky part is dealing with the C data structures you pass in and get back.  It might be easier in your case just to use inline C and ctypes, etc.

---

### Post by maxinbjohn on 2008-03-28
Dear Lars,

 
The best solution is present here... 
 [http://mirror.optus.net/sourceforge/k/kb/kbtlocker/kbtlocker-1.2.py.gz](http://mirror.optus.net/sourceforge/k/kb/kbtlocker/kbtlocker-1.2.py.gz)

We need to create the bluetooth socket to call the ioctl (the same way to call ioctls for sockets in Linux) 

hci_sock = bt.hci_open_dev()
hci_fd = hci_sock.fileno()
try:
    		fcntl.ioctl( hci_fd, bt.HCIGETCONNINFO, request, 1 )	
except:
		pass


Regards,

Maxin B John

---

### Post by highno on 2008-03-28
Hi Maxin,

i will look at it later. I am at work at the moment and kind of busy...
Thanks for your search. I've also found a general solution for ioctl missing values as there is a method on how to calculate them.
I have to look the url up but it was quite easy...

Bye
Lars

---

