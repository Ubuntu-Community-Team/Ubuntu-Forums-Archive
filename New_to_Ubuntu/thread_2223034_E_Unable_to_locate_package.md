---
title: "E: Unable to locate package"
date: 2014-05-09
forum: New to Ubuntu
---

### Post by Sieistelise on 2014-05-09
Hello there, 

I am a begginer also, whom is getting this 
```

sudo apt-get install -y grive-tools
"E: Unable to locate package"

```
 while I try to install Google Drive Grive. 
The reason is bc there is a Repository not well installed, related to tor, which I havent been able to install succesfully. 

Why I cant install other packages if this erpository has nothing to do with Grive? 
Also, I have to say I need to know the exact syntax to install a repository as I add it twice, 
one with <precise> (my system) and another without. 

This is the other answer I got, and why, I understood , that probaly, is Tor Repositry what is cousing this problem: (?) 
```

sudo apt-get update
Fetched 5,378 B in 6s (778 B/s)  
                                             
W: Failed to fetch http://deb.torproject.org/torproject.org/dists/<precise>/main/source/Sources  404  Not Found [IP: 82.195.75.101 80]

W: Failed to fetch http://deb.torproject.org/torproject.org/dists/<precise>/main/binary-amd64/Packages  404  Not Found [IP: 82.195.75.101 80]

W: Failed to fetch http://deb.torproject.org/torproject.org/dists/<precise>/main/binary-i386/Packages  404  Not Found [IP: 82.195.75.101 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.


```

```

cat /etc/apt/sources.list
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://cran.rstudio.com//bin/linux/ubuntu precise/
deb-src http://cran.rstudio.com//bin/linux/ubuntu precise/
deb http://deb.torproject.org/torproject.org <precise> main
deb-src http://deb.torproject.org/torproject.org <precise> main
deb-src http://deb.torproject.org/torproject.org precise main

```

Thanks!
I am a precise Ubuntu 13.10

---

### Post by LastDino on 2014-05-09
Out of curiosity, what does that ''-y'' in your first command does?

You can use this to install grive tool

> sudo add-apt-repository ppa:thefanclub/grive-tools
sudo apt-get update
sudo apt-get install grive-tools


About the 2nd one, I dunno. I've very little to no knowledge of commands myself so let someone else help you.

---

### Post by ian-weisser on 2014-05-09
> **Sieistelise said:**
> Why I cant install other packages if this erpository has nothing to do with Grive? 


Because dpkg keeps track of your install/uninstall preferences, and apt uses those preferences when it's calculating the order of a set of installs/uninstalls.

For example, if you try (and fail) to install grive-tools, dpkg remembers that you want to install it.
So every time you start a package manager, apt tries to calculate that install again...and fails again for the same reason.
That failure is usually a critical error, and prevents apt from telling dpkg to do anything else.

Sometimes you can keep doing other package installs/uninstalls/updates. It depends on the package, the type of error, and if anything depends on the broken package.

---

### Post by buzzingrobot on 2014-05-09
Doublecheck those Tor URL's in your sources list.  There shoud be no brackets around "precise".  I.e., don't use "<precise>".  There is no directory on that server called "<precise>". There is a directory called "precise". The '404' is telling you that the target directory is not there.

If you copied-and-pasted entries from somewhere, try again but edit out any brackets.

You can modify your list of software sources in the Software and Updates tool or in the Software Center app. You can also edit your sources list directly. It's /etc/apt/sources.list.  You'll need to use sudo to launch your editor.

The "-y" option tells apt-get that the answer to any questions it might ask you before doing an install is automatically "yes".  I like to know what's going to happen before I let it happen, so I seldom use it.

---

### Post by einheitlix on 2014-05-09
**@Sieistelise**

You are facing two different problems here:
1. Your [FONT=Arial]sources.list[/FONT] is messed up; that is why you are getting those warnings when you try to do a [FONT=Arial]sudo apt-get update[/FONT].
2. You are trying to install the [FONT=Arial]grive-tools[/FONT] package, which presumably does not exist in any of the repositories your system is set up to use.

Those two problems are not related. Your assumption that problem 1 is causing problem 2 is presumably wrong. Let's fix them both.

**Solution to problem 1: Fixing your [FONT=Arial]sources.list[/FONT]**

Does your [FONT=Arial]sources.list[/FONT] really look like this?

```
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://cran.rstudio.com//bin/linux/ubuntu precise/
deb-src http://cran.rstudio.com//bin/linux/ubuntu precise/
deb http://deb.torproject.org/torproject.org <precise> main
deb-src http://deb.torproject.org/torproject.org <precise> main
deb-src http://deb.torproject.org/torproject.org precise main
```

Or did you omit something? Because it's horribly messed up. You do not even have the normal repositories, like [FONT=Arial]main[/FONT] or [FONT=Arial]restricted[/FONT], enabled. If that is indeed the case, you will have to add at least those back to the top of your file, otherwise you will not even be able to install or update normal Ubuntu-supported packages. Add these lines to the top:

```

deb http://archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://archive.ubuntu.com/ubuntu/ precise main restricted
deb http://archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ precise-updates main restricted

```

Next, the lines which you use to include the [FONT=Arial]extra[/FONT] repository are fine.

Next, the lines you used to add [FONT=Arial]R[/FONT] are ugly. I assume you followed the instructions from [http://cran.rstudio.com/bin/linux/ubuntu](http://cran.rstudio.com/bin/linux/ubuntu)?
Remove the double slashes. It's not really important, but while we're fixing your problems... i.e., you'll end up with:
```

deb http://cran.rstudio.com/bin/linux/ubuntu precise/
deb-src http://cran.rstudio.com/bin/linux/ubuntu precise/

```

Next, concerning your installation of [FONT=Arial]Tor[/FONT], I assume you followed the instructions from [https://www.torproject.org/docs/debian](https://www.torproject.org/docs/debian)?
When they use that [FONT=Arial]<DISTRIBUTION>[/FONT] string, they don't mean you should replace that with [FONT=Arial]<precise>[/FONT]; rather, they mean that you should replace that with [FONT=Arial]precise[/FONT]. Also you have one double entry. This is how it should actually look like:
```

deb     http://deb.torproject.org/torproject.org precise main
deb-src http://deb.torproject.org/torproject.org precise main

```

Btw I doubt that you'll actually need the [FONT=Arial]deb-src[/FONT] entry unless you want to build Tor yourself, but whatever...

Summing up, you should end up with a [FONT=Arial]sources.list[/FONT] like this:

```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ precise-updates main restricted

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

## R, see http://cran.rstudio.com/bin/linux/ubuntu/
deb http://cran.rstudio.com/bin/linux/ubuntu precise/
deb-src http://cran.rstudio.com/bin/linux/ubuntu precise/

## Tor, see https://www.torproject.org/docs/debian
deb     http://deb.torproject.org/torproject.org precise main
deb-src http://deb.torproject.org/torproject.org precise main

```

Save that in [FONT=Arial]/etc/apt/sources.list[/FONT], run [FONT=Arial]sudo apt-get update[/FONT], and report back.

**Solution to problem 2: Installing [FONT=Arial]grive-tools[/FONT]**

LastDino already explained what to do here. You will have to add the [FONT=Arial]thefanclub/grive-tools[/FONT] PPA in order to be able to install that package. That is, you have to run

```

sudo add-apt-repository ppa:thefanclub/grive-tools
sudo apt-get update

```

Only then will you be able to install [FONT=Arial]grive-tools[/FONT] via
```

sudo apt-get install grive-tools

```

Cheers!

---

### Post by Sieistelise on 2014-05-09
Thanks for your reply. 
Unfortunatelly I have tried again and this is the result:
```

sudo apt-get install -y grive-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package grive-tools

```

I am thinking that perhaps,  its bc I have another distribution?  

Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

I have add the repository using Terminal commands, I have edited using "sudo gedit /etc/apt/sources.list" and clean my list as [**[COLOR=#000000]einheitlix[/COLOR]**]("http://ubuntuforums.org/member.php?u=365786") suggested. 
When I go to my Synaptic Manager the sources are differnt and are not updated, even I have run "sudo apt-get update" and therefore when "sudo apt-get install -y grive-tools" retuns a 

```

E: Unable to locate package grive-tools

```

---

### Post by Sieistelise on 2014-05-09
Thanks for your reply. I have cleaned my source list, I followed your suggestions. Thanks a lot!
Unfortunatelly I have tried again and this is the result:
```

sudo apt-get install -y grive-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package grive-tools

```

I am thinking that perhaps,  its bc I have another distribution?  

Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

I have add the repository using Terminal commands, I have edited using "sudo gedit /etc/apt/sources.list" and clean my list as [**[COLOR=#000000]einheitlix[/COLOR]**]("http://ubuntuforums.org/member.php?u=365786") suggested. 
When  I go to my Synaptic Manager the sources are differnt and are not  updated, even I have run "sudo apt-get update" and therefore when "sudo  apt-get install -y grive-tools" retuns a 

```

E: Unable to locate package grive-tools

```

---

### Post by LastDino on 2014-05-09
What it is supported in 12.04.4 LTS. Check if the fanclub PPA is added and ticked or not in Software and Update centre under list called ''other software''.

---

### Post by buzzingrobot on 2014-05-09
The fanclub PPA doesn't list any Precise pacakges: [https://launchpad.net/~thefanclub/+archive/grive-tools](https://launchpad.net/~thefanclub/+archive/grive-tools).

---

### Post by LastDino on 2014-05-09
Pardon me, I should have been more clear. And yes, you're right. 
BUT 
If it is x64 it can work with it.
[http://www.thefanclub.co.za/content/how-install-grive-tools-ubuntu-1204-64bit](http://www.thefanclub.co.za/content/how-install-grive-tools-ubuntu-1204-64bit)

Unfortunately x32 doesn't work.

---

### Post by einheitlix on 2014-05-12
**@Sieistelise**

So, after cleaning yp your [FONT=Arial]sources.list[/FONT], did your first problem disappear? I mean this one:

```

sudo apt-get update
Fetched 5,378 B in 6s (778 B/s)  
                                             
W: Failed to fetch http://deb.torproject.org/torproject.org/dists/<precise>/main/source/Sources  404  Not Found [IP: 82.195.75.101 80]

W: Failed to fetch http://deb.torproject.org/torproject.org/dists/<precise>/main/binary-amd64/Packages  404  Not Found [IP: 82.195.75.101 80]

W: Failed to fetch http://deb.torproject.org/torproject.org/dists/<precise>/main/binary-i386/Packages  404  Not Found [IP: 82.195.75.101 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Secondly, concerning grive-tools, it is as buzzingrobot and LastDino indicated: it is not supported in 12.04 because of some missing dependencies, namely, json-c and yajl, whose provided versions in Ubuntu 12.04 are just too old for grive-tools.

Of course, you could manually upgrade those dependencies to more recent versions in order to be able to install grive-tools as explained in the article that LastDino linked to.
However, if you ask me, this approach has other drawbacks. For instance, if you manually install json-c and yajl from .deb files onto your system, these packages will not be managed by apt anymore, and therefore you will not receive potential security fixes to these packages (unless you install them manually, which would require you to manually keep an eye on their development). The same holds for the grive-tools: you will not receive any updates since you do not fetch them from a PPA, but rather install some .deb package.

The "cleaner" way might be to upgrade to Ubuntu "trusty" 14.04, if this is possible for you. This is also an LTS version (like Ubuntu "precise" 12.04), and it will be supported through April 2019:
[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

After upgrading to Trusty, you will be able to properly install grive-tools from the PPA, as you originally intended. If I were you, (and if you do not have other constraints that prevent you from upgrading to Trusty), this is what I would go for.

Cheers!

---

