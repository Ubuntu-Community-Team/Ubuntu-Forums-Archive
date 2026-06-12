---
title: "[ubuntu] Red Triangle -- &quot;The update information is outdated&quot;"
date: 2013-04-01
forum: New to Ubuntu
---

### Post by jimafternoon on 2013-04-01
Hello, 

I'm running 12.10 64bit. I've recently had a red triangle appear on the top taskbar indicating that I need updates, however, when I click on 'show updates', it says everything is up to date. 

When I run 'sudo apt-get update'  I get these error messages:

```
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                              
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                       
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                        
  404  Not Found

 W: Failed to fetch [http://ppa.launchpad.net/thomas.tsai/ubuntu-tuxboot/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/thomas.tsai/ubuntu-tuxboot/ubuntu/dists/quantal/main/source/Sources)  404  Not Found  
 

 W: Failed to fetch [http://ppa.launchpad.net/thomas.tsai/ubuntu-tuxboot/ubuntu/dists/quantal/main/binary-amd64/Packages](http://ppa.launchpad.net/thomas.tsai/ubuntu-tuxboot/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found  
 

 W: Failed to fetch [http://ppa.launchpad.net/thomas.tsai/ubuntu-tuxboot/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/thomas.tsai/ubuntu-tuxboot/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found  

```

I've looked around for similar threads, but nothing seems to come up for these specific errors. Any suggestions?  I remember having to do the following to get skype to work on my computer, do you think it could be related?


In some cases similar problems of other people have turned out to be caused by a mis-configuration of the package management system related to multiarch support.

Please issue the following commands and copy/paste all output:

```
dpkg --print-foreign-architectures
dpkg --print-architecture
```

If the first comand does not show any output, and the second one gives "amd64" you shouly try the following commands
```

sudo dpkg --add-architecture i386
sudo apt-get update
```

and then again

```
sudo apt-get install skype
```


Thanks for any help!

---

### Post by jimafternoon on 2013-04-01
Hmmm, right after I posted this the red triangle disappeared. Thoughts?

---

### Post by Bashing-om on 2013-04-01
jimafternoon;

Maybe the mirror was down or all paths busy or major leg on the path down ??
[INDENT=3]
alls well that ends well

[/INDENT]

---

### Post by alphacrucis2 on 2013-04-01
The ppa you are using doesn't have any quantal packages which is what is causing the 404 (not found error). Probably means the maintainer isn't bothering to keep it up to date.

[https://launchpad.net/~thomas.tsai/+archive/ubuntu-tuxboot](https://launchpad.net/~thomas.tsai/+archive/ubuntu-tuxboot)


As you can see there are only packages for up to precise pangolin. Not really anything to do with the main problem you had.

---

### Post by jimafternoon on 2013-04-01
Ok, thanks.  I'm not sure how, when, or why that ppa is installed. Is that something that I would have done? I've had a few issues and tried a lot of different things, I honestly don't remember at this point. :oops:

---

### Post by jimafternoon on 2013-04-01
Hmm, the red triangle came back again.

---

### Post by sandyd on 2013-04-01
You can remove the ppa from
Software Center -> Edit -> Software Sources -> Other Sources tab
Just remove the checkmark beside both entries that start with [http://ppa.launchpad.net/thomas.tsai/ubuntu-tuxboot/](http://ppa.launchpad.net/thomas.tsai/ubuntu-tuxboot/)

---

### Post by jimafternoon on 2013-04-01
Thanks, I just did that and then ran 'sudo apt-get update'. No errors showed up and the red triangle disappeared. \\:D/

---

### Post by minhook on 2013-04-17
> **jimafternoon said:**
> Thanks, I just did that and then ran 'sudo apt-get update'. No errors showed up and the red triangle disappeared. \\:D/

me tooo.

---

