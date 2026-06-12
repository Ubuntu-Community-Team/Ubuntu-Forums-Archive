---
title: "Rs232: problems with tcdrain() function"
date: 2009-06-04
forum: Programming Talk
---

### Post by ritchie-w on 2009-06-04
Hi,

I just have the problem, that the tcdrain() function has not timeout function.

The case:

I sendout chars out of the rs232 interface with the write() function, via CTS/RTS Handshake, but I do not have connect a cable.

In this case, the tcdrain() will not return and hangs forever.

The write()/read() functions are working fine if a device is connected, but I would like to avoid problems, if somebody disconnect the cable.

Is there any other function useable, to take care, that the chars of the write() are sended (with timeout) ?

Thanks for help.

ritchie

---

### Post by Salvar Fawkes on 2009-06-18
Well, I don't know about tcdrain(), but here's what I did to receive data on a serial port. It's really simple, but it works well so far. There are some methods to tell the serial port to wait a certain amount of time for data ([VMIN and VTIME]("http://www.gnu.org/s/libc/manual/html_node/Noncanonical-Input.html#Noncanonical-Input")), but these use increments of .1 second, which is much longer than necessary, I think. You'll need to #include <unistd.h> to use usleep, and 10,000 microseconds is just a value that worked for me--it's probably longer than necessary, but you can tweak it.

(Oh, and that PacketTimeoutException is a custom one. You can replace that with whatever you like.)

```
string waitForBytes(unsigned int numBytes)
{
  string result;
  char buffer[numBytes];
  int bytesRead;
  int waitCounter = 0;
  
  while(numBytes > 0)
  {
    bytesRead = read(serialPort, buffer, numBytes);
    
    if(bytesRead == 0 || bytesRead == -1)
    {
      if(waitCounter < 10)
      {
        waitCounter++;
        usleep(10000);
      }
      else
      {
        throw PacketTimeoutException();
      }
    }
    else
    {
      for(int i=0;i < bytesRead; i++)
      {
        result.push_back(buffer[i]);
      }
      numBytes -= bytesRead;
    }
  }
  return result;
}
```

Note: About the "for" loop at the end... I ran into a really strange problem, where the contents of buffer would not show up when accessed all at once (with cout and with .append()). I still don't know what the problem is, but by accessing the bytes individually I was able to get the data.

---

