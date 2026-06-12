---
title: "making a kernel compilation script"
date: 2006-11-18
forum: Programming Talk
---

### Post by Brando569 on 2006-11-18
hi everyone ive created a basic shell script that extracts/copies/patches and other things that i need it to do. i have it so i have to change the kernel version and patch version in the actual script before it works right, but then i came to the idea of "why not advance it a lil more and make the script ask for input?" 

first off i have basic shell script knowledge and no knowledge of python at all (although i do know c++ but i doubt that helps) (ive seen autokernel on here written in python and thats along the lines of what i have created) my question is, is it easier to take input using python or shell script? i would imagine that to use python i would have to convert everything from shell to python, correct? all i want the input to be is on numeric var (for the kernel version, ex. 2.6.xx) and one string var (for the patch version ex. -beyond4.bz2 or -ck1.bz2) ive tried to research this a little and dont really understand it that much. is there another (simpler) way to input data then this: [input box]("http://www.freeos.com/guides/lsst/ch04sec10.html")

heres my script:
```
##make sure to edit this

##get necessary stuff from the repositories
sudo apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev wget 

#copying kernel source and patches
cd /usr/src
sudo cp ~/kernel/kernels/linux-2.6.18.tar.bz2 /usr/src
sudo cp ~/kernel/patches/patch-2.6.18-ck1.bz2 /usr/src

#extracting kernel
sudo tar -xvjf linux-2.6.18.tar.bz2
sudo rm -rf linux && sudo ln -s /usr/src/linux-2.6.18 linux
cd linux

#patching kernel
sudo bzcat ../patch-2.6.18-ck1.bz2 | patch -p1
sudo cp ~/kernel/speed_hacked.config .config

#making kernel
sudo make xconfig
sudo make-kpkg clean
sudo make-kpkg --initrd kernel_image kernel_headers

#installing kernel and headers
sudo dpkg -i kernel-image-2.6.18-beyond4_10.00.Custom_i386.deb
sudo dpkg -i kernel-headers-2.6.18-beyond4_10.00.Custom_i386.deb

```

---

### Post by Brando569 on 2006-11-18
nevermind i looked into the read command (im learning trueBASIC also and was thinking maybe it worked like the read/data commands and it kinda does) and it does EXACTLY what i need. heres the finished version for anyone who wants it:

```
echo "what kernel version are you using? linux-2.6.what?"
read kernel_version

echo "what patch are you using? patch-2.6.[kernel version].what? 
read patch_version

##get necessary stuff from the repositories
sudo apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev wget 

#copying kernel source and patches
cd /usr/src
sudo cp ~/kernel/kernels/linux-2.6.$kernel_version.tar.bz2 /usr/src
sudo cp ~/kernel/patches/patch-2.6.$kernel_version-$patch_version.bz2 /usr/src

#extracting kernel
sudo tar -xvjf linux-2.6.$kernel_version.tar.bz2
sudo rm -rf linux && sudo ln -s /usr/src/linux-2.6.$kernel_version linux
cd linux

#patching kernel
sudo bzcat ../patch-2.6.$kernel_version-$patch_version.bz2 | patch -p1
sudo cp ~/kernel/speed_hacked.config .config

#making kernel
sudo make xconfig
sudo make-kpkg clean
sudo make-kpkg --initrd kernel_image kernel_headers

#installing kernel and headers
cd ..
sudo dpkg -i kernel-image-2.6.$kernel_version-$patch_version_10.00.Custom_i386.deb
sudo dpkg -i kernel-headers-2.6.$kernel_version-$patch_version_10.00.Custom_i386.deb

```

---

### Post by xtacocorex on 2006-11-18
I had started this for a user (PingunZ) on the forums a while ago: [http://aeronerd.wordpress.com/projects/autokernel/](http://aeronerd.wordpress.com/projects/autokernel/)

Here is the thread about it (now closed): [http://ubuntuforums.org/showthread.php?t=222018](http://ubuntuforums.org/showthread.php?t=222018)

Here is another one about it on Feisty: [http://ubuntuforums.org/showthread.php?t=285029](http://ubuntuforums.org/showthread.php?t=285029)

It is currently written in python and will do automatic editing of the kernel config file sometime, but I'm having a hard time getting motivation to keep working on it since I just got a job offer and will need to learn a whole new engineering discipline quickly.

---

