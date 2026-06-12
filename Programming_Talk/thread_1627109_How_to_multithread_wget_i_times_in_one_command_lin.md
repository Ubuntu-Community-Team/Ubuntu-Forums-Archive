---
title: "How to multithread wget i times in one command line?"
date: 2010-11-21
forum: Programming Talk
---

### Post by amylase on 2010-11-21
Wget itself is not multithread but I can issue them serially linked up by & and with -N parameter to skip already existing files eg:

wget -r -N [http://www.example.com](http://www.example.com) &
wget -r -N [http://www.example.com](http://www.example.com) &
wget -r -N [http://www.example.com](http://www.example.com)

This should start up 3 simultaneous processes that are complementary to each other.

Suppose I want to issue 10 processes. Rather than doing the above ten times (link up ten wget with nine &), what's a neater way of issuing the command in command line with variable i where i is the number of simultaneous processes?

I tried for and do but that didn't work. What happened was one wget would start and then finish, and then next wget starts and then finish so on.

So my question is, how do I issue one line of command in Linux shell to achieve this effect:

wget -r -N [http://www.example.com](http://www.example.com) &
wget -r -N [http://www.example.com](http://www.example.com) &
.
.
.
wget -r -N [http://www.example.com](http://www.example.com)


Where the parameter i in the one line command specifies how many repeats.

Thanks.

---

### Post by rbprogrammer on 2010-11-21
I'm going to go out here on a limb and say if wget doesn't provide the functionality to do that, then you will just have to write a wrapper for this functionality.

I'd probably write a small bash script like such:
```

#!/bin/bash

COUNT=10
for ((i=0; i<$COUNT; i++)) ; do
    wget -r -N http://www.example.com &
done

```

Obviously you can get more fancy and use arguments to make the script more generic.

---

### Post by MadCow108 on 2010-11-21
I guess you could use parallel (from moreutils package) for this

packaged parallel:
parallel wget -r -N -- url1 url2 url3 moreurls


edit:
just saw that the gnu parallel is not packaged in ubuntu, the parallel in moreutils is some much less capable program :(
but it should still do the job

gnu parallel:
[http://savannah.gnu.org/projects/parallel](http://savannah.gnu.org/projects/parallel)

---

### Post by unc0nn3ct3d on 2012-03-01
Yea, this was bugging me too.. found the solution here: [http://blog.netflowdevelopments.com/2011/01/24/multi-threaded-downloading-with-wget/](http://blog.netflowdevelopments.com/2011/01/24/multi-threaded-downloading-with-wget/)

---

### Post by Khayyam on 2012-03-03
Actually, I don't think this will improve things as the bottleneck isn't the client, wget will pull as much data and as fast the server, and bandwidth, can provide, '--child {n}' would be fairly easy to impliment, so it's most probably not a missing feature, but something the developers see no real reason to impliment.

best ... khay

---

### Post by ofnuts on 2012-03-03
> **Khayyam said:**
> Actually, I don't think this will improve things as the bottleneck isn't the client, wget will pull as much data and as fast the server, and bandwidth, can provide, '--child {n}' would be fairly easy to impliment, so it's most probably not a missing feature, but something the developers see no real reason to impliment.

best ... khay
Well, you are mistaken... from personal experience if you are getting a lot of small files starting several connections is a huge performance boost. I also believe this is what the Firefox config value network.http.max-connections-per-server is about.

---

### Post by Khayyam on 2012-03-03
> **ofnuts said:**
> Well, you are mistaken... from personal experience if you are getting a lot of small files starting several connections is a huge performance boost. I also believe this is what the Firefox config value network.http.max-connections-per-server is about.

In which case, I stand corrected. I wonder with the above however, if the overhead of '-N' will cause any improvement to negligible. I imagine a test with wget, a [multithreaded curl](http://curl.haxx.se/libcurl/c/multithread.html), and the above script might provide some insight.

best ... khay

---

### Post by MadCow108 on 2012-03-03
loading many small files in parallel will be faster when done in parallel if the server has enough bandwidth.
where you gain is the parallelizing of all the http/https handshakes which are mostly dominated by latency not bandwidth or server cpu.
for few larger files its likely to be less significant as you open less connections.

---

### Post by Khayyam on 2012-03-03
> **MadCow108 said:**
> loading many small files in parallel will be faster when done in parallel if the server has enough bandwidth. where you gain is the parallelizing of all the http/https handshakes which are mostly dominated by latency not bandwidth or server cpu. for few larger files its likely to be less significant as you open less connections.

I see. In which case wouldn't the OP, nay, us all, be better off using [axel](http://wilmer.gaa.st/main.php/axel.html), [aget](http://www.enderunix.org/aget/), [aria](http://aria2.sourceforge.net/) or [mulk](http://sourceforge.net/projects/mulk/) in such instances.

I tend to use wget out of habit, and familiarity, and never really need anything more than it offers, but right tool for the job and all that ...

best ... khay

---

### Post by MadCow108 on 2012-03-03
> **Khayyam said:**
> I see. In which case wouldn't the OP, nay, us all, be better off using [axel](http://wilmer.gaa.st/main.php/axel.html), [aget](http://www.enderunix.org/aget/), [aria](http://aria2.sourceforge.net/) or [mulk](http://sourceforge.net/projects/mulk/) in such instances.

I tend to use wget out of habit, and familiarity, and never really need anything more than it offers, but right tool for the job and all that ...

best ... khay

no those solve a different problem, downloading large files at full speed when the server limits the per connection speed.
parallelizing wget has the goal of decreasing the effect of latency and roundtrips, a problem which is insignificant for large files.

---

### Post by Khayyam on 2012-03-03
> **MadCow108 said:**
> no those solve a different problem, downloading large files at full speed when the server limits the per connection speed.
parallelizing wget has the goal of decreasing the effect of latency and roundtrips, a problem which is insignificant for large files.

I see, I wonder then why its not a feature of wget, curl will now multithread. Actually, when looking for any discussion of the subject on the wget mailing list I stumbled upon [pwget.py]("http://grand-prismatic.blogspot.com/2011/09/multithreaded-downloading-with-wget.html") a python wrapper for multithreading (or psudo-threading) wget, maybe a better method than the above as it provides switches (--max-num-thread --sleep).

best ... khay

---

