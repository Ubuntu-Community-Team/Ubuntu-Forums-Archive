---
title: "[SOLVED] possible gcc version conflicts. compiler error"
date: 2008-05-12
forum: Programming Talk
---

### Post by zfh on 2008-05-12
Hi All, 
I am having problem with using gcc (possibly compiler version conflicts).

I am using gcc for academic purposes, so nearly all my output files are (should) consist of a two-column data, and I want to plot these data. The problem is that ALL I got is the weird characters as follow: 

[PHP]zfh@laptop:~/Desktop$ gcc -o data.dat prog.c -lm

zfh@laptop:~/Desktop$ gnuplot "data.dat"

ELF
^
"data.dat", line 1: invalid character 


zfh@laptop:~/Desktop$[/PHP]

if I cat the output (this happens to ALL "good" c-programs)

zfh@laptop:~/Desktop$ cat data.dat
[PHP]ELF`&#65533;4$4 ($!44&#65533;4&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;	&#65533;	&#65533;	&#65533;&#65533;&#65533;&#65533;(,&#65533;	&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;((&#65533;(&#65533;  Q&#65533;td/lib/ld-linux.so.2GNU
                                                  	

  
&#65533;K&#65533;&#65533;
      q&#65533;2f7&j9Y T.&E|&#65533;libm.so.6__gmon_start___Jv_RegisterClassessinsqrtcoslibc.so.6_IO_stdin_usedputs__stack_chk_failprintf__libc_start_mainGLIBC_2.0&#65533;&#1050;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;       U&#65533;&#65533;S&#65533;&#65533;&#65533;[&#65533;&#65533;(&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;t&#65533;&#65533;&#65533;&#65533;dX[&#65533;&#65533;&#65533;5&#1562;&#65533;%&#1818;&#65533;%&#65533;&#65533;h&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;%&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;%&#65533;&#65533;h&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;%&#65533;&#65533;h&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;%&#65533;&#65533;h &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;%&#65533;&#65533;h(&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;%&#65533;&#65533;h0&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;%&#65533;&#65533;h8&#65533;p&#65533;&#65533;&#65533;1&#65533;^&#65533;&#65533;&#65533;&#65533;&#65533;PTRh&#65533;&#65533;h&#1032;QVh&#65533;&#65533;&#65533;o&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;U&#65533;&#65533;&#65533;&#65533;=
                                          &#65533;t
                                            &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;u&#65533;&#65533;
                                                           &#65533;&#65533;ÐU&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;t
                                                                      [^_]Ë$Ð&#65533;U&#8804;Ð´WÒ= %12.6&#9226; %12.6&#9226;&#65533;&#65533;&#65533;&#65533;&#65533;u&#65533;&#65533;&#65533;[]Ð&#65533;&#65533;U&#65533;&#65533;S&#65533;&#65533;&#65533;[&#65533;&#65533;l&#65533;&#65533;&#65533;&#65533;Y[&#65533;&#65533;&#65533;TXA»þÖÃE

           Ð&#9149;A     @ŸÀ     è¬À      $@-DTû!@      I@    ÿÿÿÿ    ÿÿÿÿ                 ;
   \‰   Hõþÿ&#9146;ˆ   X‚   ¨
   —
                       Ôš   @            &#9670;ƒ   Xƒ          þÿÿƒÿÿÿ&#9146;ðÿÿ&#9146;ð‚                                                    ø™        æƒöƒ„„&„6„F„V„        ð™ GCC: (GNU) 4.2.3 (U&#9225;&#9508;&#9532;&#9500;&#9508; 4.2.3-2&#9508;&#9225;&#9508;&#9532;&#9500;&#9508;7)  GCC: (GNU) 4.2.3 (U&#9225;&#9508;&#9532;&#9500;&#9508; 4.2.3-2&#9508;&#9225;&#9508;&#9532;&#9500;&#9508;7)  GCC: (GNU) 4.2.3 (U&#9225;&#9508;&#9532;&#9500;&#9508; 4.2.3-2&#9508;&#9225;&#9508;&#9532;&#9500;&#9508;7)  GCC: (GNU) 4.2.3 (U&#9225;&#9508;&#9532;&#9500;&#9508; 4.2.3-2&#9508;&#9225;&#9508;&#9532;&#9500;&#9508;7)  GCC: (GNU) 4.2.3 (U&#9225;&#9508;&#9532;&#9500;&#9508; 4.2.3-2&#9508;&#9225;&#9508;&#9532;&#9500;&#9508;7)  GCC: (GNU) 4.2.3 (U&#9225;&#9508;&#9532;&#9500;&#9508; 4.2.3-2&#9508;&#9225;&#9508;&#9532;&#9500;&#9508;7)  GCC: (GNU) 4.2.3 (U&#9225;&#9508;&#9532;&#9500;&#9508; 4.2.3-2&#9508;&#9225;&#9508;&#9532;&#9500;&#9508;7) [/PHP]

the above is not the entire displayed weird characters, but you get the ideas. 
Thanks in advanced.

---

### Post by joe_bruin on 2008-05-12
gcc is a compiler.  It turns your code into an executable.  It does not turn your code into data that gnuplot is going to like.  I believe what you're trying to accomplish is compile prog.c into an executable, run it, and use gnuplot with the data that it produces.

---

### Post by zfh on 2008-05-12
Hi,
I kind of tried that already, the output should be just a data file. I just want to plot the file, if I plot a.out, the same error happens. 

[PHP]zfh@laptop:~/Desktop$ gcc prog.c -lm
zfh@laptop:~/Desktop$ cp a.out data.dat
zfh@laptop:~/Desktop$ gnuplot "data.dat"

ELF
^
"data.dat", line 1: invalid character 
zfh@laptop:~/Desktop$[/PHP]

Thanks,

---

### Post by red_Marvin on 2008-05-12
Technically, what you try to do (based on your terminal commands) is compile prog.c into an executable, and then plot the contents of the executable. If the file prog.c contains the data you should run:
*gnuplot prog.c*
But since gcc doesn't give errors it is probably source code and I guess it should output the data when running it, thus run:
[i]./a.out > data.dat
gnuplot data.dat[/i]
(I don't know if gnuplot supports piping, if it does you should be able to run *./a.out | gnuplot* too)

---

### Post by zfh on 2008-05-12
Thanks, RM
I got it this time. you are right about a.out gives the correct output. 

I used cp a.out data.dat instead of what you mentioned with ./a.out > data.dat. That probably means I was copying an executable file into a data file. Thanks again.

---

