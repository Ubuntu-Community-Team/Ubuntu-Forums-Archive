---
title: "gcc g++ versions"
date: 2013-05-28
forum: New to Ubuntu
---

### Post by adityaharish on 2013-05-28
I have installed gcc 4.8.0 from source using the instructions given in the link below 

[http://askubuntu.com/questions/271388/how-to-install-gcc-4-8-in-ubuntu-12-04-from-the-terminal](http://askubuntu.com/questions/271388/how-to-install-gcc-4-8-in-ubuntu-12-04-from-the-terminal)



But when I check the versions of gcc & g++ they unmatch each other.

```

gcc --version
shraddesh@shraddesh-Samsung-Desktop-System:~$ gcc --version
gcc (GCC) 4.8.0
Copyright (C) 2013 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

The version of g++ is 

```

shraddesh@shraddesh-Samsung-Desktop-System:~$ g++ --version
g++ (Ubuntu/Linaro 4.6.3-1ubuntu5) 4.6.3
Copyright (C) 2011 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```

How can I make the both versions match ??

---

### Post by squakie on 2013-05-28
That link appears to only show GCC.  Perhaps there is another version of jus g++ out there as well.  I've just always been sure to install build-essential not for it's intended purpose but so that I could always get all of the dependencies.  I'm not currently at an Ubuntu box, so I just have to ask why you need this - does it do something for you that the defaults from the repositories doesn't'?

---

### Post by adityaharish on 2013-05-28
I'm currently working on Webkit 

**Compiler GCC >= 4.7 or Clang >= 3.0 is required for C++ compilation**

so I need g++ to  be of version >=4.7

---

### Post by squakie on 2013-05-28
I just did a net search using the following search string:

Ubuntu g++ 4.7

Got all kinds of hits - you may want to try it.  If I read things correctly, I think it is delivered when you install quantal

---

### Post by adityaharish on 2013-05-28
**squakie** .. are you referring to this link 
[http://askubuntu.com/questions/76885/where-can-i-find-a-g-4-7-package](http://askubuntu.com/questions/76885/where-can-i-find-a-g-4-7-package)

I have tried the commands in that link already .
My version number hasn't changed even after doing it .

---

### Post by alan9800 on 2013-05-28
At this time, gcc-4.8 seems to be available only for Ubuntu 13.10; however you might try to add the following PPA:```
sudo add-apt-repository -y ppa:ubuntu-toolchain-r/test
```to your software sources; remember to run:```
sudo apt-get update -y && sudo apt-get dist-upgrade -y
```after having added the PPA.

---

### Post by adityaharish on 2013-05-28
I'm fed up installing gcc 4.8.0 .. I have installed it alteast 15 times using the source code .
gcc , g++ versions never matched .

Adding the repository didn't change any thing.

So I tried  gcc 4.7.3 
since my requirement is GCC >= 4.7

Even installing gcc-4.7.3 didn't change the version of g++

Version of g++ remains same.

Code :
[B]shraddesh@shraddesh-Samsung-Desktop-System:~$ gcc --version
gcc (GCC) 4.7.3
Copyright (C) 2012 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

shraddesh@shraddesh-Samsung-Desktop-System:~$ g++ --version
g++ (Ubuntu/Linaro 4.6.3-1ubuntu5) 4.6.3
Copyright (C) 2011 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

shraddesh@shraddesh-Samsung-Desktop-System:~$ 
[/B]

---

### Post by squakie on 2013-05-28
No - I wasn't talking about that thread.  When I do the search on yahoo there are a lot of returns showing how to install g++ 4.7.

What version of ubunti are you running?  Did you uninstall the previous version before trying to install the new?

Also - as I mentioned, g++4.7 should be in quantal

---

### Post by mc4man on 2013-05-28
When you run gcc or g++ --version it returns whatever /usr/bin/gcc or /usr/bin/g++ link to (gcc & g++ are just links
(unless you've installed gcc to /usr/local/bin or ~/bin which trump /usr/, then it'll report from there

If you used the toolchain ppa properly it would install the higher gcc source packages & replace the current links with ones pointing to those.
(for 12.04 you'd have choice of 4.6, 4.7, 4.8
[https://launchpad.net/~ubuntu-toolchain-r](https://launchpad.net/~ubuntu-toolchain-r)

Even with the ppa you can, if desired, reset the gcc & g++ links back to the 12.04 default & configure your source to use the higher gcc,  how depends on source.

ex. on 13.04, should be no different than 12.04 except for default (pre-ppa) version
> doug@doug-XPS-M1330:~$ g++ --version
g++ (Ubuntu/Linaro 4.7.3-1ubuntu1) 4.7.3
Copyright (C) 2012 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

doug@doug-XPS-M1330:~$ gcc --version
gcc (Ubuntu/Linaro 4.7.3-1ubuntu1) 4.7.3
Copyright (C) 2012 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

After enabling ppa & using synaptic to update & install 4.8
> doug@doug-XPS-M1330:~$ g++ --version
g++ (Ubuntu 4.8.0-4ubuntu1) 4.8.0
Copyright (C) 2013 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

doug@doug-XPS-M1330:~$ gcc --version
gcc (Ubuntu 4.8.0-4ubuntu1) 4.8.0
Copyright (C) 2013 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

4.7 is still there, just no longer the default - (was updated slightly from ppa, 1ubuntu1 to 2ubuntu4
> ~$ gcc-4.7 --version
gcc-4.7 (Ubuntu/Linaro 4.7.3-2ubuntu4) 4.7.3
Copyright (C) 2012 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


screen may show you, is from after ppa install/updates, searches in /usr/bin

---

### Post by adityaharish on 2013-05-29
Why am I getting this error when I run the command [SIZE=3]*sudo apt-get update -y* [/SIZE] ? Does the link exist ?


Code:
            ** sudo apt-get update -y **
[B]W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1E9377A2BA9EF27F
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1E9377A2BA9EF27F


[/B]Adding repository isn't giving me any advantage !! So can you help me with any other method sir??

---

### Post by mc4man on 2013-05-29
> **adityaharish said:**
> Why am I getting this error when I run the command [SIZE=3]*sudo apt-get update -y* [/SIZE] ? Does the link exist ?

I gave you link to the team ppa page, actual ppa that has precise builds is - 
[https://launchpad.net/~ubuntu-toolchain-r/+archive/test](https://launchpad.net/~ubuntu-toolchain-r/+archive/test)

I'd remove any related ppa's from your sources, remove any self builds, update your sources.

Then  - 
```
sudo add-apt-repository ppa:ubuntu-toolchain-r/test
```
```
sudo apt-get update

```

Open synaptic > **reload in synaptic**, then under "Origin"  tab pick the ubuntu-toolchain ppa - you'll see upgrades to 4.6 & installs of 4.7 & 4.8 available. Install gcc/g++ as desired - see screen

---

### Post by adityaharish on 2013-05-29
Thanks mc4man . that worked like a charm

This tool will be helpful to install many libraries which we cannot install  through apt-get.

Once again a Big thanks mate ..

---

