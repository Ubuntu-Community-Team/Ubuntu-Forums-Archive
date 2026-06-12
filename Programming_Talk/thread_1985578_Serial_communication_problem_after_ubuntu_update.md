---
title: "Serial communication problem after ubuntu update"
date: 2012-05-23
forum: Programming Talk
---

### Post by nevixa on 2012-05-23
Hi,

I'm interfacing via a usb to serial converter with a serial device in c++. I used to have Ubuntu 10.10 and the code below and it worked. With Ubuntu 12.04 (clean install) it won't connect any more. The device is connected and I can find it in the same directory etc.

```
int open_port(void) {
    int fd; // file description for the serial port
    fd = open("/dev/serial/by-id/usb-Name_Of_Device_USB_to_serial_bridge_0-if00", O_RDWR | O_NOCTTY);
    
    cout << "BM: Attempting to open port" << endl;
    if (fd == -1) // if open is unsucessful
    {
        printf("BM: open_port: Unable to open BM \n");
    } else {
        printf("BM: port is open.\n");
    }

    return (fd);
}

int configure_port(int fd) // configure the port
{
    struct termios port_settings; // structure to store the port settings in

    cfsetispeed(&port_settings, B115200); // set baud rates
    cfsetospeed(&port_settings, B115200);

    port_settings.c_cflag &= ~PARENB; // set no parity, stop bits, data bits
    port_settings.c_cflag &= ~CSTOPB;
    port_settings.c_cflag &= ~CSIZE;
    port_settings.c_cflag |= CS8;

    tcsetattr(fd, TCSANOW, &port_settings); // apply the settings to the port
    return (fd);
}
```Anyone any idea why this is not working on Ubuntu 12.04 and it is on Ubuntu 10.10?

Some more info:
```
$ ls -al /dev/serial/by-id
total 0
drwxr-xr-x 2 root root 60 May 23 16:22 .
drwxr-xr-x 4 root root 80 May 23 16:22 ..
lrwxrwxrwx 1 root root 13 May 23 16:22 
usb-Name_Of_Device_USB_to_serial_bridge_0-if00-> ../../ttyACM0
```

Thank you

---

### Post by roelforg on 2012-05-23
Try using /dev/ttyACM0 to connect instead of the id

---

### Post by nevixa on 2012-05-23
Thanx, tried that, not working.

---

### Post by roelforg on 2012-05-23
What's the exact error message?

---

### Post by nevixa on 2012-05-23
The program compiles, but when running the output is:

```
BM: Attempting to open port
BM: open_port: Unable to open BM 
```

I tried connecting with minicom and miniterm, but I just can't get that to work with the device. I have another system (same hardware) still running Ubuntu 10.10. The same code is working there, but I also can't get minicom or miniterm to work.

---

### Post by dwhitney67 on 2012-05-23
Check the permissions assigned to the device /dev/ttyACM0.  Perhaps you do not have write permissions?

It would be more helpful if you would print out the value of **errno **after the call to open() fails.

---

### Post by roelforg on 2012-05-23
Try running the program with sudo

---

### Post by nevixa on 2012-05-23
Thanks dwithney67! Changing the owner from root to my personal account fixed the problem. I assume it is ok for a device to be not owned by root? 

Thanks again dwithney67 and roelforg!

---

### Post by roelforg on 2012-05-23
> **nevixa said:**
> Thanks dwithney67! Changing the owner from root to my personal account fixed the problem. I assume it is ok for a device to be not owned by root? 

 
That's not ok because the /dev dir gets regenerated on boot so you need to chown it every reboot.
It's better/more permanent to run the app with sudo or as setuid.

---

### Post by dwhitney67 on 2012-05-23
> **nevixa said:**
> Thanks dwithney67! Changing the owner from root to my personal account fixed the problem. I assume it is ok for a device to be not owned by root? 

Thanks again dwithney67 and roelforg!

It's your computer; you do as you wish with it.

The better approach, as roelforg suggested, would be to run the application using 'sudo', or alternatively to set the "sticky" bit on the application.  For example:
```

$ sudo -i
# chown root:root app
# chmod u+s app
# exit
$ ./app

```

---

### Post by nevixa on 2012-05-24
Thanks again. I did face that problem this morning, after a reboot the device was owned by root again. 

The problem is that I'm running my application from within Netbeans. On  my other (Ubuntu 10.10) pc the serial device is owned by root, but I can  start the program from within Netbeans, and I can also start the  program from the terminal without sudo (./app). The compiled program (on  the Ubuntu 10.10 pc) is owned by private user, not by root!

I must have figured out this problem before (if nothing changed in Ubuntu 12.04 on this matter), but apparently I forgot..

Does one of you have an idea how I configured Netbeans (or maybe the  serial device) so I have the serial device owned by root, my compiled  programs owned by private user (not really necessary maybe) and the  communication working? 

Thanks a lot for thinking with me and guiding me through my own maze.

---

### Post by nevixa on 2012-05-25
I figured out that the private user was not allowed to communicate with 'serial modems'. Installing gnome-system-tools and then going into 'Users and groups' -> advanced settings and enabling 'serial modems' for the user fixed the problem. Thanks for all the help.

---

