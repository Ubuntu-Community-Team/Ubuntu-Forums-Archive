---
title: "lex"
date: 2007-03-29
forum: Programming Talk
---

### Post by ceezax on 2007-03-29
i got that error msg 

configure: error: Your operating system's lex is insufficient to compile
 libpcap.  flex is a lex replacement that has many advantages, including
 being able to compile libpcap.  For more information, see
 [http://www.gnu.org/software/flex/flex.html](http://www.gnu.org/software/flex/flex.html) .

how do i solve that problem ??

---

### Post by lnostdal on 2007-03-29
Why are you compiling libpcap from source?

```

root@ibmr52:~# aptitude search libpcap
p   libpcap-dev                                                                 - Development library for libpcap (transitional package)                               
p   libpcap-ruby1.8                                                             - Ruby interface for the libpcap packet capture library                                
p   libpcap0.7                                                                  - System interface for user-level packet capture                                       
p   libpcap0.7-dev                                                              - Development library and header files for libpcap 0.7                                 
i   libpcap0.8                                                                  - System interface for user-level packet capture                                       
p   libpcap0.8-dev                                                              - Development library and header files for libpcap 0.8  

```

..you probably want some of the -dev packages if you want to do programming using the pcap library.

---

### Post by lnostdal on 2007-03-29
but to answer your question; have you tried the obvious after reading the plain english message?

```

aptitude search flex

```
..?

---

### Post by ceezax on 2007-03-29
after entering that command i got that output

root@muhammad-desktop:/home/muhammad# aptitude search flex
p   cl-flexi-streams                - Flexi-streams: Flexible bivalent streams f
p   flex                            - A fast lexical analyzer generator.        
p   flex-doc                        - Documentation for flex (a fast lexical ana
p   flex-old                        - The old version of the fast lexical analyz
p   flex-old-doc                    - Documentation for an old flex (a fast lexi
p   flexbackup                      - Flexible backup tool for small to medium s
p   flexloader                      - utility to configure SRAM based ALTERA dev
v   flexmem                         -                                           
p   flexml                          - generate fast validating XML processors an
p   jflex                           - lexical analyzer generator for Java       
p   libcflexplugin                  - MuscleCard Cryptoflex PlugIn              
p   libslbreflex-dev                - Reflex 62/64 smartcard reader CT-API devel
p   libslbreflex2                   - Reflex 62/64 smartcard reader PCSC and CT-


hint : i don't need libpcap for programming , i just want to install a program that require libpcap , that's all 

so what shall i do now ??

---

### Post by lnostdal on 2007-03-29
what program requires libpcap? have you considered checking if you can get that program via the ubuntu repositories instead of installing it from source "manually"possibly messing up your whole system in the process..?

well, now that you've searched and found what you where looking for you can install it .. [https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement) ..etc..

edit:
*sigh* .. and you can just install libpcap instead of compiling that from source (also) in the first place .. but stop doing all of this .. it is stupid .. install your software from the ubuntu repositories or state clearly when posting that you actually _need_ to install your software from source (also mentioning the name of that software ...)

---

### Post by ceezax on 2007-03-29
hi there

after applying the command 

aptitude install flex , i installed felx then i tried to ./configure libpcap again and i did 

, then after entering (make) command , i got that error 

lex -t scanner.l > $$.scanner.c; mv $$.scanner.c scanner.c
yacc -d grammar.y
make: yacc: Command not found
make: *** [grammar.c] Error 127

so how this could be done ?

---

### Post by lnostdal on 2007-03-29
Listen .. before we continue down this path I'm gonna have to insist you tell me what software you want to install - ok?

---

### Post by ceezax on 2007-03-29
i think i used the aptitude command and installed all the p i need :) 

then after i try to install , i did the ./configure and it completed successfully then 

when i tried to do (make) command i got that following error

root@muhammad-desktop:/home/muhammad/Desktop/dsniff-2.3# make
gcc -g -O2 -D_BSD_SOURCE  -DDSNIFF_LIBDIR=\"/usr/local/lib/\" -I.    -I/usr/local/BerkeleyDB/include -I/usr/local/ssl/include  -I./missing -c ./arpspoof.c
./arpspoof.c:25: warning: ‘struct ether_addr’ declared inside parameter list
./arpspoof.c:25: warning: its scope is only this definition or declaration, which is probably not what you want
./arpspoof.c:26: warning: ‘struct ether_addr’ declared inside parameter list
./arpspoof.c: In function ‘arp_send’:
./arpspoof.c:49: warning: passing argument 1 of ‘libnet_get_hwaddr’ from incompatible pointer type
./arpspoof.c:49: error: too many arguments to function ‘libnet_get_hwaddr’
./arpspoof.c:60: warning: passing argument 6 of ‘libnet_build_ethernet’ from incompatible pointer type
./arpspoof.c:60: error: too few arguments to function ‘libnet_build_ethernet’
./arpspoof.c:64: error: ‘ETH_H’ undeclared (first use in this function)
./arpspoof.c:64: error: (Each undeclared identifier is reported only once
./arpspoof.c:64: error: for each function it appears in.)
./arpspoof.c:64: error: too few arguments to function ‘libnet_build_arp’
./arpspoof.c:67: warning: passing argument 1 of ‘ether_ntoa’ from incompatible pointer type
./arpspoof.c:71: warning: passing argument 1 of ‘ether_ntoa’ from incompatible pointer type
./arpspoof.c:77: warning: passing argument 1 of ‘ether_ntoa’ from incompatible pointer type
./arpspoof.c:80: warning: passing argument 1 of ‘ether_ntoa’ from incompatible pointer type
./arpspoof.c: In function ‘arp_find’:
./arpspoof.c:114: warning: passing argument 2 of ‘arp_cache_lookup’ from incompatible pointer type
./arpspoof.c: In function ‘main’:
./arpspoof.c:181: warning: assignment makes pointer from integer without a cast
make: *** [arpspoof.o] Error 1


so what is that supposed to be ??

---

### Post by ceezax on 2007-03-29
is that's all :D 
,, 

ok , i am trying to install dsniff

---

### Post by ceezax on 2007-03-29
look

i totally solved the problem :)

thank you for you care

only one last question

after installing package with the aptitdue install command

where is the directory for that installed package????

---

### Post by lnostdal on 2007-03-29
try ..

```
dpkg -L dsniff
```

.. or you can use Synaptic (GUI):

* find the package (search)
* right click it then select properties
* then select the "installed files" pane

edit:
dsniff is in the path though .. so you can just type "dsniff --help" to start it (and show some help .. also see "man dsniff" .. press q to leave the man-page)

---

