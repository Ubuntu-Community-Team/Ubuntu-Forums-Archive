---
title: "Zip compression questions"
date: 2015-01-05
forum: New to Ubuntu
---

### Post by charleswb on 2015-01-05
I recently installed Ubuntu 14.04.1  An online Ubuntu enthusiast/semi-guru recommended to me that I install packages zip and unzip via the command line as follows:  sudo apt-get install zip unzip  What would be the benefit of installing those two packages? Doesn't Ubuntu already natively have the capability to zip and unzip files? Is there something I don't understand here?  Also, did I post this in the proper part of the forum for this type question? I'm new the the forum in the sense that I don't come here much. It's been years since I last came to this forum, and I haven't used Ubuntu in a while. I just returned to Ubuntu after briefly trying Windows 8.1.

---

### Post by sudodus on 2015-01-05
I think we want to be called 'enthusiasts' rather than 'semi-gurus' ;-)

There are many tools for compression and expansion of compressed single files and libraries of files. You can use ***file-roller***, which is a GUI front end, and you can use the command line tools directly. If you add command line tools, file-roller can also use those added tools (at least some of them, which have compatible interfaces).

I think the default installation contains enough tools for compression. But sometimes you get a compressed file, that you want to expand, and you have no tool for it. Then it is a good idea to install a tool that works for that kind of compressed file.

There could be other reasons for the recommendation: Did the online Ubuntu enthusiast also describe what to do or how to use zip and unzip? Some convenient way to work with compression and expansion of compressed files?

---

### Post by bab1 on 2015-01-05
> **charleswb said:**
> I recently installed Ubuntu 14.04.1  An online Ubuntu enthusiast/semi-guru recommended to me that I install packages zip and unzip via the command line as follows:  sudo apt-get install zip unzip  What would be the benefit of installing those two packages? Doesn't Ubuntu already natively have the capability to zip and unzip files? Is there something I don't understand here?  Also, did I post this in the proper part of the forum for this type question? I'm new the the forum in the sense that I don't come here much. It's been years since I last came to this forum, and I haven't used Ubuntu in a while. I just returned to Ubuntu after briefly trying Windows 8.1.

Tes Ubuntu comes with the ability to create zipped archives.  She here to start: [https://help.ubuntu.com/community/FileCompression]("https://help.ubuntu.com/community/FileCompression")

---

### Post by Yellow Pasque on 2015-01-05
You can open and create .zip files really easily on Windows (its built into Windows Explorer). That's probably .zip files' real advantage: portability.
Basically, you would only need unzip if you need to... unzip a .zip file. You would only need to install zip if you want to create a zip file intended to be used on Windows installs.

---

### Post by Impavidus on 2015-01-05
On Xubuntu at least both zip and unzip come installed by default. If you don't have them and you want to create or unpack a .zip archive, install those packages, now or when the need arises.

---

### Post by whitesmith on 2015-01-05
> **charleswb said:**
> Doesn't Ubuntu already natively have the capability to zip and unzip files? Is there something I don't understand here?

No, but there's something the "guru" apparently misunderstands. Linux has a built-in called gzip that -- don't take this as gospel -- is better and faster at compression than zip. Also, gzip is native *nix software but zip is a borrowing from the Windows world. I don't think much of the guru's advice. Also, you are in the right forum. Cheers!

---

### Post by oldos2er on 2015-01-05
> **charleswb said:**
> I recently installed Ubuntu 14.04.1  An online Ubuntu enthusiast/semi-guru recommended to me that I install packages zip and unzip via the command line as follows:  sudo apt-get install zip unzip  What would be the benefit of installing those two packages? Doesn't Ubuntu already natively have the capability to zip and unzip files? 

As far as I'm aware Ubuntu has always come with these two packages already installed; at least I don't recall ever having to install them manually.

---

### Post by charleswb on 2015-01-12
Thanks for your replies and advice.

I just ran some tests and the native GUI compression app can zip and unzip files just fine. So I don't see any need to install anything else. Perhaps that means that zip and unzip are already installed by default. In any case, it's a non-issue since the native GUI compression app handles it fine. I did not test this from terminal.

I conclude that the fellow who suggested installing zip and unzip didn't need to recommend them because Ubuntu can already do those things. What got me confused what it was an official Things to Do After Installing Ubuntu 14.04 document that recommended installing zip and unzip via command line and apt-get install. I also saw that same info/recommendation parroted by several Ubuntu enthusiasts at various websites and by several computer magazine websites. I think they were all just quoting the original source I orignally read, but it seems to me that capability is already in native Ubuntu 14.04.

---

### Post by charleswb on 2015-01-12
Likewise there several other packages and programs that were recommended for installing, but seem to already be installed, or another app already installed that offers same capability. I'm just trying to figure out what things I actually do need to do or add to my Ubuntu 14.04 LTS install to do all I want, but I don't want to install unnecessary things, or reinstall things for no reason.

So that's why I was asking. 

Thanks again everyone for your help.

---

### Post by charleswb on 2015-01-12
P.S. - I have a lot of coworkers who use Windows and that's why I cared about being able to zip and unzip files. I need to be able to deal with zip files for them.

---

### Post by Impavidus on 2015-01-12
There are lots of lists telling you what you should install after installing Ubuntu, and they all tell you something different. Often they advise you to install something that's already installed by default or something that you don't need. If you don't want unnecessary things, install nothing until you think of something you really want and can't do yet. Then find out which software will do the job.

---

### Post by charleswb on 2015-01-20
> **Impavidus said:**
> There are lots of lists telling you what you should install after installing Ubuntu, and they all tell you something different. Often they advise you to install something that's already installed by default or something that you don't need. If you don't want unnecessary things, install nothing until you think of something you really want and can't do yet. Then find out which software will do the job.

That ^ is some good advice there ^. I have learned the hard way and now have enough experience to totally agree with everything you said.

What gets my goat is some of that unnecessary and/or conflicting advice comes from the official Ubuntu site giving advice on what to do after installing Ubuntu. Much of it also at online computer magazine websites, and various enthusiast's blogs.

The best advice I ever got on the topic is from you in your post, but by that time I'd already learned it the hardway. You confirmed what I'd just learned from experimenting with others' advice from those other sources.

---

