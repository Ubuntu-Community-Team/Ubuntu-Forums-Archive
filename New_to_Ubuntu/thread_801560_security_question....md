---
title: "security question..."
date: 2008-05-20
forum: New to Ubuntu
---

### Post by lunaluna on 2008-05-20
if i create a second account just for the p2p networks,torrents generally filesharing would that be any good or it doesn't matter..?

---

### Post by shifty_powers on 2008-05-20
in what way? what are you worried about? there are no linux virus to speak of...

---

### Post by akiratheoni on 2008-05-20
> **lunaluna said:**
> if i create a second account just for the p2p networks,torrents generally filesharing would that be any good or it doesn't matter..?

As far as I know, there's no need to do so, as there aren't really any viruses that you can be affected by.

---

### Post by lunaluna on 2008-05-20
because i use this computer for the most my internet activities... i'd like to be a bit prepaired
and..i'm not worried about virus :) but open ports...and whatever follows..
also i'm a newbe so any info would be appriciated

---

### Post by Paqman on 2008-05-20
There's no real need. Your default account does have administrative rights, but they aren't active unless they being used. That means malicious code can't execute without your specifically allowing it.

Creating a second more limited account is a good idea for Windows, but it's not necessary for Linux. Our default setup has all the security you'll need.

---

### Post by shifty_powers on 2008-05-20
heh read about a hacking competiton they had recently, the mac got hacked a few minutes into the second day, thanks to a safari exploit, the windows machine fell soon after, and the ubuntu 7.10 machine was still perfectly ok after 6 days ;)

---

### Post by Paqman on 2008-05-20
[True](http://dvlabs.tippingpoint.com/blog/2008/03/28/pwn-to-own-final-day-and-wrap-up)

[/smug Linux elitist]

---

### Post by lunaluna on 2008-05-20
yeah! :) i have already read it somewhere...
but although it's safe,assuming that might happen,if i create a second account would it be any good?

---

### Post by HermanAB on 2008-05-20
The second account is no different from the first one.

The 'open ports' scare is primarily a Windows thing.  There are usually many undocumented listeners in a Windows system.  The resulting defense against that was the 'firewall' craze, which was an attempt to plug the holes in Windows by adding a separate band-aid to the network.  In a Linux system, you can easily tell exactly what is listening where and consequently you don't need any band-aids.  

If it was otherwise, then your firewall would need a firewall, which would need a firewall, which...

So, in short, relax and enjoy your new found freedom.

---

### Post by lunaluna on 2008-05-20
> **HermanAB said:**
> In a Linux system, you can easily tell exactly what is listening where and consequently you don't need any band-aids.  

If it was otherwise, then your firewall would need a firewall, which would need a firewall, which...

So, in short, relax and enjoy your new found freedom.

ok how can i tell exactly what's listening and what not when i downloading torrents i'll have thousands of connections...?
and the second account which will be made just for torrents is just in case not affecting the data on the first one..but does it worth it(in a paranoid level lol)  ?

---

### Post by Paqman on 2008-05-20
> **lunaluna said:**
> 
and the second account which will be made just for torrents is just in case not affecting the data on the first one..but does it worth it(in a paranoid level lol)  ?

There's nothing to be gained, really.

Each user has privileges allowing them to make changes to their own /home directory, and any data contained there. Any user that is an admin can also temporarily take on privileges that allow them to make changes to the rest of the system, by providing their password.

So your second user could still mess up their own /home, just like the first could. Neither could mess up the system itself, unless you allowed them to.

---

### Post by lunaluna on 2008-05-20
> **Paqman said:**
> There's nothing to be gained, really.

Each user has privileges allowing them to make changes to their own /home directory, and any data contained there. Any user that is an admin can also temporarily take on privileges that allow them to make changes to the rest of the system, by providing their password.

So your second user could still mess up their own /home, just like the first could. Neither could mess up the system itself, unless you allowed them to.

so what about blacklists...there must be for some reason...don't they?

---

### Post by spiderbatdad on 2008-05-20
you can create a user account that has a restricted shell or no shell, that would probably make any rootkit  ineffective.

Something like this I believe:
```
useradd -d /home/<user> -m -s /bin/false
```
or:
```
useradd -d /home/<user> -m -s /sbin/nologin
```
This account could only be accessed through root.
...another reason root passwd (sudo su) should not be used, as hackers know root exists. To get into your user account not only does a password have to be know, but the user's account name as well. Avoid publishing your username.

---

### Post by 3rdalbum on 2008-05-20
The vast majority of open ports occur through processes running as either "root" or "nobody", not running as a user. So logging in as a different user will not lessen the number of open ports you have. If you're worried, you could just make a different account to "Switch User" into.

---

### Post by lunaluna on 2008-05-21
> **spiderbatdad said:**
> you can create a user account that has a restricted shell or no shell, that would probably make any rootkit  ineffective.

Something like this I believe:
```
useradd -d /home/<user> -m -s /bin/false
```
or:
```
useradd -d /home/<user> -m -s /sbin/nologin
```
This account could only be accessed through root.
...another reason root passwd (sudo su) should not be used, as hackers know root exists. To get into your user account not only does a password have to be know, but the user's account name as well. Avoid publishing your username.

so if i create a second user account with one oh these commands i should be ok...as for the user privileges what should they be(newbee)?

---

### Post by spiderbatdad on 2008-05-21
> **lunaluna said:**
> so if i create a second user account with one oh these commands i should be ok...as for the user privileges what should they be(newbee)?

No. I was making a suggestion as just another step in your security efforts. The saying, I believe, goes something like this: "The only totally safe computer is the one that isn't powered on."

My suggestion was more or less an idea of downloading your torrents to a folder owned by a non privileged user. IDK if it would really work. I do a similar thing with apache in an effort to prevent anyone gaining a shell via my webserver, but of course it isn't foolproof. I accept a certain amount of risk by connecting to the www.
Maybe this security article would interest you:[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

