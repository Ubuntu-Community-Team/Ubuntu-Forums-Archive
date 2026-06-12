---
title: "Ubuntu in the Classroom"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by onlyproductions on 2008-11-05
Hello,
A few days ago i was reading about a teacher who had his classroom all linux based.
He had a main computer which could connect and monitor all the students computers which were all connected via lan.

my question is how can i go about setting this up

---

### Post by DGortze380 on 2008-11-05
> **onlyproductions said:**
> Hello,
A few days ago i was reading about a teacher who had his classroom all linux based.
He had a main computer which could connect and monitor all the students computers which were all connected via lan.

my question is how can i go about setting this up

The LAN is easy, get a switch, plug in all the computers.
Sounds like some kind of VNC set-up to monitor them, not sure quite how to do that.

---

### Post by maybeway36 on 2008-11-05
Use an LTSP server.
The main computer is connected both to the main LAN/Internet and a private router, over which it hands out IP addresses. Each thin client is connected only to that router and boots over the network.
The Ubuntu Alternate CD has an option for installing an LTSP server. See: [https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall]("https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall")

---

### Post by nhasian on 2008-11-05
Here's what your talking about:

Free Open Source Computer Lab Monitoring Software Using VNC

[http://thetechnologyteacher.wordpress.com/vncthumbnailviewer/](http://thetechnologyteacher.wordpress.com/vncthumbnailviewer/)

here's the linux version:

[http://www.alpha.co.jp/biz/rdg/multivnc/english/demo/demo01.html](http://www.alpha.co.jp/biz/rdg/multivnc/english/demo/demo01.html)

---

### Post by brandoncolorado on 2008-11-05
> **onlyproductions said:**
> Hello,
A few days ago i was reading about a teacher who had his classroom all linux based.
He had a main computer which could connect and monitor all the students computers which were all connected via lan.

my question is how can i go about setting this up

BAM!
[http://edubuntu.org/](http://edubuntu.org/)

---

### Post by marialice on 2008-11-08
Could it be that you mean [iTALC - Intelligent Teaching And Learning with Computers](http://italc.sourceforge.net/home.php), that's in use at iMAK, where Josh Beck teaches (see [here](here)).

---

### Post by SMut on 2008-11-09
LTSP is the thing you want, imho.
With an actual computer (preferred an amd64 CPU) you can handle a complete classroom with so called 'thin-clients'.
Note that these thin-clients should be able to do 'PXE-boot' or some 'commercial' alternatives.

The idea behind this is, that _all_ applications run on the server, the client just send the mouse/keyboard interactions back to the server and displays the results. Due to the fact that Unix-like systems have a 'machine independent' X11-server you are able to add any desktop you like to the thin-clients, even different guis are possible, when configured matching to the MAC adress of the client.

Ubuntu has done a nice job now with hardy (I'd recommend LTS versions for this kind of thing) but the server alternative installation is quite - hrm - not buggy, but some dependencies are not solved properly.

So:
Get an alternative 'standard' Installation CD, a fast amd64 or i386 machine with as much RAM as you can afford it, a bunch of HDD to built an appropriate (software) RAID to prepare your machine to be tough in daily use.
Run the installation and press [F4] hit LTSP and all basic setup should run easily.
IMPORTANT!
Use 2 NICs:
The first to set up internet-connectivity.
Second one is the dhcpd- and LTSP-bootimage-server for the client which MUST reside in a seperate network!

Hope this helps, just do some googling arount ubuntu and ltsp and you will find a lot of howtos!

Regards,
Steffen from Germany

---

