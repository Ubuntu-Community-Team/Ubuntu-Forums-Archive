---
title: "Bash Script"
date: 2014-04-20
forum: Programming Talk
---

### Post by sammykur on 2014-04-20
Hello everyone and thanks for all the help in the past including post I have just read and had the same problems

I am trying to put together my first script, Much of it cut pasted and altered from other sources.

I was hoping to post it here and if there is anything way out of whack with it someone could let me know.


```
[SUB]
#!/bin/sh
##install of cuda 6.0 on ubuntu 12.04lts

apt-get install freeglut3-dev build-essential libx11-dev libxmu-dev

libxi-dev libgl1-mesa-glx libglu1-mesa libglu1-mesa-dev

apt-get update 


sed -i 's/blacklist amd76x_edac/
blacklist amd76x_edac
\\blacklist vga16fb
\\blacklist nouveau
\\blacklist rivafb
\\blacklist nvidiafb
\\blacklist rivatv
/g' /etc/modprobe.d/blacklist.conf

apt-get remove --purge nvidia*

add-apt-repository ppa:xorg-edgers/ppa

apt-get update

apt-get install nvidia-331

ppa-purge ppa:ubuntu-x-swat/x-updates

apt-get install freeglut3

dpkg -i cuda-repo-ubuntu1204_6.0-37_amd64.deb 

apt-get update 

apt-get install cuda 

export CUDA_HOME=/usr/local/cuda-6.0 
export LD_LIBRARY_PATH=${CUDA_HOME}/lib64

PATH=${CUDA_HOME}/bin:${PATH} 
export PATH 

cuda-install-samples-6.0.sh  ~ 

cd ~/NVIDIA_CUDA-6.0_Samples 

make 



fi
[/SUB]
```

I am not looking for anyone to go out of their way and debug it for me, just want to see if there are any glaring defects in it, espcially in the SED command.

Thanks

---

### Post by Habitual on 2014-04-20
Offhand, I'd use "sed -i.bak..." to make a backup.

---

### Post by steeldriver on 2014-04-20
^^^ good call

The line continuations and/or escaping of the sed command look wrong to me - have you tested it (by running it without the -i)? it should be something like this I think:

```

sed -i 's/blacklist amd76x_edac/\
blacklist vga16fb\
blacklist nouveau\
blacklist rivafb\
blacklist nvidiafb\
blacklist rivatv\
/' /etc/modprobe.d/blacklist.conf

```

The g modifier is unneccesary - there shouldn't be multiple instances.

---

### Post by steeldriver on 2014-04-20
... or fwiw you could use an insert or append command instead of the substitute e.g. (testing it with a local copy blacklist.conf):

```

$ sed -i.bak '/blacklist amd76x_edac/{a\
blacklist vga16fb\
blacklist nouveau\
blacklist rivafb\
blacklist nvidiafb\
blacklist rivatv
;d}' blacklist.conf

```

```

$ diff blacklist.conf.bak blacklist.conf
55c55,59
< blacklist amd76x_edac
---
> blacklist vga16fb
> blacklist nouveau
> blacklist rivafb
> blacklist nvidiafb
> blacklist rivatv

```

EDIT: I think on reflection I'd probably do something more like

```

sed -i.bak '/blacklist amd76x_edac/{a\
blacklist vga16fb\
blacklist nouveau\
blacklist rivafb\
blacklist nvidiafb\
blacklist rivatv
;s//# &\n/}' /etc/modprobe.d/blacklist.conf 

```

which appends the new lines and then *comments out *(rather than deleting / replacing) the original matched line. I prefer that because the file contains a preamble  about why the amd76x_edac was originally blacklisted - which kind of doesn't make sense if the line it's referring to is missing.

---

### Post by sammykur on 2014-04-20
Thanks to both of you , I will try out your suggestions.
Not to ask two questions in a post but should using .bak as standard practice something I should be doing in sed or are there drawbacks to using it in some circumstances??? (can post as separate question if appropriate.
INever thought to run locally as a test (DUH ) 
Is creating a test directory to copy file to exclusively to test script on apporiate or am I misunderstanding ?
I will get back as I cant spend much time on this till later today/tonight and I need to check out the modifierss you have suggested for sed (so i will know next time rather than blindly pasting.

Just an FYI the  line continuations and/or escaping of the sed command was something i saw on a blog where a user was having trouble with sed hanging up when he was trying something similar to what I want to do.I will try to find the link and post it later.

Thanks again (I hope I am posting in the right place I wish they had a "newbiees scripting" help forumn.)

---

### Post by GrouchyGaijin on 2014-04-20
```

apt-get install freeglut3-dev build-essential libx11-dev libxmu-dev

apt-get update 

```

Can you run run a sudo command in a script without sudo?

---

### Post by steeldriver on 2014-04-20
> **GrouchyGaijin said:**
> 
Can you run run a sudo command in a script without sudo?

The whole script would need to be run with sudo. A couple of other things I just noticed: 

1.  I don't really see the point of updating AFTER the installs; also you  can't split the list of packages to be installed across multiple lines  like that, it would need to be all on one line or split with a \ i.e.
```

apt-get update 

apt-get install freeglut3-dev build-essential libx11-dev libxmu-dev \
libxi-dev libgl1-mesa-glx libglu1-mesa libglu1-mesa-dev

```

 2.  it's probably best not to rely on shell expansion of ~ 
```

cuda-install-samples-6.0.sh  ~ 

cd ~/NVIDIA_CUDA-6.0_Samples 

```

---

### Post by Habitual on 2014-04-20
> **sammykur said:**
> should using .bak as standard practice something I should be doing in sed or are there drawbacks to using it in some circumstances??? (can post as separate question if appropriate.I can't think of any, it's just good form as I'd rather have a working copy.bak of say, grub.conf and a busted script than the other way around. :)

---

### Post by sammykur on 2014-04-21
I was planning on running it in a comand line

```
sudo ./filename
```

I read that this was preferable to using sudo within the script,however it seems better form to include sudo in the script as it asks for sudo password anyway.

Thanks for the input.

---

### Post by sammykur on 2014-04-21
I see what you mean about the updating and splitting the script,it obviously needs some work.
I am going to work on it with the advice given and look up the modifiers I am unfamiliar with.
I will repost the script after I rework it and test it.

would there be any advantage to using wget and downloading the files from Nvidia(and then installing them) instead of using apt-get to download either the drivers or the tool-kit???

---

### Post by sammykur on 2014-04-21
I see what you mean about the updating and splitting the script,it obviously needs some work.
I am going to work on it with the advice given and look up the modifiers I am unfamiliar with.
I will repost the script after I rework it and test it.

would there be any advantage to using wget then running them with a script instead of using apt-get to download and install either the drivers or the tool-kit???

---

### Post by varunendra on 2014-04-21
Using sed looks overkill to me for appending blacklist entries. You can use something simple like this -
```
BLIST=**[COLOR="#0000CD"]'[/COLOR]**blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv**[COLOR="#0000CD"]'[/COLOR]**

printf "\n$BLIST" >> /etc/modprobe.d/blacklist.conf
```
(notice the single-quote marks at the start and end of the entries, they are necessary for this kind of variable declaration)

By the way, the better (and correct) way to 'Append' lines using sed is to use "a" command with sed. Something like this -
```
sed -i '$ a blacklist vga16fb\nblacklist nouveau\nblacklist rivafb\nblacklist nvidiafb\nblacklist rivatv' /etc/modprobe.d/blacklist.conf
```
Or the same thing in a cleaner way -
```
sed -i '$ a blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv' /etc/modprobe.d/blacklist.conf
```

The "$" means the "Last Line" in the supplied file. The 'a' command appends the given lines after this last line, whatever it is. Instead of "$", you can also specify a particular line/pattern as follows -
```
sed -i '/amd76x_edac/ a line one
line two
line three' <the file to be modified>
```
In the above example, the lines "line one.... three" will be appended after the line that contains the word "amd76x_edac", wherever it is found.

---

### Post by sammykur on 2014-04-28
Thank you all for all your help once again
I have worked on this script trying to clean it up, though not completed (found more dependencies-like not having an MPI compiler) I thought I would post my progresson it, and see if anyone wants to comment on it.
I tried using  BLIST and was unsuccessful ,I wound up using sed the $ variable worked great but i had to use a forward slash after each line.
Anyway here it is

```
[CODE]#!/bin/sh
##install of cuda 6.0 on ubuntu 12.04lts

sudo apt-get update

sudo apt-get install libglapi-mesa libgl1-mesa-dri freeglut3-dev build-essential libx11-dev libxmu-dev libxi-dev libgl1-mesa-glx libglu1-mesa libglu1-mesa-dev libcr-dev mpich2 mpich2-doc

sudo sed -i.bak '$ a blacklist vga16fb\
blacklist nouveau\
blacklist rivafb\
blacklist nvidiafb\
blacklist rivatv' /etc/modprobe.d/blacklist.conf

cd /etc/modprobe.d

sudo cp -n blacklist.conf blacklist2.bk

sudo awk '!seen[$0]++' blacklist.conf > /home/user/blacklist.tmp && sudo mv /home/user/blacklist.tmp blacklist.conf

cd

sudo apt-get remove --purge nvidia*

sudo add-apt-repository ppa:xorg-edgers/ppa

sudo apt-get update

sudo apt-get install nvidia-331

sudo apt-get install nvidia-331-uvm


wget -O /home/user/cuda_6.0.37.run http://developer.download.nvidia.com/compute/cuda/6_0/rel/installers/cuda_6.0.37_linux_64.run

sudo ln -s /usr/lib/x86_64-linux-gnu/libglut.so.3 /usr/lib/libglut.so

chmod +x cuda*.run
sudo ./cuda*.run

export PATH=$PATH:/usr/local/cuda-6.0/bin

export LD_LIBRARY_PATH=/usr/local/cuda-6.0/lib64:/lib

PATH=${CUDA_HOME}/bin:${PATH} 

export PATH 

cuda-install-samples-6.0.sh  /home/user 

cd  /home/user/NVIDIA_CUDA-6.0_Samples

make 

cd  /home/user/NVIDIA_CUDA-6.0_Samples/bin/x86_64/linux/release 

./deviceQuery 






```[/CODE]


Thanks all again!!! You Rock!!!!

---

### Post by varunendra on 2014-04-28
Interesting! Because I had tested (in a terminal) the "BLIST" trick, not the sed command while posting. The sed commands without the backslash (yeah, what you used is actually a 'backslash', forward slash is this one - "/") is giving error to me too, using the backslashes fixed it.

But the BLIST trick also works for me here on Ubuntu 12.04.

Here's the test script I just tested it on -
```
#!/bin/bash

cp /etc/modprobe.d/blacklist.conf /home/varun/Desktop/blacklist.conf

BLIST='BLIST
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv'

printf "\n$BLIST" >> /home/varun/Desktop/blacklist.conf

sed -i '$ a SED\
blacklist vga16fb\
blacklist nouveau\
blacklist rivafb\
blacklist nvidiafb\
blacklist rivatv' /home/varun/Desktop/blacklist.conf
```

(using "#!/bin/sh" instead of "#!/bin/bash" also works)

---

### Post by sammykur on 2014-04-28
I just retried it in my home directory by itself and it worked fine,I am sure it was some mistake of mine,
 Thanks for the help,   	 	 	 	   I appreciate it
  The $ in the sed command sure made things alot easier!
I gotta remember that one.It seems like it will be one that could be used alot.

---

### Post by varunendra on 2014-04-28
If you don't already know about it, this is the most referenced tutorial for sed : [http://www.grymoire.com/Unix/sed.html](http://www.grymoire.com/Unix/sed.html)

Would be a good idea to bookmark it if you are going to play with sed a lot. :)

**PS:**

Also remember that "$" means the "Last Line" only when used as an address. When used as a regular expression in commands like 's' (e.g., sed 's/$/somethingnew/' <some_file>), it means "End of Line", not the "Last Line". Confused? I was initially, not anymore. :p

---

### Post by sammykur on 2014-04-28
Thanks once again,by the way is there someplace that i should post this? Or is it not worth it as its already here.(or other reasons)
Interstingly I found when running this that the samples will install by have an error for no MPI compiler, but when you run ./deviceQuery everthing shows fine.
I realize its just a sample ,but I am kind of curious how many people out there have installed cuda with the error uncorrected and had trouble with samples for that reason.
Most of the tutorials never mention it (notice the mpich addition  to the install line)

---

