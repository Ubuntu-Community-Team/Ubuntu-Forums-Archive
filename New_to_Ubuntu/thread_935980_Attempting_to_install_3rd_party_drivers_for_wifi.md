---
title: "Attempting to install 3rd party drivers for wifi"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by hatrack on 2008-10-02
Hello All,

I am looking for a little bit of help installing some 3rd party drivers for a wireless dongle. The drivers are obviously not available in Synaptic and I need this to run the dongle which connects to my router.

I have downloaded the relevant drivers in .tar.bz2 format and used 'extract here' to produce an extracted directory. I have started to follow the 'README' instructions, but it fails at a certain point and I do not understand why. The instructions are as follows....

```

Build Instructions:  

====================

1> $tar -xvzf RT73_Linux_STA_Drv_x.x.x.x.tar.gz

    go to "./RT73_Linux_STA_Drv_x.x.x.x/Module" directory.

    

2> $cp Makefile.4  ./Makefile       # [kernel 2.4]

    or

   $cp Makefile.6  ./Makefile       # [kernel 2.6]

   

3> [kernel 2.4]

    $chmod 755 Configure

    $make config         # config build linux os version



4> $make all            # compile driver source code

4.1> $make install



5> $cp rt73.bin /etc/Wireless/RT73STA/	    # copy firmware

 

6>  $dos2unix rt73sta.dat

    $cp rt73sta.dat  /etc/Wireless/RT73STA/rt73sta.dat       

    # !!!check if it is a binary file before loading !!!  

    

7> $load                

    #[kernel 2.4]

    #    $/sbin/insmod rt73.o

    #    $/sbin/ifconfig rausb0 inet YOUR_IP up

        

    #[kernel 2.6]

    #    $/sbin/insmod rt73.ko

    #    $/sbin/ifconfig rausb0 inet YOUR_IP up




```

When I get to point 3 is where the trouble begins. When you type : Make config, it gives you a sort of dialog and when you try to begin step 4, you get the following error : 

```

beric@beric:~/Desktop/2008_0506_RT73_Linux_STA_Drv1.1.0.1/Module$ make config


-------------------- Ralink RT73 Station Configuration -------------------- 

  Linux kernel source directory [/usr/src/linux-2.6.24-19-generic]: make all
 
./Configure: line 82: [: make: binary operator expected
  Linux kernel source directory : make all
 
sed: can't read make: No such file or directory
sed: can't read all/Makefile: No such file or directory
sed: can't read make: No such file or directory
sed: can't read all/Makefile: No such file or directory
sed: can't read make: No such file or directory
sed: can't read all/Makefile: No such file or directory
sed: can't read make: No such file or directory
sed: can't read all/Makefile: No such file or directory
expr: syntax error
./Configure: line 104: [: -lt: unary operator expected
  Module install directory : /lib/modules/2.6.24-19-generic/kernel/drivers/net
 
beric@beric:~/Desktop/2008_0506_RT73_Linux_STA_Drv1.1.0.1/Module$ 


```

This whole problem started because when I installed the dongle, it worked fine for a little while (about a day) but when I rebooted, it lost the dongle again. Apparently, the only fix is to unplug the dongle and plug it back in again. I understand that this is probably a driver problem and so have the correct linux drivers for this type of dongle and I am just trying to install them. My last step was going to be to add the newly installed driver to the whitelist so that it stays, but I am also unsure how to accomplish this. Can anyone help with this problem please?

Thanks in advance

---

### Post by hatrack on 2008-10-02
Hello all,

After some investigation, it seems as though the rt73 drivers are part of the Ubuntu installation. It appears that whenever the computer is re-booted, it looses the wifi connection and the dongle has to be physically pulled out and replaced for a connection to take place. I have added the drivers to /etc/modules but this does not seem to make a single bit of difference. My theory is that the act of pulling the dongle forces it to handshake with the hub and thus an internet connection is established, but that it is not doing this correctly and automatically at boot. What I cannot establish is whether there is a setting somewhere that will turn this feature on since obviously it is not practicable to keep pulling the dongle and re-applying it every time I connect to the internet. Any information or assistance would be gratefully received.

Kind Regards

---

