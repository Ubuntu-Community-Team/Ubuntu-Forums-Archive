---
title: "hard to create .debs?"
date: 2014-02-10
forum: New to Ubuntu
---

### Post by beelzebufo on 2014-02-10
Is it really that hard to create installers for linux? I just don't understand why we have to install from source all the time, even with the copy paste instructions things usually go wrong and besides that, its really tedious.  I under stand that most of us are fairly computer literate and don't mind doing some script writing and such, but it seems like any time I want to install a program that is not in the sofware center, it takes an hour to get it done, so how would you go about creating a .deb from source, is it the same ever time? the make command doesn't seem to be.  Just wondering if there was a uniform, constant way to create an installer from source.  Thanks in advance

beelzebufo

---

### Post by monkeybrain20122 on 2014-02-10
??? Where do you get your software?

In Ubuntu and most modern distros you hardly need to compile from source. Most common Software are one click away in the repository, you can access it through a gui like synaptic, phonon or (in Ubuntu  only) the Software Centre. In Ubuntu there is also the option of adding third party repositories called ppas in case the Software you want is not in the official repo or if you need more updated versions. It is very rarely that you need to compile something from source. Some people do it just because they like to as it gives them more control.

Here is my order, if I want something I will first look for it in the repo, if I can't find it or if the version is outdated then I would look for a ppa, if I can't find one I will go to the software's site and see if they offer a deb or a repository (e.g things like jitsi or Virtualbox have their own repositories which you have to add) Then there are also applications which are precompiled so that you can just download and use without installing. If all these options are exhausted and still I cannot find what I want I will compile from source. I do compile a few things that I don't have to, but mainly for more control rather than necessity.

---

### Post by beelzebufo on 2014-02-10
thanks for the reply.  I also use things in the software center and synaptic, I am also aware of how to add ppas, something I have noticed with 1310 though is that the new ppas rarely work, sudo apt-ge update rarely can connect or the ppa does not have the package, I know that ubuntu can't really do anything about that, but it just seems like I shouldn't ahve to compile from source, ./compile then make rarely seems to work for me either, probably operator error.

thanks again
beelzebufo

---

### Post by Dave_L on 2014-02-10
The reason that many GNU/Linux applications are distributed as .tar.gz source packages is that there are many configuration variables that require customizing the build process, so it's a robust one-size-fits-all solution.

Which specific packages are you having trouble with?

---

### Post by buzzingrobot on 2014-02-10
If you are constantly building from source, the simple answer is that you are either installing very new and untested code or very uncommon code.

Tar files are simple archives, just a way to bunch multiple files together for convenience.  Deb files are archives plus installation scripts, etc. and enable automatic dependency resolution.

Your first recourse when looking for some new piece of software should be the Ubuntu repositories.  Whether you use Software Center, Synaptic, apt-get, etc., you are accessing the same repos.

PPA's, as you know, are unofficial and unsupported.  They can be very useful, but can also generate problems.  It's best to read any warnings/advice at a PPA's site on launchpad.net before installing its software. Copy-and-paste articles seldom point this out.

PPA's can also become defunct or temporarily unavailable, like any web site.

---

### Post by tgalati4 on 2014-02-10
When you flush a toilet, you normally don't care where the effluent goes.  But somebody had to dig a trench and lay the pipes.  That is compiling from source and packaging.  So if you need to compile and package source code from scratch, expect to get dirty.

---

### Post by beelzebufo on 2014-02-10
thank you very much, and yes, the code is usually fairly new, although some of it has been around for years, as I said, I don't mind compiling, it just seems like it wouldn't be that hard to put it into installable form.  I should probably start a new thread, but I think what I really meant was a simple "how do you create .deb files from source" if that's even possible if you are not the devs and don't know the specific dependancies, although, if it is a .deb, dpkg usually tells you what you need.. 


thanks again

and dave, I didn't see your post, I have had problems with a number of them, most recently a game which I was able to compile after several attempts.  I will admit that a lot of them are things like postgresql (which now has an installable) or metasploit, or .. can't think of any more off the top of my head, so they are fairly large and complicated apps, I know they all put a lot of work into it, many more hours than it takes me to figure out how to compile properly, I see rpms all the time but debs are fairly rare for things like what I mentioned so I assume that it's harder to create an installable for ubuntu? maybe?

ok, here is what I am talking about, I already have nmap installed, no, as you can see,  I am interested in networking and pentesting, but that's beside the point.  I downloaded the nmap source did a ./configure then make following [http://community.linuxmint.com/tutorial/view/162](http://community.linuxmint.com/tutorial/view/162) just to see if it worked and I ended up with this in my nmap folder, as you can see there is no executable, at least not that I can see, so I would have to do a lot of research and a lot of tinkering to get it to work.  I am aware that nmap is in the ubuntu repos, this was just a test.


```
wreckingball@wreckingball-pc:~/nmap_test/nmap-6.40$ lsacinclude.m4           macosx               nse_binlib.cc    portlist.h
aclocal.m4             main.cc              nse_binlib.h     portreasons.cc
BSDmakefile            Makefile             nse_bit.cc       portreasons.h
CHANGELOG              makefile.dep         nse_bit.h        protocols.cc
charpool.cc            Makefile.in          nse_debug.cc     protocols.h
charpool.h             missing              nse_debug.h      README-WIN32
config.guess           mswin32              nse_dnet.cc      scan_engine.cc
config.log             nbase                nse_dnet.h       scan_engine.h
config.status          ncat                 nse_fs.cc        scripts
config.sub             ndiff                nse_fs.h         service_scan.cc
configure              nmap-6.40-1.spec     nselib           service_scan.h
configure.ac           nmap_amigaos.h       nse_main.cc      services.cc
COPYING                nmap.cc              nse_main.h       services.h
depcomp                nmap_config.h        nse_main.lua     shtool
description-pak        nmap_config.h.in     nse_nmaplib.cc   struct_ip.h
doc-pak                nmap_dns.cc          nse_nmaplib.h    Target.cc
docs                   nmap_dns.h           nse_nsock.cc     TargetGroup.cc
FingerPrintResults.cc  nmap_error.cc        nse_nsock.h      TargetGroup.h
FingerPrintResults.h   nmap_error.h         nse_openssl.cc   Target.h
FPEngine.cc            nmap.h               nse_openssl.h    targets.cc
FPEngine.h             nmap-mac-prefixes    nse_pcrelib.cc   targets.h
FPModel.cc             NmapOps.cc           nse_pcrelib.h    tcpip.cc
global_structures.h    NmapOps.h            nse_ssl_cert.cc  tcpip.h
HACKING                nmap-os-db           nse_ssl_cert.h   timing.cc
idle_scan.cc           NmapOutputTable.cc   nse_utility.cc   timing.h
idle_scan.h            NmapOutputTable.h    nse_utility.h    todo
INSTALL                nmap-payloads        nsock            traceroute.cc
libdnet-stripped       nmap-protocols       osscan2.cc       traceroute.h
liblinear              nmap-rpc             osscan2.h        utils.cc
liblua                 nmap-service-probes  osscan.cc        utils.h
libnetutil             nmap-services        osscan.h         xml.cc
libpcap                nmap_tty.cc          output.cc        xml.h
libpcre                nmap_tty.h           output.h         zenmap
ltmain.sh              nmap-update          payload.cc       zenmap-6.40-1.spec
MACLookup.cc           nmap_winconfig.h     payload.h
MACLookup.h            nping                portlist.cc
```

think that code thing should have worked, if not, I apologize

---

### Post by oldos2er on 2014-02-10
See [http://packaging.ubuntu.com/html/packaging-new-software.html](http://packaging.ubuntu.com/html/packaging-new-software.html)

---

### Post by beelzebufo on 2014-02-10
thank you very much Ann, that looks very helpful.

---

