---
title: "[SOLVED] I want vlc 0.9.2"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by t0p on 2008-09-15
On another forum I frequent, there were all these windows users raving about **vlc 0.9.2**.  I've got 0.8.6e.  So I figured I'd go to the [Videolan website]("http://www.videolan.org") and grab me the new goodies.

So I go there.  And on the front page they've got like this running total of 0.9.2 downloads, going up and up.  I click through to the Ubuntu Linux page... and all that's there is instructions for getting it from the repos... **sudo apt-get update**... **sudo apt-get install vlc**...

I think *Okay*... I give it a go... and apt-get tells me I've already got the newest version.

***What is going on here?!!***

Windows users get a new release... but we have to make do with a version that's been out since the days when computers ran on steam!!  *Why?? What gives??* 

I want vlc 0.9.2.  Please tell me there's a way to get it!!

---

### Post by OffAxis on 2008-09-15
just download the source and build it yourself.
here's the source:
[http://www.videolan.org/vlc/download-sources.html](http://www.videolan.org/vlc/download-sources.html)

---

### Post by Mornedhel on 2008-09-15
Why ? Packaging is hard work when done right. It's also much less gratifying than developing (since who thinks of the packagers when using a piece of software ?)

As there are no direct download links on the VLC homepage, and no package on getdeb, my guess is you'll have to compile from source.

---

### Post by phidia on 2008-09-15
There's a related thread on the latest version of VLC [here]("http://ubuntuforums.org/showthread.php?t=920204").

---

### Post by dualpretop on 2008-09-15
[http://ubuntuforums.org/showthread.php?p=5794856#post5794856](http://ubuntuforums.org/showthread.php?p=5794856#post5794856)

---

### Post by t0p on 2008-09-15
Oh man, compiling vlc up looks like a real difficult operation.  And I've never been comfortable with this stuff.

Guess I'll just have to wait til someone else packages it for us.

Should I mark this thread Solved?  I mean, it's not solved, I'm just admitting defeat.  Does defeat count as a solution?

---

### Post by Tatty on 2008-09-15
> **t0p said:**
> Oh man, compiling vlc up looks like a real difficult operation.  And I've never been comfortable with this stuff.

Guess I'll just have to wait til someone else packages it for us.

Should I mark this thread Solved?  I mean, it's not solved, I'm just admitting defeat.  Does defeat count as a solution?

It only looks hard because you have never done it before.  I think you should give it a go.  After you have compiled a couple of things you will be pretty comfortable doing it - its the only way youre going to get the latest software between ubuntu releases.

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

Just follow this guide, make sure to use checkinstall instead of make, and you will have the latest vlc in no time.

---

### Post by phidia on 2008-09-15
How about a simple (sort of) [primer on compiling]("https://help.ubuntu.com/community/CompilingEasyHowTo")-it's never too late to learn.

---

### Post by t0p on 2008-09-16
Right... I've run ./configure a couple of times, and installed a couple of required libraries.  Now, I've just run ./configure again and got this result:

```
configure: error: Could not find libmad on your system: you may get it from http://www.underbit.com/products/mad/. Alternatively you can use --disable-mad to disable the mad plugin.
t0p@ubunty:/usr/local/src/vlc-0.9.2$ sudo apt-get install libmad
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libmad

```

I'm a little confused, because Synaptic tells me I *have* got libmad0, which by its description seems to be the same as libmad as described on [www.underbit.com]("http://www.underbit.com/products/mad").  But I'm game for this now... I've just downloaded the source for libmad.  Now I've got to compile it... so I can then compile vlc.  I just hope libmad hasn't got dependencies that will require me to download another package in source!

I'll let you all know how this goes...

---

### Post by t0p on 2008-09-16
Oh heck... I just tried to extract libmad-0.15.1b.tar.gz and it failed!  I right-clicked it, selected to "open with Archive Manager", and I got this output:

```
gzip: stdin: unexpected end of file
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now
```

I need this in order to compile vlc.  What can I do??

---

### Post by linuxnoob123456789 on 2008-09-16
If you want the easy way out just install wine then install windows version. thats what i did and it works great. just remember to move the file you want to fake c drive.

---

### Post by Tatty on 2008-09-16
did you try running ```
sudo apt-get build-dep vlc
```?

This should install all the dependencies of vlc for you (or at least the dependencies of the version in the repos which should probably be the same).

EDIT: try installing libmad0-dev too.

---

### Post by mc4100 on 2008-09-16
The easiest way is found in the thread Phidia linked to:
> **phidia said:**
> There's a related thread on the latest version of VLC [here]("http://ubuntuforums.org/showthread.php?t=920204").

In which SigmundFreud provided the following blog post with step-by-step instructions (Never ever thought I'd say that, Hmm)... 
[http://blog.jetienne.com/2008/09/vlc-092-on-ubuntu-804.html](http://blog.jetienne.com/2008/09/vlc-092-on-ubuntu-804.html)

**No compiling needed -- no dependency hell either**

---

### Post by t0p on 2008-09-16
> **Tatty said:**
> did you try running ```
sudo apt-get build-dep vlc
```?

This should install all the dependencies of vlc for you (or at least the dependencies of the version in the repos which should probably be the same).

EDIT: try installing libmad0-dev too.

Thanks for the tip.  I'm running it now... it's got to download 130 MB of files! :(  I've got a pretty slow connection, so I'm gonna be at this all night!

---

### Post by t0p on 2008-09-16
> **mc4100 said:**
> The easiest way is found in the thread Phidia linked to:


In which SigmundFreud provided the following blog post with step-by-step instructions (Never ever thought I'd say that, Hmm)... 
[http://blog.jetienne.com/2008/09/vlc-092-on-ubuntu-804.html](http://blog.jetienne.com/2008/09/vlc-092-on-ubuntu-804.html)

**No compiling needed -- no dependency hell either**

Oh wow!!  Thanks for the link... that'll save me some time n headache!!  :)

**EDIT:** Successful installation.... but no sound. :(  I'm going to start a thread about that.

---

