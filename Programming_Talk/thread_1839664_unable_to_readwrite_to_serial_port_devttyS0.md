---
title: "unable to read/write to serial port /dev/ttyS0"
date: 2011-09-06
forum: Programming Talk
---

### Post by avee137 on 2011-09-06
i am trying to write a sample program to write to a serial port and read from it.
here is my code . 
```

int main()
{
        int fd , n_wrtn , n_read, ret_f,bytes ;
        char buf[100];
        //opening of port
        fd = open("/dev/ttyS0",O_RDWR | O_NOCTTY | O_NDELAY );

        if ( -1 == fd )
        {
        perror("open port error : unable to open /dev/ttyS0-");
        }
        else
        {
        fcntl( fd ,F_SETFL ,0 );
        }

        //writing somthing to port
        n_wrtn = write (fd , "ATZ\r" , 4);

//      printf("%d bytes written\n",n_wrtn);
        if( n_wrtn < 0 )
        {
        fputs ("write() of 4 bytes failed\n",stderr);
        }

        sleep(1);
        ioctl(fd, FIONREAD, &bytes);
        printf("avlbl bytes at port = %d\n",bytes);
        /*ret_f = fork();
        if(ret_f == 0)
        {
        //making the read call non blocking
        //fcntl(fd, F_SETFL, FNDELAY);
        sleep(2);
        n_read = read ( fd , buf ,4);
        
        perror("read error :"); 
        printf("%d bytes read : %s\n",n_read,buf);
        }
        
        */
        //closing port
        close(fd) ;



```




after writing when i check thru ioctl in code ii get following output :
```
avlbl bytes at port = 0

```

Please help.:confused:

---

### Post by VernonA on 2011-09-06
I'm wondering if you are expecting to get four bytes available. If so, you have misunderstood. The bytes you send out have gone to the machine on the other end of the serial cable. If you ran the ioctl call on that remote device then it would be detect four bytes in its input buffer. Similarly, if you did the write("atz") on the remote machine, then ran your program it would report 4 bytes available in the local machine's input buffer. The read and write channels are not connected together (though they can be using a special piece of hardware called a loopback cable).

---

### Post by avee137 on 2011-09-06
thanks

---

### Post by jwbrase on 2011-09-06
> **VernonA said:**
> The read and write channels are not connected together (though they can be using a special piece of hardware called a loopback cable).

Some UARTs also have a loopback mode. I'm not sure how to access it through the Linux API though. The only serial programming I've ever done has been written directly to the hardware.

---

### Post by avee137 on 2011-09-10
i got it . There was no problem with API but my understanding of whole set up. I had to configure the port in a mode where it should operate on raw bits. these links could help any beginner to get most of the concepts around serial communication:
[http://tldp.org/HOWTO/Serial-HOWTO.html#toc22](http://tldp.org/HOWTO/Serial-HOWTO.html#toc22)
[http://tldp.org/HOWTO/Serial-Programming-HOWTO/](http://tldp.org/HOWTO/Serial-Programming-HOWTO/)
[http://www.easysw.com/~mike/serial/serial.html]("http://www.easysw.com/%7Emike/serial/serial.html")

As i sorted the things out from information available here .

---

### Post by WitchCraft on 2011-09-10
> **jwbrase said:**
> Some UARTs also have a loopback mode. I'm not sure how to access it through the Linux API though. The only serial programming I've ever done has been written directly to the hardware.

Interesting. 
And I have been looking to learn serial programming, but never had a test device. 

Well in the meantime, serial changed to USB for me, but the loopback interface is a possibility to research further.

---

