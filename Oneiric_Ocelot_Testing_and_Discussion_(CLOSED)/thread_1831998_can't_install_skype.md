---
title: "can't install skype"
date: 2011-08-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by oc666 on 2011-08-24
Hello
I'm testing ubuntu 11.10.
I've try to install skype but the package didn't found.
I've try to [add partner repository](http://www.ubuntuupdates.org/ppas/36) but it didn't help, the package have an error.
This is the output after adding the repository:
```

oc666@oc666-desktop:/home/ofer$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package skype is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'skype' has no installation candidate

```

Thanks in advanced.

---

### Post by MadCow108 on 2011-08-24
the partner repository only gets added later in the cycle.
for now you have to use the natty package:
[https://launchpad.net/ubuntu/+source/skype](https://launchpad.net/ubuntu/+source/skype)

but note on amd64 you need to enable multiarch and install some 32 bit packages see [https://bugs.launchpad.net/ubuntu/+source/skype/+bug/830440](https://bugs.launchpad.net/ubuntu/+source/skype/+bug/830440)

---

### Post by oc666 on 2011-08-24
> **MadCow108 said:**
> the partner repository only gets added later in the cycle.
for now you have to use the natty package:
[https://launchpad.net/ubuntu/+source/skype](https://launchpad.net/ubuntu/+source/skype)

but note on amd64 you need to enable multiarch and install some 32 bit packages see [https://bugs.launchpad.net/ubuntu/+source/skype/+bug/830440](https://bugs.launchpad.net/ubuntu/+source/skype/+bug/830440)

Thanks for your quick reply.
Is there any step by step guide how to do that?
Thanks

---

### Post by pressureman on 2011-08-24
> **oc666 said:**
> Thanks for your quick reply.
Is there any step by step guide how to do that?
Thanks

Assuming you've added the natty partner repo to your apt sources, the following will enable multiarch support for i386, and install the i386 Skype package plus any i386 dependencies (quite a few):

```

echo foreign-architecture i386 | sudo tee /etc/dpkg/dpkg.cfg.d/multiarch
sudo apt-get update
sudo apt-get install skype:i386

```

---

### Post by kmsalex on 2011-08-24
> **pressureman said:**
> Assuming you've added the natty partner repo to your apt sources, the following will enable multiarch support for i386, and install the i386 Skype package plus any i386 dependencies (quite a few):

```

echo foreign-architecture i386 | sudo tee /etc/dpkg/dpkg.cfg.d/multiarch
sudo apt-get update
sudo apt-get install skype:i386

```

Thank you! I'm running a 64 bit install for the first time and little things like this might just send me back to 32 when 12.04 hits. I've only got 3 gigs of ram anyway.

After purging my previous install and starting over again I've got it up and running now
Now I'm gonna try and get it to iterate with emeathy, ought to be easy enough right :P

P.S. oc666 if you've done it successfully mark the tread solved.

---

### Post by oc666 on 2011-08-31
> **pressureman said:**
> Assuming you've added the natty partner repo to your apt sources, the following will enable multiarch support for i386, and install the i386 Skype package plus any i386 dependencies (quite a few):

```

echo foreign-architecture i386 | sudo tee /etc/dpkg/dpkg.cfg.d/multiarch
sudo apt-get update
sudo apt-get install skype:i386

```

How do I add the natty partner repo to my apt sources?

Thanks

---

### Post by cariboo on 2011-08-31
> **oc666 said:**
> How do I add the natty partner repo to my apt sources?

Thanks

Go to System Settings->Software Sources and enable the Partner repositories, you'll have to edit it to point to the Natty repository, as there isn't one for Oneiric yet.

---

### Post by oc666 on 2011-08-31
> **cariboo907 said:**
> Go to System Settings->Software Sources and enable the Partner repositories, you'll have to edit it to point to the Natty repository, as there isn't one for Oneiric yet.

Thanks
Works fine!
When the oneric partner repository would be updated to contain skype?

---

### Post by kuvanito on 2011-08-31
i am running oneiric 32 bit and i installed skype without any problems however in order to start it up i must call it from a terminal but it does work fine.

---

