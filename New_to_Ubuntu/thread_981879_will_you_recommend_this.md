---
title: "will you recommend this ?"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by luckydeveloper on 2008-11-14
hi,

i am actually having windows in my other partition solely because of MS Office. so i have decided(not yet  implemented) to use ubuntu fully in my system hard disk while using windows only via virtual box.But i may need to create/edit MS office documents and transfer them to my thumb drives through that virtual box itself.

would you recommend me do the above thing. will that prove reliable ?

please help

---

### Post by hyper_ch on 2008-11-14
with virtualbox you can share directly folders from the host to the guest... you could then just auto-link to save the docs on the host system. That should run well.

---

### Post by Sirron on 2008-11-14
USB support is only available in the non-open source version of VirtualBox, so make sure you're using the version from the website, not from the ubuntu repositories.

That method may prove awkward, but fundamentally I don't think there's anything wrong with it.

Perhaps a better option would be to set up a sharing folder between the guest OS and the host, and copy files to your USB key from there via the ubuntu front end.

I expect you could even set up your USB key as the destination of the shared folder ^^

---

### Post by tdreyer1 on 2008-11-14
If you're not using any of the "advanced" features of MS office, you should try Open Office. It is easy to use, and is compatible with all MS office formats. It should be installed with ubuntu by default.

---

### Post by luckydeveloper on 2008-11-14
cool !  thanks. 
i am actually a CS student. i know there wont be any problem in programming if i switch to ubuntu.
i Dont play games. i am an active internet user. i may want to program in .net in future. i currently do programming in java. i want to operate my ipod whatsoever.
from your experiences,  what are the problems i may face if i do what i said before.. i mean.. using windows through virtualbox... 
and another question... is ubuntu really ready for desktop users.. playing music, video, using digi cams, ipods... etc.,

---

### Post by nothingspecial on 2008-11-14
I`ve never used windows (except at work)
I play music and videos. I have an ipod video, a digital camera, a video camera etc etc etc and use them all.

---

### Post by tdreyer1 on 2008-11-14
I know that Programming in java is not a problem for linux. I've used eclipse just fine in ubuntu. As for .net, I'm afraid I'm not familiar enough to say one way or another.

I've been using ubuntu for a couple of years now as my primary OS, and the only things I've needed to use windows for is with my iPod touch (iTunes) and for my newer games. My older ipods work just fine in linux alone, but the touch is a little more finnicky. If you're interested in music, check out amarok. Ubuntu may not be able to do everything, but imho, it is definately ready for desktop users.

---

### Post by roelpeeters on 2008-11-14
> **luckydeveloper said:**
> cool !  thanks. 
i am actually a CS student. i know there wont be any problem in programming if i switch to ubuntu.
i Dont play games. i am an active internet user. i may want to program in .net in future. i currently do programming in java. i want to operate my ipod whatsoever.
from your experiences,  what are the problems i may face if i do what i said before.. i mean.. using windows through virtualbox... 
and another question... is ubuntu really ready for desktop users.. playing music, video, using digi cams, ipods... etc.,
As far as programming is concerned, you can use netbeans or eclipse on Ubuntu for Java development. If you want to program in .net, you can use mono which contains a c-sharp compiler. It even has bindings with gtk to develop graphical interfaces.

As for your other questions: there are plenty of applications to play music, video, digi cams, etc. To name a few: vlc, totem, mplayer, amarok, digicam for digital cameras. I don't have an ipod, so I don't have any experience with ipod software, although I have read that there is software available for ubuntu. 
If this is all you use your pc for, then you can easily switch to Ubuntu. Besides as a CS major, it has a lot of advantages to be able to use (and tinker) with a unix like environment. (Speak from experience, I am a CS major myself).

Join the club! Who needs Windows?

---

### Post by luckydeveloper on 2008-11-14
> **roelpeeters said:**
> As far as programming is concerned, you can use netbeans or eclipse on Ubuntu for Java development. If you want to program in .net, you can use mono which contains a c-sharp compiler. It even has bindings with gtk to develop graphical interfaces.

As for your other questions: there are plenty of applications to play music, video, digi cams, etc. To name a few: vlc, totem, mplayer, amarok, digicam for digital cameras. I don't have an ipod, so I don't have any experience with ipod software, although I have read that there is software available for ubuntu. 
If this is all you use your pc for, then you can easily switch to Ubuntu. Besides as a CS major, it has a lot of advantages to be able to use (and tinker) with a unix like environment. (Speak from experience, I am a CS major myself).

Join the club! Who needs Windows?

k.. i am joining your club..

i may have problems after i start working in virtualbox for MS=Office, i guess you people will help me to solve those... :)

---

### Post by roelpeeters on 2008-11-20
That goes without saying, that's what we are here for!

---

### Post by Dedoimedo on 2008-11-20
Hello,

This is an excellent idea.

Virtualization allows you to separate resources, test programs, use programs sparingly, and a whole load more.

I have written quite a few pieces on virtualization, including how to run windows in vmware server on linux, a review of vmware player, a review of various virtualization programs, including virtualbox etc. Check if you want (sig).

You can even run virtualbox from other virtual machines, creating a layer inside a layer. It can be used on other virtualization products from usb drives. And of course, you can place virtual machines on second hard disk, external hard disk, a remote network location etc.

Dedoimedo

---

