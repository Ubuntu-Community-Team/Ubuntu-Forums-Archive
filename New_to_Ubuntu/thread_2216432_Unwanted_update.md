---
title: "Unwanted update"
date: 2014-04-11
forum: New to Ubuntu
---

### Post by Cyber72 on 2014-04-11
My list of available updates includes python-lockfile. when I try to install the updates I get the message 
The action would require the installation of packages from unauthenticated sources
When i click on details it names python-lockfile. I have unticked the box for this update but I keep getting the message.
I want to install the other updates but not python-lockfile. What do i need to do?

---

### Post by richaustin on 2014-04-12
You could try the following link:

[http://askubuntu.com/questions/99774/exclude-packages-from-apt-get-upgrade](http://askubuntu.com/questions/99774/exclude-packages-from-apt-get-upgrade)

---

### Post by grumblebum2 on 2014-04-12
Use synaptic to see where the python-lockfile update is coming from.

---

### Post by Cyber72 on 2014-04-15
Many thanks

---

### Post by dewdrop_world on 2014-04-16
I'm actually curious about the details, though. Like the OP, I manually unchecked the update to python-lockfile, and the update mechanism magically re-enabled the update.

I think this must be because some other package depends on python-lockfile, but I don't do enough with apt to know how to find out which one.

In any case, isn't this a bit sloppy? If a high-priority update depends on an untrusted package, and this will cause the update to fail, shouldn't that be addressed in the appropriate package definitions? If it's a security update... kind of important that it should "just work."

For the record, richaustin's answer did allow me to proceed with the update. For convenience of future readers:

```
sudo apt-mark hold python-lockfile
```

Thanks,
hjh

---

### Post by grumblebum2 on 2014-04-17
Where is your update coming from to be untrusted?
```
apt-cache policy python-lockfile
```

---

### Post by dewdrop_world on 2014-04-20
> **grumblebum2 said:**
> Where is your update coming from to be untrusted?
```
apt-cache policy python-lockfile
```

```
$ apt-cache policy python-lockfile
python-lockfile:
  Installed: (none)
  Candidate: 1:0.8-2ubuntu1
  Version table:
     1:0.8-2ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
```

hjh

---

### Post by richard76 on 2014-07-23
As a senior citizen with absolutely no knowledge of computer code none of the above answers are a help to me. I have been using UBUNTU without any real problems for about 5 years but if I cannot install security updates due to being offered untrusted packages ( why ?) I might have to go back to Micro-soft. Can I go into settings and just remove Python altogether or is it a critical component ? could I perhaps download the latest updates without the untrusted package from the Ubuntu web page ? I realise I am out of date but surely Linux must be usable by the general non-geek public to survive.

---

### Post by coldcritter64 on 2014-07-24
> but if I cannot install security updates due to being offered untrusted packages ( why ?) I might have to go back to Micro-soft

The status of "untrusted package" will refer to a package lacking a digital signature or is incorrectly digital signed. Digital signatures are used to check authenticity of packages.

I have seen and ignored that message hundreds of times over the years without any problem, but I only ever trust the package IF it comes from the official Ubuntu repositories (knowing the repos are checked) not third party repositories/ppas or other online sources.

Windows installs require digital signing of drivers etc, but they can come from any source not just Windows update servers. Ubuntu uses digital signatures as well (usually, not so in this case), but the source is a centralized repository and as such is heavily checked/monitored. A package not being digitally signed in Ubuntu is not as important as it is in Windows because of the centralized repository set up. Personally if the source is the main repo as shown by dewdrop_world's last post I would not hesitate to install that particular package. You are operating in what is known as a "Windows Mindset" and Linux is NOT the same as Windows.

Relax a bit and enjoy yourself is my advice ... I have been using Ubuntu/Linux for 7 years now and have safely ignored that warning quite often **when** the source is the official repos. 

By all means always note the source of the package, as grumblebum2 asked above, and you can relax a bit if it is from the official repositories, as it is in this case. Cheers, coldcritter64

---

