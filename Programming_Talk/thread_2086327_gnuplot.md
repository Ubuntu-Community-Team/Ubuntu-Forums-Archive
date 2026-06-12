---
title: "gnuplot"
date: 2012-11-20
forum: Programming Talk
---

### Post by iain150 on 2012-11-20
I'm having trouble creating a plot from a data file ( table.data ) using table.gnu.
I am using the bash prompt,
p2t16@linux07:~/Lab05/lookup$ gnuplot < table.gnu
I have attached the files within a zip file.

I was a bit worried that this post doesn't convey my appreciation for your help and I thought of a reply to my own post that I found amusing, it goes as follows,

"That post has so little emotion it seems as though the worldwide LHC computing grid has gained sentience and is trying to understand itself".

Iain Taylor

---

### Post by iain150 on 2012-11-20
Also the male file contains the lines:


CC=gcc
libs=-lm
objs=lookup.o main.o

lookup.o: lookup.c
    $(CC) -c $^ -o $@

main.o: main.c
    $(CC) -c $^ -o $@

main: $(objs)
    $(CC) $^ -o $@ $(libs)

.PHONY: clear
clear:
    rm -f *.o




my question is what does "-lm" stand for i cannot find it on google.

---

### Post by iain150 on 2012-11-20
I need to g home now (was in university), I will log in when I get home.

---

### Post by drmrgd on 2012-11-20
Deleted

Nevermind.  I don't know what I'm talking about.  I found that entering in the commands one line at a time into GNU plot just as you have them seems to work fine.  I'm not sure why it's not reading from the table.gnu file correctly.  Better let an expert answer this one!

---

### Post by steeldriver on 2012-11-20
Hmm well your zip file worked for me - with the one exception that I renamed the files from

```
table (copy).data table (copy).gnu

```to

```
table.data table.gnu

```I just unzipped it in a new dir, then cd'ed there and started interactive gnuplot, then loaded the .gnu file

```
~/Documents/forums/iain150$ gnuplot

    G N U P L O T
    Version 4.4 patchlevel 3
    last modified March 2011
    System: Linux 3.2.0-33-generic-pae

    Copyright (C) 1986-1993, 1998, 2004, 2007-2010
    Thomas Williams, Colin Kelley and many others

    gnuplot home:     http://www.gnuplot.info
    faq, bugs, etc:   type "help seeking-assistance"
    immediate help:   type "help"
    plot window:      hit 'h'

Terminal type set to 'wxt'
gnuplot> 
gnuplot> load "table.gnu"
gnuplot>
```I got a nice plot of 'Kinetic energy' versus 'Velocity'

Like drmgd above I don't understand what your makefile has to do with gnuplot

---

### Post by drmrgd on 2012-11-20
Ahhhh...I think that's the difference; you started an interactive session and then loaded the file.  I was trying to load it from the commandline just as the OP did and couldn't get a plot generated.  Seems to work just fine if you follow Steeldriver's method.  I need to learn Gnuplot.  Seems very useful (I've been working with R these days).

---

### Post by iain150 on 2012-11-20
yes the commands work fine but I should be able to get 2 graphs,
one of velocity and kinetic energy and one of velocity and relative mass when I run the bash line 

gnuplot < table.gnu,

which it does not do, it makes the file but there is no data,
ie no graph.

I'm still new to c and this is my first attempt at a gnuplot so I don't know why my file ( table.gnu ) isn't working even if the commands work when entered manually on the command line.

---

### Post by iain150 on 2012-11-20
The makefile is nothing to do with gnuplot it is a seperate piece of code that I don't know what it does.

---

### Post by iain150 on 2012-11-20
Thanks for the feedback so far.

---

### Post by steeldriver on 2012-11-20
Ah I see - well I'm not much of a gnuplot expert but you probably need to tell it where to plot the 2 graphs - else by default it probably overwrites the first one with the second one

e.g. add a new term command before the second plot

```
set autoscale
unset logscale; set logscale y

set output 'Reletivistic-mass.png'
set xlabel "Velocity (m/s)"
set ylabel "Relitivistic mass (Kg)"
plot "table.data" using 1:2 title "Relitivistic Mass" w line

**[COLOR=Red]set term wxt 1[/COLOR]**

set output 'Kinetic-energy.png'
set xlabel "Velocity (m/s)"
set ylabel "Kinetic energy (J)"
plot "table.data" using 1:3 title "Kinetic Energy" w line
```You may want to replace 'wxt' with the default display terminal type for your environment

---

### Post by steeldriver on 2012-11-20
Oh and regarding your makefile question '-lm' is a directive telling the linker that your executable needs symbols from the standard math library 'libm'

---

### Post by iain150 on 2012-11-20
thanks for the speedy response and excelent answer I am just about to check it.

---

### Post by iain150 on 2012-11-20
I've been trying to figure this out and I typed 
$TERM
to get my terminal and substituted like you said but it has not worked, all I get is a bunch of gibberish in my terminal, eg

F/c;F/c;F/c;G/c;G/c;G/c;H/d;H/d;H/d;H/d;I/d;I/d;I/d;J/d;J/d;J/d;J/d;K/d;K/d;K/e;L/e;L/e;L/e;L/e;M/e;M/e;M/e;N/e;N/e;N/e;N/e;O/e;O/f;O/f;P/f;P/f;P/f;P/f;Q/f;Q/f;Q/f;R/f;R/f;R/f;R/g;S/g;S/g;S/g;T/g;T/g;T/g;T/g;U/g;U/g;U/g;V/g;V/h;V/h;V/h;W/h;W/h;W/h;X/h;X/h;X/h;X/h;Y/h;Y/h;Y/i;Z/i;Z/i;Z/i;Z/i;[/i;[/i;[/i;\/i;\/i;\/i;]/j;]/j;]/j;]/j;^/j;^/j;^/j;_/j;_/j;_/j;_/j<@/k<@/k<@/k<A/k<A/k<A/k<A/k<B/k<B/k<B/k<C/k<C/l<C/l<C/l<D/l<D/l<D/l<E/l<E/l<E/l<E/l<F/m<F/m<F/m<G/m<G/m<G/m<G/m<H/m<H/m<H/m<I/n<I/n<I/n<I/n<J/n<J/n<J/n<K/n<K/n<K/n<K/o<L/o<L/o<L/o<M/o<M/o<M/o<M/o<N/o<N/p<N/p<O/p<O/p<O/p<O/p<P/p<P/p<P/p<Q/q<Q/q<Q/q<Q/q<R/q<R/q<R/q<S/q<S/q<S/r<S/r<T/r<T/r<T/r<U/r<U/r<U/r<U/r<V/s<V/s<V/s<W/s<W/s<W/s<X/s<X/s<X/t<X/t<Y/t<Y/t<Y/t<Z/t<Z/t<Z/t<Z/u<[/u<[/u<[/u<\/u<\/u<\/u<\/v<]/v<]/v<]/v<^/v<^/v<^/v<^/v<_/w<_/w<_/w=@/w=@/w=@/w=@/w=A/x=A/x=A/x=B/x=B/x=B/x=B/x=C/y=C/y=C/y=D/y=D/y=D/y=D/y=E/z=E/z=E/z=F/z=F/z=F/z=F/{=G/{=G/{=G/{=H/{=H/{=H/|=H/|=I/|=I/|=I/|=J/|=J/}=J/}=J/}=K/}=K/}=K/}=L/~=L/~=L/~=L/~=M/~=M/~=M/=N/=N/=N/=N/=O0`=O0`=O0`=P0`=P0`=P0a=Q0a=Q0a=Q0a=Q0a=R0b=R0b=R0b=S0b=S0b=S0c=S0c=T0c=T0c=T0c=U0d=U0d=U0d=U0d=V0e=V0e=V0e=W0e=W0f=W0f=W0f=X0f=X0g=X0g=Y0g=Y0g=Y0h=Y0h=Z0h=Z0h=Z0i=[0i=[0i=[0i=[0j=\0j=\0j=\0k=]0k=]0k=]0k=]0l=^0l=^0l=^0m=_0m=_0m=_0n=_0n>@0n>@0o>@0o>A0o>A0p>A0p>A0p>B0q>B0q>B0q>C0r>C0r>C0s>C0s>D0s>D0t>D0t>E0u>E0u>E0v>E0v>F0v>F0w>F0w>G0x>G0x>G0y>G0y>H0z>H0z>H0{>I0|>I0|>I0}>J0}>J0~>J0>J0>K1`>K1a>K1a>L1b


sry for so many questions,

thanks for the reply.

Iain Taylor

---

### Post by iain150 on 2012-11-20
the result of 
$TERM
was xterm.

---

### Post by steeldriver on 2012-11-20
Probably what you want to know is the default terminal type for your particular gnuplot installation - rather than the $TERM environment variable - i.e. from the interactive gnuplot shell type 'show terminal'

```
gnuplot> show terminal

   terminal type is wxt 0

```(I believe 'wxt' is the default for most Linux systems with a regular gnuplot install). You can see what alternative terminals are available using 'set terminal' with no arguments

```
gnuplot> set terminal
```

If 'wxt' doesn't work I would try 'x11' i.e. put

```
set terminal x11 1
```(or 2,3... etc. - just anything other than the default window number which is 0) before your 2nd plot command

---

### Post by iain150 on 2012-11-20
I was unable to get this to work i'll mark this as solved and find the answer in university tomorrow.

---

