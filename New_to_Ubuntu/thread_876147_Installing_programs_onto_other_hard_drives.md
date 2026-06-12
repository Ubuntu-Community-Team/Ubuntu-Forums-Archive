---
title: "Installing programs onto other hard drives?"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by mindpulse on 2008-07-31
Hey, I currently have a dual boot setup with a 10 gig partition for each OS and a 72 gig shared partition. As of right now, I've only been able to install programs for ubuntu onto the drive the OS is on. Is there a way to change the add/remove programs manager or the synaptic package manager to allow me to install programs onto my other drive partition?

---

### Post by neurostu on 2008-07-31
No you cannot...

The Add/Remove is a front end to apt which is a front end to dpkg which install's deb packages...

Deb packages define where the program installs too, you cannot change this...

What you can do however is download programs as source and then compile them, once compiled you can install them anywhere you like.

---

### Post by mindpulse on 2008-07-31
ok, what should I use to compile the source if I obtain it?

---

### Post by Steveway on 2008-07-31
Why don't you just resize your Ubuntu-partition from a Live-CD?
I would NOT recommend changing where programs get installed because without experience that means a lot of hassle and breakage.

---

### Post by neurostu on 2008-07-31
To build from source you will need to install a couple of things first, open a terminal and then type:
```

sudo apt-get install buildessential autoconf automake

```
These are programs that will help you build and compile.


Most programs you download will have pretty standard steps to install:
-Un-tar the archive
-run ./configure (./autogen.sh if configure isn't present, then ./configure)
-run make
-run sudo make install

you can give configure a --prefix="destDir" argument that will let you install to a specific directory...

---

### Post by neurostu on 2008-07-31
> **Steveway said:**
> Why don't you just resize your Ubuntu-partition from a Live-CD?
I would NOT recommend changing where programs get installed because without experience that means a lot of hassle and breakage.

I would totally agree with this... 

The way programs are installed in linux is very different then windows, there is not a Program Files/ dir with sub directories for every program.  Programs in linux SHARE common directories for libraries, binaries, etc...

If you're new to linux I would recommend trying to resize your partition before getting into the world of building from source.


Do you want to install to the other HDD because you want to access the program from your other OS or are you simply running out of space.

---

### Post by mindpulse on 2008-07-31
hmm, it may be more convenient to just expand the partition, but on the other hand, I'm a second year student in computer engineering and am about to be going into classes on unix operating systems, and have had a bit of experiencing both in designing programs and in designing hardware in research labs, so I'd kind of feel as if I were copping out if I just took the easy way of doing things :) Plus, part of why I decided to start using linux was so that I could learn more about OS/hardware interaction, so again, learning the hard way isn't so bad

thank you very much though! I'll be trying out those programs you suggested, and I suppose if that fails I'll just extend the partition. Wish me luck!

---

### Post by mindpulse on 2008-07-31
> **neurostu said:**
> To build from source you will need to install a couple of things first, open a terminal and then type:
```

sudo apt-get install buildessential autoconf automake

```
These are programs that will help you build and compile.


Most programs you download will have pretty standard steps to install:
-Un-tar the archive
-run ./configure (./autogen.sh if configure isn't present, then ./configure)
-run make
-run sudo make install

you can give configure a --prefix="destDir" argument that will let you install to a specific directory...

so do you mean like: run ./configure --E:
or more like: run ./configure --prefix="E:"
or something different?

---

### Post by mindpulse on 2008-07-31
er, also, tried that command for the install and got this:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package buildessential

guess I should find this off the server instead of doing it through terminal?

---

### Post by neurostu on 2008-07-31
./configure --prefix=/dest/directory/

There is absoluetely nothing wrong with wanting to biuld things from source... it can just be a bit difficult at the beginning.

Also most packages you download SHOULD include a README file that should explain how to install that package.

---

### Post by neurostu on 2008-07-31
sorry the package is:
build-essential

---

### Post by mindpulse on 2008-07-31
thanks! time to get my hands dirty and try not to break stuff :)

---

### Post by stchman on 2008-07-31
> **mindpulse said:**
> Hey, I currently have a dual boot setup with a 10 gig partition for each OS and a 72 gig shared partition. As of right now, I've only been able to install programs for ubuntu onto the drive the OS is on. Is there a way to change the add/remove programs manager or the synaptic package manager to allow me to install programs onto my other drive partition?

It is not that big of a deal.  A fully loaded Ubuntu with all applications installed will never go over say 6GB.  A fresh Vista install is a little over 10GB and that is with nothing installed.

I personally save all my private data (music, video, etc.) on another partition.

When you download a .deb package you are installing the bare minimum.  Apt checks to see if the dependencies are installed.  The theory is that MANY different programs can share the same dependency and not have to install that same file many time.

---

### Post by mindpulse on 2008-07-31
hmmm.... I guess for now I'll try to keep things on the ubuntu drive. the big problem's gonna be when I start doing things like installing xilinx ISE 10.1, which I believe can ONLY be installed onto ubuntu through source and through a LOT of hassle (though supposedly worth it considering the smoothness it'll run at compared to on windows). that, any also for things like stepmania since I was gonna use that as a trial run at learning how to do things through source

---

### Post by a0u on 2008-07-31
You can also use LVM to increase the size of the root partition: [http://ubuntuforums.org/showthread.php?t=540884](http://ubuntuforums.org/showthread.php?t=540884)
If you have multiple physical drives, you can combine them into one logical partition.

---

### Post by mindpulse on 2008-07-31
by any chance can you install windows programs onto a secondary drive through wine?
I ask since one of the reasons for this shared drive is for usage under both OSes

---

### Post by cariboo on 2008-07-31
For some info on the linux file system, have a look here:

[http://www.pathname.com/fhs/2.2/](http://www.pathname.com/fhs/2.2/)

Jim

---

### Post by a0u on 2008-07-31
> **mindpulse said:**
> by any chance can you install windows programs onto a secondary drive through wine?
I ask since one of the reasons for this shared drive is for usage under both OSes

By default, Wine typically expects programs to be in ~/.wine/drive_c, but you can map "drives" using the Wine configuration tool (Applications -> Wine -> Configure Wine).  Thus, you can remap the fake "C:\" drive to another partition.

I should also add that, like programs previously installed through Windows will not normally work with Wine, programs you install through Wine will probably not work in Windows, since the necessary registry entries and DLLs are not present there.

---

