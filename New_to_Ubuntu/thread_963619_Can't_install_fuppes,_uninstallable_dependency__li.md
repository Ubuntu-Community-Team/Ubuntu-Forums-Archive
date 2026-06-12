---
title: "Can't install fuppes, uninstallable dependency  libavcodec1d"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by SSamiK on 2008-10-30
After doing a clean install of 8.10 i'm unable to install fuppes because of an dependency that is not satisfiable. Gdebi-gtk says missing dependency is libavcodec1d. I got the deb from getdeb.net, and it's actually made for Hardy but used to work with no troubles in Intrepid updated from Hardy.
Is that package gone, renamed or what? Anyone have a workaround?

---

### Post by Het Irv on 2008-10-30
Try searching in Synaptic Package Manager for that package, if it was renamed or merged into another it should come up in the search.  I have had success finding dep that way in the past.

---

### Post by SSamiK on 2008-10-30
I've tried that... But I can't find it. Also tried searching [http://packages.ubuntu.com]("http://packages.ubuntu.com/search?keywords=libavcodec1d&searchon=all&suite=intrepid&section=all"), but can't find it to Intrepid.

```
ssamik@lynx:~$ aptitude search libavcodec
p   libavcodec-dev                                                  - development files for libavcodec                                         
i   libavcodec-unstripped-51                                        - ffmpeg codec library                                                     
c   libavcodec51                                                    - ffmpeg codec library
```

---

### Post by RatSAT on 2008-10-30
I have the same problem with fuppes and intrepid. Only difference is that I upgraded from hardy instead of doing a clean install. Fuppes was apparently uninstalled during the process, probably because there is no libavcodec1d for intrepid? Would be really nice if this could be resolved, kind of use fuppes daily to stream media to my PS3.

Edit: Manually downloading and installing [libavcodec1d]("http://packages.ubuntu.com/hardy/i386/libavcodec1d/download") and [libavformat1d]("http://packages.ubuntu.com/hardy/i386/libavformat1d/download") from the hardy repository seems to have worked. Just successfully installed fuppes in intrepid :) Hope this hasn't screwed up anything else, but I guess it will be fine since those packages didn't change anything else on my system.

---

### Post by SSamiK on 2008-10-30
I've gotten fuppes to install, but I had to use some packages from Hardy.
These three is "missing" from Intrepid, blocking the installation of fuppes:

 libavcodec1d_0.cvs20070307-5ubuntu7.1_i386.deb
 libavutil1d_0.cvs20070307-5ubuntu7.1_i386.deb
 libavformat1d_0.cvs20070307-5ubuntu7.1_i386.deb

Grabbing them from [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") and installing them gets fuppes installed, but I do not know if this is a "good" way of doing it.

---

### Post by RatSAT on 2008-10-30
> **SSamiK said:**
> but I do not know if this is a "good" way of doing it.
But at least we can watch our media again :)

---

### Post by SSamiK on 2008-10-30
> **RatSAT said:**
> But at least we can watch our media again :)

Yes we can! :D 
I actually had to install one more package when installing another deb I had with fuppes, libswscale1d_0.cvs20070307-5ubuntu7.1_i386.deb, also missing from Intrepid. 

When using the deb from getdeb.net the three mentioned in my last post was enought.

---

### Post by SSamiK on 2008-10-30
I've just had two (2) hard lockups in just a few minutes, I do not know if these packages I've just installed caused it! Will investigate and post back if this seems to be the case.

Edit: Ended up with about 6-8 lockups, witch I've never had in Intrepid before.

---

### Post by SSamiK on 2008-10-30
It do seem like one or more of those packages were the cause to those hard lockups, as I've had no more of them after uninstalling. So I'm back to where I started.... Now, can anybody tell me WHY those packages are gone in Intrepid? I also noticed that I cannot use ffmpeg to convert a divx to xvid or resize a xvid, as ffmpeg spits out an error.
```
Unknown encoder "xvid"
``` 
I suspect this also beeing a problem with libavcodec, in perticular the missing libavcodec1d, but I'm not sure. I've got ffmpeg from medibuntu repos.

---

### Post by RadicalRaid on 2008-10-30
I tried all of the above, same problems here.
It installed fuppes alright, but when I tried to add files I get a lot of these errors:
```

CContentDatabase::Commit() :: SQL error: cannot commit - no transaction is active
TagLib: MPEG::Header::parse() -- Invalid sample rate.

```

And a lot more where that came from. Anyone found anything yet? I need my daily dosage of streamed goodness on my ps3! ( :P )

---

### Post by RatSAT on 2008-10-30
Strange, it works fine for me so far. Also, I only needed the two packages lbavcodec1d and libavformat1d and not the other two. Just updated my entire database which contains movies, music and images. Streaming works fine too.

Only thing that doesn't work is transcoding, but I haven't been able to get that to work since firmware 2.40 on my PS3...

Edit: Or actually, it seems I have libavutil1d and libswscale1d from Medibuntu.

---

### Post by SSamiK on 2008-10-30
RatSAT: A couple of questions; where did you get the fuppes deb your using? And second, did you get libswscale1d and libavutil1d from the medibuntu repo for Intrepid? I can't seem to find them there... 
Also, you havent had any troubles with your computer locking up after installing fuppes or any of those other packages?

---

### Post by RatSAT on 2008-10-30
> **SSamiK said:**
> RatSAT: A couple of questions; where did you get the fuppes deb your using? And second, did you get libswscale1d and libavutil1d from the medibuntu repo for Intrepid? I can't seem to find them there... 
Also, you havent had any troubles with your computer locking up after installing fuppes or any of those other packages?

First off, I used the package I downloaded a couple of months ago for Hardy from [here]("http://www.howtoforge.com/set-up-a-linux-playstation-3-media-server-with-ubuntu8.04").
I am really not sure when I got libswutil1d and libswscale1d, but according to the package manager they are from Medibuntu. I haven't downloaded or installed them manually, so I guess they are leftovers from hardy. The versions are libavutil1d-cvs20070307-5ubuntu7.1+medibuntu1 and libswscale1d-cvs20070307-5ubuntu7.1+medibuntu1.
And no, I haven't encountered a single lockup, not during installation of the packages, installation of fuppes, when updating the database, rebuilding the database or streaming to my PS3.

---

### Post by SSamiK on 2008-10-30
Ok, thanks for the input. We are using the same deb, and we both have gotten Fuppes to run. I suppose my troubles with lockups not are related to this, so i'll try to reinstall tomorrow. (at this point my comp is more or less useless, it keeps locking up every few minutes and is totaly non responsive, even to SysRq keys so i'll have to do something. The strange thing is that it appared when I was fiddelig with fuppes. ;) ) I had no troubles adding folders, update database or stream to my PS3 until the fist lockup that is. Anyway, I'll try those medibuntu packages next time, just in case.   
> And no, I haven't encountered a single lockup, not during installation of the packages, installation of fuppes, when updating the database, rebuilding the database or streaming to my PS3.
That is sooo good to know! :D It gives me hope!

---

