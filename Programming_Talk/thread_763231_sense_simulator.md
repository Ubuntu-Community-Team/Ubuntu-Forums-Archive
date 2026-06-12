---
title: "sense simulator"
date: 2008-04-22
forum: Programming Talk
---

### Post by fellya on 2008-04-22
hello everyone,
i've installed sense simulator, i've also installed gcc compliler. i'm trying to run compile the tutorial about sense simulator using the command that they have provided but i'm getting an error message.
the command that i'm using is: cxx sim_routing.cc
the error is: bash: cxx: command not found.
can somebody help me to sort it out?
thanks

---

### Post by nanotube on 2008-04-23
well according to the docs, cxx is the compc++ compiler that comes with the sense package. first, you have to compile the whole thing using gcc, then the cxx binary will be located somewhere in the directory hierarchy of the compiled package. since it will not be in the path, you have to specify cxx by complete full or relative path, you can't just say "cxx stuff".

---

### Post by fellya on 2008-04-23
thank you for this help.
the problem is if you visit this page ([http://www.ita.cs.rpi.edu/sense/index.html](http://www.ita.cs.rpi.edu/sense/index.html)) is about sense simulator tutorial. at this page they explain how to compile using cxx but it is not working.
I've used: g++ -g -Wall -o my_file my_file.cc
this compilation is giving me many errors but this should not be the case since i'm trying to use the tutorial example.
therefore something must be wrong with the compilation command.
can someone try to help me?
thanks

---

### Post by fellya on 2008-04-23
hello everyone,
i've fixed the problem that i mentioned above by changing the path in my environment variables.
but now cxx my_file.cc is now working.
there is another command that i have to make in order to fully compile the codes, the command is: g++ -Wall -o my_file my_file.cxx
but doing this command i'm getting the following error:
/cygdrive/c/Users/Owner/Appdata?local/Temp/ccrMFQW5.o:my_file.cxx:(.text+0×510d):undefined to 'Visualizer::nodeLocation(int, double, doyble)'

can someone help me about figuring out this problem of undefined to ' Visualizer.....?

---

### Post by Talpur on 2008-11-11
Still have Visualizer Problem in SENSE.......??

contact me at 
[email]taimoortalpur@hotmail.com[/email]

---

### Post by ksudan on 2009-06-02
Hi everyone,
 
I have just started working with the sense simulator. When i run the command
$ g++ -Wall -o sim_routing sim_routing.cxx
 
i get the following error
/cygdrive/c/Users/ABC/AppData/Local/Temp/ccKaU8Wb.o:sim_routing.cxx:(.text+
0x510d): undefined reference to `Visualizer::nodeLocation(int, double, double)'
/cygdrive/c/Users/ABC/AppData/Local/Temp/ccKaU8Wb.o:sim_routing.cxx:(.text+
0x74aa): undefined reference to `Visualizer::instantiate()'
collect2: ld returned 1 exit status
 
i dont understand why this is happening bcoz i haven't changed anything in the code yet.
 
any pointers will be really helpful.
 
Thanks in advance

---

### Post by Zugzwang on 2009-06-02
> **ksudan said:**
> 
i get the following error
/cygdrive/c/Users/ABC/AppData/Local/Temp/ccKaU8Wb.o:sim_routing.cxx:(.text+
0x510d): undefined reference to `Visualizer::nodeLocation(int, double, double)'
/cygdrive/c/Users/ABC/AppData/Local/Temp/ccKaU8Wb.o:sim_routing.cxx:(.text+
0x74aa): undefined reference to `Visualizer::instantiate()'
collect2: ld returned 1 exit status
 
i dont understand why this is happening bcoz i haven't changed anything in the code yet.


Looks like you will need to link against some more c++ source files (containing the implementation of some "Visualizer" methods) or a library. The documentation might contain details.

---

### Post by ksudan on 2009-06-02
Thanks Zugzwang. That was helpful.

For others like me, use the following command in which the visualizer.a library needs to be linked.

g++ -Wall -o sim_routing sim_routing.cxx ../../libraries/visualizer/lib/libvisualizer.a

This library can be found under sense-3.0.3/code/libraries/visualizer/lib

---

### Post by raziin on 2010-08-01
Hello..i am new to ubuntu and tring to install sense simulator for my univercity project.
I get some erros while tring to install it,
I follow the instructions from : [http://www.ita.cs.rpi.edu/sense/index.html](http://www.ita.cs.rpi.edu/sense/index.html)
while giving : make test a get the following error:
---------- sim_flooding ----------

/bin/sh: ./sim_flooding: not found

---------- sim_aodv ----------

/bin/sh: ./sim_aodv: not found

---------- sim_dsr ----------

/bin/sh: ./sim_dsr: not found

---------- sim_shr ----------

/bin/sh: ./sim_shr: not found

---------- sim_shr_loc ----------

/bin/sh: ./sim_shr_loc: not found


and continues like this...

Does anybody know  what to do?
thanks for your time...

---

### Post by Destonius on 2010-10-19
g++ -Wall -o sim_routing sim_routing.cxx ../../libraries/visualizer/lib/libvisualizer.a


after this when i try to run the simulation it shows 
$ sim_routing 1000 110 2000 11 1000 20
bash: sim_routing: command not found

Can you pls help me to run this simulation

Thank You

---

### Post by spjackson on 2010-10-19
> **Destonius said:**
> g++ -Wall -o sim_routing sim_routing.cxx ../../libraries/visualizer/lib/libvisualizer.a

If this command completes without error, then it creates the executable program sim_routing in the current directory.
> 
after this when i try to run the simulation it shows 
$ sim_routing 1000 110 2000 11 1000 20
bash: sim_routing: command not found
And this indicates that sim_routing is not in your PATH, because "." is not in your PATH. One way around this is to put "./" in front of your command, e.g.
```

$ ./sim_routing 1000 110 2000 11 1000 20

```

---

### Post by Destonius on 2010-10-19
Thank You very much for the response sir

I am very new to SENSE Simulator,I want to learn more about SENSE.
How can i visualize the code. How can i get Grid disabled 
There is any sample source code for creating nodes. 

Thank You

---

### Post by Destonius on 2010-10-19
Thank You very much for the response sir

$ ./sim_routing 1000 110 2000 11 1000 20
StopTime: 1000, Number of Nodes: 110, Terrain: 2000 by 2000
Number of Sources: 11, Packet Size: 20, Interval: 20.000000
X: 2000.000000, Y: 2000.000000, gridsize: 1106.166755
Grid disabled
APP -- packets sent: 1005, received: 427, success rate: 0.425, delay: 0.554
13204016.000000 427
NET -- packets sent: 69962, received: 354622, average hop: 30922.754
MAC -- packets sent: 69962, received: 354622
---------------------------------------------------------------------------
CostSimEng with HeapQueue, stopped at 1000.000000
10304700 events processed in 12.465 seconds, event processing rate: 826691

I am very new to SENSE Simulator,I want to learn more about SENSE.
How can i visualize the code. How can i get Grid disabled 
There is any sample source code for creating nodes. 

Thank You

---

### Post by Destonius on 2010-10-20
karunya@destonius-desktop:~/sense-3.0.3/code$ make
cd libraries/parseConfig/src && make
make[1]: Entering directory `/home/karunya/sense-3.0.3/code/libraries/parseConfig/src'
yacc -d -o CIParser.c CIParser.y
flex -oCIScanner.c CIScanner.l
make[1]: Leaving directory `/home/karunya/sense-3.0.3/code/libraries/parseConfig/src'
make[1]: Entering directory `/home/karunya/sense-3.0.3/code/libraries/parseConfig/src'
gcc -Wall -c -I../inc -I../../visualizer/inc -I../../../common -O3   -Wall -O3  -DVISUAL_ROUTE -DVR_SIZE=30   CIParser.c -o ../obj/CIParser.o
CIParser.c: In function &#8216;yyparse&#8217;:
CIParser.c:1315: warning: implicit declaration of function &#8216;yylex&#8217;
CIParser.y:93: warning: implicit declaration of function &#8216;atoi&#8217;
CIParser.y:95: warning: implicit declaration of function &#8216;atof&#8217;
CIParser.c:1625: warning: implicit declaration of function &#8216;yyerror&#8217;
gcc -Wall -c -I../inc -I../../visualizer/inc -I../../../common -O3   -Wall -O3  -DVISUAL_ROUTE -DVR_SIZE=30   CIScanner.c -o ../obj/CIScanner.o
CIScanner.c:1232: warning: &#8216;yyunput&#8217; defined but not used
CIScanner.c:1273: warning: &#8216;input&#8217; defined but not used
g++ -Wall -c -I../inc -I../../visualizer/inc -I../../../common -O3   -Wall -O3  -DVISUAL_ROUTE -DVR_SIZE=30   CIParseRtns.cpp -o ../obj/CIParseRtns.o
CIParseRtns.cpp: In function &#8216;void initNode()&#8217;:
CIParseRtns.cpp:35: error: &#8216;assert&#8217; was not declared in this scope
CIParseRtns.cpp: In function &#8216;void saveNode()&#8217;:
CIParseRtns.cpp:45: error: &#8216;assert&#8217; was not declared in this scope
CIParseRtns.cpp: In function &#8216;void setId(int)&#8217;:
CIParseRtns.cpp:57: error: &#8216;assert&#8217; was not declared in this scope
CIParseRtns.cpp: In function &#8216;void setLocation(double, double)&#8217;:
CIParseRtns.cpp:69: error: &#8216;assert&#8217; was not declared in this scope
CIParseRtns.cpp: In function &#8216;void gotInteger(int)&#8217;:
CIParseRtns.cpp:92: error: &#8216;assert&#8217; was not declared in this scope
CIParseRtns.cpp: In function &#8216;void gotEvent(double, SimEvent)&#8217;:
CIParseRtns.cpp:114: error: &#8216;assert&#8217; was not declared in this scope
make[1]: *** [../obj/CIParseRtns.o] Error 1
make[1]: Leaving directory `/home/karunya/sense-3.0.3/code/libraries/parseConfig/src'
make: *** [all] Error 2

I cant install SENSE in my system.Please give me some solution

Thank You

---

### Post by Zugzwang on 2010-10-21
> **Destonius said:**
> I cant install SENSE in my system.Please give me some solution


I'm afraid that your posts are a little bit confusing. You had this "sim_routing" program running already, right? So why do you want to compile something else now? 

The point is the following: Except for the people who actually asked about the "SENSE simulator" here, no one has a clue what it actually is and only gives generic answers to the questions raised that are in principle applicable to every program.

Here comes another generic answer: As far as your compiling problem is concerned, it might have to do with the fact that recently, the GNU compiler people removed some "definition overlaps" from the headers files. So you might want to add to include the line "#include <cassert>" close to the top in "CIParseRtns.cpp".

---

### Post by balambika on 2011-10-22
> **fellya said:**
> hello everyone,
i've fixed the problem that i mentioned above by changing the path in my environment variables.
but now cxx my_file.cc is now working.
there is another command that i have to make in order to fully compile the codes, the command is: g++ -Wall -o my_file my_file.cxx
but doing this command i'm getting the following error:
/cygdrive/c/Users/Owner/Appdata?local/Temp/ccrMFQW5.o:my_file.cxx:(.text+0×510d):undefined to 'Visualizer::nodeLocation(int, double, doyble)'
 
can someone help me about figuring out this problem of undefined to ' Visualizer.....?
 
Hi,
 
I am having the same issue with the cxx command. Can you please tell how you made the changes to the PATH variable.
 
Thanks

---

