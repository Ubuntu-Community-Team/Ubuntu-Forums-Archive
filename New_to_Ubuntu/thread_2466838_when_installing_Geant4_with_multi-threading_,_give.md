---
title: "when installing Geant4 with multi-threading , gives the eror of something of linux ?"
date: 2021-09-07
forum: New to Ubuntu
---

### Post by priyanshu-agrawal on 2021-09-07
Hi Experts,

I was installing Geant4 software in my system (Ubuntu 18 )with using multi-threading but getting the below error. i am not getting this why i am facing this problem. 
i have asked on Geant4 forum if it was the Geant problem but they were suggesting to ask here. 
so can anyone please help me with this. it will be very helpful.
waiting for a reply!
Thanks & Regards
Priyanshu
[IMG]scp IMG_20210907_150828209.jpg [EMAIL="priyanshu@ubuntuforums.org"]priyanshu@ubuntuforums.org[/EMAIL][/IMG]

---

### Post by Impavidus on 2021-09-07
/usr/lib/x86_64-linux-gnu/libGL.so is provided on 18.04 by the packages [libglvnd-dev]("https://packages.ubuntu.com/bionic/libglvnd-dev") (vendor neutral) and [nvidia-340]("https://packages.ubuntu.com/bionic/nvidia-340"), for those who need that nvidia driver. You need the file (actually a symlink, I presume) to compile software using openGL. On my 21.04 system the symlink is in the package [libgl-dev]("https://packages.ubuntu.com/hirsute/libgl-dev"), which in 18.04 is a virtual package provided by [libgl1-mesa-dev]("https://packages.ubuntu.com/bionic/libgl1-mesa-dev"), which in turn pulls in libglvnd-dev, which is the actual package you need.

I suggest you install libgl1-mesa-dev. Use your favourite package management tool. If you want the terminal, use```
sudo apt install libgl1-mesa-dev
```

---

### Post by priyanshu-agrawal on 2021-09-08
Thank you very much for you reply!
i have done this, this is showing me this.what does that mean , i didn't understand as i am new to this OS.
can you please tell what should i do now ?

Thanks in advance!
Priyanshu

---

### Post by priyanshu-agrawal on 2021-09-08
so sorry, i have uploaded wrong images.
and i am not getting how can i remove those.
attaching new one for which i was taking about.

---

### Post by priyanshu-agrawal on 2021-09-08
now, again trying to install with multi-threading then it is again the same problem occurring why so , really i am not getting this.
please see the attachment below.

---

### Post by QIII on 2021-09-08
Hello!

Please do not embed large images.  Some of our users have slow connections and some pay for data.  Large images may load slowly or even cost users money.

Also, please enclose all terminal commands and results in code tags rather that taking a screenshot.

To use code tags:

1. If you are using the "Reply to Thread" button, please type or paste your text, highlight the text and use the # button in the text box header. Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by priyanshu-agrawal on 2021-09-08
now, again trying to install with multi-threading then it is again the same problem occurring why so , really i am not getting this.
please see the attachment below.

---

### Post by monkeybrain20122 on 2021-09-08
On my system (Ubuntu20.04)
```
$dpkg -S /usr/lib/x86_64-linux-gnu/libGL.so
libgl-dev:amd64: /usr/lib/x86_64-linux-gnu/libGL.so

```

So you need to install libgl-dev
```

sudo apt install libgl-dev
```

---

### Post by monkeybrain20122 on 2021-09-08
Looks like you don't need to build it from source, there is a [ppa]("https://launchpad.net/~kaktusjoe/+archive/ubuntu/g4dist") for geant4. So just add it to your sources list and install it like any package
```

sudo add-apt-repository ppa:kaktusjoe/g4dist
sudo apt update
sudo apt install geant4
```

---

### Post by Impavidus on 2021-09-08
> **monkeybrain20122 said:**
> On my system (Ubuntu20.04)
```
$dpkg -S /usr/lib/x86_64-linux-gnu/libGL.so
libgl-dev:amd64: /usr/lib/x86_64-linux-gnu/libGL.so

```

So you need to install libgl-dev
```

sudo apt install libgl-dev
```Yes, but it apears to be somewhat different on 18.04.

> **monkeybrain20122 said:**
> Looks like you don't need to build it from source, there is a [ppa]("https://launchpad.net/~kaktusjoe/+archive/ubuntu/g4dist") for geant4. So just add it to your sources list and install it like any package
```

sudo add-apt-repository ppa:kaktusjoe/g4dist
sudo apt update
sudo apt install geant4
```
A PPA is definitely easier than installing from source, even for people who are not new to Ubuntu. Installing from source is a last resort. So I suggest you try the PPA. If that doesn't work, we can look further.

---

### Post by priyanshu-agrawal on 2021-09-09
Thank you very much for the reply!
I have installed Geant4 from source without having any problem and it was working also.

but now what i want that i want to switch on the multi-threading mode in Geant4 same installation as it was suggested by Geant4 forum. 
but i am doing according to the steps told by them , i am getting this error. This i want doing in lab's workstation (having Ubuntu 18.4). 

and same thing i did in my own laptop (having Ubuntu 20.04 LTS ) but it installed very easily (multi-threading) .and working fine for me.

so i want to understand why this is happening in the workstation.
can you please help me with this ? 
Thanks & Regards
Priyanshu

---

### Post by priyanshu-agrawal on 2021-09-09
so to install this file, do i need to write both the above code that you shared.
first, the above code and then second one, am i write ?
Thanks for the help!
Regards
Priyanshu

---

