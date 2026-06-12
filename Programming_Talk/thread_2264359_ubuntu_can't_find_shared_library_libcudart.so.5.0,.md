---
title: "ubuntu can't find shared library libcudart.so.5.0, but the file is there"
date: 2015-02-07
forum: Programming Talk
---

### Post by bart17 on 2015-02-07
hi, I am learning programming in cuda. So I installed cuda toolkit 5.0 on my Ubuntu 12.04 64bit. And **I tried running some cuda sample programs a few days ago, they were running smoothly**. Until today, the computer suddenly complains :" error while loading shared libraries: libcudart.so.5.0: cannot open shared object file: No such file or directory"
But I checked the folder where the shared object file is supposed to be, it is still there! _Please see the picture that I uploaded_.

So will anyone tell me how I can have the computer "see" the shared object file?
PS: I can go around the problem by making a copy of the libcudart.so.5.0 file in the folder where the executable file is located. But it's not the best way to go.....

---

### Post by dwhitney67 on 2015-02-08
Your Cuda libraries are in a non-standard location -- not that there is anything wrong with this -- but if you wish to run applications which require these libraries, then you need to 'educate' your system as to the location of the libraries.  There are at least two ways to do this:

1.  Define/augment the library search paths within the LD_LIBRARY_PATH environment variable.  Typically one would set this up in one of the following files: ~/.bashrc, ~/.bash_aliases or ~/.profile.  Personally I would recommend the latter.  Anyhow, in your case, LD_LIBRARY_PATH would be set up as:
```

export LD_LIBRARY_PATH=/usr/local/cuda-5.0/lib64:$LD_LIBRARY_PATH

```

2.  You can add your new libraries to the system library cache.  This requires admin privileges.  Here's how to do this:
```

$ sudo echo "/usr/local/cuda-5.0/lib64" > /etc/ld.so.conf.d/cuda.conf

$ sudo ldconfig

```

There might be other solutions, but either one of the suggestions discussed above will sort out the issue you are having.

---

### Post by bart17 on 2015-02-09
hi, whitney

Thanks for your reply. I tried your second method, and it works!
But just to be a bit academic, the first method was how I setup my CUDA library. But it doesn't work. If you look at my attatched picture in the first post, you will see I used "echo $LD_LIBRARY_PATH" to check. And clearly /usr/local/cuda-5.0/lib64 is included in $LD_LIBRARY_PATH. It is still unclear to me why the 1st approach doesn't work. But after all, I am happy that I don't have to make a copy of the so file for every executable. thanks again!

---

### Post by dwhitney67 on 2015-02-09
> **bart17 said:**
> hi, whitney

Thanks for your reply. I tried your second method, and it works!
But just to be a bit academic, the first method was how I setup my CUDA library. But it doesn't work. If you look at my attatched picture in the first post, you will see I used "echo $LD_LIBRARY_PATH" to check. And clearly /usr/local/cuda-5.0/lib64 is included in $LD_LIBRARY_PATH. It is still unclear to me why the 1st approach doesn't work. But after all, I am happy that I don't have to make a copy of the so file for every executable. thanks again!

Your user environment does indeed have LD_LIBRARY_PATH set up correctly; however when you attempt to run your program using 'sudo' (why?), this environment variable's setting is not promoted to the new shell.  This is a security feature of Linux, so I'm not sure there's a workaround.

---

### Post by spjackson on 2015-02-09
> **bart17 said:**
> 
But just to be a bit academic, the first method was how I setup my CUDA library. But it doesn't work. If you look at my attatched picture in the first post, you will see I used "echo $LD_LIBRARY_PATH" to check. And clearly /usr/local/cuda-5.0/lib64 is included in $LD_LIBRARY_PATH. It is still unclear to me why the 1st approach doesn't work. But after all, I am happy that I don't have to make a copy of the so file for every executable. thanks again!
I'm not sure exactly what is going on from your screenshot, but there is a sudo in there. LD_LIBRARY_PATH is not inherited across a sudo, so that might be why that method isn't working for you.

---

### Post by j-silvestre82 on 2015-09-15
Thank you it helps me a lot. i run without sudo and it works.
something is strange, I`ve tried the second method several time
echo "/usr/local/cuda-7.5/lib64" > /etc/ld.so.conf.d/cuda.conf
Strangely I need to pass in su mode to did it. sudo didn't allow me to do it
 but when i do 
sudo ldconfig
I have :
/sbin/ldconfig.real: /usr/local/cuda-7.5/lib64/libcudnn.so.7.0 is not a symbolic link
 why ? nobody seems to have this problem with cuda...

---

