---
title: "Almost There with LTSP 5 for Netvista"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by boyfrienddan on 2008-05-02
Hello all,

I've been trying to make an IBM Netvista 2200 8363 work following the advise from this [link]("http://www.ltsp.org/twiki/bin/view/Ltsp/NetVistaN2200").

I installed Kubuntu 8.04 in a 512MB, P4 with 1.8Mhz, then installed LTSP 5 after the install. Have DHCP working, the kernel, and everything, except later it told me connect:Connection Refused. Just now I discovered that my NFS server was not installed (I was wondering why it was not installed by default.) So I installed it and the thin client was able to boot until a prompt that said ltsp login. I tried to login but it said Invalid password. I noticed something above the login prompt, and it said:

mktemp: cannot create temp file /tmp/tmp.ECmXfD1892: Read-only file system
/usr/lib/ltsp/configure-x.sh: line 27: ${TEMPFILE}: ambiguous redirect

checked out the configuration file and I have no idea what to do with it. I already did ltsp-update-sshkeys and ltsp-update-image, and shutdown the server a couple of times to no avail. This has been a project that I am wishing I could finish because we are up to buy more netvistas for our school (they are dirt cheap). Anybody out there?

Thanks

---

### Post by mlambie on 2009-02-04
As a thought, you mentioned the need for and NFS server so I'd check that the NFS exports have the right permissions (read/write). The error indicates that something doesn't have write permissions and it looks like it needs them.

---

### Post by haddog on 2009-02-15
bdan. Try this page.

[https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)

Use the Hardy Heron (8.04) Ubuntu alternate CD. It has an option to install the LTSP server. Works out of the box. I have had better luck with 8.04 that 8.10. Plus 8.04 has LST (Long Term Support)

I'm doing some voluteer work for a my church. Not really work, I just wanted to try it! Going to setup up a computer lab.

So far I have 4 thin clients running, 3 Dell Optiplex GX200's w/256 MB ram and 1 GX240 w/1GB ram. 40 GB hard drive for testing. Going to upgrade to a 250GB drive. The thi clients connect to the Ubuntu LTSP server through a 16 port switch. All 4 of the thin clients have PXE capable nic cards.

The LTSP server is an old home built box. AMD 1.8 Ghz processor, 1 gig DDR ram, two 3com 905 nics, one connected to the switch, the other to an airlink 101 router that supplies the internet connection.

The thin clients and the server all share a keyboard/mouse/monitor via a belkin KVM switch for testing. I think I'm about ready to get the computer lab going.

---

### Post by haddog on 2010-04-02
my LTSP box is STILL crankin along on Ubuntu 8.04.2

---

