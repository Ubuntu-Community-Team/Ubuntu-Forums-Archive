---
title: "Read Serial Port with PHP"
date: 2013-05-25
forum: Programming Talk
---

### Post by Unknown7 on 2013-05-25
Hi, 

I'm new at linux world and i'm basically trying to talk with a device with PHP.
The script is working fine, but i can't read the "answer" from the device. 

PHP CODE:
```
<?php
$fp = fopen("/dev/ttyUSB0", "r+");
if(!$fp)
{
        echo "something wrong";
        die();
}

 fwrite($fp, "command\r");  // this works, sends a command to device
 $buffer = fread($fp,1024); //doesn't work, page just start loading and nothing happens
 //$buffer = fgets( $fp ); // same here
fclose($ficheiro);
?>

```


stty result ( stty -F /dev/ttyUSB0 ):
```
speed 9600 baud; line = 0;
kill = ^H; eof = ^A; min = 1; time = 0;
-icrnl ixoff ixany -imaxbel
-opost -onlcr
-isig -icanon -echo -echoe

```

setserial result ( setserial -av /dev/ttyUSB0 ):
```
/dev/ttyUSB0, Line 0, UART: unknown, Port: 0x0000, IRQ: 0
    Baud_base: 9600, close_delay: 12, divisor: 0
    closing_wait: none
    Flags: spd_normal

```



Any sugestions? I don't know if is a linux setting or a php problem...

---

