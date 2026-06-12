---
title: "Read GPIO value from BLACKFIN 548"
date: 2014-09-02
forum: Programming Talk
---

### Post by Lawrance on 2014-09-02
I am trying to program in C# for eighter setting or reading GPIO value from blackfin 548.  uclinux 
I have also uploaded an attachment of the full version code below.

From the blacfin manual we can use the command line below to set the GPIO to low or high
root:/> [B]echo 0 > /sys/class/gpio/gpio23/value

[/B]the command line below to read the gpio value
root:/> **cat /sys/class/gpio/gpio23/value**




The first section of my code below **can successfully** set GPIO output to HIGH or LOW.

```

int gpio_value(unsigned gpio, unsigned value)
{
    int fd, len;
    char buf[60];
 
    len = snprintf(buf, sizeof(buf), "/sys/class/gpio/gpio%d/value", gpio);
 
    fd = open(buf, O_WRONLY);
    if (fd < 0) {
        perror("gpio/value");
        return fd;
    }
 
    if (value)
        write(fd, "1", 2);
    else
        write(fd, "0", 2);
 
    close(fd);
    return 0;
}
```



However code below **cannot read anything** the value from GPIO.

```

int gpio_get(unsigned gpio)
{
    int fd, len;
        int value;
    char buf[60], buf2[64];
 
    len = snprintf(buf, sizeof(buf), "/sys/class/gpio/gpio%d/value", gpio);

    fd = open(buf, O_WRONLY);

     if (fd < 0) 
        { perror("gpio/value");
      return fd;
    }

        value=read(fd, buf,64); 

    printf("read %d from pin: %s\n", value, buf2);
    
    close(fd);

    return value;
}

```

[SIZE=4]
**Question:** [U]Whats wrong of code for GPIO reading? 
[/U]                  _Why my code cannot read the GPIO value but it can set the value_[/SIZE]?

---

### Post by spjackson on 2014-09-03
Welcome to the forums.

In gpio_get you have
```

    fd = open(buf, O_WRONLY);

```
You cannot read from a file that you have opened for Write Only. I suggest you use O_RDONLY.

---

### Post by Lawrance on 2014-09-05
> **spjackson said:**
> Welcome to the forums.

In gpio_get you have
```

    fd = open(buf, O_WRONLY);

```
You cannot read from a file that you have opened for Write Only. I suggest you use O_RDONLY.

[B]
Hi, thanks for your suggestion. The code can read the GPIO now. However, the value read from GPIO pin always be "2", even the GPIO pin has 3.3V (high level) or 0V (low level). The GPIO value should be "0" for low level and "1" for high level.

I am using read() function to get this GPIO value. Is it a wrong choice?
[/B]

---

### Post by spjackson on 2014-09-05
> **Lawrance said:**
> [B]
Hi, thanks for your suggestion. The code can read the GPIO now. However, the value read from GPIO pin always be "2", even the GPIO pin has 3.3V (high level) or 0V (low level). The GPIO value should be "0" for low level and "1" for high level.
[/B]

You are reading the value into buf but then printing out the uninitialised contents of buf2.
> 
```

        value=read(fd, buf,64); 

    printf("read %d from pin: %s\n", value, buf2);

```

Is the incoming data terminated by a nul byte? Probably not. May it contain embedded nuls? Probably not, but if it does, then you can't really printf it as a string, I would suggest (assuming no embedded nuls):
```

    value=read(fd, buf2,64); 

    if (value >= 0) {
        printf("read %d from pin: %.*s\n", value, value, buf2);
    }
    /* else handle error */

```

---

### Post by Lawrance on 2014-09-05
[QUOTE=spjackson;13115622]You are reading the value into buf but then printing out the uninitialised contents of buf2.

Is the incoming data terminated by a nul byte? Probably not. May it contain embedded nuls? Probably not, but if it does, then you can't really printf it as a string, I would suggest (assuming no embedded nuls):



**Thank you so much.The problem is fixed. :razz:**

---

