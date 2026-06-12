---
title: "C++ and Octave Problems"
date: 2012-09-08
forum: New to Ubuntu
---

### Post by mark allyn on 2012-09-08
Hello everyone, 
 
I downloaded 12.04 about two weeks ago. As far as I know, the download was successful. However, in attempting to install Octave 3.6.3 during the ./configure process, the program terminated claiming that I had a deficient C++ installed. When I went to find C++ in /usr/bin I couldn't find it, although GCC was there. Since I've compiled a bunch of C programs in the last two weeks I wasn't surprised. However, if I try to compile a C++ program, the system reports that it doesn't know what g++ means on the command line. I've searched using "whereis", "find", and "locate", and I can't find any trace of a the CXX compiler.
 
Also, from earlier postings on this site it appears that there should be an earlier version of Octave on my machine, but using 
 
sudo apt-get install octave3.2
 
doesn't work. 
 
Can someone enlighten me?
 
Thanks,
Mark Allyn

---

### Post by spjackson on 2012-09-08
The best option for getting g++ is to install the build-essential package.

I don't know about Octave, however, [it is available for Precise]("http://packages.ubuntu.com/precise/octave3.2"), so your apt-get install should work.

You might need to install additional packages such as octave3.2-headers, I don't know.

What error do you get when you try to install it? The above link indicates that it is in the "universe" repository. Do you have this enabled in your sources?

---

### Post by mark allyn on 2012-09-08
Hi spjackson,
 
Thanks for your help on this.
 
I assume that the way to install build-essential is:  sudo apt-get install build-essential?
 
How do I enable the "universe" repository?  I have been puzzled by this "universe" concept from the beginning.
 
Thanks,
Mark Allyn

---

### Post by spjackson on 2012-09-08
> **mark allyn said:**
> 
I assume that the way to install build-essential is:  sudo apt-get install build-essential?
 
Yes.
> 
How do I enable the "universe" repository?  I have been puzzled by this "universe" concept from the beginning.
 You can use sudo to edit the file /etc/apt/sources.list . I think the lines to add (or maybe uncomment) would be
```

deb http://gb.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise universe
deb http://gb.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-updates universe

```However, I strongly recommend that you use a tool to enable it instead. With synaptic, you select Settings->Repositories and check the boxes you require. Even if you prefer to use apt-get over a gui tool, I would still use synaptic (or similar) to enable additional repositories, because it is far less error prone than editing by hand.

---

### Post by mark allyn on 2012-09-08
Hi spjackson,
 
Uh-oh.  I see URL's in the 4 lines of code you kindly sent me.....  My ubuntu machine is without internet connectivity.  I fear my goose is cooked, unless there is some way to access the sites with a Windows machine, download the necessary files, and burn them to a CD... and then use the deb command to load them on the ubuntu box.
 
Thanks for getting me this far...
 
Cheers,
Mark

---

### Post by spjackson on 2012-09-08
Hmm, well it's possible that the packages you need are on whatever media you installed from. I would doubt it, but I don't know.

In theory yes you can get the packages you need and burn them onto CD then install them. However, packages have dependencies and you need to follow what these are and install them in the right order. 

I don't think I've done a Ubuntu install that didn't involve internet access. Perhaps someone else can help you with this.

---

### Post by mark allyn on 2012-09-09
Hi spjackson,
 
Slow getting back to you.  Downed tree from storm knocked out my internet connectivity.  
 
As it turns out, I can't even install "build-essential"  There is no evidence that this thing exists anywhere on my system, and yet one would assume that anything so named would be available.  
 
Moreover, when I go to the sources window, it claims that libstdc++v.3 is INSTALLED!  How is this possible when it can't be found?
 
When I installed 12.04 I did so from a CD.  The CD was clean.  Is it possible that somehow I didn't configure the 12.04 with the right switches (options) set so that certain files were not installed---like for example "build-essential"?  
 
Thanks,
Mark

---

### Post by newb85 on 2012-09-09
> **mark allyn said:**
> Hi spjackson,
 
Slow getting back to you.  Downed tree from storm knocked out my internet connectivity.  
 
As it turns out, I can't even install "build-essential"  There is no evidence that this thing exists anywhere on my system, and yet one would assume that anything so named would be available.  
 
Moreover, when I go to the sources window, it claims that libstdc++v.3 is INSTALLED!  How is this possible when it can't be found?
 
When I installed 12.04 I did so from a CD.  The CD was clean.  Is it possible that somehow I didn't configure the 12.04 with the right switches (options) set so that certain files were not installed---like for example "build-essential"?  
 
Thanks,
Mark

build-essential isn't installed by default.  I don't know whether it's available on the CD.  You could check.  Pop the CD back in, Open the Software Center.  Edit>Software Sources and select the CD.  Then search for the package in the Software Center.

---

### Post by mark allyn on 2012-09-09
Hello Newb85,
 
Thanks.  That is a terrific idea.  I'll try and let you know the outcome later this afternoon.
 
Regards,
Mark

---

### Post by mark allyn on 2012-09-09
Hi Newb85,
 
Well, it didn't work, but that is probably because I don't know what I'm doing. The part where you wrote
 
> Edit>Software Sources and select the CD. Then search for the package in the Software Center. 

 
is where I'm unclear about what to do. I don't see how to select the CD when I get to Software Sources. So, I can't see how to do the search in the Software Center.
 
Could you amplify a bit more.
 
Cheers,
Mark

---

### Post by newb85 on 2012-09-09
> **mark allyn said:**
> Hi Newb85,
 
Well, it didn't work, but that is probably because I don't know what I'm doing. The part where you wrote
 

 
is where I'm unclear about what to do. I don't see how to select the CD when I get to Software Sources. So, I can't see how to do the search in the Software Center.
 
Could you amplify a bit more.
 
Cheers,
Mark

In the "Ubuntu Software" tab of "Software Sources", at the bottom there's a section titled "Installable from CD-ROM/DVD".  In that box, there should be an item titled "Cdrom with Ubuntu 12.04 'Precise Pangolin'".  Make sure it's checked.

In the Software Center, in the top right corner there's a search box.

As I said before, I don't know if build-essentials is included on the CD.

---

