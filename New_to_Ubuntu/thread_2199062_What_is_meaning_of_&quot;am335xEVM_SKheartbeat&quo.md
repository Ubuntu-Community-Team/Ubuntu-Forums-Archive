---
title: "What is meaning of &quot;am335x:EVM_SK:heartbeat&quot;?"
date: 2014-01-11
forum: New to Ubuntu
---

### Post by ruwan2 on 2014-01-11
Hi,
I am new to Linux. I run some example projects on embedded ARM based Linux. I am curious about the semicolon below. These are LED device files.
Could you explain it to me?

Thanks,


root@am335x-evm:/sys/devices/platform/leds-gpio/leds# ls                                                          
am335x:EVM_SK:heartbeat  am335x:EVM_SK:usr0                                                                       
am335x:EVM_SK:mmc0       am335x:EVM_SK:usr1

---

### Post by ian-weisser on 2014-01-12
A semicolon ';' does not appear in the strings you have provided.
The colon ':' on the first line (root@am335x-evm[COLOR=#ff0000]:[/COLOR]/sys/devices/platform/leds-gpio/leds#) is part of the prompt. It separates the machine name from the path.
The colons ':' on the second and third lines have no significance to the system. They are simply characters in the long filenames.
They may have some significance to the application(s) that uses those files, for example indicating a location or position or property.

---

