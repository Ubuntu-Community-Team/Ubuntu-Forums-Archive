---
title: "Serial port interfacing ..."
date: 2010-03-02
forum: Programming Talk
---

### Post by shg234 on 2010-03-02
How to setup the ubuntu serial port in an expected mode?? :o
I want to talk with my embedded touch panel from Ubuntu through an user interface.
Can anyone guide me a bit .... plzzzzzzz
Any kind of suggestion will be appreciating.

---

### Post by cacycleworks on 2010-03-02
We wrote a php daemon to monitor a serial port and then access it with a webpage:

[PHP]$port="/dev/ttyS0";
	$result=0;
	$set_mode = "stty 9600 oddp -cstopb < $port";
	if( $fp = fopen ($port,"w+") ){
		system($set_mode, &$result);
		$error = ($result!=0) ?  "$set_mode failure: \$result=$result<br><br>" :  "";
		if( ! ($result = fwrite($fp, "W", 1)) ) 
			$error = "fwrite failed and returned: [$result]<br>";
		//usleep(1500);
		if( $error == "" )
			if( ! ($read = fgets($fp)) )
				$error = "fgets failed and returned: FALSE<br>";
	}
	else
		$error = "fopen failed and returned: [$fp]<br>";

	fclose($fp);
[/PHP]

Problem with this is that the serial port is very finicky hardware and if you bang on it too quickly with something (via php and apache), the port will shutdown. And I think it requires a system reboot.

There is some good info on the net about serial ports, but it's all pretty old. Especially if you look at trying to set up serial printers. 

:) Chris

---

### Post by radeon21 on 2010-03-02
If you want to interact with a serial port from c++, I'd check out libserial (libserial-dev in the repositories).

```
#include <SerialPort.h>

...

{
	char byte;

	//connect to ttyUSB0
	SerialPort mySerialPort("/dev/ttyUSB0");
	
	//open
	mySerialPort.Open(SerialPort::BAUD_9600, SerialPort::CHAR_SIZE_8, SerialPort::PARITY_NONE, SerialPort::STOP_BITS_1, SerialPort::FLOW_CONTROL_NONE);
	
	//read with a timeout of 500 ms
	byte = mySerialPort.ReadByte(500);
	
	//write a byte
	mySerialPort.WriteByte(0xaf);
	
	//
	mySerialPort.Close();
}
```

Pretty simple if you don't want to do anything really fancy.

---

