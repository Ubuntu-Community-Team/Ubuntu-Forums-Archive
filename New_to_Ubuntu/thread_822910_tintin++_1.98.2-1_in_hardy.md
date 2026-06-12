---
title: "tintin++_1.98.2-1 in hardy"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by animalprimate on 2008-06-08
i had some problems with the version of TinTin 1.97 (in Hardy)

apt-get install tintin++ gives you version 1.97

**this link:** 
[http://packages.ubuntu.com/search?keywords=tintin%2B%2B]("http://packages.ubuntu.com/search?keywords=tintin%2B%2B")

**provides this information:**
# hardy (games): classic text-based MUD client [universe]
 1.97.9-2: amd64 i386

 # intrepid (games): classic text-based MUD client [universe]
 1.98.2-1: amd64 i386

However i took version 1.98.2-1 and installed it on hardy, things seem to be working fine but I understand this is not the version supported by hardy, I dont want to open up security vulnerabilities or mess up my OS,
**could some please tell me why not TinTin 1.98.2-1 for Hardy Ubuntu?**

---

### Post by Oldsoldier2003 on 2008-06-08
> **animalprimate said:**
> i had some problems with the version of TinTin 1.97 (in Hardy)

apt-get install tintin++ gives you version 1.97

**this link:** 
[http://packages.ubuntu.com/search?keywords=tintin%2B%2B]("http://packages.ubuntu.com/search?keywords=tintin%2B%2B")

**provides this information:**
# hardy (games): classic text-based MUD client [universe]
 1.97.9-2: amd64 i386

 # intrepid (games): classic text-based MUD client [universe]
 1.98.2-1: amd64 i386

However i took version 1.98.2-1 and installed it on hardy, things seem to be working fine but I understand this is not the version supported by hardy, I dont want to open up security vulnerabilities or mess up my OS,
**could some please tell me why not TinTin 1.98.2-1 for Hardy Ubuntu?**

because when the distribution was finalized 1.97 was the current stable version. The repos get locked except for major security updates or stabilty updates that involve core components. If you want updated versions of games and etc you need to compile them or find binaries as these non essential bits are not maintained in the repos between versions.

---

### Post by animalprimate on 2008-06-08
well then I think TinTin++ 1.98.2-1 should continue to work fine with hardy.  thanks for the response, I'd just about giving up on waiting.

---

### Post by Oldsoldier2003 on 2008-06-08
> **animalprimate said:**
> well then I think TinTin++ 1.98.2-1 should continue to work fine with hardy.  thanks for the response, I'd just about giving up on waiting.

There shouldn't be any problems. Since hardy is a LTS you will find yourself either sticking with older versions of software or compiling your own latest versions if you decide to stick with it. Intrepid will have newer and more up to date versions of almost everything when it is released in October.

---

### Post by spiderbatdad on 2008-06-08
Have you checked out kildclient...I would recommend it over tintin++

---

### Post by DirtDawg on 2008-06-08
> **animalprimate said:**
> well then I think TinTin++ 1.98.2-1 should continue to work fine with hardy.  thanks for the response, I'd just about giving up on waiting.

Hey, just download the Linux 1.9.2 pre-compiled binary from the [tintin++ website]("http://tintin.sourceforge.net/download.php") and extract it. Then use the terminal to run the "tt++" file. It works great and you don't need to install it. I believe it is perfectly secure to use in this way.



> **spiderbatdad said:**
> Have you checked out kildclient...I would recommend it over tintin++

I've never even heard of this client. Even if I did, I would have thought it was a KDE app! Who decides to call a gtk+ a name that starts with "K"? :o

Anyways, any reason you would recommend kildclient to tintin++? Perhaps the GUI makes it a little easier, or is it more than that?

---

### Post by spiderbatdad on 2008-06-08
> **DirtDawg said:**
> Hey, just download the Linux 1.9.2 pre-compiled binary from the [tintin++ website]("http://tintin.sourceforge.net/download.php") and extract it. Then use the terminal to run the "tt++" file. It works great and you don't need to install it. I believe it is perfectly secure to use in this way.

. 



I've never even heard of this client. Even if I did, I would have thought it was a KDE app! Who decides to call a gtk+ a name that starts with "K"? :o

Anyways, any reason you would recommend kildclient to tintin++? Perhaps the GUI makes it a little easier, or is it more than that?



kildclient is in synaptic package manager. It runs perfectly on gnome. It is written with the GTK windowing toolkit. The gui is good...but the perl interpreter is what makes it better than tintin++

Has a lot of great built-in functions.

I guess it's a matter of what you get used to

---

### Post by DirtDawg on 2008-06-08
> **spiderbatdad said:**
> kildclient is in synaptic package manager. It runs perfectly on gnome. It is written with the GTK windowing toolkit. The gui is good...but the perl interpreter is what makes it better than tintin++

Has a lot of great built-in functions.

I guess it's a matter of what you get used to

Cool. I don't actually know Perl, but I'll still give this client a shot. I'll likely stick with tintin (because I've already taken the time to learn the ins and outs), but I'm happy to know there's a GUI alternative besides the defunct gnome-mud.

---

