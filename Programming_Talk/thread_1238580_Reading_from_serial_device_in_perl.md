---
title: "Reading from serial device in perl"
date: 2009-08-12
forum: Programming Talk
---

### Post by pomegrante on 2009-08-12
Hello everyone!

I have an ADSSR4xPROXR from National Control Devices ([www.controlanything.com](www.controlanything.com)).  This device connects via RS232 (serial) and allows me to open and close relays, and to read input voltages, by sending commands to and reading from it.

I am attempting to do this in perl.

Writing to the device (I.e. commands "254" and "0" to close relay 0) works - verified with a multimeter - however reading from the device is another story.

Sending commands "254" and "27" turn on reporting mode and the device will send back "85" confirming this.  The below script should accomplish this, no?  I know that the device is receiving my two commands as the status LED blinks when I execute the script.

```
#!/usr/bin/perl

use strict;
use warnings;
use Fcntl;

my $port = "/dev/ttyS0";
my $PORT;

sysopen($PORT, $port, O_RDWR | O_NONBLOCK) || die "can not open $port: $!\n";
select((select($PORT), $|=1)[0]); # Make $PORT hot

print $PORT chr(254); # 254 tells the device to listen for commands
print $PORT chr(27); # 27 enables reporting and should send back 85

my $char = getc($PORT); # Get the response (85)
print ord($char) . "\n"; # Print the response

close($PORT);
```

I do not know what I am doing wrong.  The baud rate (115200) has been correctly set, using stty.  I also know that this method works, as I have it working in ruby.  Is it my script?  Is it my serial settings?  Any help is appreciated.

Thanks!

---

