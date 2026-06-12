---
title: "Having trouble installing and updating software in 14.04 LTS"
date: 2017-01-15
forum: New to Ubuntu
---

### Post by samrocks204 on 2017-01-15
Hi, this is my first post to the forums and I hope it will be a big help. I'm relatively new to Ubuntu and while I have run into problems before I have been able to consult forums for answers. This issue is a bit different. I have found dozens of other people with my problem and about 6 different ways it has been solved but nothing has worked up to this point and so I need to ask for help.

Yesterday I tried to download GUFW from the software center only to get this error message 
```

Failed to download repository information
Check your internet connection

Details:
E:GPG error: http://srchive.canonical.com trusty InRelease: Clearsigned file isn't valid, got 'NODATA' (does the network require authentication?)


```

I used to get a message telling me that my download included untrusted packages and gave me the options "ok" and "repair", neither of which did anything. After trying some of the fixes on this forum for similar issues I no longer recieve this message but I couldn't tell you which one it was.

I've seen most people with this issue asked right off the bat to post the messages given after entering
```

sudo apt-get update

```
this into the terminal and this is what I get
```

Hit http://repo.steampowered.com precise InRelease
Get:1 http://srchive.canonical.com trusty InRelease                            
96% [1 InRelease gpgv 318 B] [Waiting for headers] [Waiting for headers] [ConneSplitting up /var/lib/apt/lists/partial/srchive.canonical.com_dists_trusty_InRele
Hit http://repo.steampowered.com precise/steam Sources                         
Ign http://srchive.canonical.com trusty InRelease                              
Hit http://security.ubuntu.com trusty-security InRelease                       
E: GPG error: http://srchive.canonical.com trusty InRelease: Clearsigned file isn't valid, got 'NODATA' (does the network require authentication?)

```

Thanks in advance!

---

### Post by santosh83 on 2017-01-15
Shouldn't those entries be archive.canonical.com instead of srchive.canonical.com?

---

### Post by TheFu on 2017-01-15
Looks like your /etc/apt/sources.list are mixed between 2 different releases.  Clean that up. If that file doesn't look odd, mixed, then the repo could be the issue. Try other repos (sorry, don't know how to do that) - perhaps do an install into a VM and choose a nearby country that isn't your own? 

I would use whatever is in /etc/lsb-release as the truth about which version you have installed.

Could the steam installer have screwed things up?

---

### Post by samrocks204 on 2017-01-19
> [COLOR=#000000] perhaps do an install into a VM and choose a nearby country that isn't your own? [/COLOR]

I have just installed VirtualBox but have never worked with VM's. I assume I will need to install an OS into it. Does it make a difference what I install into VirtualBox?

---

### Post by wildmanne39 on 2017-01-19
Hello, if you need help with virtualbox please start a thread in virtualisation, we only allow one topic per thread there is less confusion that way and when people search for a topic they will actually find that topic and not another.
Thanks

---

### Post by TheFu on 2017-01-19
The point of installing into a VM would be to use the same version of the OS to get a new /etc/apt/sources.list from a different country. That would be all.

Thinking about it more today, I'd just do some googling and find the repos in a nearby country.  Or if you just posted where you were, someone here might know the answer for the repos nearby.  

Then just edit the list with the new URLs.

---

