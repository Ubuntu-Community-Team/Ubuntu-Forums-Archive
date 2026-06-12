---
title: "Precise Guidelines: Compiling a vanilla kernel (2.6.18.3) in Edgy Eft"
date: 2006-11-26
forum: Outdated Tutorials &amp; Tips
---

### Post by EmanuilTolev on 2006-11-26
This is a document (compiled from personal notes, i.e. flying-paper-notes-taken-while-surfing-the-net) which will give you precise guidelines on how to recompile your new shiny vanilla 2.6.18.3 kernel you just downloaded from the site below. Also includes some VERY basic and VERY CUSTOM (PERSONAL) information on setting up patch-o-matic and using the 'ttl' patch from there.

[www.kernel.org](www.kernel.org)
[http://www.netfilter.org/documentation/HOWTO//netfilter-extensions-HOWTO-2.html#ss2.1](http://www.netfilter.org/documentation/HOWTO//netfilter-extensions-HOWTO-2.html#ss2.1)

 HOWTO: Kernel compilation

1. First of all, download the kernel package you want from kernel.org .

Now type 'su' in the console and enter the root pass. If you don't have one, than you'll have to add 'sudo' in front of all my commands and type your pass at every command. I know you won't like it, so set a root password NOW with 'sudo passwd root'.

2. Secondly, you need to download the following packages in Ubuntu Edgy Eft.

apt-get update
apt-get install build-essential kernel-package gcc libncurses5 libncurses5-dev libqt3-mt-dev

3. Extract the kernel sources:

cd /usr/src
tar xvf linux-2.6.18.3.tar.gz

4. Create the following symlink:

ln -s /usr/src/linux-2.6.12 /usr/src/linux

(if you'll use patch-o-matic ONLY) 5. Extract the current iptables source to /usr/src/

(if you'll use patch-o-matic ONLY) 6. Create a symbolic link:

ln -s /usr/src/iptables-x.xx.xx iptables

(if you'll use patch-o-matic ONLY) 7. Extract Patch-o-Matic (anywhere). CD into it's dir now.

(if you'll use patch-o-matic ONLY) 8. Delete all folders except 'TTL' and 'update'

(if you'll use patch-o-matic ONLY) 9. './runme base/ttl' in it's directory

./runme base/ttl

10. Now you can start customizing your kernel configuration using xconfig.

cd /usr/src/linux
make xconfig

11. Then, after having finished the customization, we have to start the compile process:

make-kpkg clean
make-kpkg --initrd --append-to-version=YourName261106 kernel_image modules_image

12. Install the fresh .deb package:

dpkg -i linux-image*.deb


Obviously, at step 11, '--append-to-version=' option, you should put YOUR name and the CURRENT date, instead of the dummy 'YourName261106' string.

Enjoy :)!

The 'ttl' patch was needed, because my ISP is trying to be nasty, limiting the computers that can use the Internet to 1 at time. And I have to pay for another cable and another static real IP every month, just because they're setting the ttl of every packet, which passes through their Gateway to TTL=1 -.- .
I'm working on a workaround at the time being and will probably post it after I'm finished with it :).

---

### Post by dubrict on 2006-12-07
Thanks a lot!  I used your guide to compile my first kernel.  I used 2.6.19 and stripped off support for everything I don't have... now it's a lot faster!

---

### Post by moreon on 2007-01-27
I followed all the steps up to 11, although I skipped steps 4-9 cause I'm not using patch-o-matic, but then I can't find the .deb file anywhere in my filesystem. What has happened?

P.S. Nevermind. I found it! Thanx for the walkthrough.

---

