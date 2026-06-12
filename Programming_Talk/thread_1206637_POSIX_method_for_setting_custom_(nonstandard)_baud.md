---
title: "POSIX method for setting custom (nonstandard) baud rate?"
date: 2009-07-07
forum: Programming Talk
---

### Post by hugecolin on 2009-07-07
I have a USB serial adapter that supports arbitrary baud rates. To set a nonstandard rate in code, I'd been using the TIOCGSERIAL like so:

```
struct serial_struct ser_info;
ioctl(ser_dev, TIOCGSERIAL, &ser_info);
ser_info.flags = ASYNC_SPD_CUST | ASYNC_LOW_LATENCY;
ser_info.custom_divisor = ser_info.baud_base / CUST_BAUD_RATE;
ioctl(ser_dev, TIOCSSERIAL, &ser_info);
```

I'd like to make this portable, but the termios serial I/O API doesn't seem to support setting nonstandard baud rates. Is there a POSIX alternative to the ioctl() for doing this?

--Colin

---

