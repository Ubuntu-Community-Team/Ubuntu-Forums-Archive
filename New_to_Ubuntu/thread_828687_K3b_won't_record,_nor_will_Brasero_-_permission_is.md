---
title: "K3b won't record, nor will Brasero - permission issue +"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by simontaylor on 2008-06-14
I've trawled through the literature on the cdrecord vs cdrdoa issue - a split in coding practices? - and had a stab at the terminal and installed and uninstalled various CD-burning apps in order to get my writer writing. K3b, which worked well for me on Gutsy, on Hardy has ceased to proceed. Brasero, which is said to be the go on Hardy, fails to produce an audio CD for me. Gnomebaker, which out of desperation I tried, also has problems. The underlying problem appears to be the CD/DVD writer and how the apps now go about talking to it under Hardy. 

I can cut and paste code and follow directions quite well ... but get lost in the back and forth of previous solves for similar issues. Is there a generic solve? 

I've even gone so far as to synaptically download Kcontrol in the hope that some mysterious dendrite will bring about a syzygy. 

Please help me out!

Yours
Simon Taylor

[www.brazilcoffee.co.nz](www.brazilcoffee.co.nz)
[www.squarewhiteworld.com](www.squarewhiteworld.com)

---

### Post by bumanie on 2008-06-14
Have you installed the multi-media codecs? If not > sudo apt-get install restricted-extras Also go to the medibuntu site and follow the instructions there for more multi-media codecs.

---

### Post by simontaylor on 2008-06-14
thanks bumanie,
terminal reads:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package restricted-extras

followed through on medibuntu but haven't tried to write to CD/DVD-writer. Am pretty sure my burning issues relate to this thread [http://ubuntuforums.org/showthread.php?t=676848](http://ubuntuforums.org/showthread.php?t=676848) which scares me because it came down to choosing either cdrecord or cdrdao for different tasks ---- or am I getting that wrong?

s.

---

### Post by simontaylor on 2008-06-15
opened up medibuntu and permitted installation of all additional codecs etc. However, this does not help K3b talk to my CD/DVD writer. More help requested.

Thanks,
simon

---

### Post by simontaylor on 2008-06-15
Read somewhere that Serpentine might do the do where Brasero and K3b failed. Something to do with Nautilus?

Tried and Serpentine told me to choose a lower speed. At the end of its long and arduous "preparing media." Leaving me with another useless shiny plastic disc.

I can't believe this. Really. No. I don't think speed is the issue here. 

Are software clashes common?

Should I be extirpating all that code and all those libs from the other apps that promise to burn me a simple audio cd? 

there must be a simple solve.

yours,

speechlessly frustrated,

simon

---

### Post by simontaylor on 2008-06-15
keyword=simple

---

### Post by simontaylor on 2008-06-15
Does anybody recognise this:

> sudo chown root:cdrom /usr/bin/cdr*
sudo chmod 4754 /usr/bin/cdr*

from: [http://ubuntuforums.org/showthread.php?t=391558](http://ubuntuforums.org/showthread.php?t=391558)

The 2007 thread reports problems with the same model CD/DVD writer as mine, Pioneer DVD RW 111-D and the above change of ownership and subsequent modification is supplied as a potential solve.

There seems to be something missing from the quoted code. Can you help? I don't know enough about this issue to risk plugging inadequately understood code into my terminal.

simon

---

### Post by cariboo on 2008-06-16
I don't don't think it is a permission problem, I think you are missing the **libk3b2-extracodecs** it is located in the repository, you can use synaptic to install it. Synaptic is located in System-->Administration-->Synaptic Package Manager.

Jim

---

### Post by alienexplorers on 2008-06-16
can you post the /etc/fstab file and put the results on here?

Brassero is a piece of junk.  Have never got it to burn a thing.  I use gnomebaker instead.

---

