---
title: "Hello everyone!  I am new to Ubuntu and would like some tips!"
date: 2015-01-19
forum: New to Ubuntu
---

### Post by Sam_Osman on 2015-01-19
[INDENT]Hello everyone,

I recently decided to dual boot Linux on my laptop that was primarily   running Win 8.1.  I am beginning to think that this was the best   decision that I have made all week!

[B]Anyhow, I was just wondering which apps you guys would recommend   installing and/or would consider essential.  So far I have done the   apt-get update/upgrade and I installed g++ and set up the thunderbird   e-mail service.  

What apps do you think are important and which apps do you use the most  often?[/B]  I am a mathematics student at a 2 year community college and I  intend  to transfer to a 4 year university to study computer engineering  (and  computer science).

I want to learn more about what else a Linux system can do; A friend of   mine once explained to me that a Linux machine can do pretty much   anything you can think of because it does not have the same limitations   as a Windows based computer.  I don't know if that is 100% true but I   believe it :grin:.

I plan on reading more about how to use the Linux shell (I saw the   sticky thread) and I'll be sure to lurk around the forums to see what   else is out there.

Thank you for reading, and I am super excited to join your awesome community!

- Sam

p.s. I plan on using Ubuntu as a Windows replacement.  I was planning on using Wine to re-install my video games such as Starcraft and Dota 2, as well as to install MS Office 2013.

Edit(s):  This post has been trimmed to better comply with the rules of the forum.  Please delete the 2 previous threads that were closed.
[/INDENT]

---

### Post by whitesmith on 2015-01-19
Some versions of MS Office--the latest Gold version of Word that I see supported is 2010--work under Wine (check winehq.org). Games are always problematic. Some work under Wine, many others don't. Knowing what I now do I would not have dual booted when I joined the forum in 2008. I should have just installed 100% Ubuntu and depended on VirtualBox for Windows support. This is truly the best of both worlds because the running OSes are pure Ubuntu and (almost) pure Windows. Mull my experience over and see if it makes sense to you. Of course, the longer you wait, the more difficult this approach will be without a significant reinvestment of time. Regards.

[edit] VirtualBox works best if a fair amount of RAM can be allocated to it on the fly. I have 32 GB in my box. Before jumping on the VirtualVox approach I would post a question under Virtualization and get the opinion of an expert. I would hate to recommend one approach only to have it blow up in your face because you lack the resources to implement it.

---

### Post by Sam_Osman on 2015-01-19
That makes sense.  Should I be concerned about lag and errors when running those high-resouce demanding games via Virtual Box on an Ubuntu system?  Ubuntu was lagging when I did the opposite (used Ubuntu vbox on Win 8.1 system) but Ubuntu is running super-fast now when I use it as the main OS.  I will definitely check winehq.org to see what is supported.  Thank you for that.  I am guessing Office 2010 might work and I still have my academic license for it.  And just to clarify, you are saying that Ubuntu + vbox windows is much better than dual booting?

Edit: I suppose I should have mentioned that I am on an ASUS laptop with icore 7 2.4 ghz processor, 8 gigs RAM, nvidia 840M with 2gb ram, and 750 gb hdd @ 5400 RPM (I forgot the exact RPM number but its the 5xxx one).

---

### Post by Lars Noodén on 2015-01-19
> **Sam_Osman said:**
> What apps do you think are important and which apps do you use the most  often?[/B]  I am a mathematics student at a 2 year community college and I  intend  to transfer to a 4 year university to study computer engineering  (and  computer science).

The typesetting tool Te*X* would be useful to know in that context, last I checked.  It's how math and comp sci is written.

---

### Post by Sam_Osman on 2015-01-19
> **Lars Noodén said:**
> The typesetting tool Te*X* would be useful to know in that context, last I checked.  It's how math and comp sci is written.

Good call!  I definitely need that!  I still need to learn how to use it.  Is there a name of a specific app you would recommend downloading to edit and compile TeX documents?  (I assume compile is the right word, and I do not know if TeX is itself the name of an editor.  In the past my peers recommend using a LaTeX editor but I was unable to get it working at the time).

--Sam

---

### Post by whitesmith on 2015-01-19
#Sam_Osman: I think your post and an edit to mine crossed. Please read the EDIT to that post, since it brings up an important point. Regards.

---

### Post by Sam_Osman on 2015-01-19
> **whitesmith said:**
> VirtualBox works best if a fair amount of RAM can be allocated to it on  the fly. I have 32 GB in my box. Before jumping on the VirtualVox  approach I would post a question under Virtualization and get the  opinion of an expert. I would hate to recommend one approach only to  have it blow up in your face because you lack the resources to implement  it.

Wow that is a lot of RAM you have there!  I will look into posting under virtualization, but before that I will simply try installing vbox + win 7 + dota 2 to see how it runs.  From my experience with vbox, this should work well (in theory).  I think a vm of windows 8.1 with at least 4 gb RAM would also run pretty well.  I will give it a try and report back when I have time in a few days!

Thanks for letting me know you editted because I did not see that earlier.

-- Sam

---

### Post by Impavidus on 2015-01-19
> **Sam_Osman said:**
> Good call!  I definitely need that!  I still need to learn how to use it.  Is there a name of a specific app you would recommend downloading to edit and compile TeX documents?  (I assume compile is the right word, and I do not know if TeX is itself the name of an editor.  In the past my peers recommend using a LaTeX editor but I was unable to get it working at the time).

--Sam

Just install **texlive** from the software centre. It will get you the command line tools and a decent set of LaTeX packages. If you want more, search the software centre. Or instead of the software centre, use synaptic, which is a far more powerful interface to the Ubuntu repositories (and also recommended).

---

### Post by Sam_Osman on 2015-01-19
Thanks, Impavidus.  I did "sudo apt-get install texlive && sudo apt-get install synaptic" in the shell.  Does texlive also have an editor? or do I just write the files in gedit and then compile with texlive?

Many thanks!

--Sam

---

### Post by Impavidus on 2015-01-19
It does not come with an editor. I write my .tex files in vim, but you can use any text editor you like (gedit, nano, emacs, ...). On the command line you can call```
#To create a .dvi file
latex file.tex
#Or a .pdf file
pdflatex file.tex
```or one of the other associated tools. But if you're a mathemathics student you should be able to find people who are already experienced LaTeX users.

But editors (that is, front ends) with everything integrated are available. You can get TeXworks from the repositories, maybe some others. I don't know them. I prefer the command line stuff.

---

### Post by whitesmith on 2015-01-19
> **Sam_Osman said:**
> That makes sense.  Should I be concerned about lag and errors when running those high-resouce demanding games via Virtual Box on an Ubuntu system?  Ubuntu was lagging when I did the opposite (used Ubuntu vbox on Win 8.1 system) but Ubuntu is running super-fast now when I use it as the main OS.  I will definitely check winehq.org to see what is supported.  Thank you for that.  I am guessing Office 2010 might work and I still have my academic license for it.  And just to clarify, you are saying that Ubuntu + vbox windows is much better than dual booting?

Edit: I suppose I should have mentioned that I am on an ASUS laptop with icore 7 2.4 ghz processor, 8 gigs RAM, nvidia 840M with 2gb ram, and 750 gb hdd @ 5400 RPM (I forgot the exact RPM number but its the 5xxx one).

My experience with VB is that--provided you have enough memory available--it is much better than Ubuntu+Wine. For one thing it's faster, way faster because no application compatibility layer stands between the OS and the app. Also, pure honest-to-goodness Windows is executing your app, so a wider range of programs can be handled the way the developers intended. I've had a dozen Wine problems for every VB issue, but--I harp on this with good cause--you've got to have RAM, RAM, glorious RAM. How much, of course, depends on what the guest OS (Windows) is running. Unfortunately Windows is a memory hog, so experimentation is called for. I wish I could be more helpful that that. Cheers.

---

### Post by sudodus on 2015-01-19
If you want to improve your multimedia experience, I suggest that you install ***ubuntu-restricted-extras***

Maybe you should also explore the other desktop environments (live, without installing). You might like one of the others better than standard Ubuntu.

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")                 

For math you might like ***octave*** (free program with syntax similar to matlab) and ***bc***.

And in order to really get linux at your finger-tips, you need to learn ***bash***, the shell-script language, that is much more advanced than 'DOS-prompt' alias cmd in Windows. Don't rush - ask here, when you need to do something, and be prepared that some things are done in a different way compared to Windows.

Finally, for security maybe you can get some tips from [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by Sam_Osman on 2015-01-19
> **Beta_Lith said:**
> This is a good site! [http://linuxnewbieguide.org/](http://linuxnewbieguide.org/)

Happy to have you onboard!

Once you are satisfied you can run windows inside on Ubuntu and you can run windows applications in Ubuntu by downloading WINE fro the Ubuntu store (Its free)


Thanks you very much! :D I bookmarked and will read later.  I also already have Wine installed but someone else suggested running Windows in virtual box for video games like dota 2 / starcraft / etc.

> **Impavidus said:**
> It does not come with an editor. I write my  .tex files in vim, but you can use any text editor you like (gedit,  nano, emacs, ...). On the command line you can call```
#To create a  .dvi file
latex file.tex
#Or a .pdf file
pdflatex file.tex
```or one of the other associated tools. But if  you're a mathemathics student you should be able to find people who are  already experienced LaTeX users.

But editors (that is, front ends) with everything integrated are  available. You can get TeXworks from the repositories, maybe some  others. I don't know them. I prefer the command line stuff.


Thank you!  Duly noted.  I will try to make a simple tex document with a math function when I have time later to make sure it works right.  I will definitely let you know when I have further TeX related questions! (If you don't mind).


> **whitesmith said:**
> My experience with VB is that--provided you  have enough memory available--it is much better than Ubuntu+Wine. For  one thing it's faster, way faster because no application compatibility  layer stands between the OS and the app. Also, pure honest-to-goodness  Windows is executing your app, so a wider range of programs can be  handled the way the developers intended. I've had a dozen Wine problems  for every VB issue, but--I harp on this with good cause--you've got to  have RAM, RAM, glorious RAM. How much, of course, depends on what the  guest OS (Windows) is running. Unfortunately Windows is a memory hog, so  experimentation is called for. I wish I could be more helpful that  that. Cheers.


Yes, that makes sense and I agree.  Vbox used almost 90% of my RAM when I was on Windows running: Win 7, pfSense, and Server 2008 R2 VMs.  I am considering uprading my RAM to 16 gb (~$180) and maybe my HDD to 1TB SSD (~$450).  I am still debating if these upgrades are worth doing or if I should buy a new computer.  Perhaps I should save the money and just build a solid gaming/power rig (I only own a laptop atm).

> **sudodus said:**
> If you want to improve your multimedia experience, I suggest that you install ***ubuntu-restricted-extras***

Maybe you should also explore the other desktop environments (live,  without installing). You might like one of the others better than  standard Ubuntu.

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")                 

For math you might like ***octave*** (free program with syntax similar to matlab) and ***bc***.

And in order to really get linux at your finger-tips, you need to learn ***bash***,  the shell-script language, that is much more advanced than 'DOS-prompt'  alias cmd in Windows. Don't rush - ask here, when you need to do  something, and be prepared that some things are done in a different way  compared to Windows.

Finally, for security maybe you can get some tips from [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)


Thank you sir!  I definitely appreciate all of the suggestions! :).  I am familiar with the restricted extras and I think they might already be installed.  If not, I will definitely install them when I end up using multimedia.  I normally just listen to pandora radio instead of mp3 files so it might not be for a while, but I suppose I do need something that can play movies in .avi and .mp3 format.  I am guessing those might be apart of the restricted extras package?  I have tried those other guis in the past.  I will give them a try again when I have time, but I am pretty content with the standard ubuntu gui.  I think I will need matlab for my university classes in the next few years so I will definitely install octave!  And yes, I definitely agree about the bash scripting.  I already know how to do a few things but I am still learning.  I found a few reference guides so far but if you have any others you would recommend I would love to read them later!

---

### Post by Sam_Osman on 2015-01-19
One issue I seem to be having right now is that the computer freezes while I am typing on here.  It lets me type a few sentences, sometimes even paragraphs, and then the mouse and keyboard both freeze.  I did alt + ctrl + F1 and then the same with F7 which unfreezes it.  I recently installed nvideo 340, do you think that might be the cause of it?  I apologize if this is beyond the scope of this thread, I can definitely post on a different section if necessary.

---

### Post by DuckHook on 2015-01-19
> **Sam_Osman said:**
> That makes sense.  Should I be concerned about lag and errors when running those high-resouce demanding games via Virtual Box on an Ubuntu system?  Ubuntu was lagging when I did the opposite (used Ubuntu vbox on Win 8.1 system) but Ubuntu is running super-fast now when I use it as the main OS.  I will definitely check winehq.org to see what is supported.  Thank you for that.  I am guessing Office 2010 might work and I still have my academic license for it.  And just to clarify, you are saying that Ubuntu + vbox windows is much better than dual booting?

Edit: I suppose I should have mentioned that I am on an ASUS laptop with icore 7 2.4 ghz processor, 8 gigs RAM, nvidia 840M with 2gb ram, and 750 gb hdd @ 5400 RPM (I forgot the exact RPM number but its the 5xxx one).


It's... well, it's... complicated.

A very few things will run faster in VBox than WINE, but most things will run faster in WINE... *if* they run at all. It's this last that's usually the Achille's heel with WINE.

You see, WINE is actually an implementation of Windows system calls directly onto the Linux kernel. Therefore, it is running on bare metal and, everything else being peachy, it *ought* to run as quickly as any native Linux app. Of course, most times, things aren't peachy. The implementation might be slightly flawed, or the WINE dll is obsolete, or some of WINE's system calls are incomplete. There are thousands of little items that must be running almost perfectly for WINE to do its magic. The fact that it can be done at all is already mindboggling.

VBox on the other hand (or any VM) runs sandboxed within a pretend computer that is a software illusion of a real computer, complete with a pretend CPU, pretend video card, pretend HDD, etc. A genuine Windows install is then fooled into thinking that it is inhabiting an actual physical machine, but at no point is it touching bare metal (an oversimplification but sufficient to give the right idea). It's like "The Matrix" where everyone lives in an induced dream of a seemingly real world. Every Windows system call is intercepted by the virtual machine, translated into a Linux system call, and passed to the kernel within tightly controlled and constrained parameters. This multi-layered process with translations and sandboxing is fundamentally much less efficient than the WINE approach, but has the huge advantage of using an actual Windows OS. Recent improvements to some VMs like Xen and KVM give the guest OS almost bare metal access to some system components and this has improved system responsiveness tremendously, especially with the GPU and therefore games, but this improvement has yet to make its way to VBox.

Therefore, most programs that can be gotten to run under WINE tend to run faster. They use less system resources, less RAM (don't have to run a second OS just to run the app), have direct access to the HDD/NIC/USB port, etc. However, most Windows programs won't run in WINE. There's enough missing or incomplete or unexpected that the program just throws up its hands, picks up its marbles and goes home. If you simply must run such apps, you have no choice but to run them in a VM.

A really powerful modern box has so much power to spare that it may run a VM of Windows at what initially appears to be native speed. But if you try to run a really intense 3D game on it, or a real time 3D CAD rendering, the hit from the additional system overhead becomes obvious. On a WINE install that meets the WINE "platinum" standard, the game runs as fast as it does on native Windows. But unless your base system is some home-built supercomputer, the added overhead and inefficiency imposed by the VM is noticeably slower.

I have both WINE and a VM installed on my computer. If a Windows app runs in WINE, then I leave it there and enjoy the benefit of the higher speed. But if it doesn't work, then some time ago, I gave up trying to really tinker with it, and I just run it in a VM. But then, I don't run modern 3D-intensive games, so my resource requirements are very modest, which a VM can easily handle.

Your laptop is a top-grade machine. An icore 7, 8GB RAM and nVidia 840M is, frankly, nuts, and you don't need to do anything to it to get desktop-level performance from your VM. If your VM won't give you acceptable gaming performance, then your game is not meant to be VM'd and you will have to run it either dual boot or on WINE.

Last but not least, it is isn't a matter of whether a VM is "better" than dual booting. It is more *convenient*. So, if a VM is fast enough to service all your needs, then the fact that it can be run inside a window on your base OS while you are multitasking at a whole bunch of other things is a truly sublime experience. But if it means that you can't stand the lag in your favourite game, then there's nothing "better" about it and you are better off dual booting.

---

### Post by Sam_Osman on 2015-01-19
Another question:  What backup program do you guys recommend?  I am currently installing and going to try clonezilla.  I want a program that basically clones an exact copy of my hard drive (and all partitions) so that if something got messed up with my hard drive I can just paste that copy on top of another hard drive and everything will be the same as before.  I am guessing computers work like that right?  If you make an exact copy of the hard drive then everything will be exactly the same, right? lol XD

Edit: @DuckHook: Thank you for your detailed explanation, that makes a lot of sense.  I saw that when you run VBOX (or perhaps I am thinking of VMWare, I don't recall) on a native Windows system there's a feature where the VM and the native system become merged together.  It is related to guest additions (which let you drag and drop stuff back and forth for example) but it takes it a step further where the two machines are truly seemless and the windows are transparent and stuff.  I don't remember the name for it but you might know what I am talking about.  Do you think that feature would make a difference in the performance?  I guess you would still have the overhead of the VM because that VM is still open in the background regardless.  Anyway, thank you for the compliment about my laptop.  I agree, it is definitely a great laptop and I bought it so that I can play newer games with a high frame rate at a reasonable graphics setting.  I can run league of legends on ultra at 60 fps, and starcraft at high or so (but I haven't measured the frames)... What I am getting at is I noticed the system is getting slowed down due to the hard drive being at a constant 100% when I do a few things and then when I run all those VMs on native windows it will use about 90% RAM so I was thinking of upgrading those two components for ~$600 or so. Not sure if it's worth?

---

### Post by DuckHook on 2015-01-19
*Clonezilla* is excellent at cloning, but it is inflexible and does not make a good actual backup app. Power-users like the flexibility of the command line and the power of scripting and will usually use *rsync*, which is one of the best apps ever developed for Linux. You can wrap a GUI around it by installing *grsync*. The native backup software in Ubuntu, *deja-dup*, is also just another graphical front end for *rsync*. All of these tools allow for incremental backups, touches only changed files, and so forth, which *Clonezilla* will not handle.

Re: VBox

The mode you are thinking of is called "Seamless Mode" and it does nothing to speed up anything. In my experience it actually makes your VM more fragile, more brittle. I've had VM apps freeze up on me because they are being run in seamless mode whereas they are well behaved in a visibly defined and windowed VM. As a general rule, whenever you make anything more complicated, you introduce more surface for breakage. And as a budding computer engineer, you probably know that the more tricks you must use to achieve a desired appearance, the more complexity you are actually employing for those tricks. It's only natural at this stage of experimentation that you will want to download everything and try everything, but I've gotten to the point where I want to simplify, simplify, simplify.

Your 8GB will go a long way but it has limits. You can't run too many VMs at once, especially if they are all taxing the CPU, the HDD or the GPU hard. Also, if you are running a lot of processes in a lot of VMs, your OS will start going to SWAP which will just bog your system down like nothing. Everything in moderation, like the old philosophers said, and you won't get into trouble.

I would not find the additional $600 worth it, but this is a personal decision. If you simply want the bragging rights of running five VMs at once plus a low-endish game at the same time, then maybe it is worth it, for you. I will note that practically any Linux distro uses RAM more efficiently than Windows, so you might want to keep this in mind before shelling out your hard-earned cash. At least give it a go with what you've got before jumping to conclusions.

---

### Post by sudodus on 2015-01-20
> **Sam_Osman said:**
> ...

I normally just listen to pandora radio instead of mp3 files so it might not be for a while, but I suppose I do need something that can play movies in .avi and .mp3 format. I am guessing those might be apart of the restricted extras package?
 Yes,

'Installing this package will pull in support for MP3 playback and decoding,
support for various other audio formats (GStreamer plugins), Microsoft fonts,
Flash plugin, LAME (to create compressed audio files), and DVD playback.'
> 
... And yes, I definitely agree about the bash scripting.  I already know how to do a few things but I am still learning.  I found a few reference guides so far but if you have any others you would recommend I would love to read them later!

You can browse the internet for ***bash tutorial***. You can also start at

[https://help.ubuntu.com/community/Beginners/BashScripting](https://help.ubuntu.com/community/Beginners/BashScripting)

[https://help.ubuntu.com/community/CategoryCommandLine](https://help.ubuntu.com/community/CategoryCommandLine)

---

### Post by mastablasta on 2015-01-20
I think Dota 2 has Linux version.

edit - yes: [http://www.omgubuntu.co.uk/2013/07/dota-2-now-available-on-steam-for-linux](http://www.omgubuntu.co.uk/2013/07/dota-2-now-available-on-steam-for-linux)

---

### Post by Sam_Osman on 2015-01-20
> **sudodus said:**
> Yes,
'Installing this package will pull in support for MP3 playback and decoding,
support for various other audio formats (GStreamer plugins), Microsoft fonts,
Flash plugin, LAME (to create compressed audio files), and DVD playback.'


Sorry I meant to say .mp4 (video) not .mp3. Not sure if that makes a difference but I just caught that typo.

p.s. I am still reading and will respond to the other posts soon.

---

### Post by sudodus on 2015-01-20
Yes, mp4 codecs are also included. If you want to convert between video formats, you can do it with the advanced tool ***ffmpeg***. There are also easier alternatives, for example avidemux and openshot (the latter is also an editor for video-clips). ***audacity*** is an editor for sound-tracks.

---

