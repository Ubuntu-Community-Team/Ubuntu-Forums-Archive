---
title: "How to compile a windows compatible exe under Ubuntu"
date: 2019-05-29
forum: Packaging and Compiling Programs
---

### Post by flawlessvictory2 on 2019-05-29
I am a complete idiot and would really appreciate some help. 

I've been struggling for 2 days straight how to figure out a way to compile rtmpdump from within Ubuntu 16.04.6 (64-bit).
What I've done on a fresh install of Ubuntu is the following:

apt install git build-essential libssl-dev
 git clone [https://github.com/sstativa/rtmpdump-ksv.gitcd](https://github.com/sstativa/rtmpdump-ksv.gitcd) rtmpdump-ksv
//(I usually dont run this line because it seems like the files are already patched? Otherwise the line is) patch -p0 -i Patch.diff
 make 
make install prefix=/usr

So far, so good. This compiles just fine. 
Now the problem is that the resulting executable isn't compatible with windows. So how would I go on about compiling this in a way that works in Windows?

I did try doing "make SYS=mingw" and I also tried changing the gcc entries in makefile to the i686 win32 version of mingw, but it would complain about missing files and/or undefined references. 
So i added what I thought were the missing libraries:
 [ftp://ftp.zlatkovic.com/libxml/zlib-1.2.5.win32.zip](ftp://ftp.zlatkovic.com/libxml/zlib-1.2.5.win32.zip) 
[https://www.openssl.org/source/old/1.0.1/openssl-1.0.1e.tar.gz](https://www.openssl.org/source/old/1.0.1/openssl-1.0.1e.tar.gz) (I was unable to compile this one)

Maybe someone could help me find a way to compile this so that the resulting exe works under windows 7 x64?

---

### Post by dmnur on 2019-06-01
To compile for Windows, you need to install MinGW toolchain and set up environment accordingly.
You also need to compile OpenSSL with MinGW. As for zlib, Ubuntu already provides the MinGW version of it in the **libz-mingw-w64-dev** package.

Works this way in Ubuntu 18.04, should work in 16.04 too:
```

# Install necessary packages
apt-get install git build-essential mingw-w64 libz-mingw-w64-dev

# Prepare environment
export CROSS_COMPILE=x86_64-w64-mingw32-

# Get and build OpenSSL; use version 1.0.x, build fails with 1.1.x
openssl_ver=1.0.2s
wget https://www.openssl.org/source/openssl-$openssl_ver.tar.gz
tar xf openssl-$openssl_ver.tar.gz
cd openssl-$openssl_ver
openssl_dir=$PWD
./Configure mingw64
make

# Get and build rtmpdump
cd ..
git clone https://github.com/sstativa/rtmpdump-ksv.git
cd rtmpdump-ksv
make SYS=mingw XCFLAGS=-I$openssl_dir/include XLDFLAGS=-L$openssl_dir

# Put it all together
cd ..
mkdir result
cp -t result rtmpdump-ksv/*.exe rtmpdump-ksv/librtmp/librtmp-1.dll /usr/x86_64-w64-mingw32/lib/zlib1.dll

```

Then copy everything from the **result** directory to Windows.

---

### Post by flawlessvictory2 on 2019-06-02
Thanks a lot for your reply! Do you recommend trying this out on 32 or 64-bit Ubuntu?
Or maybe I should just get ubuntu 18.04, if that's what you were using to compile it?

Sorry, I've actually never used Linux before so I'm completely new to all this stuff, and maybe compiling isn't very beginner's friendly. but I'll definitely give this a try!
Thanks again!

---

### Post by flawlessvictory2 on 2019-06-02
> **dmnur said:**
> To compile for Windows, you need to install MinGW toolchain and set up environment accordingly.
You also need to compile OpenSSL with MinGW. As for zlib, Ubuntu already provides the MinGW version of it in the **libz-mingw-w64-dev** package.

Works this way in Ubuntu 18.04, should work in 16.04 too:
```

# Install necessary packages
apt-get install git build-essential mingw-w64 libz-mingw-w64-dev

# Prepare environment
export CROSS_COMPILE=x86_64-w64-mingw32-

# Get and build OpenSSL; use version 1.0.x, build fails with 1.1.x
openssl_ver=1.0.2s
wget https://www.openssl.org/source/openssl-$openssl_ver.tar.gz
tar xf openssl-$openssl_ver.tar.gz
cd openssl-$openssl_ver
openssl_dir=$PWD
./Configure mingw64
make

# Get and build rtmpdump
cd ..
git clone https://github.com/sstativa/rtmpdump-ksv.git
cd rtmpdump-ksv
make SYS=mingw XCFLAGS=-I$openssl_dir/include XLDFLAGS=-L$openssl_dir

# Put it all together
cd ..
mkdir result
cp -t result rtmpdump-ksv/*.exe rtmpdump-ksv/librtmp/librtmp-1.dll /usr/x86_64-w64-mingw32/lib/zlib1.dll

```

Then copy everything from the **result** directory to Windows.

Wow, this all actually worked _on the first try_.

You sir, are a Genius and a life saver! THANK YOU VERY MUCH!!

---

