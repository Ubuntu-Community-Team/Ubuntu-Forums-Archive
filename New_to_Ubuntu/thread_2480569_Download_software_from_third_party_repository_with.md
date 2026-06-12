---
title: "Download software from third party repository without source list"
date: 2022-11-02
forum: New to Ubuntu
---

### Post by sash5 on 2022-11-02
Is it possible to download software from third party repository without adding repository to a source list. My intention is to install some particular version of the software from the third party repository, but first to scan this software with VirusTotal. I also want to check the signature, and because this signature is not provided separately I want to use apt to do it for me.

 
 
 For example if I want to install new version of double commander I have an option to download deb,but there is not signature check. There is also a possibility to add repository, but then I will get all updates destructed with repository and that I don’t want because I’m too paranoid.  
 
 
 [https://software.opensuse.org/download.html?project=home%3AAlexx2000&package=doublecmd-gtk](https://software.opensuse.org/download.html?project=home%3AAlexx2000&package=doublecmd-gtk)

---

### Post by Frogs Hair on 2022-11-02
Not sure I can help , without the repository enabled there will be no automatic updates, but you can view the latest version if needed. The code is posted publicly on Github and this software is available for many Linux operating  systems and has been since 2007. [Total Virus]("https://www.virustotal.com/gui/home/upload") gives me the following result for the .deb package.

 ```
No security vendors and no sandboxes flagged this file as malicious
          84bc42025be7324bb089d367525d7a341ea5eb6b89cf69c8e799e978c2f4eb58
  doublecmd-gtk_1.0.8-0+svn191~testing_amd64.deb 
 

```

---

### Post by chiashurb on 2022-11-04
You've got a couple of good options for this.  Usually if I just want to download a one-off .deb and not add its parent repository, I'll just fetch the .deb file and then dpkg -i my_new_app.deb for example.  You mentioned that you would like to also verify the cryptographic signature (wise!).  If you look at the instructions for adding the repository to apt, you'll see the second line contains the url of the key.  You can use that to manually verify the signature using gpg, then use the dpkg command to install the .deb file.  

Alternatively, you could follow the instructions for adding the repository to your sources.list, install the package, then remove the repository from your sources.list immediately.

---

### Post by TheFu on 2022-11-04
Repos automatically check for gpg signatures to authenticate the package.

Not sure what "no aromatic updates" means.  Perhaps a funny typo. ;)

---

### Post by sash5 on 2022-11-06
> **chiashurb said:**
>  I'll just fetch the .deb file 
This was my question, how to fetch .deb from repo?


> **chiashurb said:**
> If you  look at the instructions for adding the repository to apt, you'll see  the second line contains the url of the key.  You can use that to  manually verify the signature using gpg

It is a public key, but not a signiture of .deb. If you somehow fetch .deb,  then you should get somewhere .sig

> **chiashurb said:**
> Alternatively, you could follow the  instructions for adding the repository to your sources.list, install the  package, then remove the repository from your sources.list  immediately.
Yes, this should work, but pretty complicated.

---

### Post by ActionParsnip on 2022-11-06
Add it to another system with Web access on the same release. Download the deb for every installed package then transfer them all to the other system and install as needed using dpkg

---

### Post by TheFu on 2022-11-06
> **sash5 said:**
>  Yes, this should work, but pretty complicated.

Running 1 command, then renaming 1 file is complicated?

---

### Post by sash5 on 2022-11-06
> **TheFu said:**
> Running 1 command, then renaming 1 file is complicated?

No, but if you install deb it will use the dependencies, and also can install them from that repository. And don't 100% trust that repository, that's the reason for this overhead. When I'm using --download-only does apt verifies the signature?

I was thinking about using docker for this.

---

### Post by TheFu on 2022-11-06
> **sash5 said:**
>  I was thinking about using docker for this.

What is "this"?
Docker has a number of security problems that have been whitewashed for over a decade, yet not really addressed most of the time.

---

### Post by sash5 on 2022-11-07
Install package in a docker container, and then fetch that package from it.

---

### Post by Frogs Hair on 2022-11-07
> **TheFu said:**
> Repos automatically check for gpg signatures to authenticate the package.

Not sure what "no aromatic updates" means.  Perhaps a funny typo. ;) I was smelling the repository :o (automatic)

---

### Post by DuckHook on 2022-11-07
> **sash5 said:**
> Install package in a docker container, and then fetch that package from it.
Docker is still better than installing onto the bare metal host. I encourage anyone who is proficient with containers like Docker to use them. TheFu is right in cautioning against a false sense of security, but containerizing questionable apps is good practice as one more step in a multilayered defence against possible nasties. For added security, substitute a VM for Docker.

Apt will not work as you want it to (signature check) unless you add the repo to sources.list. However, if the app is hived off to its own container/VM, I see the risk as being minimal. FWIW, that's my own setup (but I use LXD, not Docker), even for apps as proven as Firefox and Brave. *Almost nothing* runs on my host except the OS itself and that, in as default a condition as I can leave it.

---

### Post by TheFu on 2022-11-07
> **DuckHook said:**
> Docker is still better than installing onto the bare metal host. I encourage anyone who is proficient with containers like Docker to use them. TheFu is right in cautioning against a false sense of security, but containerizing questionable apps is good practice as one more step in a multilayered defence against possible nasties. For added security, substitute a VM for Docker.

Apt will not work as you want it to (signature check) unless you add the repo to sources.list. However, if the app is hived off to its own container/VM, I see the risk as being minimal. FWIW, that's my own setup (but I use LXD, not Docker), even for apps as proven as Firefox and Brave. *Almost nothing* runs on my host except the OS itself and that, in as default a condition as I can leave it.

lxd/lxc containers run as a non-root account by default.  Docker should have that same capability, but it doesn't seem to be the default. [https://docs.docker.com/engine/security/rootless/](https://docs.docker.com/engine/security/rootless/) That is one risk with using Docker.  Other container managers typically do not run as root.  Googling for "linux containers run as root" to see all the warning articles about doing that with examples.  The vast majority of docker users in a home environment are completely unaware of this critical issue. Beware.

---

### Post by DuckHook on 2022-11-07
Very useful info re: Docker. I did not know this about it, but then, I don't know much about Docker to start with. That's an odd, surprising and dangerous default. I shall be more wary of Docker from now on.

Thanks for the details.

---

### Post by sash5 on 2022-11-18
At the end i come to this solution:

Create a small image to install a package in docker container. For security as noticed before docker should run rootless.

Dockerfile
```

FROM ubuntu:jammy

COPY inContainer.sh ./

RUN chmod +x ./inContainer.sh

ENTRYPOINT ["./inContainer.sh"]



```

inContainer.sh
```

#!/bin/bash

apt-get update

rm /etc/apt/apt.conf.d/docker-clean

apt-get install -y $1

ls -la /var/cache/apt/archives/



```

and then 3 small scripts

download.sh script to install a package in a container, and prepare deb files
```

#!/bin/bash

if [ $# -eq 0 ]; then

    echo "No package name provided"

    exit 1

fi

docker run --cidfile tmp.cid dockeraptget $1



```

get.sh script to copy necessary files from the container
```

#!/bin/bash

if [ ! -f "tmp.cid" ]; then

    echo "tmp.cid not found. Please run download.sh <package name> to download a package"

    exit 1

fi

cid=$(cat tmp.cid) ||

echo "using container id:$cid"

if [ -z "$2" ]

then

    dir="./"

else

    dir="$2"

fi

echo "save $1 into $dir"

docker cp "$cid:/var/cache/apt/archives/$1""$dir" || exit 2



```

cleanup.sh script to remove the container
```
#!/bin/bash

if [ ! -f "tmp.cid" ]; then

    echo "tmp.cid not found. Nothing to cleanup"

    exit 1

fi

cid=$(cat tmp.cid)
echo "removing container id:$cid"

docker rm "$cid" || exit 1

rm tmp.cid



```

---

### Post by TheFu on 2022-11-19
Rather than docker, I'd probably use lxc managed by lxd for something like this. lxd gets pre-installed on Ubuntu systems now, but both are container management systems. lxc "feels"more like a virtual machine. The cost is a little more disk, but performance is similar to any other Linux container.  Of course, if someone is more comfortable using docker, provided it is without root, seems like an excellent option.

I use apt-cacher-ng to cache packages on a system on my LAN.  Only once is the package pulled from the internet, then all the other systems hit the local repo to get it for installation.  Currently, I have multiple debian, 18.04, 20.04 and 22.04 systems. apt-cacher-ng's cache of packages is using 2.7GB total for all of those.  I don't mirror full repos, just the packages installed.

---

### Post by DuckHook on 2022-11-19
Though I know little about Docker, I can't imagine that it is insecure if configured properly. Don't millions use it precisely to containerize content that they want to deny access to either the base system or to other Docker containers? (My ignorance could be on full display here!)

---

### Post by TheFu on 2022-11-19
> **DuckHook said:**
> Though I know little about Docker, I can't imagine that it is insecure if configured properly.  

The key here is "configured properly".

The millions of users are either in a professional situation building deployment setup 5x a day via automation or downloading pre-built packs created by professionals.  Much of the security for docker containers comes by not having a full OS, having only the specific service needed to run the network service and nothing else.  Docker containers with a shell or ssh or anything beyond the single, primary, tools for the single, primary, purpose are a security risk to be mitigated.  

If you work with docker all day, building up the minimal docker container to have only what is necessary becomes 2nd nature.  It is hard to hack a container that can only run 1 thing because there's nothing else inside it.  But doing apt stuff has lots of dependencies, increasing the attack vectors once the container is cracked. Each of those things needs to be mitigated.  More tools inside the container, means more of a chance to hack it or to break out of the container into the hosting system.  [https://book.hacktricks.xyz/linux-hardening/privilege-escalation/docker-breakout/docker-breakout-privilege-escalation](https://book.hacktricks.xyz/linux-hardening/privilege-escalation/docker-breakout/docker-breakout-privilege-escalation) has some examples.
and [https://ubuntu.com/security/CVE-2022-0185](https://ubuntu.com/security/CVE-2022-0185) which is mitigated by preventing privileged containers ... as stated above.

As usual, security stuff is more subtle than "secure" or "non-secure", but the only safe stances is to assume something is non-secure until it is know that the issue is resolved.  Docker could solve this by making non-privileged containers the default.  [https://docs.docker.com/engine/install/linux-postinstall/](https://docs.docker.com/engine/install/linux-postinstall/) has some postinstall best practices. Why aren't those settings the standard defaults?
There are probably historical reasons for not doing that ... sorta like how CIFS had poor security until recently.  The fact that a password is used for CIFS mounts is still a problem in my book.

---

### Post by DuckHook on 2022-11-19
Thanks for this. As usual, a wealth of useful info. I'm bookmarking your post for future reference.

---

### Post by TheFu on 2022-11-19
> **DuckHook said:**
> Thanks for this. As usual, a wealth of useful info. I'm bookmarking your post for future reference.

There are lots of Linux conference sessions on youtube about Linux Containers, for those looking to know more. I happened to attend a conference that was 50% about Linux Containers and it jump started my understand along with hearing from industry experts about best practices for designing, building and deploying containers.  The main thing is not to trust random containers built by "Joe", but stick to containers created by either the project team (we're already running their code) or from a company you have a financial relationship with - i.e. you are paying them, so if they want those payments to continue, they'd better make excellent, secure, containers.

It is also great to hear from others doing devops about "lazy is good."  Automate everything you can, but be very careful picking the tools, or the solution can easily be worse than the original problem.  Hearing their examples of that can be enlightening ... seems certain very popular devops tools fall into that problem - or at least at the time of their talk they did. Hearing the unfiltered stuff, without marketing (docker has/had fantastic marketing) involved is important.

---

### Post by mIk3_08 on 2022-11-20
> **DuckHook said:**
> Apt will not work as you want it to (signature  check) unless you add the repo to sources.list. However, if the app is  hived off to its own container/VM, I see the risk as being minimal.  FWIW, that's my own setup (but I use LXD, not Docker), even for apps as  proven as Firefox and Brave. *Almost nothing* runs on my host  except the OS itself and that, in as default a condition as I can leave  it. Wow! This is another great idea. Maybe I might be using this in  the future. Thanks a lot DuckHook. Regards and cheers.

---

### Post by TheFu on 2022-11-20
This reminds me about the trust problem. Who should we trust and who can we trust?
> Reflections on Trusting Trust by Ken Thompson
Ref: [http://genius.cat-v.org/ken-thompson/texts/trusting-trust/](http://genius.cat-v.org/ken-thompson/texts/trusting-trust/)
If you don't recognize that name, wikipedia can help. In short, he's the reason Ubuntu Forums exists, Linux exists, and UNIX was created.  UTF8 is partially his fault, The Go language is too and if you want to curse him for anything - regex is partially his fault. ;)

I love this quote from someone trying to give credit to a bunch of people.
> "The names of Ritchie and Thompson may safely be assumed to be attached to almost everything not otherwise attributed."
Linus T is about the same level as Thompson. Hard to say who did more for computing and Unix-Like systems.

---

### Post by mIk3_08 on 2022-11-21
> **TheFu said:**
> This reminds me about the trust problem. Who should we trust and who can we trust?

Ref: [http://genius.cat-v.org/ken-thompson/texts/trusting-trust/](http://genius.cat-v.org/ken-thompson/texts/trusting-trust/)
If you don't recognize that name, wikipedia can help. In short, he's the reason Ubuntu Forums exists, Linux exists, and UNIX was created.  UTF8 is partially his fault, The Go language is too and if you want to curse him for anything - regex is partially his fault. ;)

I love this quote from someone trying to give credit to a bunch of people.

Linus T is about the same level as Thompson. Hard to say who did more for computing and Unix-Like systems.
Thanks for this TheFu's. Thanks for the information. It reminds me why internet exist. I knew already who is Kenneth lane Thompson, Linus T. of course Richard Stallman. That is why I decided to move to Linux from MS Windows historically known for its opposition to the open source software paradigm but then they turned to embrace the approach of open source in the 2010s. I know I have lots to learn. 
That is why I'm here. I am way a lot to learn. I knew already the POWER of Linux but they choose to stay humble of it. Regards and cheers

---

### Post by sash5 on 2022-12-10
> **DuckHook said:**
>  FWIW, that's my own setup (but I use LXD, not Docker), even for apps as proven as Firefox and Brave. *Almost nothing* runs on my host except the OS itself and that, in as default a condition as I can leave it.
Are you running LXC as VM or Container?

---

### Post by DuckHook on 2022-12-10
> **sash5 said:**
> Are you running LXC as VM or Container?
Both, actually, but primarily as container. I have a Windows 10 instance running as a VM and I like it a lot more than the old separate KVM + virt-manager setup&#8212;mainly because, with LXD, I can leverage its underlying ZFS foundation to snapshot, clone and copy the whole VM to different machines over the LAN and even over the internet with ease. After initially setting up both machines, it's a dead simple one-liner:```
lxc copy win10/snapshot remote_machine:win10 --refresh
```and only the changed bits are transferred for wicked efficiency.

I used to run many VMs in order to try out different distros, but once I started using containers, I found that this was no longer necessary. I can run all sorts of distros, from Alpine to Arch to Fedora, purely as containers. It's as simple as:```
lxc launch images:alpine/edge --profile default my_alpine
```&#8230;and I have an Alpine OS up and running. Not only is the resulting instance way faster than a VM, but it has dynamic storage as large as my LXD pool, a tiny memory footprint and is far more efficient. I have little use for VMs anymore except for incompatible OSes like Windows, BSD or Android.

\\:D/ containers. \\:D/ LXD.

---

### Post by Tadaen_Sylvermane on 2022-12-11
Chroot might be safer if it's that big a concern. Or firejail to use the browser if needed.

Again if it's that big a issue though I'd personally add the repo then apt-source the package in question. Then  remove the repo and inspect it. Then manually build it myself. Always build as non privileged user.

---

### Post by DuckHook on 2022-12-11
There are other advantages to containers that chroot, firejail and building from source don't bring you.

I can easily suitcase my whole working environment and port it between machines with almost no effort. This is not just better for redundancy, but is awesome for portability.

Example: by installing T-Bird, F-fox, Libreoffice, GIMP, games, etc into a container along with all associated data, I can just "lxc copy…" the whole works into my laptop prior to travelling, and my entire digital life is at my fingertips while on the road. When I get home, just sync the other way and, presto, in five minutes, everything I did on the road is now updated at home.

I tend to focus too much on security, but the other advantages are just as important.

---

### Post by sash5 on 2022-12-13
> **Tadaen_Sylvermane said:**
> Chroot might be safer if it's that big a concern. Or firejail to use the browser if needed.

Again if it's that big a issue though I'd personally add the repo then apt-source the package in question. Then  remove the repo and inspect it. Then manually build it myself. Always build as non privileged user.

I try to define a standard process of getting software packages, that i can use every time i need a new package, and that at  some level is secure and at a certain level i can trust my PC.  But it should be not over complicated. For example:
1. find software origin
2.  check if repository or download URL is mentioned in some well known  sources, for example wiki, alternativeto, this forum, ask ubuntu etc..
3. download the package and check signature or *checksum*.
4. check for malware using virustotal
5. install as non root user, or in some VM or container and use the software

---

### Post by DuckHook on 2022-12-13
> **sash5 said:**
> …that i can use every time i need a new package, and that at  some level is secure and at a certain level i can trust my PC.  But it should be not over complicated…
Commendable practices. You don't need any further ramblings from me on security.

By way of contrast, I just installed Windows 11 in a VM.

Wow (in a spectacularly bad way).

I didn't realize how the default process now forces one to create an account and register with Big Brother. It won't even install if you don't. A bit of web searching turned up the workaround, but… really???

This was not necessary in Windows 10. What a bad, sad state of affairs.

As if it's possible, I'm now even happier that I run Linux.

---

