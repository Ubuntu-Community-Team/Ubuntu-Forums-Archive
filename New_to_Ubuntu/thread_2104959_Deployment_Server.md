---
title: "Deployment Server"
date: 2013-01-14
forum: New to Ubuntu
---

### Post by poptikx on 2013-01-14
Hello,

I am going to be implementing a deployment server at work to reduce error when staging some of our servers.

We currently use Ubuntu 10.04 LTS and 12.04 LTS.  

Now we normally stage 4-5 servers a week at minimum and i would like to semi automate this with a deployment server. However i would need something that could push out windows images as well.

Do you have any reccomendations? I am pretty new to Linux but have an excellent group that has been dealing with it for a very long time at my work.

So basically i need to be able to push out 3 different images for Linux based on hardware models of the servers, and 3 different images for windows based on roles in my company. 

Like i said i am just looking for suggestions or advice on this one. 

Thank you for your time and help!

---

### Post by CharlesA on 2013-01-14
[Clonezilla]("http://clonezilla.org/") would probably work.

Otherwise look into something like Ghost or Acronis.

---

### Post by poptikx on 2013-01-14
That's what i was currently looking at. Do you know if that will allow me to sue the built in PXE boot options to stage these devices?

---

### Post by CharlesA on 2013-01-14
Clonezilla server edition should be able to boot via PXE, but I am not sure if Ghost or Acronis is able to.

---

### Post by eenofonn on 2013-01-14
Though I've not used either of them I've heard you can do some powerful things with Puppet and Razor.

[Puppet]("http://puppetlabs.com/puppet/puppet-open-source/")
[Razor]("http://puppetlabs.com/blog/razor-now-100-percent-open-source/")

---

### Post by poptikx on 2013-01-14
Ill check it out.

---

### Post by lykwydchykyn on 2013-01-14
We used G4L for a long time to do imaging here; the server side is just FTP, and it can certainly be booted using PXE.

You can also boot to a command-line ubuntu installer (Debian Installer) over PXE and use a system like preseed or FAI to setup the system.  I've used preseed before on Debian (should work on Ubuntu too, it's the same installer), but I've been told FAI is better.  

That, combined with a local apt-mirror, may be more efficient than disk images.

---

### Post by Cheesemill on 2013-01-15
I set up a Fog server at work to deploy our Windows workstations (1000's of them).

I've not tried using it to deploy Windows Servers but it should work in exactly the same fashion.

[http://www.fogproject.org/](http://www.fogproject.org/)

---

### Post by poptikx on 2013-01-16
Thank you all for the advice.
I am currently looking into this and appreciate all the help.

---

