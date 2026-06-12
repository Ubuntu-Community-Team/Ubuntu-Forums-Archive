---
title: "Java RXTX installation problem on Feisty"
date: 2008-06-05
forum: Programming Talk
---

### Post by ctaskiran on 2008-06-05
I am trying to set up connectivity to the serial port using RXTX. I am experiencing difficulty in installing the RXTX drivers, though.

I am testing the install by trying to run SimpleWrite.java program that comes with Sun's COMM API with the following change:
```

//import javax.comm.*;
import gnu.io.*;

```
as suggested [here.]("http://rxtx.qbang.org/wiki/index.php/Writing_%22Hello_World%22_to_a_USB_to_serial_converter")

When I compile this, none of the serial port related methods gets recognized.

I tried the following
[LIST]
[*]apt-get install librxtx-java
[*]the script given [here]("http://decoderpro.com/install/Ubuntu.shtml")
[*]donwloading the binaries from rxtx.org and copying
sudo cp rxtx-2.0-7pre1-i686-pc-linux-gnu/librxtxParallel.so /usr/lib/Java6u10/jre/lib/i386/
sudo cp rxtx-2.0-7pre1-i686-pc-linux-gnu/librxtxSerial.so /usr/lib/Java6u10/jre/lib/i386/
sudo cp rxtx-2.0-7pre1-i686-pc-linux-gnu/RXTXcomm.jar /usr/lib/Java6u10/jre/lib/ext/
[/LIST]
None of these worked! The instructions seem to be outdated and/or hazy, too. Any help from someone who got RXTX working would be greatly appreciated, already spent two days on this :(

Thanks,

Cuneyt

---

