---
title: "Read USB or COM scale from PHP"
date: 2012-05-08
forum: Programming Talk
---

### Post by CrusaderAD on 2012-05-08
Is it possible to read a com or usb scale from PHP?

---

### Post by CrusaderAD on 2012-05-08
I found this:

[http://code.google.com/p/php-serial/]("http://code.google.com/p/php-serial/")

But it seems geared towards windows. Anyone know of an example with linux?

---

### Post by Bachstelze on 2012-05-08
How are you reading it normally?

---

### Post by Zugzwang on 2012-05-08
> **CerealCypher said:**
> But it seems geared towards windows. Anyone know of an example with linux?

I don't know what makes you say that. According to a quick glimpse at the page, you only need to replace "COM1" in the example code by "/dev/ttyS0" or whatever port you are using to make the code run on Linux.

---

### Post by CrusaderAD on 2012-05-08
> **Zugzwang said:**
> I don't know what makes you say that. According to a quick glimpse at the page, you only need to replace "COM1" in the example code by "/dev/ttyS0" or whatever port you are using to make the code run on Linux.

Doesn't matter, that code didn't include the function needed to execute it. I found and tried this code:

```
<?php
    $usb = 'ttyS0';        
    `stty -F /dev/$usb 9600`;
    `stty -F /dev/$usb -parity`;
    `stty -F /dev/$usb cs8`;
    `stty -F /dev/$usb -cstopb`;
    $f = fopen("/dev/$usb", "r+");
    if(!$f) {
        echo "error opening file\n";
        exit;
    }

    statusRequest($f);
    sleep(1);
    $c = readPort($f);
    echo "$c\n";

function statusRequest($port) {
    $data = "request";
    fwrite($port, $data);
    fflush($port);
}

function readPort($port) {
    $read = 1;
    $c = '';
    while($read > 0) {
        $bytesr = unpack("h*", fread($port, 1));
        $c .= $bytesr[1];
        //echo $bytesr[1];
        if($bytesr[1] == 'ff') {
            $read = 0;
        }
    }    
    return $c;
}

?>
```

But I get this error:

> Warning: fopen(/dev/ttyS0): failed to open stream: Permission denied in /home/user/website/scaletest2.php on line 7 error opening file 

Any ideas?

---

### Post by SeijiSensei on 2012-05-08
On my machine, /dev/ttyS0 has these permissions:

```
crw-rw---- 1 root dialout 4, 64 Apr 30 23:53 /dev/ttyS0
```

This grants read and write privileges to the root user and members of group dialout.  The easiest solution is to add the www-data user, which Apache runs as, to the dialout group.  Edit (as root with sudo) the file /etc/group and modify the "dialout" entry as follows:

```
dialout:x:20:[color=blue]www-data[/color]
```

---

### Post by CrusaderAD on 2012-05-08
> **SeijiSensei said:**
> On my machine, /dev/ttyS0 has these permissions:

```
crw-rw---- 1 root dialout 4, 64 Apr 30 23:53 /dev/ttyS0
```

This grants read and write privileges to the root user and members of group dialout.  The easiest solution is to add the www-data user, which Apache runs as, to the dialout group.  Edit (as root with sudo) the file /etc/group and modify the "dialout" entry as follows:

```
dialout:x:20:[color=blue]www-data[/color]
```

Tried this and verified the /etc/group file. Still produces the same error.

---

### Post by SeijiSensei on 2012-05-08
Just a quick check; run "groups www-data" and make sure that "dialout" is listed.

There's always a brute force solution:

```
sudo chmod a+rw /dev/ttyS0
```

If that doesn't solve the problem, then I'm at a loss.  I'm quite puzzled that adding www-data to the dialout group didn't work.  Perhaps before taking the brute force route, try restarting Apache with "sudo service apache2 restart" and testing that first.

My concern about changing the permissions on /dev/ttyS0 manually is that I don't know if the change will survive a reboot.

---

### Post by CrusaderAD on 2012-05-08
> **SeijiSensei said:**
> try restarting Apache with "sudo service apache2 restart" and testing that first.

That seemed to have an effect. The script just loads... doesn't post anything to the screen now, which I guess is progress. I even executed it from the command line, same result... just loads... never proceeds.

---

### Post by SeijiSensei on 2012-05-08
The running instance had the old group memberships; restarting gave it a membership in dialout.

I'm afraid I can't help with the rest of the problem.  Do you just get a blank screen with no entries in /var/log/apache2/error.log?

Couple of other things you can try. First, I'd uncomment the "echo" line in readPort() so you can see whether it's doing something or not.  You could also try reproducing the status request from the command line like this:

```
sudo echo 'request' /dev/ttyS0
```

Does that produce the expected reply?  That's all that statusRequest() is doing.

---

### Post by CrusaderAD on 2012-05-08
Thanks for the suggestions. I tried a new script:

```
<?php
include "php_serial.class.php";

echo "<html>
      <head><title>Test MySQL</title></head>
      <body>";


// Let's start the class
$serial = new phpSerial;

// First we must specify the device. This works on both linux and windows (if
// your linux serial device is /dev/ttyS0 for COM1, etc)
$serial->deviceSet("/dev/ttyS0");

$serial->confBaudRate(9600);

// Then we need to open it
$serial->deviceOpen();

// To write into
$serial->sendMessage("Hello !");

// Or to read from
$read = $serial->readPort();

echo "here it is<br>";
echo $read;
echo "<br>here it was";


sleep(1);

// If you want to change the configuration, the device must be closed
$serial->deviceClose();



// We can change the baud rate
//$serial->confBaudRate(2400);

// etc...
?>
</body></html>
```

which seems to run fine, but it write $read back as being empty. Do you know of a way I can check to see if the serial port is even being hit?

Edit: I do have the include file loaded with the proper serial device pointed at.

---

