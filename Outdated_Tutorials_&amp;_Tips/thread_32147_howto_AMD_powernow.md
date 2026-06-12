---
title: "howto: AMD powernow"
date: 2005-05-06
forum: Outdated Tutorials &amp; Tips
---

### Post by laue on 2005-05-06
When booting linux, it is stated with exclamationmarks that the amd xp 2000+ does _not_ support power-saving. I find it very disturbing as it might discourage people from using amd or ubuntu. 

i have an amd xp-m, and did not have frequency scaling working in the default ubuntu installation, nor with other pre-built kernels from ubuntu repositories. However, I had frequency scaling working in gentoo, with a kernel i had built myself.

Therefore, I started comparing the ubuntu kernel with the kernel i had compiled in gentoo and came to the belief that the amd powernow and all the other acpi drivers should not be loaded as modules, but should be compiled into the kernel. 

Anyway it worked for me, so here's a (brief) howto if you've never compiled a kernel:

1. use synaptic to download the kernel sources (i use linux-source-2.6.11, but 2.6.10 should do fine as well)
These sources will be installed in /usr/src/linux-source-2.6.11.
If not already done, you should make a symlink called 'linux' to afore mentioned directory
=> ```
cd /usr/src
sudo rm ./linux
sudo ln -s ./linux-source-2.6.11 ./linux
cd linux
```
      
2. now we are in the source directory of the kernel, where we can start building your new kernel.
=> ```
sudo make menuconfig
```

3. You will either see a bleu environment (called ncurses), or the console will tell you to install a few additional packages (forgot which ones). If so, install them using synaptic and issue 'sudo make menuconfig' again.

4. Go to: Power management options (ACPI, APM) -> ACPI (Advanced 
                 Configuration and Power Interface) Support 
    Go to the 'processor' option and use spacebar to replace the <M> with <*>.     
    This will ensure the driver will be compiled into the kernel <*> instead of as a 
    module <M>

5. Go to: Power management options (ACPI, APM) -> CPU Frequency scaling
    - Make sure you enable 'AMD Mobile Athlon/Duron PowerNow!' and nothing else
    - replace all <M> with <*>
    - use userspace as the default governor

6. exit menuconfig, saving your configuration to the default location

7. Compile your kernel and modules, and install the modules:
    ```
make && make modules_install
```

8. Put the kernel into your /boot directory:
    ```
sudo cp arch/i386/boot/bzImage /boot/kernel-2.6.11
sudo cp .config /boot/config-2.6.11
sudo cp System.map /boot/System.map-2.6.11

```

9. Change your grub menu so you can actually choose to use this kernel at boot       
    time
    ```
sudo gedit /boot/grub/menu.lst
```
    In the bottom, you will find the entries for the older kernels. Copy one of them 
    (_copy_, don't remove, so you can still boot your old kernels if something has 
    gone wrong)
    Change the kernel entry to the new kernel path (as shown in red)
    Change the tiltle entry to whatever you would like to be displayed in the grub     
         menu at boot time (as shown in blue)
    example:
   
 copy and alter:```

title          [COLOR=Navy] Ubuntu, kernel 2.6.10-5-386[/COLOR]
root            (hd0,3)
kernel          [COLOR=Red]/boot/vmlinuz-2.6.10-5-386[/COLOR] root=/dev/hda4 ro quiet splash
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot
```

to: ```

title           [COLOR=Navy]Ubuntu, kernel 2.6.11-k7[/COLOR]
root            (hd0,3)
kernel          [COLOR=Red]/boot/kernel-2.6.11[/COLOR] root=/dev/hda4 ro quiet splash
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot

```

Good luck!!!

Disclaimer: I do not garantee that the previous howto will work for you, nor that it is free of errors!

PS: Please add comments and corrections

---

### Post by poofyhairguy on 2005-05-13
Bump.

---

### Post by darkaudit on 2005-05-13
I've got frequency scaling working with a stock kernel (2.6.10-5-k7). The modules necessary weren't loaded by default, but once I added them to /etc/modules, it works just fine.

What I added (motherboard is Abit NF7-S v.2):

cpufreq-nforce2
cpufreq-userspace

---

### Post by willistg on 2005-05-13
[QUOTE=darkaudit]I've got frequency scaling working with a stock kernel (2.6.10-5-k7). The modules necessary weren't loaded by default, but once I added them to /etc/modules, it works just fine.

What I added (motherboard is Abit NF7-S v.2):

cpufreq-nforce2
cpufreq-userspace[/QUOTE]


I just tried this cuz I was a bit concerned when I saw the AMD2600 is known not to support powersaving nah nah etc.

I'm using 2.6.10-5-k7 but powernowd hangs at boot up with the above 2 modules in there.

So I guess my question is ...Any gearheads know whether AMD2600 will work with powernowd or not?

---

### Post by harryc on 2005-05-18
I know that when I boot my SuSE partition (I run an AMD64 3200) It throws up a message that AMD K8's are not compatible with powernow. So I'd say that is a good indication.

---

### Post by laue on 2005-05-19
[QUOTE=darkaudit]I've got frequency scaling working with a stock kernel (2.6.10-5-k7). The modules necessary weren't loaded by default, but once I added them to /etc/modules, it works just fine.

What I added (motherboard is Abit NF7-S v.2):

cpufreq-nforce2
cpufreq-userspace[/QUOTE]

what processor do you use?
Are you sure it works? Or do you guess is works?

---

### Post by Jarz Corp on 2005-05-20
I am on a 3500+ amd64 and powernow works on a stock 2.6.10-5-amd64-k8 kernel.

---

### Post by spookymulder825 on 2005-06-18
(laugh if you have to - i don't know a million terminal commands like the rest of you linux people do)

i was just trying to escape from microsoft (actually, i've been trying for years)... but i couldn't get cpu frequency scaling to work with any of the distributions i tried.  that includes fedora, knoppix, mandrake/mandriva, and now, ubuntu.

cpu frequency scaling is an absolute must for me, as i use a bottom-of-the-line compaq presario 710us notebook with fan that's both loud and ineffective.  windows takes care of the situation without me even asking, but when i run linux, the computer just sits and cooks itself (as well as the unfortunate object or person it's sitting on).

when i found this thread, i thought my problems were finally over.  i started following the directions.  i didn't know what "use synaptic to download the kernel sources" meant, so i just typed synaptic into the terminal and hit enter... i was surprised when something actually appeared (synaptic, i guess).  so i did a search for "linux-source," downloaded it, and installed it.  so far so good.  then i went to the next step:

cd /usr/src
sudo rm ./linux

i didn't know what sudo, rm, or sudo rm meant, but i typed it in anyway, and it said rm: cannot remove `./linux': No such file or directory.

but i ignored that and went on to:

sudo ln -s ./linux-source-2.6.11 ./linux

since i had the 2.6.10 kernel/package/whatever in /usr/src, i had to use

sudo ln -s ./linux-source-2.6.10 ./linux

instead.  that seemed to have worked... but when i went to

cd linux

it said "no such file or directory."  i discovered that there was no linux-source-2.6.10 directory... only a .tar.bz2 file called linux-source-2.6.10.  i figured i could extract it, but "file roller"/"archive manager" told me i didn't have the right permissions.  so i entered "nautilus /usr/src" in the root terminal (something i figured out all by myself - it made me so proud!), and tried again.  this time file roller said

An error occurred while extracting files.
Failed to execute child process "/bin/sh" (Argument list too long)

I'M SICK OF LINUX.  all i wanted was a non-microsoft operating system that worked, and that i could afford (unlike mac os and the associated hardware).  i thought linux would be better than the sloppy, crush-helpless-little-software-companies-and-steal-their-code, download your critical updates for your critical updates for your critical updates because we can't get it right the first, second, or third time... mess that is windows.  but it turned out that linux was worse.  in every distribution i've tried, everything has to be done from the terminal, no matter how fancy/bloated the GUI is... in windows, i could install a program just by opening a .exe file, and when that was over, i would have shortcuts waiting for me in the start menu... in linux, i spend hours searching the internet for something that can teach me what to do with my .tar.gz or .bin or whatever file, then spend more hours figuring out where to get the packages/software that i've just been told are needed to continue, then spend more hours installing more software, then start over when i find out i have the wrong version... all from the terminal.

i TRIED.  i really thought i could make the switch to linux.  but until you people start making it easier to install software and configure hardware (i.e. i don't have to waste my life digging through the web for the right commands), i can't.

in my humble, disillusioned opinion... when you linux people design your software, you should be thinking "will my mother be able to use this WITHOUT me beside her?"  THEN, and ONLY THEN, will you be able to win over the 99% or so of computer users who are still slaves to bill gates.

(sorry, it's 4 a.m. and i'm tired and angry)

---

### Post by blackpaw on 2005-10-23
can this go to the "breezy" forums?

I am having an issue with powernowd right now and trying to fix it using this thread (spookymulder: noone is laughing. But it will not work if you don't show a little effort, sorry. I also want to get away from MS and I am getting better and better at Linux because Ubuntu gives me the chance to do so. But I have to read documents and inform myself a little nevertheless. You can't just issue the command "rm" without knowing what it will do and just compiling a kernel is also not what you should do. Get familiar with things like "symlink" and basic shell commands then everything will be a lot easier for you to understand. and then compiling a kernel is a piece of cake.)

anyway just some additions: 

synaptic provides a linux-source [my kernel here] and puts it into /usr/src/ as a tar.bz2
jsut search for "linux-source", easier than downloading it manually

unpack with: sudo tar jxvf linux-source-2.6.12.tar.bz2
create a symlink: sudo ln -s linux-source-2.6.12 linux

then continue according to plan.

---

### Post by regeya on 2005-10-23
[QUOTE=spookymulder825] in my humble, disillusioned opinion... when you linux people design your software, you should be thinking "will my mother be able to use this WITHOUT me beside her?" THEN, and ONLY THEN, will you be able to win over the 99% or so of computer users who are still slaves to bill gates[/QUOTE] 

How many non-technical people (usually referred to as "mothers" in rants and/or tired anti-Linux trolls) can deal with technical problems and/or non-standard installations in Windows or MacOS X unaided?

I say this because I've heard it a million times.  Someone is rightfully frustrated because all the knowledge they've accumulated over the years counts for nothing.  Despite the revelation that their experience isn't going to help them, rather than leading them in the correct direction--as in, "hey, I should start reading"--it leads them on the same, tired rant we've heard a million times before.  For Linux to be ready for the drooling masses, it needs to be instantly configured to the million or so "normal" configurations people should be used to.  On top of that, all hardware should instantly be configured correctly, and to the user's specifications--all without user intervention.  Further, the system should be, in all ways, self-repairing so the user has no need to ever fix anything manually!

When someone finds this Utopian vision of an operating system, someone please let me know; people have been saying for years that Linux needs to be this all-knowing, all-powerful system, and I've yet to see *anything* that *anywhere* close to the ideal.

---

