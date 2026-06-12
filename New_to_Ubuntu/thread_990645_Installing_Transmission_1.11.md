---
title: "Installing Transmission 1.11"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by h8uthemost on 2008-11-22
I made a thread here a while ago on how to install the alpha build of Seamonkey in Ubuntu, so since it's not in the synaptics, and there isn't a .deb. And I don't really know how to start .tarz.

So I'm hoping someone can give me the commands of how to install Transmission 1.11 through Terminal. I've searched for commands on how to do it, but didn't really find anything.

If anyone knows the commands on how to install 1.11, I'd really appreciate it.

Thank you.

---

### Post by ITAndrew on 2008-11-22
Un-tar the file

tar -zxvf yourfile.tar.gz

cd yourextracteddir

---READ THE README or INSTALL file---

or

./configure
then
make
then
sudo make install

Should be good to go.

---

### Post by h8uthemost on 2008-11-22
Yeah, I tried all that and I'm getting all kinds of bash and syntax errors. Not sure what to do.

Thanks anyways.

---

### Post by ITAndrew on 2008-11-22
just curious, why are you tring to install an old version of transmission?

You may be missing tools or dependencies required to buid from source. You may want to install 

sudo apt-get install build-essential

this meta-package installs many tools required to build binarys from source.

---

### Post by h8uthemost on 2008-11-22
I'm installing the older version because a couple of private torrent sites that I use are no longer accepting any Transmission version past 1.11, because the newer version are having trouble accepting a hand shake with these trackers. So they've banned these newer version. And...I get my fastest upload speeds with Transmission, so I don't really want to switch to any other client(I've tried Deluge and KTorrent in Linux already).

I do however finally come across [this](http://www.myscienceisbetter.info/2008/04/how-to-install-latest-transmission-bittorrent-client-ubuntu-hardy.html). The site says to use this command:

tar xvjf transmission-1.11.tar.bz2
cd transmission-1.11
./configure --prefix=/usr && make -s
sudo make install

Which I did, and it went through the building process. But then terminal finally gets to Make Install, and it just sits there. So I hit Enter, and Terminal asks for my password. So I give the password, hit Enter again, and the Terminal gives me this error:

*** No rule to make target `install'.  Stop.

And then that's it. So I'm not sure what to do then.

---

### Post by Ryadt on 2008-11-23
Just make sure that you have got build-essential installed.

---

### Post by h8uthemost on 2008-12-06
Can you tell me what build essential installed is?

Ok, this is from the Readme from Transmission 1.11:

Building a Transmission release from the command line:

    $ tar xvfj transmission-1.0.tar.bz2
    $ cd transmission-1.0
    $ ./configure -q && make -s
    $ su (if necessary for the next line)
    $ make install

I get trouble after entering ./configure.(if I enter /configure -q && make -s I get some messed up error).

Now, looking through the Install.txt that came with Transmission 1.11, it says the basic commands are cd, ./configure, make, and make install.

So, doing the cd and ./configure commands everything goes fine. I run into trouble when I try the make command(I even tried sudo command). This is the error after I type in make:

make: *** No targets specified and no makefile found.  Stop.


Can someone please tell me what that means?

Thank you.

---

### Post by rev0lv3r on 2008-12-06
Why do you want to use 1.11?
It's such an old version

1.41 beta 2 is either out, or coming out very soon
1.40 is out stable.

Many improvements.

---

### Post by h8uthemost on 2008-12-06
Because of the private trackers do not allow the newer versions because they have a problem making a handshake with the tracker.

And I need Transmission because I get the fastest upload speeds with. I've tried Deluge and KTorrents, and the speeds aren't as fast as Transmission.

---

### Post by rev0lv3r on 2008-12-06
Is that a bug that you have reported to the Transmission developers?

It's something that sounds uncommon, perhaps the admins of the private trackers need to take a look at Transmission 1.40 once more.

1.11 is VERY old.

---

### Post by h8uthemost on 2008-12-06
*double*

---

### Post by h8uthemost on 2008-12-06
Yeah, I've already reported to the devs. But who knows if something comes of it. And I don't really care if it's old. Every single private tracker allows 1.11, so it must be good. And as long as I get the same speeds as I do with the newer versions I'll be happy. And it's not just the admins of the tracker that saw it, everyone on the tracker that used 1.40(or the one before it) couldn't become connectible to the tracker.

So can anyone tell me what the error: make: *** No targets specified and no makefile found. Stop. means? I get this right after I input the 'make' command.

---

### Post by xjcannonx on 2008-12-06
Get it working yet?

---

### Post by h8uthemost on 2008-12-06
Nah, still got the same problem. And I also get this same problem when trying to install KTorrent 2.2.8.

I guess that error means something like makefile can't be found, but there are makefiles in the folders.

---

### Post by rev0lv3r on 2008-12-06
> **h8uthemost said:**
> Nah, still got the same problem. And I also get this same problem when trying to install KTorrent 2.2.8.

I guess that error means something like makefile can't be found, but there are makefiles in the folders.

Pastebin the stuff

I still don't understand why you are using 1.11 rather than 1.22 or 1.34?

---

### Post by h8uthemost on 2008-12-06
I have told you already why I'm using 1.11. Twice actually. And I posted it when I first made this thread a week ago. So three times so far I have said why I'm wanting to use 1.11. I really don't see what's not to understand. One of my favorite private lossless music trackers only allow 1.11(this is my fourth time now), there's no way I can't get around it. Trust me, if I could use 1.22 or 1.34...I would. But I can't.

I'll just ask my question elsewhere as I don't want to keep explaining my reason over and over and...

But thank you.

---

### Post by zvacet on 2008-12-06
In terminal go to the directory where Transmission is and type 

```
sudo apt-get build-dep transmission
```

If that doesn´t give you all dependencies you need read [this.]("http://trac.transmissionbt.com/wiki/Building#OnUnix") You will find there commands how to compile too.

---

### Post by h8uthemost on 2008-12-07
Thank you zvacet. When I typed that into Terminal, this is what I get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libcurl-dev is a virtual package provided by:
  libcurl4-openssl-dev 7.18.2-1ubuntu4
  libcurl4-gnutls-dev 7.18.2-1ubuntu4
You should explicitly select one to install.
E: Package libcurl-dev has no installation candidate
E: Failed to satisfy Build-Depends dependency for transmission: libcurl-dev

---

### Post by zvacet on 2008-12-08
> For Ubuntu users wanting to build Transmission from source code, the build dependencies are reportedly satisfied by this list of packages:

build-essentials
automake
autoconf
libtool
pkg-config
libssl-dev
libcurl4-openssl-dev
intltool
libxml2-dev 
libgtk2.0-dev
libnotify-dev

Taken from [here]("http://forum.transmissionbt.com/viewtopic.php?f=13&t=5604&sid=f3a8bb852f6a7e8acf9ae02272e54dd7#p31095") and it worked for me.

---

