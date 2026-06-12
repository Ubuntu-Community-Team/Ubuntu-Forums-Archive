---
title: "How to Open .tar.gz file?"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by Armaniboy on 2008-07-01
Hi,

  I have the hardest issue opening file that have an extension of .tar.gz. For example I wanted to download this free movie editing software called Open Movie Player. I downloaded it and the file name says:

openmovieeditor-0.0.20080523.tar.gz

How would I go about installing this program step by step through the terminal. I know it had to be easy, I've just never been able to get it right :(


Thank you,

Armaniboy

---

### Post by hyper_ch on 2008-07-01
it's a compressed file and you have frist to unpack it.

---

### Post by philinux on 2008-07-01
Just double click the file to start with and extract it. Remember zip files.

Then have a look for a read me file.

---

### Post by ChameleonDave on 2008-07-01
First of all, make absolutely sure that you need to install the program in that manner.  Have you tried looking for a DEB package first?  Ubuntu software comes in DEB packages.  You only use tar.gz when you can't find a DEB.

To open a gzipped tar archive, type this on the command line:

```

tar -zvxf openmovieeditor-0.0.20080523.tar.gz

```

Alternatively, you can use any of many graphical tools that handle such files.

---

### Post by iaculallad on 2008-07-01
You can use your terminal to unpack the archive:

```
tar -xvfz openmovieeditor-0.0.20080523.tar.gz
```

---

### Post by doorman on 2008-07-01
[This link]("http://ubuntuforums.org/showthread.php?p=5185023#post5185023") will probably reveal the answers you're looking for :)

cheers!

---

### Post by Archmage on 2008-07-01
Sorry, but isn't this in Ubuntu already? Can't you install it over the package manager?

---

### Post by philinux on 2008-07-01
If you read the sites documentation and look in synaptic you can install it from there. Simple

Or as the site says.

If you are working on Ubuntu Gutsy Gibbon(And Hardy), you can follow the following commands to install the latest Version of Open Movie Editor.

sudo apt-get install openmovieeditor
sudo apt-get build-dep openmovieeditor

The commands above install the Open Movie Editor and all the necessary dependencies for compiling it. Now you just need to download the latest Version of the Open Movie Editor and put the downloaded File in your Home Folder. Then follow those instructions:


tar xzf Desktop/openmovieeditor-*.tar.gz
cd openmovieeditor-*/
./configure --prefix=/usr
make
sudo make install

---

### Post by ChameleonDave on 2008-07-01
Why are you trying to compile the software from its source code if you don't know how?

Here is a page with Ubuntu DEB packages for this software:

[http://packages.ubuntu.com/search?keywords=openmovieeditor&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=openmovieeditor&searchon=names&suite=all&section=all)

Edit:  In fact, it's even available in the Ubuntu repositories.  Just install it using Synaptic, or type the following at the command line:

```
sudo apt-get install openmovieeditor
```

---

### Post by hyper_ch on 2008-07-01
> **philinux said:**
> tar xzf Desktop/openmovieeditor-*.tar.gz
cd openmovieeditor-*/
./configure --prefix=/usr
make
sudo make install
This won't work ;)

---

### Post by philinux on 2008-07-01
> **hyper_ch said:**
> This won't work ;)

Direct from there site. I'd just use apt-get.

---

### Post by hyper_ch on 2008-07-01
but it won't work... as he does not know what a .tar.gz is I doubt that he has installed and compiling tools and if they are lacking, you can't compile ;)

```

sudo apt-get install build-essential

```
is missing

---

### Post by Armaniboy on 2008-07-02
Thank you!! I got it to work using the sudo apt-get install command. :KS

---

### Post by Ian Clark on 2008-07-16
> **ChameleonDave said:**
> Why are you trying to compile the software from its source code if you don't know how?

The 2008 version is the only version I found to be reasonably functional, but its only included in the Intrepid repositories (not in Hardy's).  I think it's a reasonable question to ask: how do I install OME 2008 with all the dependencies into Hardy Heron?

---

### Post by a0u on 2008-07-16
One way is to simply download the deb file directly from [the repositories]("http://packages.ubuntu.com/intrepid/openmovieeditor").  However, because of potentially conflicting dependency versions, I would recommend that you either compile from source or wait until it is backported to Hardy.

---

### Post by ribe on 2011-09-14
example:
wget [http://www.foxsurfer.com/wordnet/wordnet.php.tgz](http://www.foxsurfer.com/wordnet/wordnet.php.tgz)
then:
tar ztvf wordnet.php.tgz

...for noobs..

---

### Post by nothingspecial on 2011-09-14
This thread is old

Thread closed

---

