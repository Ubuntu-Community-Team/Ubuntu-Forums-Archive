---
title: "RPM support on Ubuntu"
date: 2007-02-18
forum: Programming Talk
---

### Post by j_g on 2007-02-18
I've just finished creating some free software that I'd like others to be able to use. Now, since they've got the C source and dev files (makefile), they could compile/link it themselves. But being a Windows developer, I've gotten used to the idea of creating a single installation file (containing the binaries) that is easy for non-programmers to install. So, I'd like to at least give Ubuntu users the option of a single install file to install the binaries.

So, I went ahead and read a tutorial about the "Debian packaging format". I even downloaded and tried some debian tools which, after I was forced to rename my source directory (talk about unfriendly and uncooperative software), proceeded to fill up a directory with unappealing, incomprehensible poot like a cat fills a litterbox.  I'm sure someone somewhere (maybe not even on this planet) loves this thing, and is going to go ballistic at my not-so-much-love-as-disgust for it. Suffice it to say that I absolutely refuse to use Debian packaging format. It does not come even close to my bare minimum expectations of usability.

So I got looking at RPM format, and this seems much saner and closer to my expectations. The question is: Can Ubuntu easily install RPM packages? If so, how does one go about installing an RPM package on Ubuntu? Can it be done from Synaptic, or is the user forced to run rpm from the command line?

---

### Post by ansi on 2007-02-18
> **j_g said:**
>  The question is: Can Ubuntu easily install RPM packages? If so, how does one go about installing an RPM package on Ubuntu? Can it be done from Synaptic, or is the user forced to run rpm from the command line?

```
sudo apt-get install alien
sudo alien <your_package.rpm>
sudo dpkg -i <obtained_new_package.deb>
```

``alien'' makes reformation from one kind of package to another :).

---

### Post by j_g on 2007-02-18
Thank god for Alien.

I was able to make an RPM and then convert it over to the Debian packager format without having to stick my hands into that latter, messy litterbox.

The only thing now is that one file in my RPM is a daemon, and I don't know how to write the RPM spec file to notate that this file should be installed/run as a daemon. But I could put some instructions in a PDF for the enduser. It's still easier than dealing with Debian package format.

---

### Post by Tomosaur on 2007-02-18
Don't worry - virtually everyone I've ever spoken to absolutely hates creating debian packages, it really is crying out for improvement. Unfortunately, the Debian system (ie, Debian and it's derivatives) are so popular, that .deb packages are almost a requirement for many projects. That's not to say that red hat systems are any less popular, or worse than Debian, but it seems like .deb is just 'preferred'. It's an interesting situation, but one which doesn't look like it'll be resolved any time soon. I personally prefer supplying a shell script rather than a package - since the main purpose of a package is just to satisfy dependencies. If you know what your dependencies are, it's fairly easy to set up a shell script to detect some system info and download and install the required files / packages.

---

