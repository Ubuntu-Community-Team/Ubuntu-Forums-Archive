---
title: "libpcap problem"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by scuba123 on 2008-08-04
Hi Everybody,

I downloaded libpcap0.9.8 for upgrades from this link -> [https://launchpad.net/ubuntu/intrepi...ibpcap/0.9.8-5](https://launchpad.net/ubuntu/intrepi...ibpcap/0.9.8-5). I then ran the command as follows:
1. ./configure
2. sudo make install
My question is that I couldn't find **/usr/lib/libpcap.so.0.9.8**. I only found:
-rw-r--r-- 1 root root 147048 2004-08-12 19:33 /usr/lib/libpcap.a
lrwxrwxrwx 1 root root 14 2008-08-04 00:00 /usr/lib/libpcap.so -> libpcap.so.0.7
lrwxrwxrwx 1 root root 16 2008-07-12 16:46 /usr/lib/libpcap.so.0.7 -> libpcap.so.0.7.2
-rw-r--r-- 1 root root 117136 2004-08-12 19:33 /usr/lib/libpcap.so.0.7.2
lrwxrwxrwx 1 root root 16 2006-12-27 03:15 /usr/lib/libpcap.so.0.8 -> libpcap.so.0.9.4
-rw-r--r-- 1 root root 155152 2006-06-19 12:41 /usr/lib/libpcap.so.0.9.4

Do you have any ideas? Please help. Thanks in advance.

Regards,

scuba123

---

### Post by Claus7 on 2008-08-04
Hello,

your link doesn't seem to work so I cannot see the library you are talking about. The only thing I can think of, is that you haven't installed the library where you think it should. In the configure file it should tell you where it should be installed. In your case :
i) I would check the README file and the configure file for information about the installation and 
ii) I would search to find where the library is, like that :
```
cd /
find -name "libpcap.so.0.9.8"
``` (either as root or not).

Now in case I wanted to see about every libcap library on my system I would replace the above find command with the following :
```
find -name "*libpcap*"
```

The second find command is more general. So if your library has a name, let's say  libpcap.so.0.9.8-5, the first find command will give you null results. Try both and see.

Regards!

---

### Post by scuba123 on 2008-08-06
Hi Claus7,

Thanks for your suggestion. I installed the libpcap 0.9.8 on another pc. 
rack1@rack1:~/errorman3$ ls -l /usr/lib/libpca*
-rw-r--r-- 1 root root 240320 2007-11-15 09:13 /usr/lib/libpcap.a
lrwxrwxrwx 1 root root     14 2008-08-01 17:47 /usr/lib/libpcap.so -> libpcap.so.0.8
lrwxrwxrwx 1 root root     16 2008-07-31 10:29 /usr/lib/libpcap.so.0.8 -> libpcap.so.0.9.8
-rw-r--r-- 1 root root 162532 2007-11-15 09:13 /usr/lib/libpcap.so.0.9.8
rack1@rack1:~/errorman3$ sudo chmod uog+wx /usr/lib/libpcap.so.0.9.8
----------------------------------------------------
rack1@rack1:~/errorman3$ ls -l /usr/lib/libpca*
-rw-r--r-- 1 root root 240320 2007-11-15 09:13 /usr/lib/libpcap.a
lrwxrwxrwx 1 root root     14 2008-08-01 17:47 /usr/lib/libpcap.so -> libpcap.so.0.8
lrwxrwxrwx 1 root root     16 2008-07-31 10:29 /usr/lib/libpcap.so.0.8 -> libpcap.so.0.9.8
-rwxrwxrwx 1 root root 162532 2007-11-15 09:13 /usr/lib/libpcap.so.0.9.8

The problem here is that when I ran a program on gdb, the libpcap still showed /usr/lib/libpcap.so.0.8 instead of /usr/lib/libpcap.so.0.9.8. I am attaching the screenshot of the error. Is this a link error? Please help. Thank you.

Regards,

scuba123

---

### Post by Claus7 on 2008-08-06
Hello,

it seems that the installation of the libpcap.so.0.9.8 library is correct. Yet, the gdb program should be configured in a way so as to understand it. Searching via synaptic, I saw that the gdb package is already there. 
Reading this :
[http://ubuntuforums.org/showthread.php?t=228383](http://ubuntuforums.org/showthread.php?t=228383)
I make out that first before compiling the library you need, you should run the : 
autoreconf -f -i -s
so as to make all the other packages that depend on an old version to understand what is going on.

One other thing should be to try and compile gdb for yourself, yet I would go for the first solution.

Regards!

---

### Post by AdamWood on 2008-08-06
Often a ./configure script defaults to installing in /usr/local/ and not /usr/

---

### Post by Claus7 on 2008-08-06
Hello,

> **AdamWood said:**
> Often a ./configure script defaults to installing in /usr/local/ and not /usr/

yes indeed :
> configure takes many options, but the only one that is usually mandatory is `--prefix'. This option tells configure where you want glibc installed. This defaults to /usr/local, but the normal setting to install as the standard system library is `--prefix=/usr' for GNU/Linux systems and `--prefix=' (an empty prefix) for GNU/Hurd systems

Regards!

---

### Post by scuba123 on 2008-08-06
Hello,

I removed all libpcap files under /usr/lib/ then I reinstalled libpcap 0.9.8 with the following instruction:

1. ./configure CPPFLAGS="-I/usr/local/include" LDFLAGS="-L/usr/local/lib" CFLAGS="-D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64"

2. make && gcc -shared -Wl,-soname -Wl,libpcap.so.`cat VERSION` -o libpcap.so.`cat VERSION` *.o -lc

3. make install && cp libpcap.so.0.9.8 /usr/local/lib
4. make install && cp libpcap.so.0.9.8 /usr/lib
5. cp libpcap.a /usr/lib
I added/replicated few commands that I originally got from [here]("http://bjou.homeunix.net/blog/2006/12/advanced-packet-capturing-howto-pf_ring-napi-and-extended-libpcap-on-debian-sarge/") 

6. I then reinstalled gdb. 

I am not sure if this is correct but I don't see that error message anymore. However, I received another error message :( . Thanks alot for all your helps.

Regards,

scuba123

---

### Post by scuba123 on 2008-08-12
Hi Everybody,

I installed gdb in order to debug a program. I have also installed libpcap0.9.8. However when I debugged the program by using "backtrace", I saw that gdb was still using libpcap0.8.

[New Thread 0xb7c8a8d0 (LWP 6010)]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb7c8a8d0 (LWP 6010)]
0x01cfcc20 in ?? ()
(gdb) backtrace
#0  0x01cfcc20 in ?? ()
#1  0xb7d863a7 in getifaddrs () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7f4fe66 in pcap_findalldevs () from **/usr/lib/libpcap.so.0.8**
#3  0xb7f50f3e in pcap_lookupdev () from **/usr/lib/libpcap.so.0.8**
#4  0x0804c28e in PacketSniffer::PacketSniffer ()
#5  0x0804f1a4 in mpeg2_network::mpeg2_network ()
#6  0x0804b27e in consoleUI ()
#7  0x0804c06c in main ()
--------------------------------------------------

The following is the proof that I have installed libpcap0.9.8:
rack2@ubuntu:~$ ls -la /usr/lib/libpca*
-rw-r--r-- 1 root root 240320 2007-11-15 09:13 /usr/lib/libpcap.a
lrwxrwxrwx 1 root root     14 2008-07-17 22:59 /usr/lib/libpcap.so -> libpcap.so.0.8
lrwxrwxrwx 1 root root     16 2008-07-15 09:17 /usr/lib/libpcap.so.0.8 -> libpcap.so.0.9.8
-rw-r--r-- 1 root root 162532 2007-11-15 09:13 /usr/lib/libpcap.so.0.9.8

The way I installed libpcap is
./configure --prefix=/usr
make && sudo make install

Please help. Thanks in advance.

Regards,

scuba123

---

### Post by Claus7 on 2008-08-28
Hello,

I think that you have missed the soft link part (the ln command) and also the fact that you have to declare which library the gdb program should use. 

Regards!

---

