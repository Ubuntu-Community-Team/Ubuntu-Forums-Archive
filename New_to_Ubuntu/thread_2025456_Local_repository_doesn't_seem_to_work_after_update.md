---
title: "Local repository doesn't seem to work after update"
date: 2012-07-14
forum: New to Ubuntu
---

### Post by mr.akik on 2012-07-14
Hi,
I'm using ubuntu12.04. 
I've created a local offline repository this way:

sudo mkdir -p /usr/local/mydebs
sudo cp /var/cache/apt/archives/*.deb /usr/local/mydebs
cd /usr/local/mydebs
dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz

Then I added this line on /etc/apt/sources.list file :
deb file:/usr/local/mydebs ./

Then I update repository using this command:
sudo apt-get update

I can easily install my previously downloaded packages using apt-get.
But after I use this command with internet connection :
sudo apt-get update
, my local repository doesn't seem to work.
For example :
 I have all the dependencies of the package "wammu" in my local source
(/usr/local/mydebs).
But when I try to install wammu with "sudo apt-get install wammu" command,
it says I've to download 12.5 mb, but I have those packages in my /usr/local/mydebs
directory that it wants to download.
I can now understand that apt-get is using the other mirrors like multiverse, universe,
main etc before it checks my local mirror.
Please tell me how can I make apt-get to use my local repository at first.
I actually want apt-get to install the existing files first and if necessary it should bring
 packages from internet.
Thanks in advance.

---

### Post by Cheesehead on 2012-07-14
I use the apt-move package to do the same thing.

I don't see where your manual method is organizing the packages in the directory structure expected by apt-get. Happily, apt-move does that automatically, too.

---

### Post by mr.akik on 2012-07-15
> **Cheesehead said:**
> I use the apt-move package to do the same thing.

I don't see where your manual method is organizing the packages in the directory structure expected by apt-get. Happily, apt-move does that automatically, too.
Thank you Cheesehead. But this is not my solution. Please read the thread and give me a solution.

---

### Post by Cheesehead on 2012-07-15
Well, if you insist: You must create a folder structure in your local repository.

For example, you're putting packages at /usr/local/mydebs/packagename
apt-get expects to find packages at /usr/local/mydebs/pool/main/p/packagename

To see the file structure apt-get expects to find within a mirror for the (example) *hello* package:
```
$ apt-cache show hello | grep Filename
Filename: pool/main/h/hello/hello_2.7-1_i386.deb
```

---

### Post by mr.akik on 2012-07-15
> **Cheesehead said:**
> Well, if you insist: You must create a folder structure in your local repository.

For example, you're putting packages at /usr/local/mydebs/packagename
apt-get expects to find packages at /usr/local/mydebs/pool/main/p/packagename

To see the file structure apt-get expects to find within a mirror for the (example) *hello* package:
```
$ apt-cache show hello | grep Filename
Filename: pool/main/h/hello/hello_2.7-1_i386.deb
``` Does it mean that the directory structure of my repository should be /usr/local/mydebs/pool/main/p/ 
rather than /usr/local/mydebs/ ?
Did I get you?
I made the directory stucture like:
/usr/local/mydebs/pool/main/p/ and copied the packages inside the "p" folder.
Then I added this line to /etc/apt/sources.list:
deb file:///usr/local/mydebs/pool/main/p /

But it didn't work.

---

