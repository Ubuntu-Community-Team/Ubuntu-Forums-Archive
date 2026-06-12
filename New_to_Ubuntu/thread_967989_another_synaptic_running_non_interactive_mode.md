---
title: "another synaptic running non interactive mode"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by aw76 on 2008-11-02
Hi,

I just installed ubuntu 8.10, and have a couple questions..

1) The red arrow with the ! mark is informing me that there are 6 updates available.  I looked at them and they are for various things like base filess, linux headers, linux libc-dev, linux-images, etc.

should i install all of them? do i have to know what they are for and be selective as to which ones i install? i dont plan on doing any developing, so it would seem that i dont need the -dev updates????am i correct, or just clueless?

2) I was trying to download the codecs necessary to watch a video, but when it tried to update the list, it returned the message that "another synaptic was running in non interactive mode" ....i went to system monitor, but there was nothing there that looked like it was running, other than the system monitor process itself...

how can i stop the other synaptic and get on with getting the codecs?



thanks for your help

s

---

### Post by Paqman on 2008-11-02
> **aw76 said:**
> 
should i install all of them? do i have to know what they are for and be selective as to which ones i install? i dont plan on doing any developing, so it would seem that i dont need the -dev updates????am i correct, or just clueless?


Yep, go for it. The package manager keeps a very good eye on what you need for your system. If there's stuff in there you don't understand, it's because its system stuff, or a dependency of something. It generally doesn't need any monitoring to get it right.

> 
"another synaptic was running in non interactive mode" 


This is most likely related to the above. Synaptic, Add/Remove and Update Manager all use the same system under the hood, and you can't have more than one of them open at once. Run the update then try downloading your codec again.

Top tip: the meta-package ubuntu-restricted-extras will install all the codecs you should ever need, plus a lot of other good stuff (also comes in Kubuntu and Xubuntu flavours).

---

### Post by MichaelSwengel on 2008-11-02
Welcome to Ubuntu!

First of all...generally speaking, you should always install all of the available updates. If you're seeing available updates, that means that you have an old version installed. So it won't hurt anything to update and often fixes bugs and performance issues.

Now...to this synaptic that's running....

Do you get the same error even after rebooting the computer? That will stop all processes and start fresh. Let us know. 

Regards,
MS

---

### Post by MichaelSwengel on 2008-11-02
> **Paqman said:**
> Top tip: the meta-package ubuntu-restricted-extras will install all the codecs you should ever need, plus a lot of other good stuff (also comes in Kubuntu and Xubuntu flavours).

I prefer the Medibuntu packages personally. With that you can play encrypted DVDs, MP3s....and really anything that you can in other operating systems.

Medibuntu = Multimedia Entertainment and Distractions in Ubuntu

[http://www.medibuntu.org/]("http://www.medibuntu.org/")

Paqman's suggestion or mine should either be great for you. :)

ALSO, I highly recommend VLC Media Player. It plays DVDs and pretty much anything else you throw at it - except Real Player files.

---

### Post by Paqman on 2008-11-02
> **MichaelSwengel said:**
> 
ALSO, I highly recommend VLC Media Player.

^This^

You can pretty much forget about needing codecs if you have VLC.

---

### Post by aw76 on 2008-11-02
thanks guys, i have installed the updates, and will just grab vlc....in retrospect that shoulda been evident to me, as that is the player i used in windows...just got caught up in trying to make my new system work...hehe....


i imagine i will be on here again soon with some more questions as they arise....

thanks

s

---

