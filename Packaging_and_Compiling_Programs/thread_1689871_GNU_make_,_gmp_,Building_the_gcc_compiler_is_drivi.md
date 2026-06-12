---
title: "GNU make , gmp ,Building the gcc compiler is driving me crazy"
date: 2011-02-17
forum: Packaging and Compiling Programs
---

### Post by lubna on 2011-02-17
i'm trying to compile and build the gcc compiler , as i read i must intsall the gmp library and GNU make and other stuff

i downloaded the 2 available version of gmp fom [http://gmplib.org/](http://gmplib.org/) ... extract then configure , make , but when i do the make check i get errors that i can't resolve , this is what i get :

libtool: link: gcc -std=gnu99 -m32 -O2 -pedantic -fomit-frame-pointer -mtune=core2 -march=core2 -o .libs/t-bswap t-bswap.o  ./.libs/libtests.a /home/lubna/.libs/libgmp.so ../.libs/libgmp.so
./.libs/libtests.a(refmpn.o): In function `refmpn_binvert':
refmpn.c:(.text+0x39c2): undefined reference to `__gmpn_sbpi1_bdiv_q'
/home/lubna/.libs/libgmp.so: undefined reference to `__gmpn_mullo_n'
/home/lubna/.libs/libgmp.so: undefined reference to `__gmpn_lshiftc'
/home/lubna/.libs/libgmp.so: undefined reference to `__gmpn_bdiv_q_itch'
/home/lubna/.libs/libgmp.so: undefined reference to `__gmpn_sbpi1_bdiv_qr'
/home/lubna/.libs/libgmp.so: undefined reference to `__gmpn_toom_eval_pm2'
/home/lubna/.libs/libgmp.so: undefined reference to `__gmpn_dcpi1_bdiv_q'
/home/lubna/.libs/libgmp.so: undefined reference to `__gmpn_toom43_mul'
/home/lubna/.libs/libgmp.so: undefined reference to `__gmpn_toom8h_mul'
/home/lubna/.libs/libgmp.so: undefined reference to `__gmpn_toom_eval_dgr3_pm1'
/home/lubna/.libs/libgmp.so: undefined reference to `__gmpn_redc_1_sec'
/home/lubna/.libs/libgmp.so: undefined reference to `__gmpn_toom6h_mul'
/home/lubna/.libs/libgmp.so: undefined reference to `__gmpn_sbpi1_div_q'
/home/lubna/.libs/libgmp.so: undefined reference to `__gmpn_div_q'
/home/lubna/.libs/libgmp.so: undefined reference to `__gmpn_redc_n'
/home/lubna/.libs/libgmp.so: undefined reference to `__gmpn_toom63_mul'
/home/lubna/.libs/libgmp.so: undefined reference to `__gmpn_mulmod_bnm1'
/home/lubna/.libs/libgmp.so: undefined reference to `__gmpn_sqr'
/home/lubna/.libs/libgmp.so: undefined reference to `__gmpn_mulmod_bnm1_next_size'
/home/lubna/.libs/libgmp.so: undefined reference to `__gmpn_preinv_mod_1'
/home/lubna/.libs/libgmp.so: undefined reference to `__gmpn_invertappr'
/home/lubna/.libs/libgmp.so: undefined reference to `__gmpn_nussbaumer_mul'
/home/lubna/.libs/libgmp.so: undefined reference to `__gmpn_perfect_power_p'
/home/lubna/.libs/libgmp.so: undefined reference to `__gmpn_ni_invertappr'
/home/lubna/.libs/libgmp.so: undefined reference to `__gmpn_invert_limb'
/home/lubna/.libs/libgmp.so: undefined reference to `__gmpn_sbpi1_div_qr'
/home/lubna/.libs/libgmp.so: undefined reference to `__gmpn_toom_eval_pm1'
/home/lubna/.libs/libgmp.so: undefined reference to `__gmpn_dcpi1_div_qr'
/home/lubna/.libs/libgmp.so: undefined reference to `__gmpn_dcpi1_bdiv_qr'
/home/lubna/.libs/libgmp.so: undefined reference to `__gmpn_toom_eval_dgr3_pm2'
/home/lubna/.libs/libgmp.so: undefined reference to `__gmpn_bdiv_q'
collect2: ld returned 1 exit status
make[4]: *** [t-bswap] Error 1
make[4]: Leaving directory `/home/lubna/tests'
make[3]: *** [check-am] Error 2
make[3]: Leaving directory `/home/lubna/tests'
make[2]: *** [check-recursive] Error 1
make[2]: Leaving directory `/home/lubna/tests'
make[1]: *** [check-recursive] Error 1
make[1]: Leaving directory `/home/lubna'
make: *** [check] Error 2


and i get errors in the make check of MPFR as well , and errors when making the GNU make , the output is :

main.o: In function `printf':
/usr/include/bits/stdio2.h:105: undefined reference to `version_string'
main.o: In function `print_version':
/home/lubna/Downloads/make-3.82/main.c:3054: undefined reference to `make_host'
/home/lubna/Downloads/make-3.82/main.c:3056: undefined reference to `make_host'
main.o: In function `print_usage':
/home/lubna/Downloads/make-3.82/main.c:2476: undefined reference to `make_host'
/home/lubna/Downloads/make-3.82/main.c:2478: undefined reference to `make_host'
variable.o: In function `sprintf':
/usr/include/bits/stdio2.h:34: undefined reference to `version_string'
collect2: ld returned 1 exit status
make[2]: *** [make] Error 1
make[2]: Leaving directory `/home/lubna'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/lubna'
make: *** [all] Error 2



so please , could someone tell me what i should do , what am i missing here ? :(


thanks alot

---

### Post by nickleboyblue on 2011-02-17
Why do you want to compile gcc from source?  If you don't have any VERY specific programming needs, just install it by running the following command in a terminal:

```
sudo apt-get install build-essential
```

That will install all the generic tools, like gcc etc., that you will need to do c/c++ programming.

---

### Post by lubna on 2011-02-17
i actually i'm planning to try to change stuff in the gcc , so the first step is knowing how to build it properly without errors !

---

### Post by SevenMachines on 2011-02-17
Is there a reason you're trying to build make, gmp and so on? Or is it just the gcc you're looking to patch/build?

---

### Post by lubna on 2011-02-17
i want to build the gcc , but those are it's prerequisites , and i had errors while building the gcc , so i figues i should build the prerequisites correctly first , coz when i ignored those make check errors when i tried building the gcc

---

### Post by SevenMachines on 2011-02-17
As a rule, unless you specifically need to change something, don't build it. So, if you want to build gcc don't build the pre-requisites, use the -dev packages. If i were going about this i would do something like, for gcc-4.5 which is on my version of ubuntu
```

# Get all the build dependencies  
$ sudo apt-get build-dep gcc-4.5

# Get the current ubuntu source and packaging and unpack it into this directory
$ apt-get source gcc-4.5
```You'll now have everything you need to build gcc , you'll have the source code, the debian packaging and patches should you want to use them, and all the build dependencies installed. You could now change it directly and build it manually, build it using the debuild system, or use the patch system to make your changes and use debuild, its up to you

---

### Post by ibuclaw on 2011-02-17
> **SevenMachines said:**
> As a rule, unless you specifically need to change something, don't build it. So, if you want to build gcc don't build the pre-requisites, use the -dev packages. If i were going about this i would do something like, for gcc-4.5 which is on my version of ubuntu
```

# Get all the build dependencies  
$ sudo apt-get build-dep gcc-4.5

# Get the current ubuntu source and packaging and unpack it into this directory
$ apt-get source gcc-4.5
```You'll now have everything you need to build gcc , you'll have the source code, the debian packaging and patches should you want to use them, and all the build dependencies installed. You could now change it directly and build it manually, build it using the debuild system, or use the patch system to make your changes and use debuild, its up to you

You'll pull in more than you actually need.

The minimum you need to build is:
[LIST]
[*]gcc (and optionally g++)
[*]autoconf2.59
[*]automake1.9
[*]libmpc-dev
[*]libmpfr-dev
[*]libgmp3-dev
[/LIST]

Regards

---

### Post by SevenMachines on 2011-02-18
> **ibuclaw said:**
> You'll pull in more than you actually need.
Yep, the package build-deps aren't optimal but it also opens up the option of 'quilt' patching and debuilding to get customised packages should that be preferred. Generally i tend to find its not unusual for 'apt-get build-dep' not to be the least required deps for building the source, or sometimes not enough, or if the source version is different enough, perhaps even not the right ones! The vast majority of the time its fine though, and handy if you're like me and a lot of the time dont want to actually properly check the source deps :)

---

### Post by ibuclaw on 2011-02-18
> **SevenMachines said:**
> Yep, the package build-deps aren't optimal but it also opens up the option of 'quilt' patching and debuilding to get customised packages should that be preferred. Generally i tend to find its not unusual for 'apt-get build-dep' not to be the least required deps for building the source, or sometimes not enough, or if the source version is different enough, perhaps even not the right ones! The vast majority of the time its fine though, and handy if you're like me and a lot of the time dont want to actually properly check the source deps :)

I actually have the source deps tattooed under my eyelids. ;)

Just an extra note that
[LIST]
[*]libppl-dev
[*]libcloog-dev
[/LIST]
Are optional dependencies that need turning on with configure flags '--with-ppl --with-cloog'

Bye.

---

### Post by lubna on 2011-02-19
thanks everybody ... i have tried everything u said , i downloaded the dependencies .... still no luck
i get errors while making the gcc , something about collect 2 ld .... i really need this , i've tried all possible packages to download ... nothing seems to be working ! :(

---

### Post by SevenMachines on 2011-02-19
Do you want to try the following steps, which work here, and post any errors/logs that are causing you problems

```
$ sudo apt-get build-dep gcc-4.5
$ wget ftp://ftp.fu-berlin.de/unix/languages/gcc/releases/gcc-4.5.2/gcc-4.5.2.tar.bz2
$ tar -jvxf gcc-4.5.2.tar.bz2
$ cd gcc-4.5.2
$ ./configure 
$ make

```

---

### Post by lubna on 2011-02-19
i tried the commands you posted , i got the same old error .. here it is :

libbackend.a(toplev.o): In function `print_version':
toplev.c:(.text+0x15b9): undefined reference to `mpfr_get_version'
toplev.c:(.text+0x16a9): undefined reference to `mpfr_get_version'
//usr/local/lib/libgmp.so: undefined reference to `__gmpn_mullo_n'
//usr/local/lib/libgmp.so: undefined reference to `__gmpn_dcpi1_bdiv_q'
//usr/local/lib/libgmp.so: undefined reference to `__gmpn_toom_eval_pm1'
//usr/local/lib/libgmp.so: undefined reference to `__gmpn_sbpi1_div_q'
//usr/local/lib/libgmp.so: undefined reference to `__gmpn_toom43_mul'
//usr/local/lib/libgmp.so: undefined reference to `__gmpn_toom_eval_pm2'
//usr/local/lib/libgmp.so: undefined reference to `__gmpn_sbpi1_div_qr'
//usr/local/lib/libgmp.so: undefined reference to `__gmpn_dcpi1_bdiv_qr'
//usr/local/lib/libgmp.so: undefined reference to `__gmpn_redc_1_sec'
//usr/local/lib/libgmp.so: undefined reference to `__gmpn_invert_limb'
//usr/local/lib/libgmp.so: undefined reference to `__gmpn_sbpi1_bdiv_qr'
//usr/local/lib/libgmp.so: undefined reference to `__gmpn_bdiv_q'
//usr/local/lib/libgmp.so: undefined reference to `__gmpn_nussbaumer_mul'
//usr/local/lib/libgmp.so: undefined reference to `__gmpn_lshiftc'
//usr/local/lib/libgmp.so: undefined reference to `__gmpn_bdiv_q_itch'
//usr/local/lib/libgmp.so: undefined reference to `__gmpn_div_q'
//usr/local/lib/libgmp.so: undefined reference to `__gmpn_dcpi1_div_qr'
//usr/local/lib/libgmp.so: undefined reference to `__gmpn_redc_n'
//usr/local/lib/libgmp.so: undefined reference to `__gmpn_sqr'
//usr/local/lib/libgmp.so: undefined reference to `__gmpn_mulmod_bnm1'
//usr/local/lib/libgmp.so: undefined reference to `__gmpn_toom63_mul'
//usr/local/lib/libgmp.so: undefined reference to `__gmpn_preinv_mod_1'
//usr/local/lib/libgmp.so: undefined reference to `__gmpn_toom8h_mul'
//usr/local/lib/libgmp.so: undefined reference to `__gmpn_toom_eval_dgr3_pm2'
//usr/local/lib/libgmp.so: undefined reference to `__gmpn_toom6h_mul'
//usr/local/lib/libgmp.so: undefined reference to `__gmpn_invertappr'
//usr/local/lib/libgmp.so: undefined reference to `__gmpn_ni_invertappr'
//usr/local/lib/libgmp.so: undefined reference to `__gmpn_perfect_power_p'
//usr/local/lib/libgmp.so: undefined reference to `__gmpn_toom_eval_dgr3_pm1'
//usr/local/lib/libgmp.so: undefined reference to `__gmpn_sbpi1_bdiv_q'
//usr/local/lib/libgmp.so: undefined reference to `__gmpn_mulmod_bnm1_next_size'
collect2: ld returned 1 exit status
make[3]: *** [cc1-dummy] Error 1
make[3]: Leaving directory `/home/lubna/gcc-4.5.2/host-i686-pc-linux-gnu/gcc'
make[2]: *** [all-stage2-gcc] Error 2


so what's wrong ? what am i missing ?

---

### Post by SevenMachines on 2011-02-19
What version of ubuntu are you on? I'll try and replicate on a virtual machine if needed. I tend to use the dev version so it might be the case that, for ease, you might want a slightly older version of gcc such as 4.4 or 4.3.

---

### Post by gmargo on 2011-02-20
At least part of the problem is that libgmp you have in /usr/local/lib.  Get rid of it.

If you are running 10.04 Lucid or above, all of the dependencies and prerequisites for gcc-4.5 are available in the repositories.

---

### Post by lubna on 2011-02-20
i have ubuntu 10.10 netbook

---

### Post by SevenMachines on 2011-02-23
As gmargo mentioned, you seem to have some different headers/libraries installed in /usr/local, did you try removing them? The commands i mentioned previously use the headers/libraries from the repositories not local installs

---

