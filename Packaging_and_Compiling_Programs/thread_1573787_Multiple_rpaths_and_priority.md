---
title: "Multiple rpaths and priority"
date: 2010-09-13
forum: Packaging and Compiling Programs
---

### Post by nerdopolis on 2010-09-13
Hi. I was just wondering as I could not find anything about this.

I read that it is possible to compile an app with an option so that it searches certain folders for libraries. I read that under Linux it its possible to give these apps multiple rpaths.

My question is, is that how does it know what order to go through the list rpaths? does it go in the order that they where passed when the app was compiled?

---

### Post by SevenMachines on 2010-09-13
Order as passed when compiled i think, i never use rpath myself but say as an example....

hello.cpp:
> #include <iostream>

int main (int args, char ** argv){
    std::cout<<"Hello!"<<std::endl;
    return 0;
}
> g++ -o hello hello.c -Wl,-rpath,/usr/local/lib/hello/B,-rpath,/usr/local/lib/hello/AThis sets the compiled in order as.
> $ readelf -d ./hello|grep RPATH
 0x0000000f (RPATH)                      Library rpath: [/usr/local/lib/hello/B:/usr/local/lib/hello/A]If these directories dont exist then...
> $ ldd ./hello
    linux-gate.so.1 =>  (0x00440000)
    libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00caf000)
    libm.so.6 => /lib/libm.so.6 (0x00110000)
    libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00a86000)
    libc.so.6 => /lib/libc.so.6 (0x00466000)
    /lib/ld-linux.so.2 (0x006d1000)
Since libraries are searched in the LD_LIBRARY_PATH, RPATH, SYSTEM LIBS order as far as i know anyway, you can see the order if you make /usr/local/lib/hello/A and B dirs and put some lib links in them

> $ sudo mkdir -p /usr/local/lib/hello/A
$ sudo mkdir -p /usr/local/lib/hello/B
$ sudo ln -s /lib/libm.so.6 /usr/local/lib/hello/A
$ sudo ln -s /lib/libm.so.6 /usr/local/lib/hello/B
Now we can get a libm from A, B, or /lib but B was first when we compiled in rpath so
> $ ldd ./hello
    linux-gate.so.1 =>  (0x00244000)
    libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00447000)
    libm.so.6 => /usr/local/lib/hello/B/libm.so.6 (0x00f79000)
    libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00ef4000)
    libc.so.6 => /lib/libc.so.6 (0x00843000)
    /lib/ld-linux.so.2 (0x00e8f000)
but A is still on the search path if we need it so lets link a needed lib in there but not in B
> $ sudo ln -s /lib/libgcc_s.so.1 /usr/local/lib/hello/Aso with 
* libm in A, B or /lib
* libgcc in only A or /lib
* a search path of LD_LIBRARY_PATH, rpaths in order specified when compiling, system libs

Hopefully the following makes sense...

> 
$ ldd ./hello
    linux-gate.so.1 =>  (0x00110000)
    libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00dac000)
    libm.so.6 => /usr/local/lib/hello/B/libm.so.6 (0x0024b000)
    libgcc_s.so.1 => /usr/local/lib/hello/A/libgcc_s.so.1 (0x00a97000)
    libc.so.6 => /lib/libc.so.6 (0x003b8000)
    /lib/ld-linux.so.2 (0x007cb000)
So the short answer is, I dont know if theres a man page or something that makes it clear ( post a link if you find one) but order on the command line seems to be it :)

---

### Post by apmcd47 on 2010-09-13
For most Unix/Linx commands system default settings are normally over-ridden by (1) local (user) config settings; (2) environment variables and (3) command-line switches. In the case of library search paths when compiling programs there is some form of system-wide rpath; no user config files; RUN_LIBRARY_PATH or RPATH environment variable; compiler switches (ie the -R switch).
So the switch should take precedence over the environment variable which takes precedence over the system settings.

I'm not at my linux box now so I can't tell you about the system setting. Possibly the ld or collect2 man pages can help.


Andrew

---

### Post by nerdopolis on 2010-09-13
**SevenMachines **: looking at the results from your experiments, it seems that way. 

Thank you very much for taking the time trying those experiments for me! They helped! I could not find a *thing* about having individual rpath priorities on Google.

---

