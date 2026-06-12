---
title: "How to extract a tar.bz2 file to /opt?"
date: 2014-01-09
forum: New to Ubuntu
---

### Post by ruwan2 on 2014-01-09
Hi,
I have a tarball file who has the file name extension tar.bz2. I can extract it to my user folder. But I see its usage said that it is under /opt folder. I have tried extract it with 

sudo bzip2 -cd ~/Downloads/gcc-linaro-4.7-2013.12.tar.bz2  | tar xvf -

but it still cannot create folder under /opt

I am new to Linux. It reminds me to login as a root user? but I am not clear what does that really mean.

Could you help me on that?

Thanks,

---

### Post by deadflowr on 2014-01-09
I think
```
sudo tar xvjf the-file.bz2 -C /opt
```
should work.

Edit: I think changing directory first helps.
Then I can use the TAB completion to more easily complete the file name.

---

### Post by devine.steve on 2014-01-09
```

sudo su -
cd /opt
bzip ~/Downloads/gcc-linaro-4.7-2013.12.tar.bz2 |tar xvf -

```

Also be aware you will now be executing commands as root. Beware!!

---

### Post by steeldriver on 2014-01-09
What do you mean exactly by "its usage said that it is under /opt folder"? deadflower's suggestion will do what you asked, but personally I'm not a fan of unpacking source tarballs as root - it means you need to be root (i.e. use sudo) to configure and build as well. IMHO it keeps things simpler if you unpack in your user area, then configure / build as yourself and FINALLY when you have a successful build (which may take a few tries, unless you have a very complete list of dependencies ahead of time) do a 'sudo make install' (or even better, use checkinstall).

---

### Post by deadflowr on 2014-01-09
> **steeldriver said:**
> What do you mean exactly by "its usage said that it is under /opt folder"? deadflower's suggestion will do what you asked, but personally I'm not a fan of unpacking source tarballs as root - it means you need to be root (i.e. use sudo) to configure and build as well. IMHO it keeps things simpler if you unpack in your user area, then configure / build as yourself and FINALLY when you have a successful build (which may take a few tries, unless you have a very complete list of dependencies ahead of time) do a 'sudo make install' (or even better, use checkinstall).

Aye.
This would be far better in the scheme of things.
I'd add that you could simply make a directory to work in.
Something like
```
mkdir test_build
```
which you could then work in on the build.
you'd run the tar command, but remove the sudo designation and change the directory output to ~/test_build.
Then play to your hearts content.

---

### Post by oldos2er on 2014-01-10
According to their [web page]("https://wiki.linaro.org/WorkingGroups/ToolChain") you should be able to find what you need in the repositories: ```
sudo apt-get install gcc-arm-linux-gnueabi
```

---

