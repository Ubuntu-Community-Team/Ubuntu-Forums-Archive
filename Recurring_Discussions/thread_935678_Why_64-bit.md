---
title: "Why 64-bit?"
date: 2008-10-01
forum: Recurring Discussions
---

### Post by Forbees on 2008-10-01
i know with 64-bit my computer can go from 4gig ram max to 8 gig



but what are the main reasons to want to use 64-bit? i know some programs are  harder to find/install but thats what they said about linux in general and i think thats been proved wrong :-p



so what are the key features and limitations of 64-bit

should i give it a try?  (install a new partition just for 64-bit)

---

### Post by ShinUmbra on 2008-10-01
i would like to know myself, i just installed the 64bit using wubi atleast i think this is the 64 bit, and it's working great, but i'm new at this so i'm trying to get some of the functionality i'm used too =/ terminals are.. well.. slightly annoying atm, but thats only because i'm not used to it, what i would really like tho is a self extractor. I heard about Automatix and Ultramatix but i'm not sure how to go about getting them lol.

Also i'm trying to install a flash player so i can make watch a video on how to install wine on ubuntu and maybe beryl. anyone know of any resorce i should use to get all these things done lol

---

### Post by Yellow Pasque on 2008-10-01
Please see the sticky in this forum (or the hundreds of other threads like this in the "Recurring Discussions" forum).

---

### Post by stmiller on 2008-10-02
Computers have gone 8bit --> 16bit (windows 3.1) --> 32bit (windows 95-XP/Vista) -->64bit (now!) -->128bit (far future).

There are some overall big picture differences, though for most users you won't perceive any difference right now.

---

### Post by Sef on 2008-10-02
Unless you were doing movie editing, heavy gaming, or constantly downloading 600 pictures at a time, not a lot of difference to be seen.

---

### Post by 3rdalbum on 2008-10-02
> **Forbees said:**
> i know with 64-bit my computer can go from 4gig ram max to 8 gig

64-bit CPUs can address waaaaaaay more than 8 GiB of RAM. The main limitation will be what the chipset on your motherboard will allow.

---

### Post by Yellow Pasque on 2008-10-02
> for most users you won't perceive any difference right now.

I recently installed i686 Arch Linux on my laptop drive (this is what I use to play around with other distros). I was surprised, but I could tell the difference in "everyday" usage between the i686 version of Arch Linux and the Arch64 install I once used.

I wouldn't say the "32-bit lag" was a major annoyance, but once you're used to instant response, it spoils you.

---

### Post by lisati on 2008-10-03
> **stmiller said:**
> Computers have gone 8bit --> 16bit (windows 3.1) --> 32bit (windows 95-XP/Vista) -->64bit (now!) -->128bit (far future).

There are some overall big picture differences, though for most users you won't perceive any difference right now.

(sighs) The first ASM programming I did was in what was effectively a 24-bit platform. Must get round to learning 32-bit some time: most of my x86 ASM knowledge is based around 16-bit DOS......

---

### Post by jwaiwit on 2008-10-03
So 64 bit can be faster than 32 bit? or just for use huge memory only ?

If it faster may be we could move to 64 bit. I found that once I move to Ubuntu It's no need to find any application to installed on it. I think the problem for move to 64 bit because lack of 64 bit 's software.

Just my opinion...

---

### Post by t4thfavor on 2008-10-03
64 bit can not only use more memory, but it can execute more code at a time effectively doubling the performance of a properly compiled application (such as the linux kernel). I use it on my laptop, and it is a major improvement (even 64 bit Windows is faster). Also I have only ever had to "Cheat" to get applications to run a few times mostly involving flash.

I did get it (flash) going in less than half an hour even with the workaround.

I would say if you want to run linux, run the 64 bit version, if you have to run windows run 64 bit Vista (eww), its better than XP_64.


Any more questions reguarding 64 bit stuffs?

---

### Post by philinux on 2008-10-03
I've been running 64 bit Hardy since it it came out. Last week on my spare HD I installed 32 bit Intrepid. To my surprise intrepid seems snapier. Could be intrepid who knows.

I'll find out for sure when I upgrade Hardy.

---

### Post by TVMA on 2008-10-03
Yeah, 32-bit OS can only address I believe 3.2 gigs of ram?
I am running 64-bit with 4 gigs of ram on an AMD phenom quad core. It comes in nice when you are encoding video, audio, working with large images for print, or anything that is heavily resource intensive and taxing the processor. In windows there are some apps that really utilize 64-bit computing such as Adobe Photoshop. There are some issues here and there with trying to install 32-bit apps, or finding a 64-bit app for your system, but that's quickly becoming a non-issue.

---

### Post by jespdj on 2008-10-03
> **jwaiwit said:**
> So 64 bit can be faster than 32 bit? or just for use huge memory only ?

If it faster may be we could move to 64 bit. I found that once I move to Ubuntu It's no need to find any application to installed on it. I think the problem for move to 64 bit **because lack of 64 bit 's software.**

Just my opinion...
No!! Linux is not Windows! Why do you think there is a lack of 64-bit software? Stop spreading that nonsense. The 64-bit Ubuntu repository contains everything that the 32-bit Ubuntu repository contains. There is no lack of 64-bit software.

The only things that are not (yet) available as native 64-bit applications are a handful of proprietary, closed source applications such as Adobe Flash and Skype.

And that's no problem, because 32-bit software can also run on 64-bit Ubuntu. Running Adobe Flash and Skype on 64-bit Ubuntu is just as easy as on 32-bit.

Please note that all these questions about 64-bit Ubuntu have been asked and answered in this forum many, many times. Please [read the sticky](http://ubuntuforums.org/showthread.php?t=765428), so we don't have to start all over again with answering all the frequently asked questions.

---

### Post by Idefix82 on 2008-10-03
> **jespdj said:**
> No!! Linux is not Windows! Why do you think there is a lack of 64-bit software? Stop spreading that nonsense. The 64-bit Ubuntu repository contains everything that the 32-bit Ubuntu repository contains. There is no lack of 64-bit software.

The only things that are not (yet) available as native 64-bit applications are a handful of proprietary, closed source applications such as Adobe Flash and Skype.

And that's no problem, because 32-bit software can also run on 64-bit Ubuntu. Running Adobe Flash and Skype on 64-bit Ubuntu is just as easy as on 32-bit.

Please note that all these questions about 64-bit Ubuntu have been asked and answered in this forum many, many times. Please [read the sticky](http://ubuntuforums.org/showthread.php?t=765428), so we don't have to start all over again with answering all the frequently asked questions.

I am using Ubuntu 64 bit and I can second every word of what jespdj said (except that I wouldn't use the word nonsense, maybe misinformation). To install the 32 bit Flash plugin for Firefox you don't actually need to do anything, Firefox downloads the 32bit plugin wrapper for you and sets it all up, without you doing a single extra click.
The only thing that **really** doesn't work properly on 64 bit is the Sun Java JRE, which is a disgrace and will change in the near future. There are open source alternatives which are not perfect though and which can't cope with every Java applet. It will suffice for the most common needs and will only be an issue if you know that you will need to open rather sophisticated Java applets.

---

### Post by Rocket2DMn on 2008-10-03
Moved to Recurring Discussions.

---

### Post by jespdj on 2008-10-04
> **Idefix82 said:**
> The only thing that **really** doesn't work properly on 64 bit is the Sun Java JRE, which is a disgrace and will change in the near future. There are open source alternatives which are not perfect though and which can't cope with every Java applet. It will suffice for the most common needs and will only be an issue if you know that you will need to open rather sophisticated Java applets.
That's ofcourse not entirely correct. Sun Java runs fine on 64-bit Ubuntu. The only problem is that Sun doesn't have a 64-bit browser plug-in, so with Sun Java on 64-bit Ubuntu you cannot run applets in your browser.

However, if you install Open JDK Java, which is Sun's project to make Java open source, you will be able to run applets on 64-bit Ubuntu.

But again, unfortunately Open JDK is not yet perfect, so not every applet works correctly.

---

### Post by Idefix82 on 2008-10-04
> **jespdj said:**
> That's ofcourse not entirely correct. Sun Java runs fine on 64-bit Ubuntu. The only problem is that Sun doesn't have a 64-bit browser plug-in, so with Sun Java on 64-bit Ubuntu you cannot run applets in your browser.

However, if you install Open JDK Java, which is Sun's project to make Java open source, you will be able to run applets on 64-bit Ubuntu.

But again, unfortunately Open JDK is not yet perfect, so not every applet works correctly.

Sorry, you are right. I did mean the browser plugin. Unfortunately the Open JDK plugin doesn't load the only applet that I regularly need. But I can wait until Sun brings out their 64 bit browser plugin.

---

### Post by saru411 on 2008-10-05
> **jwaiwit said:**
> I think the problem for move to 64 bit because lack of 64 bit 's software.

Just my opinion...

If you look at repos in synaptic package manager you will notice 99% of packages from 32 bit ubuntu are available in 64 bit ubuntu. The reason less people use ubuntu 64 is because they are either scared, misinformed, happy with their current install, or have some other issue with hardware/software that cann't be addressed in AMD64 architecture.

64 is fully supported TODAY!

---

### Post by saru411 on 2008-10-05
> **Idefix82 said:**
>  But I can wait until Sun brings out their 64 bit browser plugin.

Good luck waiting. We AMD64 users have been waiting for a 64 bit Java browser plugin  for years. I've always found Kilz post on how to install 32 bit firefox with plugins to be the simplest work around, but feel free to wait for the plugin.

---

