---
title: "errors in installing source codes"
date: 2012-01-20
forum: New to Ubuntu
---

### Post by sagar_aarya on 2012-01-20
hi frnds

I am trying to install one software from source code...
but its giveing some errors yaar

Plz help i dnt knw how to rectify it....:confused:

./configure   //this was OK .no errors generated
[B]sagar@MRFRODO:~/sagar/softys/source codes/trayfreq-0.2.x-dev2$ make
Making all in src
make[1]: Entering directory `/home/sagar/sagar/softys/source codes/trayfreq-0.2.x-dev2/src'
make  all-am
make[2]: Entering directory `/home/sagar/sagar/softys/source codes/trayfreq-0.2.x-dev2/src'
make[2]: Leaving directory `/home/sagar/sagar/softys/source codes/trayfreq-0.2.x-dev2/src'
make[1]: Leaving directory `/home/sagar/sagar/softys/source codes/trayfreq-0.2.x-dev2/src'
Making all in data
make[1]: Entering directory `/home/sagar/sagar/softys/source codes/trayfreq-0.2.x-dev2/data'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/sagar/sagar/softys/source codes/trayfreq-0.2.x-dev2/data'
make[1]: Entering directory `/home/sagar/sagar/softys/source codes/trayfreq-0.2.x-dev2'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/sagar/sagar/softys/source codes/trayfreq-0.2.x-dev2'
sagar@MRFRODO:~/sagar/softys/source codes/trayfreq-0.2.x-dev2$ 
[/B]


****plz help wat to do??

---

### Post by sagar_aarya on 2012-01-23
[B]hello frnds...

m waiting for your reply...

somebody help me.....

[/B]
:(

---

### Post by Cheesemill on 2012-01-23
I don't see what your problem is?

It looks like make worked just fine.

---

### Post by sandyd on 2012-01-23
> **sagar_aarya said:**
> hi frnds

I am trying to install one software from source code...
but its giveing some errors yaar

Plz help i dnt knw how to rectify it....:confused:

./configure   //this was OK .no errors generated
[B]sagar@MRFRODO:~/sagar/softys/source codes/trayfreq-0.2.x-dev2$ make
Making all in src
make[1]: Entering directory `/home/sagar/sagar/softys/source codes/trayfreq-0.2.x-dev2/src'
make  all-am
make[2]: Entering directory `/home/sagar/sagar/softys/source codes/trayfreq-0.2.x-dev2/src'
make[2]: Leaving directory `/home/sagar/sagar/softys/source codes/trayfreq-0.2.x-dev2/src'
make[1]: Leaving directory `/home/sagar/sagar/softys/source codes/trayfreq-0.2.x-dev2/src'
Making all in data
make[1]: Entering directory `/home/sagar/sagar/softys/source codes/trayfreq-0.2.x-dev2/data'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/sagar/sagar/softys/source codes/trayfreq-0.2.x-dev2/data'
make[1]: Entering directory `/home/sagar/sagar/softys/source codes/trayfreq-0.2.x-dev2'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/sagar/sagar/softys/source codes/trayfreq-0.2.x-dev2'
sagar@MRFRODO:~/sagar/softys/source codes/trayfreq-0.2.x-dev2$ 
[/B]


plz help wat to do??
You just compiled it.
You didn't install it.
```

sudo make install
```

---

### Post by sagar_aarya on 2012-01-23
[B]
sagar@MRFRODO:~/sagar/softys/source codes/trayfreq-0.2.x-dev2$ make install
Making install in src
make[1]: Entering directory `/home/sagar/sagar/softys/source codes/trayfreq-0.2.x-dev2/src'
make[2]: Entering directory `/home/sagar/sagar/softys/source codes/trayfreq-0.2.x-dev2/src'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c trayfreq trayfreq-set '/usr/local/bin'
/usr/bin/install: cannot create regular file `/usr/local/bin/trayfreq': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/bin/trayfreq-set': Permission denied
make[2]: *** [install-binPROGRAMS] Error 1
make[2]: Leaving directory `/home/sagar/sagar/softys/source codes/trayfreq-0.2.x-dev2/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/sagar/sagar/softys/source codes/trayfreq-0.2.x-dev2/src'
make: *** [install-recursive] Error 1
[/B]

---

### Post by Cheesemill on 2012-01-23
You need to do
```
sudo make install
```
not
```
make install
```

---

### Post by sagar_aarya on 2012-01-23
thank you .....
done....



sucess with ma first source code.... compilation n installation


:guitar:  :popcorn:  :guitar:



****************************THREAD CLOSED*************

---

### Post by oldos2er on 2012-01-23
Please mark the thread as 'Solved' under Thread Tools. Thanks.

---

### Post by Paqman on 2012-01-23
A good tip is instead of doing:
```
sudo make install
```
Instead try:
```
sudo checkinstall
```

This will build a normal Ubuntu package so that it can be easily and cleanly removed using the normal package management tools (eg: Ubuntu Software Centre)

---

