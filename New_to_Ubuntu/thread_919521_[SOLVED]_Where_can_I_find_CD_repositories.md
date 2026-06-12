---
title: "[SOLVED] Where can I find CD repositories?"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by AndyJG on 2008-09-14
Hello everyone.

I installed Ubuntu 8.04 on to an oldish Sony Vaio laptop this morning and it went very smoothly. This is my first experience with Linux and as you can imagine I'm finding it quite different to Windows in places. Anyway, enough chat - here's my query:

The laptop isn't connected to the Internet and I don't want it to be. However, there's a couple of additions I'd like to make to the software: I'd like to install Kaffeine and the codecs etc for DVD/MP3 playback and also I'd like to add Scribus.

I've read  on this site about repsoitories that are available on CD but can find no mention of where. Kaffeine is on the cover DVD of the latest Linux Format magazine but on trying to install from there I'm getting an error message saying it's not a valid disc for installing from.

Where can I find the CDs mentioned or how do I make them?

Thanks in advance.

Andy.

---

### Post by Mornedhel on 2008-09-14
Hello.

Kaffeine and Scribus are available from the Ubuntu CD (in general, every package that shows up with a Ubuntu logo in Synaptic is available from the CD). Unfortunately, neither MP3 support nor DVD support are available from the official CD, for legal reasons.

Installing software from other distributions is not recommended, as the dependencies are awful to manage by hand. If you can get, at least temporarily, an Internet connection for your laptop, all you would need to do is install the ubuntu-restricted-extras metapackage.

---

### Post by aomlives on 2008-09-14
You can use the instructions [here]("https://help.ubuntu.com/community/Medibuntu") to individually download the necessary components for DVD/MP3 playback [here]("http://packages.medibuntu.org/hardy/index.html"). It seems you only need libdvdcss2 and the w32codecs, w64codecs, ppc-codecs packages.

Good luck.

---

### Post by Yannick Le Saint kyncani on 2008-09-14
> **AndyJG said:**
> The laptop isn't connected to the Internet and I don't want it to be. However, there's a couple of additions I'd like to make to the software: I'd like to install Kaffeine and the codecs etc for DVD/MP3 playback and also I'd like to add Scribus.

Hi Andy,

I would not recommend installing these without access to the internet, as it makes the process much more difficult for a newbie.

I am at times without any internet connection for some weeks/months, and the easiest way for me to be able to install software is to download the entire repositories archives using debmirror and setting up file:// repositories in sources.list.

I would definitely not recommend this for a newbie and suggest you reconsider the "never connect to the internet, even for installing software" rule you have.

---

### Post by Mornedhel on 2008-09-14
AFAIK, w64codecs and ppc-codecs are the same as w32codecs, compiled respectively for 64b and PPC architectures. Installing non-free-codecs will automatically pull the correct version for your architecture. Parent is correct though : you will probably need libdvdcss2 if you are planning to watch encrypted DVDs. The instructions provided by his link will let you add Medibuntu to your list of repositories, which is a must if you have Internet, but not so useful otherwise, although you could download the packages manually here : [http://packages.medibuntu.org/](http://packages.medibuntu.org/)
(be careful of stray dependencies !)

Edit : Next post from parent provides a correction. My bad.

---

### Post by aomlives on 2008-09-14
> **Mornedhel said:**
> The instructions provided by his link will let you add Medibuntu to your list of repositories, which is a must if you have Internet, but not so useful otherwise, although you could download the packages manually here : [http://packages.medibuntu.org/](http://packages.medibuntu.org/)

I didn't mean the instructions for adding Medibuntu to the repo list, I meant the instructions under "Installing Individual Packages", which is exactly what Andy would want to do I think. That's also where I copied the separate packages names from, I'm sorry about that, thanks for the correction about architecture there :)

---

### Post by Mornedhel on 2008-09-14
> **aomlives said:**
> I meant the instructions under "Installing Individual Packages", which is exactly what Andy would want to do think.

Oops, my fault for not reading the entire page.

---

### Post by AndyJG on 2008-09-15
Thanks to everyone for all the advice. It'll be a few days before I'm able to dedicate any time to this but it looks like an Internet connection is the way to go.

I've just ordered a USB WiFi adapter, chosen from the Ubuntu wiki of supported hardware to work from straight the box, so when that arrives I'll see if I can link to my existing Orange wireless broadband and report back.

Thanks again, folks.

Andy.

---

### Post by AndyJG on 2008-09-24
Hello everyone.

I'm now stuck connecting to the Internet (I have another thread running for that) so will post back here once I'm on the web and able to try downloading software.

Regards.

Andy.

---

### Post by Paqman on 2008-09-24
The [Ubuntu DVD](http://cdimage.ubuntu.com/releases/hardy/release/) contains all the software in the repos.

---

### Post by AndyJG on 2008-10-28
Hello everyone.

Sorry for the delay in writing again.

I've taken the advice above, connected to the Internet and have successfully dowmloaded the software I wanted.

It's so easy I'd reccommend this method to anyone rather than messing around with CDs!

Thanks to everyone for their help.

Andy.

---

