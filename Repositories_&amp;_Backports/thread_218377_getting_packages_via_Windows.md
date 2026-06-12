---
title: "getting packages via Windows"
date: 2006-07-18
forum: Repositories &amp; Backports
---

### Post by mikesorrelle on 2006-07-18
Is there a Web utility for recursively getting packages?

I'm working in a restrictive environment, and my Ubuntu box does not have an Internet connection, so I can't simply do an apt-get to pull down all the packages that a higher-level package is dependent upon.
But right beside it, I have a Windows box that DOES have an Internet connection, and so far, I've been using the manual process of pulling down packages from packages.ubuntu.com, and copying it/them to a thumb drive for transport to the Ubuntu box.
But that puts me in "dependency hell"  ](*,) when trying to install it, only to discover that package A needs package B, which needs package C, which needs .... ad nauseum.
Yes, the page for each package lists what other packages it is dependent upon, but that requires a lot of either: a) looking back and forth to see if those are already installed or not, or b) downloading many packages needlessly.

So is there a web site (or Windows utility) that allows simply specifying the top-level package you need, and it recursively generates a single list (or even better, a collection, suitable for zip/tar'ing) of all the needed packages?

aTdHvAaNnKcSe (thanks in advance),
Mike

---

### Post by mikesorrelle on 2006-07-27
I guess the answer is no, since there were no replies? :confused: 

Did I post this in the wrong forum?
Would "Installation & Upgrade" be better?

---

### Post by aysiu on 2006-07-27
I think the best thing to do is get this:
[https://ubuntuplus.bountysource.com/](https://ubuntuplus.bountysource.com/)

Or... use a Ubuntu live CD on your computer with a faster connection. Let's say you wanted to install *alien*, *kword*, and *epiphany*.

Boot up the live CD on the Windows computer. Then go to the terminal and type in ```
sudo apt-get clean
sudo aptitude update
sudo aptitude install kword epiphany-browser alien
``` Then go to /var/cache/apt/archives and copy all the .deb files to a USB key or iPod or some external drive.

Then copy those .deb files to the other computer's desktop and then ```
cd ~/Desktop
sudo dpkg -i *.deb
```

---

### Post by mikesorrelle on 2006-07-27
Cool!  I hadn't thought of using the Live CD like that.
And the add-on CD is a great idea I wasn't aware of.
Thanks!!

---

### Post by SoftGround on 2006-07-31
You may need to watch out for proxy problems (set http_proxy to include any username and password).

**Synaptic**
You can also use synaptic on the live CD. This will work out the dependencies for you. 

Synaptic has an option to create a download script (it uses wget).  You can then download the debs onto a memory key.
If a wget download fails it will retry but rename the filename, so check for *.deb.1 etc or you may be using broken files.

You cannot create the script on your local machine as you cannot do a successful apt-get update without a connection.

**Installing**
To install them on your Ubuntu machine you can either just add them one by one or you can make a local repository by putting them all in a sutable folder and running scanpackages to create an index to them.  Do not create sub-folders as it is not sophisticated enough for that.

```
dpkg-scanpackages ./ /dev/null | gzip > Packages.gz
```
You then need to put the local folder in your
etc/apt/sources.list  e.g. (but use your location)

```
deb file:/hda3/packages/dapper/ ./
```
Then do sudo apt-get update and start synaptic.  It will load the files from the local repository instead of from the internet when you try to install them.

---

