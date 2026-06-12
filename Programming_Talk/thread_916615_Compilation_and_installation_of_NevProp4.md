---
title: "Compilation and installation of NevProp4"
date: 2008-09-11
forum: Programming Talk
---

### Post by wess126 on 2008-09-11
Hi all,

My system is a Dell Precision 690 running Ubuntu 7.10

I am trying to install some software to run an Artificial Neural Network (non-linear regression) and am having some trouble getting it going. The software is called NevProp4 and was downloaded from the following website. 

[http://brain.cs.unr.edu/FILES_PHP/show_papers.php](http://brain.cs.unr.edu/FILES_PHP/show_papers.php) 
(Look down at the bottom of the page).

Once the software has been unzipped etc, the README.source.txt file suggests a make command for use on Linux

make "CC = gcc"

I run this command and get the following output. Unfortunately I am a noob when it comes to programming and don't really understand the output. I have emailed the author but am yet to get a reply.

Any help on this matter would be greatly appreciated as this software does exactly what I need and would really make my life a whole lot easier.

Many thanks for your help,
Wesley

************************output from make command************************

wroberts@wroberts-desktop:~/progs/NevProp/NevProp/NPsource$ make "CC = gcc"
/bin/rm -f 1ofN.o
gcc -g -DHAVE_RAND48=1    -c 1ofN.c
/bin/rm -f aNet.o
gcc -g -DHAVE_RAND48=1    -c aNet.c
aNet.c: In function ‘CONNECT_ARCHITECTURE’:
aNet.c:520: warning: incompatible implicit declaration of built-in function ‘exit’
aNet.c:526: warning: incompatible implicit declaration of built-in function ‘exit’
/bin/rm -f ards.o
gcc -g -DHAVE_RAND48=1    -c ards.c
/bin/rm -f atox.o
gcc -g -DHAVE_RAND48=1    -c atox.c
/bin/rm -f auTrn.o
gcc -g -DHAVE_RAND48=1    -c auTrn.c
/bin/rm -f boot.o
gcc -g -DHAVE_RAND48=1    -c boot.c
/bin/rm -f calibrate.o
gcc -g -DHAVE_RAND48=1    -c calibrate.c
/bin/rm -f cind.o
gcc -g -DHAVE_RAND48=1    -c cind.c
/bin/rm -f create.o
gcc -g -DHAVE_RAND48=1    -c create.c
/bin/rm -f datPr.o
gcc -g -DHAVE_RAND48=1    -c datPr.c
/bin/rm -f describe.o
gcc -g -DHAVE_RAND48=1    -c describe.c
/bin/rm -f dmem.o
gcc -g -DHAVE_RAND48=1    -c dmem.c
/bin/rm -f effWts.o
gcc -g -DHAVE_RAND48=1    -c effWts.c
/bin/rm -f eigens.o
gcc -g -DHAVE_RAND48=1    -c eigens.c
/bin/rm -f ensemble.o
gcc -g -DHAVE_RAND48=1    -c ensemble.c
/bin/rm -f epsilon.o
gcc -g -DHAVE_RAND48=1    -c epsilon.c
/bin/rm -f extra.o
gcc -g -DHAVE_RAND48=1    -c extra.c
/bin/rm -f gammas.o
gcc -g -DHAVE_RAND48=1    -c gammas.c
/bin/rm -f getdata.o
gcc -g -DHAVE_RAND48=1    -c getdata.c
/bin/rm -f hessian.o
gcc -g -DHAVE_RAND48=1    -c hessian.c
/bin/rm -f init.o
gcc -g -DHAVE_RAND48=1    -c init.c
/bin/rm -f ivs.o
gcc -g -DHAVE_RAND48=1    -c ivs.c
/bin/rm -f netTr.o
gcc -g -DHAVE_RAND48=1    -c netTr.c
/bin/rm -f np.o
gcc -g -DHAVE_RAND48=1    -c np.c
/bin/rm -f parUpd.o
gcc -g -DHAVE_RAND48=1    -c parUpd.c
/bin/rm -f qsort.o
gcc -g -DHAVE_RAND48=1    -c qsort.c
qsort.c: In function ‘quicksort’:
qsort.c:76: warning: incompatible implicit declaration of built-in function ‘calloc’
/bin/rm -f rank.o
gcc -g -DHAVE_RAND48=1    -c rank.c
/bin/rm -f textf.o
gcc -g -DHAVE_RAND48=1    -c textf.c
textf.c: In function ‘PRINT_PRED_TO_FILE’:
textf.c:812: warning: incompatible implicit declaration of built-in function ‘calloc’
/bin/rm -f trakmem.o
gcc -g -DHAVE_RAND48=1    -c trakmem.c
/bin/rm -f usr_resp.o
gcc -g -DHAVE_RAND48=1    -c usr_resp.c
/bin/rm -f util.o
gcc -g -DHAVE_RAND48=1    -c util.c
/bin/rm -f np
gcc -g -o np 1ofN.o aNet.o ards.o atox.o auTrn.o boot.o calibrate.o cind.o create.o datPr.o describe.o dmem.o effWts.o eigens.o ensemble.o epsilon.o extra.o gammas.o getdata.o hessian.o init.o ivs.o netTr.o np.o parUpd.o qsort.o rank.o textf.o trakmem.o usr_resp.o util.o -lm
effWts.o: In function `INTER_UPDATE':
/home/wroberts/progs/NevProp/NevProp/NPsource/effWts.c:4207: warning: the `gets' function is dangerous and should not be used.
np.o: In function `READ_NET_FILE':
/home/wroberts/progs/NevProp/NevProp/NPsource/np.c:2826: undefined reference to `strnicmp'
collect2: ld returned 1 exit status
make: *** [np] Error 1

---

