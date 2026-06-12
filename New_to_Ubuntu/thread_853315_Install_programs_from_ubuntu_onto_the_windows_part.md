---
title: "Install programs from ubuntu onto the windows partition?"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by Nebelhom on 2008-07-08
Hi guys,

this is a general question and will eventually pan out to be about games ;).

I installed ubuntu in a dual boot with windows and left the largest partition to be used by windows, for two reasons:

A) I wanted to try out ubuntu first and wasn't sure if I could make the switch (turned out that I haven't used windows in quite sometime now)

and B) which is related to A, I had my music files and all the rest on that partition and wanted it to be accessible to both operating systems.

What I didn't take into account is, because I didn't know it, that linux automatically installs on the linux partitions (I guess that would have been kinda obvious but I dont know much about computers... yet).

Is it possible to transfer the game installation onto the windows partition and still be able to play the game in linux? If so, how? So far, I only ever came across terminal commands that gave you little choice in the matter.

I am not sure whether this is an easy question to answer, but any feedback would be really appreciated.

Thanks

---

### Post by billgoldberg on 2008-07-08
> **Nebelhom said:**
> Hi guys,

this is a general question and will eventually pan out to be about games ;).

I installed ubuntu in a dual boot with windows and left the largest partition to be used by windows, for two reasons:

A) I wanted to try out ubuntu first and wasn't sure if I could make the switch (turned out that I haven't used windows in quite sometime now)

and B) which is related to A, I had my music files and all the rest on that partition and wanted it to be accessible to both operating systems.

What I didn't take into account is, because I didn't know it, that linux automatically installs on the linux partitions (I guess that would have been kinda obvious but I dont know much about computers... yet).

Is it possible to transfer the game installation onto the windows partition and still be able to play the game in linux? If so, how? So far, I only ever came across terminal commands that gave you little choice in the matter.

I am not sure whether this is an easy question to answer, but any feedback would be really appreciated.

Thanks

I'm not entirely sure what you are asking.

You can access your music files from the windows partition under ubuntu easily.

Just open up the home folder, and on the left your windows partition will be listed.

Open it and you'll have access to all files.

--

About the games.

Are you asking if you can play the games from your windows partition under linux, or the other way around?

The answer would be no.

---

### Post by apswartz on 2008-07-08
> **Nebelhom said:**
> Is it possible to transfer the game installation onto the windows partition and still be able to play the game in linux? If so, how? So far, I only ever came across terminal commands that gave you little choice in the matter.

I not sure of what you mean by "game installation." Do you want to install your Linux games on your Windows partition? If that is what you mean, then yes, you can. You can create a directory in your Windows partition and include the mounted partition and directory in your path. The main problem is that you may have to compile the games yourself so that they will run and look for the libraries in the right places.

Did I understand your question? Does my answer make any sense? :-)

---

### Post by KIAaze on 2008-07-08
It is possible as explained above, but it would probably be easier to resize the partitions.

This is possible without data loss using gparted from a LiveCD, but just to be safe you should of course back up what's important.
And you'll probably need to defragment the windows partition too before shrinking it.

---

### Post by Nebelhom on 2008-07-08
@ all: yes, I meant install linux games on the windows partition. :)

in all that explaining as much as poss, I seem to have gotten tangled up in details making not much sense in the end. sorry ;)

@KIAaze: I'd rather stay away from LiveCD action cos I have to do quite a lot of specific configuring to get the LiveCD from giving me a useable output (I had to use noapic nolapic pci=off etc and so on, and after installation of some drivers removal of these again)... I just don't want to end up spending hours ;(

@apswartz: thanks. I will see what I can do and if I get stuck (very likely), I will call for help, if that's ok ;)

Thanks very much guys for the quick replies!

---

### Post by Nebelhom on 2008-07-10
Hi sorry to bother you people again.

I am trying to do what has been suggested, i.e. create a mount point for my windows partition in ubuntu in order to be able to put games onto that partition as well.

I found this website:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

is that the right way of doing it? I would appreaciate a second opinion, cos I have no idea if that is correct. it looks... convincing.

thanks for your help already :)

---

### Post by tjwoosta on 2008-07-10
that site looks like they pretty much cover everthing, but ill just include a link to a thread i made awile ago asking about mounting windows parition 

[http://ubuntuforums.org/showthread.php?t=782363&highlight=mount]("http://ubuntuforums.org/showthread.php?t=782363&highlight=mount")

---

