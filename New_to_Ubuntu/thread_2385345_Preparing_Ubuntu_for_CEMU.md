---
title: "Preparing Ubuntu for CEMU"
date: 2018-02-19
forum: New to Ubuntu
---

### Post by armadal on 2018-02-19
After learning that AMD's OpenGL performance is much better in Linux than Windows, I decided to do a dual boot with Ubuntu and Windows 7. The initial installation was easy enough; take some free space, split it into two partitions for the "/" and "/home" directories, and follow the installer.

But the big roadblock now is actually installing software. In Windows, it's easy enough. Go to the download page, download the .exe, double click it, et voila. Linux, on the other hand, is a throwback to the DOS days with all the stuff you need to do in the terminal. So I've really no idea how to actually get stuff installed properly.

According to [guide #1](https://www.reddit.com/r/cemu/comments/6o0obp/complete_guide_to_cemu_on_linux/) and [guide #2](https://www.reddit.com/r/cemu/comments/7nw0me/wip_linux_guide_for_fresh_install_amd_gpu_and/), I need the following installed:

Docker
Mesa-mild
Wine
Wine-staging
Winetricks
VC++ 2015 Redist

Right off the bat, there's an incompatibility with the second guide. It says to use the following commands to install Docker:

```


[LIST]
[*]$ sudo pacman -Syyu
[*]$ sudo pacman -Sy git
[*]$ sudo usermod -aG docker "your_user_name_without_quote"
[*]$ sudo systemctl enable docker
[/LIST]

```

But **pacman** isn't a recognized command in Ubuntu. I assumed that it's trying to install git and docker, so I did:

```

sudo apt install git
sudo apt install docker

```

No errors were thrown in the terminal when installing them, but calling **sudo usermod -aG docker MyUsername** threw the error:

```

usermod: group 'docker' does not exist

```

So right in the first couple of steps, I've no idea how to proceed. How do I properly install docker?

Thanks in advance.

Specs:
OS - Windows 7 64bit & Ubuntu 17.10.1
CPU - Intel i7 6700k @ 4.0Ghz
GPU - AMD Radeon HD 7850 2GB
RAM - 2x16GB DDR4 @ 3000Mhz
Soundcard - Creative Soundblaster X-Fi Titanium Fatal1ty Pro

---

### Post by armadal on 2018-02-19
I managed to get Docker installed with the following commands:

```

sudo apt-get update
sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt-get update
sudo apt-get install docker-ce

```

So that's docker installed. But there's a new problem.

When I use these two commands:

```

cd MildInstaller/
./kazhedctl build --radeon --vulkan --optlevel=15 

```

This error is thrown:

```
Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get http://%2Fvar%2Frun%2Fdocker.sock/v1.35/images/json?all=1&filters=%7B%22reference%22%3A%7B%22kazhed%2Fgaming-container%22%3Atrue%7D%7D: dial unix /var/run/docker.sock: connect: permission denied

Parametres de construction :
--build-arg dri_drivers='' --build-arg gallium_drivers=swrast,radeonsi --build-arg vulkan_drivers=radeon --build-arg MY_USERNAME=username --build-arg mesa_version=master
ERRO[0000] failed to dial gRPC: cannot connect to the Docker daemon. Is 'docker daemon' running on this host?: dial unix /var/run/docker.sock: connect: permission denied 
context canceled

```

---

### Post by armadal on 2018-02-19
The solution to the docker error, is to type this command into the terminal:

```

sudo usermod -aG docker $USER

```

Punt that in, and then restart. Now calling the **./kazhedctl** command works. I'll report back how it goes once the terminal has done it's thing.

Edit: Well, it works. Talk about boilerplate, Linux is too god damn finicky. But at least I can get CEMU to launch now.

---

