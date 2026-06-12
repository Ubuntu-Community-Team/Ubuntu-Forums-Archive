---
title: "mp3 support amarok 11.10"
date: 2011-12-08
forum: New to Ubuntu
---

### Post by BananaPeal on 2011-12-08
Good evening folks,

I recently installed kubuntu and have been by and large pleased with it, aside ofcourse from networking and ... sadly... now amarok.

I can't get it to play mp3. I think I've installed all the gstreamer plugins muon shows me. Amarok tries to install it itself, but when it lists the packages to be installed, the list is empty. It starts package manager, installs nothing, then complains again that it cant play mp3. 

Can't even listen to the radio stations b.c of this... 

mp4 seems to work fine if extensions are .mov. .m4a extension is not recognized by amarok, though it plays fine when finding it in dolphin and double clicking on it.

Any suggestions? I read on amarok's page that this stuff should install "perfectly" since v6.10... is there something wrong with my OS?

Thanks for your help

---

### Post by BBQdave on 2011-12-08
> **BananaPeal said:**
> I can't get it to play mp3. I think I've installed all the gstreamer plugins muon shows me. Amarok tries to install it itself, but when it lists the packages to be installed, the list is empty. It starts package manager, installs nothing, then complains again that it cant play mp3.

Short answer: Software Center, select fluendo mp3 plugin.

Or you can go to Fluendo's site and download it for free *(make sure to get the **.deb** file)* :)

---

### Post by BananaPeal on 2011-12-08
Fluendo Worked like a charm. Thanks!:popcorn:

I have a question still though, I tried installing an mp3 decoder called: libmpeg3-1

```
LibMPEG3 decodes several MPEG standards into uncompressed data suitable for editing and playback. It currently decodes:

 • MPEG-2 video
 • MPEG-1 video
 • mp3 audio
 • mp2 audio
 • ac3 audio
 • MPEG-2 transport streams
 • MPEG-2 program streams
 • MPEG-1 program streams
 • IFO files

```

**Why does fluendo work and this one not?**:confused: I guess I mean to ask how do you know which one works with amarok?

Also, anyone know why .m4a doesn't show up in amarok's navigation, but works when selected thru dolphin?

Thanks for the insighsts, I'm just trying to wrap my head around why this works the way it does...

Banana

---

### Post by beew on 2011-12-08
To get  Amarok to play mp3 you have to install the package libxine1-ffmpeg. For other players installing the restricted-extras seems sufficient but Amarok is peculiar that way. 

The fluendo thing is for DVD from what I understand.

---

### Post by BananaPeal on 2011-12-08
> **beew said:**
> To get  Amarok to play mp3 you have to install the package libxine1-ffmpeg. For other players installing the restricted-extras seems sufficient but Amarok is peculiar that way. 

The fluendo thing is for DVD from what I understand.

Perhaps, but for now gstreamer0.10-fluendo-mp3 works. I suppose the thing to take away from this is that not anything with "lib" and "mp3" in its name works as an mp3 codec.

---

### Post by realitykid on 2011-12-08
Hmmm. I'm surprised that it didn't give you an option to install the decoders upon installation of Kubuntu.

Maybe it only does this in Ubuntu. Cause I was given that option when installing Ubuntu 11.10, and I chose it and all my stuff worked just fine.

---

### Post by BananaPeal on 2011-12-09
it doesn't for wubi/cd install. I did the wubi install so that i can still boot win server 08. However, aside from minor office issues, I'm not seeing the point anymore...

---

### Post by jonycobain on 2011-12-09
I can also confirm that, at least for Amarok, this fluendo library worked like a charm...thanks!!!

---

