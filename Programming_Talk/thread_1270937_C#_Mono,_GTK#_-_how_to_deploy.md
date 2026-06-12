---
title: "C# Mono, GTK# - how to deploy?"
date: 2009-09-20
forum: Programming Talk
---

### Post by dchurch24 on 2009-09-20
Hi all,

I have just bought an eeepc for my daughter. I got rid of that limiting Xandros and put eeebuntu on there. All is good, everything worked as it should, and to be honest I'm bowled over by it. Fantastic little box.

However, I control all the lights, amps, TV's, doors etc... through another box running Xubuntu with various Windows satelites also able to control the lights et al by sending messages to the Xubuntu box using TCPIP.

I have written a front end on my main Ubuntu box to do the same as the Windows boxes (I can finally get rid of my windows boxes) - 64bit 8.04LTS - using C# and Gtk# (thanks due to the people on here pointing me in the right direction), my question is, how do I deploy it on the eeebuntu (32bit) netbook?

I have installed all manner of mono-* through Synaptic, but every time I click the .exe file, it opens Archive Manager.

What am I doing wrong, or what haven't I installed?

...or, indeed, is it possible to even do this?

---

### Post by huwnet on 2009-09-20
If you view the properties of the exe and goto "Open With" does it give you the option of opening the file with Mono instead? :)

Are you able to open the file by running something like this at the terminal:

mono filename.exe

mono might need to be replaced with a different mono command. I've never used it so I'm afraid I can't be more specific.

---

### Post by dchurch24 on 2009-09-20
Oh dear. I'm ebarrassed now!

I did: mono file.exe

...and it worked straight away!

Thank you very much, I must have been half asleep when I was trying it earlier!

---

### Post by dchurch24 on 2009-09-24
Hi again.

The project I'm working on has quite a few references that need packages installing before they appear in the list, e.g. MySQL.

As I'm only going to be running this on my home network, that's not much of a problem, I can installed the dependencies easily, but how would you package this up in say a rpm file if I needed to?

---

### Post by directhex on 2009-09-24
> **dchurch24 said:**
> Hi again.

The project I'm working on has quite a few references that need packages installing before they appear in the list, e.g. MySQL.

As I'm only going to be running this on my home network, that's not much of a problem, I can installed the dependencies easily, but how would you package this up in say a rpm file if I needed to?

You'd need to try an RPM-specific list for RPM tips. A SUSE list of some kind is likely to work better than a Red Hat list

---

### Post by dchurch24 on 2009-09-24
So I create a list, and use something like rpmbuild presumably?

What format is the list in?

---

### Post by directhex on 2009-09-24
> **dchurch24 said:**
> So I create a list, and use something like rpmbuild presumably?

What format is the list in?

No, as in "this is Ubuntuforums, nobody knows about RPM here, try an OpenSUSE mailing list or forum"

What you need to write is a .spec file, but that's RPM voodoo, a skill not found in the land of Ubuntu

---

### Post by dchurch24 on 2009-09-24
....okay.....?

What about .deb files then?  Ubuntu being Debian based, presumably this ok?

---

### Post by directhex on 2009-09-24
> **dchurch24 said:**
> ....okay.....?

What about .deb files then?  Ubuntu being Debian based, presumably this ok?

[https://wiki.ubuntu.com/MeetingLogs/devweek0901/MonoPackaging](https://wiki.ubuntu.com/MeetingLogs/devweek0901/MonoPackaging) contains a reasonable introduction with links to examples, it's probably best to read that

---

### Post by dchurch24 on 2009-09-24
Excellent. I'll have a read. Thanks.

---

