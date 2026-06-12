---
title: "Trouble with Skype in 8.04"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by Felicia_ on 2008-11-10
Hi,

I've been having troubles with Skype ever since I switched to ubuntu, now it's getting pretty annoying. The video resizes after about 40 seconds. I found an explanation of how to fix it, but I'm not sure how to do it. And the Terminal say that the internet address cannot be found. Perhaps somebody could explain in a bit more basic way?


I've downloaded the drivers, but where am I supposed to save them if it should work?

//Felicia


[http://forum.skype.com/index.php?showtopic=127561&st=0](http://forum.skype.com/index.php?showtopic=127561&st=0)

Hi all,

OK, I think I've got it solved. In a nutshell: the patch that can be found from the ekiga forum works in general, however, it doesn't do so out of the box, because ubuntu doesn't place the gspca driver in the default directory, and so it doesn't get removed when the patched version installs.

Do the following:
1. download the GSPCA driver source:
wget [http://mxhaard.free.fr/spca50x/Download/gs...20071224.tar.gz](http://mxhaard.free.fr/spca50x/Download/gs...20071224.tar.gz)

2. unpack the source:
tar xzf gspcav1-20071224.tar.gz

3. download the patch:
wget [http://saillard.org/ekiga/gspcav1-20070508...e_mode_v3.patch](http://saillard.org/ekiga/gspcav1-20070508...e_mode_v3.patch)

4. apply the patch:
cd gspcav1-20071224
patch -p1 < ../gspcav1-20070508_force_using_hardware_mode_v3.patch

5. remove the ubuntu gspca driver(!):
sudo rm -f /lib/modules/`uname -r`/ubuntu/media/gspcav1/gspca.ko

6. build and install the gspca driver:
sudo ./gspca_build

If you want to make double sure, use
locate gspca | grep ^/lib/modules/`uname -r`
in step 5 to verify that there are no gspca.ko drivers sitting around elsewhere. If there they do, remove them before proceeding to step 6.

You will probably have to re-apply this procedure after every kernel-upgrade. So just keep the source around and repeat steps 5 and 6 after a kernel-upgrade.

I hope this works for everyone. Please let me know if it doesn't -- just out of personal interest, I'm not affiliated with Skype or anything.

cheers,
Christian

---

### Post by th89 on 2008-11-10
If you just follow the instructions, that should work. When you run sudo ./gspca_build it appears that it installs it to the correct location. Just follow everything step by step and you should get it.

---

### Post by elord on 2010-08-12
Is there any solution how to fix this skype problem using Ubuntu 8.04? i just read and surf every site and i found nothing but it's not working on hardy..please guys need it badly..

---

