---
title: "MATLAB: serial communication and timers"
date: 2012-06-25
forum: Programming Talk
---

### Post by cguy on 2012-06-25
I have configured serial communication (9600, 8N1, async, input buffer length 2) and a timer with a period of 0.1 seconds.

Inside that timer's callback function I send one octet to my device and attempt to read 2 afterwards. I then print the 2 octets with disp().

What works: sending/receiving from serial and displaying the received values

What doesn't work: I can no longer use MATLAB's console. Only after I stop the program with Ctrl-C are my commands interpreted.
The serial communication is async, 'continuous' mode.

---

### Post by Zugzwang on 2012-06-25
> **cguy said:**
> 
What doesn't work: I can no longer use MATLAB's console. Only after I stop the program with Ctrl-C are my commands interpreted.
The serial communication is async, 'continuous' mode.

That sounds like reasonable behaviour: the console allows you to type in commands. Once you started some command, the console will be available for you once the program has terminated. Since your program does not terminate (since the timer is still running), the console might not be available for you.

However, you might convince MATLAB to behave differently, though. Do you call wait(...) on the time object somewhere? See [http://www.mathworks.de/help/techdoc/matlab_prog/f9-38272.html](http://www.mathworks.de/help/techdoc/matlab_prog/f9-38272.html)

---

### Post by cguy on 2012-06-25
I didn't call wait() anywhere.
If I disable reading from the serial console, the command line works fine.
Here's my code:
```

COM_PORT = 'COM12';
serial_port = instrfind('Type', 'serial', 'Port', COM_PORT, 'Tag', '');
if (0 == isempty(serial_port))
    disp('The COM port was already opened; closing it.');
    fclose(serial_port);
    delete(serial_port);
end

serial_port = serial(COM_PORT);
set(serial_port, 'InputBufferSize', 20);
set(serial_port, 'ReadAsyncMode', 'continuous');
set(serial_port, 'FlowControl', 'hardware');
set(serial_port, 'BaudRate', 9600);
set(serial_port, 'DataBits', 8);
set(serial_port, 'Parity', 'none');
set(serial_port, 'StopBit', 1);
set(serial_port, 'Timeout', 1);
disp('Serial port configured (9600 8N1, 1sec timeout).');

disp('Opening the serial port.');
fopen(serial_port);


data_timer = timer('Period', 1, 'TasksToExecute', 100000000, 'ExecutionMode', 'fixedRate');
data_timer.TimerFcn = { @main_loop, serial_port, shared_data };

```
and the callback fcn:
```

    msb = bitshift(shared_data.r, -8);
    lsb = bitand(shared_data.r, 255);
    fwrite(serial_port_handler, msb);
    fwrite(serial_port_handler, lsb);
    
    while (serial_port_handler.BytesAvailable)
        spd = fread(serial_port_handler, 1 ,'uint8');
        disp(spd);
    end
    disp('================================');

```
My device sends only 2 bytes after it receives the 2nd byte (lsb).

---

### Post by cguy on 2012-06-26
I remove the `while' and only used `fread' (uint16).
```

while (serial_port_handler.BytesAvailable)
    spd = fread(serial_port_handler, 1 ,'uint8');
    disp(spd);
end

```
After a bit more fiddling (including the software running on my device) the communication is now OK.

---

