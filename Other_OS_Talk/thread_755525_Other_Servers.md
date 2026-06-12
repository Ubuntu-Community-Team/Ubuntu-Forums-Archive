---
title: "Other Servers"
date: 2008-04-14
forum: Other OS Talk
---

### Post by ism. on 2008-04-14
Hi!

Does anyone know of any other good linux servers besides Ubuntu?  I've read that suse is ok. I love Ubuntu as a desktop but I'm not so sure about the server part.

Thanks in advanced,

-ism.

---

### Post by tamoneya on 2008-04-14
debian, redhat, gentoo, slax.

[http://www.distrowatch.com](http://www.distrowatch.com)

---

### Post by cardinals_fan on 2008-04-14
Slackware.

---

### Post by LaRoza on 2008-04-15
CentOS.

---

### Post by mips on 2008-04-15
Not linux but FreeBSD & Solaris comes to mind.

---

### Post by ibutho on 2008-04-15
Red Hat (and its derivative CentOS) are quite popular on servers as well as Debian. FreeBSD is also quite popular (its used extensively at Yahoo).

---

### Post by kellemes on 2008-04-15
I'd go Debian or CentOS.

---

### Post by ism. on 2008-04-15
Thanks guys those are great and i plan to try out a couple (centroOS,FreeBSD, and Debian) but i have a question.  Why does Red hat cost money? Isn't linux supposed to be free? or.....

Thanks again for the replies

-ism.

---

### Post by kellemes on 2008-04-15
> **ism. said:**
>  Why does Red hat cost money?

Support.

If you want RH and feel you can handle it yourself with the volunteer support allover the net, go get CentOS. It's the same thing.

---

### Post by christianxxx on 2008-04-15
As far as I've understood, Linux is not necessarily free of charge, but it's free in the sense of open source.
But the two have a tendency to go hand in hand...

---

### Post by ism. on 2008-04-15
o.  Ok thanks

---

### Post by 3rdalbum on 2008-04-15
Fedora.

---

### Post by ism. on 2008-04-15
i looked at Fedora but im kinda intrested in the FreeBSD and CentralOS

---

### Post by ibutho on 2008-04-15
Did you mean CentOS ;) If you want to use FreeBSD, take a look at the [FreeBSD]("http://www.freebsd.org/doc/en/books/handbook/") Handbook. I found it to be a very valuable resource when I first started with FreeBSD. If you are going to use CentOS, then take a look at the [RHEL Deployment Guide]("http://www.redhat.com/docs/manuals/enterprise/RHEL-5-manual/en-US/RHEL510/Deployment_Guide/index.html").

---

### Post by lespaul_rentals on 2008-04-15
> **tamoneya said:**
> gentoo

I personally wouldn't use Gentoo for a server.  While it is very customizable, stability isn't exactly the best.  I could see it being good for some uses but I wouldn't trust it running the main production server.  Same with Arch.  While Arch is fairly stable, it is continually under development and kernel updates are always coming out.  This == more reboots, which == more downtime.  I love Arch for the desktop though.

Debian is very stable and I would recommend it as a server distro.  Somebody from IBM once said that an updated, properly configured Debian server is as secure as an OpenBSD box.  Whether that is true or not (it is a big statement), it's still a compliment to Debian.

Slackware is good in situations where it's okay to use processor power for compiling applications.

I liked using Ubuntu Server 6.06 for my home server.  It seemed stable during the simple stuff I was doing with it, and the Ubuntu security team is good about getting security fixes out quickly.

In the real world, you will see a lot of SuSE and Red Hat servers.  SuSE is often used in situations where interaction with Microsoft products is neccessary.  The reason you have to pay for them is for support.  When you buy the distro it comes with support for corporations.  I personally don't like either one too much, especially SLES, because it seems kind of n00by and a waste of resources to have a GUI on a server.  If you want an interesting experience, you can always try OpenSuSE and install all the server functions.  If you want a free Red Hat, go with CentOS.

For LAN servers, FreeNAS is great.  It's also a very small LiveCD that can run a fully functional server using just a few MB of RAM.  It even has features like RAID.

---

### Post by notwen on 2008-04-15
+1 Debian Etch

I've been running Debian Stable on my file server for the past 4 years and it is solid as a rock.  I don't think I'll ever use anything other than Debian Stable for my server needs unless I get into more advanced services.

---

### Post by lespaul_rentals on 2008-04-15
> **notwen said:**
> +1 Debian Etch

I've been running Debian Stable on my file server for the past 4 years and it is solid as a rock.  I don't think I'll ever use anything other than Debian Stable for my server needs unless I get into more advanced services.

LOL, Debian UNstable is pretty much solid as a rock.

Seriously, I think that the Debian developers asked themselves, "How can we make an operating system that would survive a fall into the Grand Canyon?"

---

### Post by notwen on 2008-04-15
Very true, I actually dual-boot Lenny and Arch on my tinker machine currently and have had no issues w/ Lenny for basic usage, playing media, surfing the web and email.  I did have sid installed, but just like to keep up w/ what's in store for my future 'stable' release.  Just to play it safe though, I'll use stable for my file server, jeebus knows what may happen if I can't stream my media to my laptops.  =p

---

### Post by lespaul_rentals on 2008-04-15
> **notwen said:**
> Very true, I actually dual-boot Lenny and Arch on my tinker machine currently and have had no issues w/ Lenny for basic usage, playing media, surfing the web and email.  I did have sid installed, but just like to keep up w/ what's in store for my future 'stable' release.  Just to play it safe though, I'll use stable for my file server, jeebus knows what may happen if I can't stream my media to my laptops.  =p

Do you use sshfs, Samba, or NFS to stream?

---

### Post by ism. on 2008-04-15
> **ibutho said:**
> Did you mean CentOS ;) If you want to use FreeBSD, take a look at the [FreeBSD]("http://www.freebsd.org/doc/en/books/handbook/") Handbook. I found it to be a very valuable resource when I first started with FreeBSD. If you are going to use CentOS, then take a look at the [RHEL Deployment Guide]("http://www.redhat.com/docs/manuals/enterprise/RHEL-5-manual/en-US/RHEL510/Deployment_Guide/index.html").

o hahaha my bad i did mean CentOS :cool:  Also thanks for those links! Very Helpful!

Thanks alot,

-ism.

---

### Post by quickshade on 2008-04-15
Have heard great things about CentOS and it's hosting abilities. Thats what i would use.

---

### Post by ism. on 2008-04-15
i can see why Ubuntu is more popular for beginners. these others are all much more confusing to install for the new to linux people.  But i eventually got them!

---

### Post by notwen on 2008-04-16
> **lespaul_rentals said:**
> Do you use sshfs, Samba, or NFS to stream?

NFS unless, I run into some issues somewhere down the road.

---

