---
title: "Problem when complie C application"
date: 2006-01-30
forum: Packaging and Compiling Programs
---

### Post by healychan on 2006-01-30
Hello,

I was trying to complie a network application with make.
The system gave me this```
gcc -Wmissing-prototypes -c TCPdaytime.c
gcc -Wmissing-prototypes -c connectsock.c
connectsock.c:33: warning: no previous prototype for ‘connectsock’
gcc -Wmissing-prototypes -c errexit.c
errexit.c:14: warning: no previous prototype for ‘errexit’
gcc -Wmissing-prototypes -c connectTCP.c
connectTCP.c:17: warning: no previous prototype for ‘connectTCP’
gcc -Wmissing-prototypes -c connectUDP.c
connectUDP.c:17: warning: no previous prototype for ‘connectUDP’
gcc -o TCPdaytime TCPdaytime.o  connectsock.o errexit.o connectTCP.o connectUDP.o -lsocket -lnsl
/usr/bin/ld: cannot find -lsocket
collect2: ld returned 1 exit status
make: *** [TCPdaytime] Error 1

```

and this is my makefile
```
TCP_CL_OBJ = TCPdaytime.o
UDP_CL_OBJ = UDPtime.o
OBJ = connectsock.o errexit.o connectTCP.o connectUDP.o
FLAGS = -Wmissing-prototypes

all:    TCPdaytime UDPtime

TCPdaytime:     $(TCP_CL_OBJ) $(OBJ)
        gcc -o TCPdaytime $(TCP_CL_OBJ) $(OBJ) -lsocket -lnsl

TCPdaytime.o: TCPdaytime.c
        gcc $(FLAGS) -c TCPdaytime.c

UDPtime:        $(UDP_CL_OBJ) $(OBJ)
        gcc -o UDPtime $(UDP_CL_OBJ) $(OBJ) -lsocket -lnsl

UDPtime.o: UDPtime.c
        gcc $(FLAGS) -c UDPtime.c

connectsock.o: connectsock.c
        gcc $(FLAGS) -c connectsock.c

connectTCP.o:   connectTCP.c
        gcc $(FLA
GS) -c connectTCP.c

connectUDP.o:   connectUDP.c
        gcc $(FLAGS) -c connectUDP.c

errexit.o: errexit.c
        gcc $(FLAGS) -c errexit.c

clean:
        rm $(TCP_CL_OBJ) $(UDP_CL_OBJ) $(OBJ)
```
Was it because some lib was missing?? 
Many thanks

---

### Post by Juergen on 2006-01-30
> /usr/bin/ld: cannot find -lsocket
If you see a message like this you can usually just replace the '-l' with 'lib' and have the name of the missing library.

So I think you have to install 'happycoders-libsocket' and, to compile against it, 'happycoders-libsocket-dev' with apt or synaptic.
Hm, but it seems to be a C++-lib and your proggy 'pure' C - I don't know if this will work. Maybe you need another lib with the same name...

---

### Post by healychan on 2006-01-31
[QUOTE=Juergen]If you see a message like this you can usually just replace the '-l' with 'lib' and have the name of the missing library.[/QUOTE]
Do you mean I should do like this  ```
gcc -o TCPdaytime $(TCP_CL_OBJ) $(OBJ) libsocket libnsl

```

I can complie it on Solaris with the same makefile. I though it will be the same for Linux since they are using gcc.

---

