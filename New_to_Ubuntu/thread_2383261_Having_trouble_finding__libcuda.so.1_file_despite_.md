---
title: "Having trouble finding  libcuda.so.1 file despite CUDA being installed."
date: 2018-01-22
forum: New to Ubuntu
---

### Post by saya18 on 2018-01-22
I've installed CUDA and have a Nvidia driver installed but when I run a Python module that uses CUDA, I'm getting an 
error that  "libcuda.so.1 file" is not found. 

I'm using ubuntu 16.04 and using Python 3.6 /Python 2.7

This is the exact error:

```
ImportError: libcuda.so.1: cannot open shared object file: No such file or directory
```



From what I've been told, this file is a link and it needs to be  linked to my graphics card driver.

I wasn't sure how to check if i have this link but I ran this command and I got back this as an output (abridged):

```
find / -type f -name "libcuda.so.1
```




```
ind: &#8216;/etc/cups/ssl&#8217;: Permission denied
find: &#8216;/etc/polkit-1/localauthority&#8217;: Permission denied
find: &#8216;/etc/ssl/private&#8217;: Permission denied
find: &#8216;/tmp/systemd-private-bfc953f066c54c8f8989b0585e58681d-colord.service-QhckWW&#8217;: Permission denied
find: &#8216;/tmp/systemd-private-bfc953f066c54c8f8989b0585e58681d-systemd-timesyncd.service-A46ooI&#8217;: Permission denied
find: &#8216;/tmp/systemd-private-bfc953f066c54c8f8989b0585e58681d-rtkit-daemon.service-pZ6U3J&#8217;: Permission denied
find: &#8216;/lost+found&#8217;: Permission denied
find: &#8216;/var/tmp/systemd-private-7216baf4e9e24f4b99aa9cd9d37e9779-rtkit-daemon.service-vEpGYO&#8217;: Permission denied
find: &#8216;/var/tmp/systemd-private-c9508c53c88848febd8d6b9c7758d44d-colord.service-6sVMbw&#8217;: Permission denied
find: &#8216;/var/tmp/systemd-private-7216baf4e9e24f4b99aa9cd9d37e9779-systemd-timesyncd.service-DifcXc&#8217;: Permission denied
find: &#8216;/var/tmp/systemd-private-7216baf4e9e24f4b99aa9cd9d37e9779-colord.service-j5hYyg&#8217;: Permission denied
find: &#8216;/var/tmp/systemd-private-81dcc732570e47799cb04c3cb0c5a2c6-systemd-timesyncd.service-dSg1Cz&#8217;: Permission denied
find: &#8216;/var/tmp/systemd-private-f72e80f0374645bda6c2d99c5628e374-colord.service-FbxlSK&#8217;: Permission denied
find: &#8216;/var/tmp/systemd-private-5065912711c44bfd880f3aca2d0008e7-colord.service-rq0MKq&#8217;: Permission denied
find: &#8216;/var/tmp/systemd-private-bfc953f066c54c8f8989b0585e58681d-rtkit-daemon.service-W2mqTy&#8217;: Permission denied
find: &#8216;/var/tmp/systemd-private-5065912711c44bfd880f3aca2d0008e7-rtkit-daemon.service-Nmhoc5&#8217;: Permission denied
find: &#8216;/var/tmp/systemd-private-bfc953f066c54c8f8989b0585e58681d-colord.service-yD6AKb&#8217;: Permission denied
find: &#8216;/var/tmp/systemd-private-310aa08f8dac48c087fb3d04eb13211d-rtkit-daemon.service-2aRSdk&#8217;: Permission denied
find: &#8216;/var/tmp/systemd-private-cc0e6bd6ee4c4e5a8e66d39c662b4262-systemd-timesyncd.service-cR7tKn&#8217;: Permission denied
find: &#8216;/var/tmp/systemd-private-81dcc732570e47799cb04c3cb0c5a2c6-colord.service-RpnOff&#8217;: Permission denied
find: &#8216;/var/tmp/systemd-private-93e35b4b8e084692829998454c625032-rtkit-daemon.service-FPP0C0&#8217;: Permission denied
find: &#8216;/var/tmp/systemd-private-f72e80f0374645bda6c2d99c5628e374-rtkit-daemon.service-KSb7II&#8217;: Permission denied
find: &#8216;/var/tmp/systemd-private-93e35b4b8e084692829998454c625032-colord.service-umcrrr&#8217;: Permission denied



```


Running this command:

```
ls /usr/local/cuda-8.0/doc/man/man7/libcuda.so.7 -la

```

Got me this output:

```
-rw-r--r-- 1 root root 26 Jan 26  2017 /usr/local/cuda-8.0/doc/man/man7/libcuda.so.7

```

But I couldn't find libcuda.so.1 within the same vicinity of folders. 

If i run:

And if I run nvidia-smi I get back this:



```

------------------------------------------------------+                       
| NVIDIA-SMI 340.104    Driver Version: 340.104        |                       
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 260     Off  | 0000:01:00.0     N/A |                  N/A |
| 40%   46C   P12    N/A /  N/A |    226MiB /   895MiB |     N/A      Default |
+-------------------------------+----------------------+----------------------+

    +-----------------------------------------------------------------------------+
    | Compute processes:                                               GPU Memory |
    |  GPU       PID  Process name                                     Usage      |
    |=============================================================================|
    |    0            Not Supported      




```



I'm stumped as to how to overcome this error.

Is libcuda.so.7 also a symlink?

How do I find where libcuda.so.1 is ?
And how do I link it with my graphic card driver (I don't know how to locate the driver as well)

Thank you.

---

### Post by monkeybrain20122 on 2018-01-25
What is the output for
```
locate libcuda.so.1
```

---

### Post by Yellow Pasque on 2018-01-25
Do you have packages libcuda1-340 and pyhton3-pycuda installed?

---

### Post by saya18 on 2018-01-26
> **monkeybrain20122 said:**
> What is the output for
```
locate libcuda.so.1
```


Hi. I seem to get back an empty response.

Does that mean libcuda.so.1 is not installed?


EDIT:

If I browse my computer directory, I noticed that there is a CUDA-8.0 at this location:

```
/usr/local/
```

I also see a CUDA folder with an arrow on it (which I presume represents a shorcut) here in 

```
/usr/local/
```

---

### Post by saya18 on 2018-01-26
> **Temüjin said:**
> Do you have packages libcuda1-340 and pyhton3-pycuda installed?


I'm not sure what python3-pycuda is, but I try "locate libcuda1-340" I get back a blank response.

---

### Post by deadflowr on 2018-01-26
libcuda would be in the /usr/lib/x86_64-linux-gnu directory (or /usr/lib/i386-linux-gnu if on 32-bit Ubuntu)
How'd you install cuda?

---

### Post by saya18 on 2018-01-26
> **deadflowr said:**
> libcuda would be in the /usr/lib/x86_64-linux-gnu directory (or /usr/lib/i386-linux-gnu if on 32-bit Ubuntu)
How'd you install cuda?


It was a few weeks ago so it's either this command:

sudo apt install nvidia-cuda-tookit

Or I ran a  run file which I downloaded from the Nvidia website. 


Using this command adds the path to the environmental variable?

   ```
 export PATH=$PATH:/usr/local/cuda-8.0/bin
```

I just tried it and now nvcc seems to work.

Now when I run ```
 nvcc --version
```



```



 nvcc --version
nvcc: NVIDIA (R) Cuda compiler driver
Copyright (c) 2005-2016 NVIDIA Corporation
Built on Tue_Jan_10_13:22:03_CST_2017
Cuda compilation tools, release 8.0, V8.0.61


```


However, when I run 

```
locate libcuda.so.1
```

I get back an empty screen.

---

### Post by mc4man on 2018-01-27
If you installed your nvidia drivers from a .deb package then a corresponding libcuda package would also be installed. If you install the drivers from a .run file then I gather libcuda may come with it (the .7 .so) but apparently you need  one named .1

So you could probably
1. Remove the current nvidia drivers & install from a .deb package (- making sure you get at least the min. version needed for your cuda toolkit version
2. create a symlink named libcuda.so.1 linking to the actual .so you have.

More current nvidia drivers in .deb form can be gotten here 
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

---

### Post by pauljw on 2018-01-27
I'm no expert here at all, but I have sometimes needed to:  "sudo updatedb"  before the locate command would show recently installed files.  Maybe that's the case here.

---

### Post by saya18 on 2018-01-27
> **mc4man said:**
> If you installed your nvidia drivers from a .deb package then a corresponding libcuda package would also be installed. If you install the drivers from a .run file then I gather libcuda may come with it (the .7 .so) but apparently you need  one named .1

So you could probably
1. Remove the current nvidia drivers & install from a .deb package (- making sure you get at least the min. version needed for your cuda toolkit version
2. create a symlink named libcuda.so.1 linking to the actual .so you have.

More current nvidia drivers in .deb form can be gotten here 
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)


Going through my terminal commands it seems I installed Nvidia drivers like this:

sudo apt-get install nvidia-current
sudo add-apt-repository
sudo add-apt-repository ppa:graphics-drivers
sudo apt-get update

sudo apt-get install nvidia-340

This seems to be same method you are suggesting? 

Thank you. 


I remember I was having problems with with some versions, but nvida-340 seems to work fine.

---

### Post by saya18 on 2018-01-27
> **pauljw said:**
> I'm no expert here at all, but I have sometimes needed to:  "sudo updatedb"  before the locate command would show recently installed files.  Maybe that's the case here.


Thank you. I tried it, but still can't find the file.

---

### Post by pauljw on 2018-01-27
No problem, thought it may be worth a shot.  :)

---

### Post by The Cog on 2018-01-27
It is probably worth taking mc4man's suggestion and creating a symlink named libcuda.so.1 to your existing file. The later version probably just has new features that anything wanting to use version 1 won't call.

---

### Post by saya18 on 2018-01-27
> **The Cog said:**
> It is probably worth taking mc4man's suggestion and creating a symlink named libcuda.so.1 to your existing file. The later version probably just has new features that anything wanting to use version 1 won't call.


Thank you. So is this the proper to create a symlink in my case?


```
ln -s /usr/local/cuda-8.0/doc/man/man7/libcuda.so.7   libcuda.so.1


```

---

### Post by The Cog on 2018-01-27
I always have trouble with paths and symlinks. I would do it this way:
```
cd /usr/local/cuda-8.0/doc/man/man7/
sudo ln -s libcuda.so.7 libcuda.so.1
```
If it doesn't work, you can just rm the symlink again.

---

### Post by saya18 on 2018-01-27
> **The Cog said:**
> I always have trouble with paths and symlinks. I would do it this way:
```
cd /usr/local/cuda-8.0/doc/man/man7/
sudo ln -s libcuda.so.7 libcuda.so.1
```
If it doesn't work, you can just rm the symlink again.


Thank you. I tried what you suggested, but I'm still getting the same error:

```
ImportError: libcuda.so.1: cannot open shared object file: No such file or directory


```


It seems like I did create the symlink, as If I run the code, I get that there is a libcuda.so.1 file already.
So is the next problem a path issue? 

Not sure what I should be adding to the PATH.

Thank you.

---

### Post by The Cog on 2018-01-27
Hmm. I wonder if it needs to be in a different location. If so, I don't know where it needs to be.

---

### Post by Yellow Pasque on 2018-01-27
> /usr/local/cuda-8.0/doc/man/man7/libcuda.so.7

This is a man(ual) page. This is not what you need. Symlinking to a manpage will not help you.

> "locate libcuda1-340" I get back a blank response. 

No. libcuda1-340 is the package which has the file you need. Make sure it is installed:
```
sudo apt-get install libcuda1-340
```
Is there a reason you couldn't use the version in the repository or at least use Nvidia's .deb file?

---

### Post by saya18 on 2018-01-28
> **Temüjin said:**
> This is a man(ual) page. This is not what you need. Symlinking to a manpage will not help you.



No. libcuda1-340 is the package which has the file you need. Make sure it is installed:
```
sudo apt-get install libcuda1-340
```
Is there a reason you couldn't use the version in the repository or at least use Nvidia's .deb file?


Ah, I see. Going to try installing it. I tried the .debian file, but I forget the problems I was having. Honestly, I tried so many ways to install CUDA TOOLS and Nvidia drivers, that I lost count.
I was following the Nvidia instructions, then multiple blogs and get running into strange bugs (login bug with newest drivers). I was finally able to install drivers and CUDA (which I thought) but following instructions on some blog.
So that's why my install setup has been so wacky.


UPDATE:

I installed libuca1-340,

and now I seem to be getting a different error, not sure if it's because of the earlier symlink I created or maybe a PATH issue?

ImportError: /home/moondra/.local/lib/python3.6/site-packages/tensorflow/python/../libtensorflow_framework.so: undefined symbol: cuDevicePrimaryCtxSetFlags

---

### Post by mc4man on 2018-01-29
see here
[https://github.com/tensorflow/tensorflow/issues/6787](https://github.com/tensorflow/tensorflow/issues/6787)
The gist of it seems to be to try newer nvidia driver than 340, the ppa has 384, 387, 390, ubuntu repos for 16.04 probably has 384

---

### Post by Yellow Pasque on 2018-01-29
> **mc4man said:**
> see here
[https://github.com/tensorflow/tensorflow/issues/6787](https://github.com/tensorflow/tensorflow/issues/6787)
The gist of it seems to be to try newer nvidia driver than 340, the ppa has 384, 387, 390, ubuntu repos for 16.04 probably has 384

The two people who reported success there were using a GTX750 (Maxwell) and a Grid K520 (Kepler), so they had the option to run the latest stable driver. 
OP here is using a GTX 260, and is limited to 340.xx driver.

---

### Post by Yellow Pasque on 2018-01-29
TensorFlow requires "GPU card with CUDA Compute Capability 3.0 or higher"
[https://www.tensorflow.org/install/install_linux](https://www.tensorflow.org/install/install_linux)

Your GTX 260 only supports CUDA Compute 1.3:
[https://developer.nvidia.com/cuda-legacy-gpus](https://developer.nvidia.com/cuda-legacy-gpus)

You must use the CPU version of TensorFlow (or get a better GPU).

---

### Post by saya18 on 2018-02-06
> **Temüjin said:**
> TensorFlow requires "GPU card with CUDA Compute Capability 3.0 or higher" [https://www.tensorflow.org/install/install_linux](https://www.tensorflow.org/install/install_linux)  Your GTX 260 only supports CUDA Compute 1.3: [https://developer.nvidia.com/cuda-legacy-gpus](https://developer.nvidia.com/cuda-legacy-gpus)  You must use the CPU version of TensorFlow (or get a better GPU).   Ah. Thank you so much. Despite, listing my graphics card info, none of the nvdia members pointed this out.  I thought because my graphics card was CUDA okay, I could use it with Tensorflow etc.   Anyway, after restarting the computer I'm stuck in a login loop, which I will make another thread about.

---

