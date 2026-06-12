---
title: "Installing Flac (audio codec)"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by Computerwiz1990 on 2008-11-10
I am trying to install flac, the audio codec so i can install Rose Garden. I have a tar.gz file. I go through all of the steps and i have (myname)@Linux-Computer-1:~/src/flac-1.2.1-linux-i386$ in my console and then i am suppose to type ./configure... right? Well when i do that i get
bash: ./configure: No such file or directory

How can there be no directory? The cd is in it! 

Can anyone help me? Do i need that build essentials crap or what?!Because some guides say that i need it while others say that i don't.

---

### Post by MasterSander on 2008-11-10
no just install w32codecs if you're on a 32bit installation, > sudo apt-get install w32codecs

---

### Post by Pro-reason on 2008-11-10
Firstly, why are you trying to compile the source code for FLAC instead of just installing it in the normal way?  Simply open up Synaptic, and install Rose Garden.  It will automatically install all dependent packages, such as FLAC.

What guide says that build-essential is not necessary for compiling software?

---

### Post by MasterSander on 2008-11-10
> **Pro-reason said:**
> Firstly, why are you trying to compile the source code for FLAC instead of just installing it in the normal way?

What guide says that build-essential is not necessary for compiling software?

yeah if you're trying to compile you do need build essentials ;P
and an even easier way is to try and play the .flac file with totem media player and it'll ask you if it needs to search for the codecs

---

### Post by Pro-reason on 2008-11-10
> **MasterSander said:**
> no just install w32codecs if you're on a 32bit installation,

No, don't tell people to install *w32codecs*.  Tell them to install *non-free-codecs*, which will automatically install either *w32codecs* or *w64codecs* depending on their architecture.  In any case, it is necessary to add the Medibuntu repository to one's /etc/apt/sources/list file before that will work.

---

### Post by SuperSonic4 on 2008-11-10
flac is also it's own package:```
sudo apt-get install flac
```

---

### Post by Pro-reason on 2008-11-10
> **SuperSonic4 said:**
> flac is also it's own package:```
sudo apt-get install flac
```

Is there an echo in here?  I seem to remember already having told him that.

And, more to the point:

```
sudo apt-get install **rosegarden**
```

---

### Post by Bölvaður on 2008-11-10
oh please people. That person has 11 posts on this forum and might even not know about installing software. He even might be scared of the terminal, so what I would suggest is this:


Dear sir.
You can install flac by going into an installer program which you find through System &#8594; Administrator &#8594; Synaptic Package Manager
And there you look for "non-free-codecs"
You need to mark, apply and accept that you are installing the codecs.


But you can also do all that by going into the terminal (Applications &#8594; Accessories &#8594; Terminal) and type ```
sudo apt-get install non-free-codecs
```


ok Im going to take a bath

---

### Post by Pro-reason on 2008-11-10
> **Bölvaður said:**
> oh please people. That person has 11 posts on this forum and might even not know about installing software. He even might be scared of the terminal, so what I would suggest is this:


Dear sir.
You can install flac by going into an installer program which you find through System &#8594; Administrator &#8594; Synaptic Package Manager
And there you look for "non-free-codecs"
You need to mark, apply and accept that you are installing the codecs.



And how would that help him install Rose Garden?  How would it even work unless he enabled Medibuntu?

He needs to open Synaptic (I'm assuming he's intelligent enough to find it in the menu), and install Rose Garden.  End of story.

I don't know why I bother... I come in, solve a problem, and then half a dozen people come in and either give wrong information or repeat what I've already said.

---

