---
title: "Revisit problem: SoX was compiled without MP3 encoding support"
date: 2013-02-22
forum: New to Ubuntu
---

### Post by rkircher on 2013-02-22
With Ubuntu 11.04 sox was working fine in converting .wav to .mp3 files.  I switched to Debian AMD64 Squeeze and sox no longer produced mp3 output with this error: sox FAIL formats: can't open output file `Busted.mp3': SoX was compiled without MP3 encoding support

I found and applied a procedure in this old post that fixed the problem: 
[http://ubuntuforums.org/showpost.php?p=9859875&postcount=8](http://ubuntuforums.org/showpost.php?p=9859875&postcount=8)  
I ended up with sox 14.3.1 and the sox mp3 output was restored and worked fine.

The next day I received update notices shown in attached files to update sox 14.3.1-1 to sox 14.3.1-1+b1.  After updating, I tested sox with the same command "sox filename.wav filename.mp3" and now have the same problem again, i.e., SoX was compiled without MP3 encoding support.

I don't fully understand the procedure that I followed in the post by andrew.46, but certainly its results worked, but were again over-written by the latest update to sox.  Can anyone suggest how I can get sox working again with mp3 output and keep it working?  I get mp3 output using audacity, but it lacks the concatenating features of sox, so I have a less convenient work-around, but it does not make sense that audacity in the same Linux Distribution should work while sox does not!

Any help or suggestions would be greatly appreciated. thanx

---

### Post by andrew.46 on 2013-02-22
Perhaps install *libmp3lame* and sox may dynamically load the library and enable mp3 conversion...

---

### Post by Sealbhach on 2013-02-22
Did you see [this post]("http://ubuntuforums.org/showpost.php?p=12519241&postcount=6")? Check to see if you have lbmp3lame installed. Otherwise, you will need to recompile again and if you want, you can pin the version (preventing updates) using [this method]("https://help.ubuntu.com/community/PinningHowto#Synaptic") in Synaptic.

.

---

### Post by rkircher on 2013-02-22
> **andrew.46 said:**
> Perhaps install *libmp3lame* and sox may dynamically load the library and enable mp3 conversion...
I have/had libmp3lame0 version 3.98.4+repack2-3~bpo60+1 installed.  I don't know if that is the same as libmp3lame but that is all I can find from any source.  Since the error message I get from sox says "SoX was compiled without MP3 encoding support" that probably applies to libmp3lame too since the only thing that seems to get it working is a recompile of sox using source that is edited to removes the code that Debian has deliberately included to disable mp3 encoding support.  None of this makes any sense to me since audacity in the same Debian AMD64 Linux Distribution produces mp3 output without any fuss.

---

### Post by rkircher on 2013-02-22
> **Sealbhach said:**
> Did you see [this post]("http://ubuntuforums.org/showpost.php?p=12519241&postcount=6")? Check to see if you have lbmp3lame installed. Otherwise, you will need to recompile again and if you want, you can pin the version (preventing updates) using [this method]("https://help.ubuntu.com/community/PinningHowto#Synaptic") in Synaptic.

.
I re-installed from the build of sox 14.3.1-1 that I had compiled a few days ago from the procedure at [http://ubuntuforums.org/showpost.php...75&postcount=8](http://ubuntuforums.org/showpost.php...75&postcount=8)  and then locked that version using the Synaptic package manager as you suggested (thanks).  Is there a narrative description somewhere that tells what the update to sox 14.3.1-1+b1 from 14.3.1-1 provides so I can tell if it is worth the effort of editing the new source and recompiling again? Maybe the "+b1" suffix to the version number means something. Any ideas?

---

