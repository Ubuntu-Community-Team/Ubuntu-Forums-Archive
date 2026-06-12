---
title: "compiz/fusion in internal video card"
date: 2009-12-15
forum: Philippine Team
---

### Post by sixrodriguez on 2009-12-15
compiz/fusion in internal video card....

sir loell....

ask lang po....

sa windows kaya po ng effects nila internal video ng pc ko...

sa ubuntu karmic po kaya.....

kaya po ba ito ng compiz....

salamat po in advance...

Mabuhay Ubuntu ph!!!

---

### Post by loell on 2009-12-15
ba't naka address lang sa akin ang question? ;)

depende sa internal video processing unit kung may  proper support sya sa Linux with 3d acceleration, ano pala ang make and model ng internal video?

---

### Post by sixrodriguez on 2009-12-15
> **loell said:**
> ba't naka address lang sa akin ang question? ;)

depende sa internal video processing unit kung may  proper support sya sa Linux with 3d acceleration, ano pala ang make and model ng internal video?

wehehe

sir loell eto po yung inboard ko....

 *-display UNCLAIMED
                description: VGA compatible controller
                product: CN896/VN896/P4M900 [Chrome 9 HC]
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: latency=64 mingnt=2
                resources: memory:f8000000-fbffffff(prefetchable) memory:fd000000-fdffffff memory:feaf0000-feafffff(prefetchable)

---

### Post by loell on 2009-12-15
Yes you can, install the chrome driver from [VIA Linux Portal]("http://linux.via.com.tw/support/downloadFiles.action") choose ubuntu then  download the driver.  

you can then enable desktop effects, in fact there is already a spoiler, [http://www.youtube.com/watch?v=wm-oDfBZQAA](http://www.youtube.com/watch?v=wm-oDfBZQAA) ;)

---

### Post by sixrodriguez on 2009-12-15
> **loell said:**
> Yes you can, install the chrome driver from [VIA Linux Portal]("http://linux.via.com.tw/support/downloadFiles.action") choose ubuntu then  download the driver.  

you can then enable desktop effects, in fact there is already a spoiler, [http://www.youtube.com/watch?v=wm-oDfBZQAA](http://www.youtube.com/watch?v=wm-oDfBZQAA) ;)

wow :popcorn:

excited na ako yahoooo!!

maraming salamat po sir loell....

makakabawi din po ako sa inyo wehehehe......

now i know.....

ala talaga kayo time para sa farmvile weheheh....

---

### Post by sixrodriguez on 2009-12-15
waaa nosebleed naku ah....

sixrodriguez@sixrodriguez:~$ tar xjvf /root/via-xserver-86a-50283_src.tgz
tar: /root/via-xserver-86a-50283_src.tgz: Cannot open: Permission denied
tar: Error is not recoverable: exiting now

bzip2: Compressed file ends unexpectedly;
    perhaps it is corrupted?  *Possible* reason follows.
bzip2: Invalid argument
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

@.@

---

### Post by loell on 2009-12-15
lagyan mo ng **sudo** ang mga commands na nasa instructions.

---

