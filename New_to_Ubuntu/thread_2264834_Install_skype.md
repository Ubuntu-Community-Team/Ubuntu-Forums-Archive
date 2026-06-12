---
title: "Install skype?"
date: 2015-02-10
forum: New to Ubuntu
---

### Post by Carmen286 on 2015-02-10
I just installed 14.04.1  64 bit....  do not find any answer searching software center or forum about sykpe. The downloads on the skype site are for earlier versions.  Not sure which to choose and if I download from skype, how do I install?

---

### Post by slickymaster on 2015-02-10
Hi Carmen286, welcome to the forums.

Here's a link that will help you: [http://askubuntu.com/questions/504689/cant-install-skype-4-3-on-ubuntu-14-04-64-bit](http://askubuntu.com/questions/504689/cant-install-skype-4-3-on-ubuntu-14-04-64-bit)

---

### Post by Carmen286 on 2015-02-10
is there some way to install  skype (which is the right one?) without the terminal?

---

### Post by monkeybrain20122 on 2015-02-10
Yes, of course. :) Open the software Centre. Click Edit > Software Sources, go to 'Other Software', check the box Canonical Partners. Wait for the Software Centre to update the sources (there is a rotating icon on the top, wait til it to stop). Then search for Skype and install.

---

### Post by ajgreeny on 2015-02-10
In fact the version you see on the skype website is fine for 14.04 and beyond, in spite of saying it is for 12.04 (I think) and I'm not sure if it's different from the repos version.

However, as monkeybrain20122 says, all you need to do is enable the partner repos and you can install skype from there.

Having just checked I see I am at the moment using the 4.3.0.37-1 version from skype direct, the version for the repos being 4.3.0.37-0ubuntu0.

I do not know how different they are, but it may be that the skype direct version is multi-architecture, ie, both 32 and 64 bit in the one package, whilst the repos version is not as far as I'm aware.  They both work, that much I do know having used both versions, and I can not see any obvious difference when they're used.

---

### Post by mailfordannym on 2015-02-14
You can install Skype without the terminal by going to the Skype website and go to the downloads page and select the option that says Ubuntu 12.04(multiarch). Download the file and double-click it and open it in the Ubuntu Software Center and click install.

---

### Post by SayakBiswas on 2015-02-15
Go to the Skype website, and download the version meant for Ubuntu 12.04 multiarch.
It should download as a .deb file, which you can simply double click and it will install through the software centre, no terminal/commands needed.

---

### Post by monkeybrain20122 on 2015-02-15
In the past there have been people having problems installing skype's deb that's why I recommended the Partners' repo. I haven't tried it though, always use Partners'

---

### Post by DiamondBoy1979 on 2015-02-15
**&#8203;Thanks this helped me fix my problem with installing skype.**

---

