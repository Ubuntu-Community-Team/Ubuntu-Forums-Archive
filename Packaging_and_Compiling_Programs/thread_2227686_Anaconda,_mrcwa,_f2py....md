---
title: "Anaconda, mrcwa, f2py..."
date: 2014-06-03
forum: Packaging and Compiling Programs
---

### Post by felipe10 on 2014-06-03
Greetings,

I am sorry if this is the wrong section but I am starting to get desperate, please someone help me...

I  need to install the program mrcwa-20080820 ([http://sourceforge.net/projects/mrcwa/](http://sourceforge.net/projects/mrcwa/)) because a summer project  that I am involved. I need to use it together with anaconda ([SIZE=2][https://store.continuum.io/cshop/anaconda/]("https://mail.student.gla.ac.uk/owa/redir.aspx?C=dVKqJJOUf0G1f22ZQRlCLC8RyE_bUtFI3eOgpkVH0_RPT1Y_YpDxPR1ba02ISQ6fMpsYh3fgAM8.&URL=https%3a%2f%2fstore.continuum.io%2fcshop%2fanaconda%2f"))[/SIZE], I already  installed Anaconda and apparently it is working. When I type ```
conda  --version
``` i got the expected answer ```
conda 3.5.2
```. If I tried to import numpy or scipy with python or simple type f2py there are no errors. So far so good. But when I tried to install this program (```
sudo python setup.py install
```) I got these errors:

```
running install
running build
sh: 1: f2py: not found
cp: cannot stat ‘mrcwaf.so’: No such file or directory
running build_py
running install_lib
running install_egg_info
Removing /usr/local/lib/python2.7/dist-packages/mrcwa-20080820.egg-info
Writing /usr/local/lib/python2.7/dist-packages/mrcwa-20080820.egg-info

```

Obs: I am trying to use intel fortran 64-bits and Ubuntu 14.04 LTS.

So I was checking f2py and tried to execute the program hello world (```
f2py -c -m hello hello.f
```) from here: [http://cens.ioc.ee/projects/f2py2e/index.html#usage](http://cens.ioc.ee/projects/f2py2e/index.html#usage) and I had some problems too:

```
running build
running config_cc
unifing config_cc, config, build_clib, build_ext, build commands --compiler options
running config_fc
unifing config_fc, config, build_clib, build_ext, build commands --fcompiler options
running build_src
build_src
building extension "hello" sources
f2py options: []
f2py:> /tmp/tmpf8P4Y3/src.linux-x86_64-2.7/hellomodule.c
creating /tmp/tmpf8P4Y3/src.linux-x86_64-2.7
Reading fortran codes...
    Reading file 'hello.f' (format:fix,strict)
Post-processing...
    Block: hello
            Block: foo
Post-processing (stage 2)...
Building modules...
    Building module "hello"...
        Constructing wrapper function "foo"...
          foo(a)
    Wrote C/API module "hello" to file "/tmp/tmpf8P4Y3/src.linux-x86_64-2.7/hellomodule.c"
  adding '/tmp/tmpf8P4Y3/src.linux-x86_64-2.7/fortranobject.c' to sources.
  adding '/tmp/tmpf8P4Y3/src.linux-x86_64-2.7' to include_dirs.
copying /home/felipe/.local/lib/python2.7/site-packages/numpy/f2py/src/fortranobject.c -> /tmp/tmpf8P4Y3/src.linux-x86_64-2.7
copying /home/felipe/.local/lib/python2.7/site-packages/numpy/f2py/src/fortranobject.h -> /tmp/tmpf8P4Y3/src.linux-x86_64-2.7
build_src: building npy-pkg config files
running build_ext
customize UnixCCompiler
customize UnixCCompiler using build_ext
customize Gnu95FCompiler
Could not locate executable gfortran
Could not locate executable f95
customize IntelFCompiler
Found executable /opt/intel/composer_xe_2013_sp1.3.174/bin/intel64/ifort
customize LaheyFCompiler
Could not locate executable lf95
customize PGroupFCompiler
Could not locate executable pgfortran
customize AbsoftFCompiler
Could not locate executable f90
Could not locate executable f77
customize NAGFCompiler
customize VastFCompiler
customize CompaqFCompiler
Could not locate executable fort
customize IntelItaniumFCompiler
customize IntelEM64TFCompiler
customize IntelEM64TFCompiler
customize IntelEM64TFCompiler using build_ext
building 'hello' extension
compiling C sources
C compiler: gcc -pthread -fno-strict-aliasing -g -O2 -DNDEBUG -g -fwrapv -O3 -Wall -Wstrict-prototypes -fPIC

creating /tmp/tmpf8P4Y3/tmp
creating /tmp/tmpf8P4Y3/tmp/tmpf8P4Y3
creating /tmp/tmpf8P4Y3/tmp/tmpf8P4Y3/src.linux-x86_64-2.7
compile options: '-I/tmp/tmpf8P4Y3/src.linux-x86_64-2.7 -I/home/felipe/.local/lib/python2.7/site-packages/numpy/core/include -I/home/felipe/anaconda/include/python2.7 -c'
gcc: /tmp/tmpf8P4Y3/src.linux-x86_64-2.7/hellomodule.c
In file included from /home/felipe/.local/lib/python2.7/site-packages/numpy/core/include/numpy/ndarraytypes.h:1761:0,
                 from /home/felipe/.local/lib/python2.7/site-packages/numpy/core/include/numpy/ndarrayobject.h:17,
                 from /home/felipe/.local/lib/python2.7/site-packages/numpy/core/include/numpy/arrayobject.h:4,
                 from /tmp/tmpf8P4Y3/src.linux-x86_64-2.7/fortranobject.h:13,
                 from /tmp/tmpf8P4Y3/src.linux-x86_64-2.7/hellomodule.c:17:
/home/felipe/.local/lib/python2.7/site-packages/numpy/core/include/numpy/npy_1_7_deprecated_api.h:15:2: warning: #warning "Using deprecated NumPy API, disable it by " "#defining NPY_NO_DEPRECATED_API NPY_1_7_API_VERSION" [-Wcpp]
 #warning "Using deprecated NumPy API, disable it by " \
  ^
gcc: /tmp/tmpf8P4Y3/src.linux-x86_64-2.7/fortranobject.c
In file included from /home/felipe/.local/lib/python2.7/site-packages/numpy/core/include/numpy/ndarraytypes.h:1761:0,
                 from /home/felipe/.local/lib/python2.7/site-packages/numpy/core/include/numpy/ndarrayobject.h:17,
                 from /home/felipe/.local/lib/python2.7/site-packages/numpy/core/include/numpy/arrayobject.h:4,
                 from /tmp/tmpf8P4Y3/src.linux-x86_64-2.7/fortranobject.h:13,
                 from /tmp/tmpf8P4Y3/src.linux-x86_64-2.7/fortranobject.c:2:
/home/felipe/.local/lib/python2.7/site-packages/numpy/core/include/numpy/npy_1_7_deprecated_api.h:15:2: warning: #warning "Using deprecated NumPy API, disable it by " "#defining NPY_NO_DEPRECATED_API NPY_1_7_API_VERSION" [-Wcpp]
 #warning "Using deprecated NumPy API, disable it by " \
  ^
compiling Fortran sources
Fortran f77 compiler: /opt/intel/composer_xe_2013_sp1.3.174/bin/intel64/ifort -FI -fPIC -xhost -openmp -fp-model strict
Fortran f90 compiler: /opt/intel/composer_xe_2013_sp1.3.174/bin/intel64/ifort -FR -fPIC -xhost -openmp -fp-model strict
Fortran fix compiler: /opt/intel/composer_xe_2013_sp1.3.174/bin/intel64/ifort -FI -fPIC -xhost -openmp -fp-model strict
compile options: '-I/tmp/tmpf8P4Y3/src.linux-x86_64-2.7 -I/home/felipe/.local/lib/python2.7/site-packages/numpy/core/include -I/home/felipe/anaconda/include/python2.7 -c'
ifort:f77: hello.f
/opt/intel/composer_xe_2013_sp1.3.174/bin/intel64/ifort -shared -shared -nofor_main /tmp/tmpf8P4Y3/tmp/tmpf8P4Y3/src.linux-x86_64-2.7/hellomodule.o /tmp/tmpf8P4Y3/tmp/tmpf8P4Y3/src.linux-x86_64-2.7/fortranobject.o /tmp/tmpf8P4Y3/hello.o -L/home/felipe/anaconda/lib -lpython2.7 -o ./hello.so
Removing build directory /tmp/tmpf8P4Y3

```

Obs: It's a problem similar to this one [http://ubuntuforums.org/showthread.php?t=1920882](http://ubuntuforums.org/showthread.php?t=1920882) but I already tried to install the python2.6-dev.

Please help me I am new in ubuntu and python. I really need this program, my advisor is waiting an answer.

Thank you very much,
Felipe Oliveira.

---

### Post by felipe10 on 2014-06-04
Ok, I solved this problem but now I have another one. To solve this I changed the path for sudo.

    nano .bashrc

Then paste this code in the end of the file:

    # because sudo doesn't export LD_LIBRARY_PATH for our apps
    alias sudo='sudo env PATH=/home/felipe/anaconda/lib:/usr/arm-linux-gnueabi/lib:/usr   /lib:$PATH'

Now  I need to know which library I have to use with Intel Fortran to make  this works because every time I try to run some examples I got something  similar to this:

    ImportError: libmkl_core.so: cannot open shared object file: No such file or directory

---

### Post by felipe10 on 2014-06-05
For future users, I finally suceed to install this library. I used gfortran and this is my machine_cfg.py:

f2py_options  = ['--fcompiler=gnu95',
                 '--f90exec=/usr/bin/gfortran',
                 '--opt="-O3"']

libs          = ['lapack']
libpaths      = ['/usr/lib']

If anybody has any trouble installing this feel free to send a Email to me, maybe I can help:

[email]zeus644@hotmail.com[/email]

SOLVED.

---

