---
title: "Library link error [ undefined reference]"
date: 2007-12-17
forum: Programming Talk
---

### Post by jsatubnutufroums on 2007-12-17
Hi,
This is the Makefile I use:
```
CFLAGS+=-g -O -Wall
LDFLAGS+=-g -O -Wall
CC = gcc

clean:
        - rm *.o client

client: client.o stun.o udp.o
        $(CC) $(LDFLAGS) -o $@  $^

%.o:%.c
        $(CC)  -c  $(CFLAGS) $< -o $@

libstun.a: stun.o udp.o
        ar rv $@ $<
```
I enter [**make client**] to compile the program and the compilation is completed. I can execute the program. And now, I want to build a library by entering [**make libstun.a**] and get the *libstun.a* static library. I try to link the library and generate the binary file by entering this [**gcc client.c -I. -L. -lstun -o client**]
But I get the following error code:
```
/tmp/cc4Z3LWu.o: In function `main':
client.c:(.text+0x2a): undefined reference to `initNetwork'
client.c:(.text+0x354): undefined reference to `closesocket'
./libstun.a(stun.o): In function `stunParseHostName':
stun.c:(.text+0x1a62): undefined reference to `getErrno'
./libstun.a(stun.o): In function `stunFindLocalInterfaces':
stun.c:(.text+0x1d6a): undefined reference to `closesocket'
./libstun.a(stun.o): In function `stunSendTest':
stun.c:(.text+0x2110): undefined reference to `sendMessage'
./libstun.a(stun.o): In function `stunTest':
stun.c:(.text+0x225d): undefined reference to `openPort'
stun.c:(.text+0x22ec): undefined reference to `getMessage'
./libstun.a(stun.o): In function `stunNatType':
stun.c:(.text+0x24ea): undefined reference to `openPort'
stun.c:(.text+0x2512): undefined reference to `openPort'
stun.c:(.text+0x275e): undefined reference to `getErrno'
stun.c:(.text+0x2a68): undefined reference to `getMessage'
stun.c:(.text+0x2c80): undefined reference to `openPort'
stun.c:(.text+0x2ca1): undefined reference to `closesocket'
stun.c:(.text+0x2cd2): undefined reference to `closesocket'
stun.c:(.text+0x2ced): undefined reference to `closesocket'
./libstun.a(stun.o): In function `stunOpenSocket':
stun.c:(.text+0x2e1d): undefined reference to `openPort'
stun.c:(.text+0x2ecc): undefined reference to `getMessage'
./libstun.a(stun.o): In function `stunOpenSocketPair':
stun.c:(.text+0x309f): undefined reference to `openPort'
stun.c:(.text+0x30db): undefined reference to `closesocket'
stun.c:(.text+0x31de): undefined reference to `getMessage'
stun.c:(.text+0x330a): undefined reference to `closesocket'
stun.c:(.text+0x3386): undefined reference to `closesocket'
stun.c:(.text+0x33b3): undefined reference to `closesocket'
collect2: ld returned 1 exit status
```
The main function in client.c will call functions in udp.c and stun.c. Funcions in stun.c will call functions in udp.c. I can't figure out why the link error happen. What shall I do? Thank you.

---

