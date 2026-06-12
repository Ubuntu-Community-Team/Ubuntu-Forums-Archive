---
title: "Small LiveCD Server?"
date: 2006-11-21
forum: Other OS Talk
---

### Post by jimhaddon on 2006-11-21
Hi,

I'm looking for a distro that is server on a LiveCD, which has built in PHP + MySQL capability.

I have already tried the old Lamppix, but it doesnt seem to be able to serve, only on the host machine.

Is there anything else out there?

Thanks
James

---

### Post by arox on 2006-11-21
Slax Server edition maybe?

---

### Post by jimhaddon on 2006-11-22
I found an amazing solution!

OssWatch knoppix remastered does this job fantastically:

[http://www.oss-watch.ac.uk/resources/osswatchknoppix402.xml](http://www.oss-watch.ac.uk/resources/osswatchknoppix402.xml)

---

### Post by greggh on 2006-11-22
> **arox said:**
> Slax Server edition maybe?

I would second that. At only 192 MB Slax Server Edition 5.1.8 is small (fits on a mini-CD) and fast, and includes DNS, DHCP, HTTP, FTP, MySQL, SMTP, POP3, IMAP and SSH.

[http://www.slax.org/download.php](http://www.slax.org/download.php)

---

### Post by RAV TUX on 2006-11-22
> **jimhaddon said:**
> Hi,

I'm looking for a distro that is server on a LiveCD, which has built in PHP + MySQL capability.

I have already tried the old Lamppix, but it doesnt seem to be able to serve, only on the host machine.

Is there anything else out there?

Thanks
James

I highly recommend:
[IMG]http://www.tinysofa.org/images/tinysofa.gif[/IMG]
**[[B]tinysofa** classic server]("http://www.tinysofa.org/")[/B]

[IMG]http://www.tinysofa.org/images/imagine.gif[/IMG]

> **What is tinysofa?**

         tinysofa classic server is a small, fast and secure enterprise grade operating system based on the Linux kernel.
         **Why should I use tinysofa?**[LIST]
[*]**Fast.** Optimised for i586 and up, tinysofa classic server is built with speed as a prime priority.
[*]**Stable.** Based on proven technology, tinysofa classic server has been thoroughly tested in a vast array of mission critical roles with amazing stability.
[*]**Secure.** Our number one priority, security is no afterthought in tinysofa classic server, which incorporates the [grsecurity]("http://www.grsecurity.net/") patch set. Only one service is enabled by default (postfix running on 127.0.0.1). Our default settings are as secure as possible. And the IBM stack protector patch for GCC makes stack smashing attacks a worry of the past.
[*]**Well Supported.** Our mailing lists provide you with access to a friendly and helpful community of tinysofa classic server users. In case you need professional assistance with tinysofa classic server, a global network of tinysofa professional engineers is at your fingertips.
[*]**Easily Managed.** The [APT]("http://classic.tinysofa.org/documentation/index.cgi?UsingApt") tool keeps your tinysofa classic server installations up to date with the latest security fixes and application enhancements. Additionally, running your own *APT* repositories is simple and, best of all, completely free.
[*]**Free(dom).** As in beer. Free, as in speech. tinysofa classic server is guaranteed to remain free throughout its lifetime.[/LIST]**Where can I get tinysofa?**

         [Download]("http://www.tinysofa.org/download/") the next generation tinysofa classic server now.
> 
**About**

     **Heritage**

     tinysofa classic server is a server targeted, enterprise grade Linux distribution that combines the the vision and expertise of multiple open source developers with the best components and ideas of multiple enterprise focused operating systems.
     tinysofa classic server is based on Fedora, tinysofa enterprise server 1.0 and Trustix 2.1. It features a very similar package set to Trustix.
     **Motivation**

     tinysofa aims to become the de facto community run server oriented Linux distribution, and therefore fill an ever growing void in the availability of a free (as in beer and speech) Linux solution that is deployable in mission critical roles throughout the enterprise.
     **Distinction**

     The meticulously crafted software packages that compose tinysofa, coupled with a focus on security, stability and manageability make it the only completely free Linux solution suitable for enterprise use.
     The global network of independent consultants supporting tinysofa aims to level the playing field with the commercial providers of Linux solutions and most importantly, foster local economic growth.
     **Suitability**

     tinysofa is currently used in a vast array of real time business systems that require the utmost in security and stability. From VPN end points, firewalls, bridges and network IDS to application servers and database workhorses, tinysofa has proven itself up to the task.
     **Outlook**

         The 1.x release series will maintain platform stability throughout its lifetime, with ongoing incremental enhancements and security fixes and a minor release every six months. This release series will also be available for the x86_64 hardware platform.
> ** tinysofa classic server 2.0 **

** Update 6 **[LIST]
[*] anaconda[LIST]
[*] support USB keyboards[/LIST] 
[*] bind[LIST]
[*]  9.3.2-P1, fixes CVE-2006-4095, CVE-2006-4095[/LIST] 
[*] binutils[LIST]
[*]fix a gas buffer overflow[/LIST] 
[*] e2fsprogs[LIST]
[*] new upstream[/LIST] 
[*] gzip[LIST]
[*] CVE-2006-4334, CVE-2006-4335, CVE-2006-4336, CVE-2006-4337, CVE-2006-4338[/LIST] 
[*] initscripts[LIST]
[*] default sysctl.conf update[/LIST] 
[*] kernel[LIST]
[*] update to 2.6.16.29 which fixes various issues[/LIST] 
[*] openssl[LIST]
[*] CVE-2006-4339[/LIST] 
[*] php[LIST]
[*] security fixes[/LIST] 
[*] procmail[LIST]
[*] fix default system mailbox location[/LIST] 
[*] stunnel[LIST]
[*] initscript fix[/LIST] [/LIST][LIST]
[*] **All errata packages integrated.**[/LIST]

> **Download**

 	These are the official mirrors of tinysofa. Please try to use one near you.
 	You can either grab one of the boot disks and install directly from the distribution sites, download a bootable ISO image or download the entire distribution tree and install locally afterwards.
 	(Are you looking for [tinysofa enterprise server]("http://www.tinysofa.org/download/")?)
 	The tinysofa gpg stable sign key is [0F1240A2]("http://pgp.mit.edu:11371/pks/lookup?op=get&search=0x0F1240A2").
	 Key fingerprint = **0371 2340 1FA6 7911 09E2  B209 DAC0 AD37 0F12 40A2**. 	
The latest tinysofa classic server (stable) version is **2.0 Update 6** (Ceara). Released on the 17th of October, 2006.
          **Asia**

         [LIST]
[*]Bandung, Indonesia - ITB (HTTP)
        [2.0: [Root dir]("http://linux.tf.itb.ac.id/tinysofa/releases/classic-2.0")] [[Bootdisk]("http://linux.tf.itb.ac.id/tinysofa/releases/classic-2.0/i586/images")] [[Bootable ISO images]("http://linux.tf.itb.ac.id/tinysofa/releases/classic-2.0/iso")] [[Source RPMS]("http://linux.tf.itb.ac.id/tinysofa/releases/classic-2.0/srpms.os")]
        <URI:http://linux.tf.itb.ac.id/tinysofa/>[/LIST] 	**Australia**

 	[LIST]
[*]Brisbane - PlanetMirror (FTP)
	[2.0: [Root dir]("ftp://ftp.planetmirror.com/pub/tinysofa/releases/classic-2.0")] [[Bootdisk]("ftp://ftp.planetmirror.com/pub/tinysofa/releases/classic-2.0/i586/images")] [[Bootable ISO images]("ftp://ftp.planetmirror.com/pub/tinysofa/releases/classic-2.0/iso")] [[Source RPMS]("ftp://ftp.planetmirror.com/pub/tinysofa/releases/classic-2.0/srpms.os")]
	<URI:ftp://ftp.planetmirror.com/pub/tinysofa>
[*]Brisbane - PlanetMirror (HTTP)
	[2.0: [Root dir]("http://www.planetmirror.com/pub/tinysofa/releases/classic-2.0")] [[Bootdisk]("http://www.planetmirror.com/pub/tinysofa/releases/classic-2.0/i586/images")] [[Bootable ISO images]("http://www.planetmirror.com/pub/tinysofa/releases/classic-2.0/iso")] [[Source RPMS]("http://www.planetmirror.com/pub/tinysofa/releases/classic-2.0/srpms.os")]
	<URI:http://www.planetmirror.com/pub/tinysofa>
[*]Brisbane - PlanetMirror (RSYNC)
	[2.0: [Root dir]("rsync://rsync.planetmirror.com/tinysofa/releases/classic-2.0")] [[Bootdisk]("rsync://rsync.planetmirror.com/tinysofa/releases/classic-2.0/i586/images")] [[Bootable ISO images]("rsync://rsync.planetmirror.com/tinysofa/releases/classic-2.0/iso")] [[Source RPMS]("rsync://rsync.planetmirror.com/tinysofa/releases/classic-2.0/srpms.os")]
	<URI:rsync://rsync.planetmirror.com/tinysofa>
[*]Sydney - Link Innovations (FTP)
	[2.0: [Root dir]("ftp://tinysofa.mirror.linkinnovations.com/releases/classic-2.0")] [[Bootdisk]("ftp://tinysofa.mirror.linkinnovations.com/releases/classic-2.0/i586/images")] [[Bootable ISO images]("ftp://tinysofa.mirror.linkinnovations.com/releases/classic-2.0/iso")] [[Source RPMS]("ftp://tinysofa.mirror.linkinnovations.com/releases/classic-2.0/srpms.os")]
	<URI:ftp://tinysofa.mirror.linkinnovations.com>
[*]Sydney - Link Innovations (HTTP)
	[2.0: [Root dir]("http://tinysofa.mirror.linkinnovations.com/releases/classic-2.0")] [[Bootdisk]("http://tinysofa.mirror.linkinnovations.com/releases/classic-2.0/i586/images")] [[Bootable ISO images]("http://tinysofa.mirror.linkinnovations.com/releases/classic-2.0/iso")] [[Source RPMS]("http://tinysofa.mirror.linkinnovations.com/releases/classic-2.0/srpms.os")]
	<URI:http://tinysofa.mirror.linkinnovations.com>
[*]Sydney - Pacific Internet (FTP)
	[2.0: [Root dir]("ftp://mirror.pacific.net.au/linux/tinysofa/releases/classic-2.0")] [[Bootdisk]("ftp://mirror.pacific.net.au/linux/tinysofa/releases/classic-2.0/i586/images")] [[Bootable ISO images]("ftp://mirror.pacific.net.au/linux/tinysofa/releases/classic-2.0/iso")] [[Source RPMS]("ftp://mirror.pacific.net.au/linux/tinysofa/releases/classic-2.0/srpms.os")]
	<URI:ftp://mirror.pacific.net.au/linux/tinysofa/>
[*]Sydney - Pacific Internet (HTTP)
	[2.0: [Root dir]("http://mirror.pacific.net.au/linux/tinysofa/releases/classic-2.0")] [[Bootdisk]("http://mirror.pacific.net.au/linux/tinysofa/releases/classic-2.0/i586/images")] [[Bootable ISO images]("http://mirror.pacific.net.au/linux/tinysofa/releases/classic-2.0/iso")] [[Source RPMS]("http://mirror.pacific.net.au/linux/tinysofa/releases/classic-2.0/srpms.os")]
	<URI:http://mirror.pacific.net.au/linux/tinysofa/>
[*]Hobart - KeyPoint (FTP)
	[2.0: [Root dir]("ftp://ftp.tas.keypoint.com.au/pub/tinysofa/releases/classic-2.0")] [[Bootdisk]("ftp://ftp.tas.keypoint.com.au/pub/tinysofa/releases/classic-2.0/i586/images")] [[Bootable ISO images]("ftp://ftp.tas.keypoint.com.au/pub/tinysofa/releases/classic-2.0/iso")] [[Source RPMS]("ftp://ftp.tas.keypoint.com.au/pub/tinysofa/releases/classic-2.0/srpms.os")]
	<URI:ftp://ftp.tas.keypoint.com.au/pub/tinysofa>
[*]Hobart - KeyPoint (HTTP)
	[2.0: [Root dir]("http://ftp.tas.keypoint.com.au/pub/tinysofa/releases/classic-2.0")] [[Bootdisk]("http://ftp.tas.keypoint.com.au/pub/tinysofa/releases/classic-2.0/i586/images")] [[Bootable ISO images]("http://ftp.tas.keypoint.com.au/pub/tinysofa/releases/classic-2.0/iso")] [[Source RPMS]("http://ftp.tas.keypoint.com.au/pub/tinysofa/releases/classic-2.0/srpms.os")]
	<URI:http://ftp.tas.keypoint.com.au/pub/tinysofa>
[*]Hobart - KeyPoint (RSYNC)
	[2.0: [Root dir]("rsync://ftp.tas.keypoint.com.au/tinysofa/releases/classic-2.0")] [[Bootdisk]("rsync://ftp.tas.keypoint.com.au/tinysofa/releases/classic-2.0/i586/images")] [[Bootable ISO images]("rsync://ftp.tas.keypoint.com.au/tinysofa/releases/classic-2.0/iso")] [[Source RPMS]("rsync://ftp.tas.keypoint.com.au/tinysofa/releases/classic-2.0/srpms.os")]
	<URI:rsync://ftp.tas.keypoint.com.au/tinysofa>[/LIST] 	**Europe**

 	[LIST]
[*]France - Netsolux (HTTP)
	[2.0: [Root dir]("http://www.netsolux.ch/tinysofa/releases/classic-2.0")] [[Bootdisk]("http://www.netsolux.ch/tinysofa/releases/classic-2.0/i586/images")] [[Bootable ISO images]("http://www.netsolux.ch/tinysofa/releases/classic-2.0/iso")] [[Source RPMS]("http://www.netsolux.ch/tinysofa/releases/classic-2.0/srpms.os")]
	<URI:http://www.netsolux.ch/tinysofa/>
[*]Budapest, Hungary - Iszerviz (FTP)
	[2.0: [Root dir]("ftp://tinysofa.iszerviz.hu/tinysofa/releases/classic-2.0")] [[Bootdisk]("ftp://tinysofa.iszerviz.hu/tinysofa/releases/classic-2.0/i586/images")] [[Bootable ISO images]("ftp://tinysofa.iszerviz.hu/tinysofa/releases/classic-2.0/iso")] [[Source RPMS]("ftp://tinysofa.iszerviz.hu/tinysofa/releases/classic-2.0/srpms.os")]
	<URI:ftp://tinysofa.iszerviz.hu/tinysofa/>
[*]Budapest, Hungary - Iszerviz (HTTP)
	[2.0: [Root dir]("http://tinysofa.iszerviz.hu/releases/classic-2.0")] [[Bootdisk]("http://tinysofa.iszerviz.hu/releases/classic-2.0/i586/images")] [[Bootable ISO images]("http://tinysofa.iszerviz.hu/releases/classic-2.0/iso")] [[Source RPMS]("http://tinysofa.iszerviz.hu/releases/classic-2.0/srpms.os")]
	<URI:http://tinysofa.iszerviz.hu/>
[*]Netherlands - EasyNet (FTP)
	[2.0: [Root dir]("ftp://ftp.easynet.nl/mirror/tinysofa/releases/classic-2.0")] [[Bootdisk]("ftp://ftp.easynet.nl/mirror/tinysofa/releases/classic-2.0/i586/images")] [[Bootable ISO images]("ftp://ftp.easynet.nl/mirror/tinysofa/releases/classic-2.0/iso")] [[Source RPMS]("ftp://ftp.easynet.nl/mirror/tinysofa/releases/classic-2.0/srpms.os")]
	<URI:ftp://ftp.easynet.nl/mirror/tinysofa>
[*]Netherlands - EasyNet (HTTP)
	[2.0: [Root dir]("http://ftp.easynet.nl/mirror/tinysofa/releases/classic-2.0")] [[Bootdisk]("http://ftp.easynet.nl/mirror/tinysofa/releases/classic-2.0/i586/images")] [[Bootable ISO images]("http://ftp.easynet.nl/mirror/tinysofa/releases/classic-2.0/iso")] [[Source RPMS]("http://ftp.easynet.nl/mirror/tinysofa/releases/classic-2.0/srpms.os")]
	<URI:http://ftp.easynet.nl/mirror/tinysofa>
[*]Sweden - Skellefteå (FTP)
	[2.0: [Root dir]("ftp://ftp.campus.skelleftea.se/pub/mirror/tinysofa.org/tinysofa/releases/classic-2.0")] [[Bootdisk]("ftp://ftp.campus.skelleftea.se/pub/mirror/tinysofa.org/tinysofa/releases/classic-2.0/i586/images")] [[Bootable ISO images]("ftp://ftp.campus.skelleftea.se/pub/mirror/tinysofa.org/tinysofa/releases/classic-2.0/iso")] [[Source RPMS]("ftp://ftp.campus.skelleftea.se/pub/mirror/tinysofa.org/tinysofa/releases/classic-2.0/srpms.os")]
	<URI:ftp://ftp.campus.skelleftea.se/pub/mirror/tinysofa.org/tinysofa/>
[*]Sweden - Skellefteå (HTTP)
	[2.0: [Root dir]("http://ftp.campus.skelleftea.se/pub/mirror/tinysofa.org/tinysofa/releases/classic-2.0")] [[Bootdisk]("http://ftp.campus.skelleftea.se/pub/mirror/tinysofa.org/tinysofa/releases/classic-2.0/i586/images")] [[Bootable ISO images]("http://ftp.campus.skelleftea.se/pub/mirror/tinysofa.org/tinysofa/releases/classic-2.0/iso")] [[Source RPMS]("http://ftp.campus.skelleftea.se/pub/mirror/tinysofa.org/tinysofa/releases/classic-2.0/srpms.os")]
	<URI:http://ftp.campus.skelleftea.se/pub/mirror/tinysofa.org/tinysofa/>[/LIST] 	**North America**

 	[LIST]
[*]North Carolina - ibiblio (FTP)
	[2.0: [Root dir]("ftp://ftp.ibiblio.org/pub/linux/distributions/tinysofa/releases/classic-2.0")] [[Bootdisk]("ftp://ftp.ibiblio.org/pub/linux/distributions/tinysofa/releases/classic-2.0/i586/images")] [[Bootable ISO images]("ftp://ftp.ibiblio.org/pub/linux/distributions/tinysofa/releases/classic-2.0/iso")] [[Source RPMS]("ftp://ftp.ibiblio.org/pub/linux/distributions/tinysofa/releases/classic-2.0/srpms.os")]
	<URI:ftp://ftp.ibiblio.org/pub/linux/distributions/tinysofa>
[*]North Carolina - ibiblio (HTTP)
	[2.0: [Root dir]("http://www.ibiblio.org/pub/linux/distributions/tinysofa/releases/classic-2.0")] [[Bootdisk]("http://www.ibiblio.org/pub/linux/distributions/tinysofa/releases/classic-2.0/i586/images")] [[Bootable ISO images]("http://www.ibiblio.org/pub/linux/distributions/tinysofa/releases/classic-2.0/iso")] [[Source RPMS]("http://www.ibiblio.org/pub/linux/distributions/tinysofa/releases/classic-2.0/srpms.os")]
	<URI:http://www.ibiblio.org/pub/linux/distributions/tinysofa>
[*]North Carolina - ibiblio (RSYNC)
	[2.0: [Root dir]("rsync://ibiblio.org/distros/tinysofa/releases/classic-2.0")] [[Bootdisk]("rsync://ibiblio.org/distros/tinysofa/releases/classic-2.0/i586/images")] [[Bootable ISO images]("rsync://ibiblio.org/distros/tinysofa/releases/classic-2.0/iso")] [[Source RPMS]("rsync://ibiblio.org/distros/tinysofa/releases/classic-2.0/srpms.os")]
	<URI:rsync://ibiblio.org/distros/tinysofa>
[*]Florida - tinysofa backup site (FTP)
	[2.0: [Root dir]("ftp://ftp.tinysofa.org/pub/tinysofa/releases/classic-2.0")] [[Bootdisk]("ftp://ftp.tinysofa.org/pub/tinysofa/releases/classic-2.0/i586/images")] [[Bootable ISO images]("ftp://ftp.tinysofa.org/pub/tinysofa/releases/classic-2.0/iso")] [[Source RPMS]("ftp://ftp.tinysofa.org/pub/tinysofa/releases/classic-2.0/srpms.os")]
	<URI:ftp://ftp.tinysofa.org/pub/tinysofa>
[*]Ohio - tinysofa main site (FTP)
	[2.0: [Root dir]("ftp://minbar.tinysofa.org/pub/tinysofa/releases/classic-2.0")] [[Bootdisk]("ftp://minbar.tinysofa.org/pub/tinysofa/releases/classic-2.0/i586/images")] [[Bootable ISO images]("ftp://minbar.tinysofa.org/pub/tinysofa/releases/classic-2.0/iso")] [[Source RPMS]("ftp://minbar.tinysofa.org/pub/tinysofa/releases/classic-2.0/srpms.os")]
	<URI:ftp://minbar.tinysofa.org/pub/tinysofa>
[*]Ohio - tinysofa main site (HTTP)
	[2.0: [Root dir]("http://minbar.tinysofa.org/pub/tinysofa/releases/classic-2.0")] [[Bootdisk]("http://minbar.tinysofa.org/pub/tinysofa/releases/classic-2.0/i586/images")] [[Bootable ISO images]("http://minbar.tinysofa.org/pub/tinysofa/releases/classic-2.0/iso")] [[Source RPMS]("http://minbar.tinysofa.org/pub/tinysofa/releases/classic-2.0/srpms.os")]
	<URI:http://minbar.tinysofa.org/pub/tinysofa>
[*]Ohio - tinysofa main site (RSYNC)
	[2.0: [Root dir]("rsync://minbar.tinysofa.org/tinysofa/releases/classic-2.0")] [[Bootdisk]("rsync://minbar.tinysofa.org/tinysofa/releases/classic-2.0/i586/images")] [[Bootable ISO images]("rsync://minbar.tinysofa.org/tinysofa/releases/classic-2.0/iso")] [[Source RPMS]("rsync://minbar.tinysofa.org/tinysofa/releases/classic-2.0/srpms.os")]
	<URI:rsync://minbar.tinysofa.org/tinysofa>[/LIST] 	

---

### Post by jimhaddon on 2006-11-23
Wow, thankyou for your replies..

I have tried Slax, and it is very small and very fast indeed. The only problem I have with it, is that I would maybe want moodle already installed on the LiveCD so that it just works, and having looked through it, I cant really see a way of doing that.

TinySofa does look good, but again I would have the same problems.

---

### Post by RAV TUX on 2006-11-23
> **jimhaddon said:**
> I found an amazing solution!

OssWatch knoppix remastered does this job fantastically:

[http://www.oss-watch.ac.uk/resources/osswatchknoppix402.xml](http://www.oss-watch.ac.uk/resources/osswatchknoppix402.xml)

if it's based on KNOPPIX it has to be good;)

---

### Post by jimhaddon on 2006-11-23
maybe, but knoppix is way too slow to be a server.

SLax server is really good, but i cant get phpmyadmin working on it!

---

### Post by rattlerviper on 2006-11-23
> **jimhaddon said:**
> maybe, but knoppix is way too slow to be a server.

SLax server is really good, but i cant get phpmyadmin working on it!Yes it is slow.  Spend some time with Slax, you should be able to get it to work.

---

### Post by RAV TUX on 2006-11-23
> **jimhaddon said:**
> maybe, but knoppix is way too slow to be a server.

SLax server is really good, but i cant get phpmyadmin working on it!

Actually I was joking about this,...my sense of humor.

Again Tiny Sofa or SLAX should be good....but I am sure there are other options.

---

### Post by jimhaddon on 2006-11-24
Definately. I would like to use slax, as it is so fast and small. Just wish I could get phpmyadmin working...

The problem I have is setting up the config for it. I have it loaded etc, but it just gives me an error saying Mysql cannot find config or something..


Either way, I would like to make a LiveCD that just loaded with phpmyadmin already installed on it, and maybe with the mysql data already in the database too!

---

### Post by jimhaddon on 2006-11-24
Does anyone know how i can modofy either slax, or some other distro to include phpmyadmin as standard?

---

