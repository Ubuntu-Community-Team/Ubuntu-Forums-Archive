---
title: "Performance Issues"
date: 2012-10-15
forum: New to Ubuntu
---

### Post by GaryTheCat on 2012-10-15
Hello

I've been using Ubuntu since 10.04 and have upgraded when each new release has come along using a fresh install from CD.

I'm now on 12.04 and have noticed that the performance of my machine has deteriorated over recent weeks.

I'm FAR from an expert with Linux and was wondering if there's anything I can do (short of bumping up memory) to resolve the performance issue?

Happy to post any additional system info required to diagnose this.

TIA

G

---

### Post by alenn on 2012-10-15
you can try with preload, it will slightly increese performace
sudo apt-get install preload

---

### Post by NikTh on 2012-10-15
Yes you can provide some additional info if you want. 

Open a terminal and give the results of these commands 

```
lscpu 
free -m 
lspci -nnk | grep -iA2 vga
df -Th
/usr/lib/nux/unity_support_test -p
``` 

Thanks

---

### Post by GaryTheCat on 2012-10-18
The output is:

```

gary@gary-Inspiron-1720:~$ lscpu 
Architecture:          i686
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                2
On-line CPU(s) list:   0,1
Thread(s) per core:    1
Core(s) per socket:    2
Socket(s):             1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 15
Stepping:              13
CPU MHz:               1867.000
BogoMIPS:              3724.50
L1d cache:             32K
L1i cache:             32K
L2 cache:              1024K
gary@gary-Inspiron-1720:~$ free -m 
             total       used       free     shared    buffers     cached
Mem:          2011       1884        127          0         96        215
-/+ buffers/cache:       1572        439
Swap:         2043        146       1897
gary@gary-Inspiron-1720:~$ lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G84 [GeForce 8600M GT] [10de:0407] (rev a1)
	Subsystem: Dell Device [1028:01f2]
	Kernel driver in use: nvidia
gary@gary-Inspiron-1720:~$ df -Th
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sdb5      ext4      120G   30G   85G  27% /
udev           devtmpfs  999M  4.0K  999M   1% /dev
tmpfs          tmpfs     403M  940K  402M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs    1006M   26M  981M   3% /run/shm
/dev/sdb1      fuseblk   342G  255G   88G  75% /home/gary/MountedData
gary@gary-Inspiron-1720:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 8600M GT/PCIe/SSE2
OpenGL version string:  3.3.0 NVIDIA 295.40

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

```

Thanks in advance

G

---

### Post by NikTh on 2012-10-19
Ok , 

**first** do what [alenn]("http://ubuntuforums.org/member.php?u=1050705") said. Preload is a good and very light package (I think its a script) , it will help with the opening of programs that you use often (opening faster). 

```
sudo apt-get install preload
```**Second**

Ubuntu is pre-configured to use swap when the physical memory exceeds the 50% of use. You can change that and tell to Ubuntu to use swap only when physical memory is close to 80%-90%. 

Give this command 
```
echo 'vm.swappiness = 10' | sudo tee -a /etc/sysctl.conf
```**Third**
You can update your graphics driver to a newer version as 295.40 had some bugs and issues (maybe performance issues too)

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update 
sudo apt-get dist-upgrade
```You can undo with these commands 
```
sudo add-apt-repository --remove ppa:ubuntu-x-swat/x-updates
sudo apt-get update 
sudo apt-get dist-uprgade
```**Last **
You can change the Desktop Environment to a more lighter. 
It is the same desktop (Unity) , but without all the fancy 3D effects. You have not to install something , this Desktop is pre-installed , just select it from the Login screen.
Ubuntu-2D

Thanks

---

### Post by GaryTheCat on 2012-10-21
I've done all you suggested and think I'll sit back and see whether I notice a difference.

Thanks so much for your help

G

---

