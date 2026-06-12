---
title: "New to Ubuntu &amp; Linux - a quick &amp; possibly simple question"
date: 2020-01-01
forum: New to Ubuntu
---

### Post by camarillo-brillo on 2020-01-01
Hello,

So, after years of using a Mac (and PCs before that), I finally decided to give Linux a try. 
I'm a complete novice, and learning as I go along. 
I have a very basic question. I hope it doesn't sound foolish.

It seems I need to add some codecs or packs. 
My question is: after I have downloaded it, where do I keep/place the codecs/packages, etc.?

Should I create a folder for ell the files I need to add/download?

Any help would be greatly appreciated.

---

### Post by Bashing-om on 2020-01-01
camarillo-brillo; Hello - Welcome to the forum.

> 
It seems I need to add some codecs or packs.
My question is: after I have downloaded it, where do I keep/place the codecs/packages, etc.?


NOoooo :) going about this in the wrong fashion in linux. We have a software repository.

See:
in terminal execute:
```

apt show ubuntu-restricted-extras

```

is ubuntu-restricted-extras the package you want/need ?
Else provide additional background information as to what your need and end goal is.

[INDENT][INDENT]ubuntu - 
[INDENT][INDENT]we take care of our own
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by camarillo-brillo on 2020-01-01
Thanks for the quick reply. 
It seems I need to add something to Rhythmbox to let me play AIFF files.

---

### Post by CatKiller on 2020-01-02
Rhythmbox uses the GStreamer media framework. AIFF support is provided by gstreamer-plugins-bad, which is in the Universe repository.

---

### Post by guiverc on 2020-01-02
Read Catkiller's answer

> [COLOR=#000000]AIFF support is provided by gstreamer-plugins-bad, which is in the Universe repository.[/COLOR]

As I'm using Lubuntu (a flavor) 'universe' or the community-supported repository is already installed (flavor files are found only in 'universe', which applies equally to any other flavor Xubuntu, Kubuntu, Ubuntu-MATE, Ubuntu-Budgie, Ubuntu-Studio etc)

It needs to be enabled for main Ubuntu though ([https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu))

For standard releases there is little consequence (support-in life terms) between main & universe; but in LTS releases it's more significant.

Everything in 'main' is supported by Canonical for five years for LTS releases, however the standard length of support in 'universe' is only 3 years for LTS with some packages having different (eg. Ubuntu Studio 18.04 was not a LTS, thus 9 months for its packages; extended support being provided via PPA).  Ubuntu server/desktop enable only 'main' or Canonical guaranteed supported packages with a known/fixed support life, 'universe' can be enabled if desired.

---

### Post by Autodave on 2020-01-02
Simply said, you do not want to download and install anything from the 'net.  Everything that you are probably ever going to need is available from the Software center.  Click on what you want and it is downloaded and installed for you.  Very simple.  And very different from anything that you are used to.

---

### Post by camarillo-brillo on 2020-01-02
> **Autodave said:**
> Simply said, you do not want to download and install anything from the 'net.  Everything that you are probably ever going to need is available from the Software center.  Click on what you want and it is downloaded and installed for you.  Very simple.  And very different from anything that you are used to.

Thanks. 
OK, so I download what  need, then I install it. 

But I don't need to drag anything from the downloads folder?
I don't need to copy anything?

And, once it's been installed, do I remove it from the download folder?

---

### Post by tea for one on 2020-01-02
The software (from the Software Centre) will be downloaded and installed automatically.

No dragging, no copying, no user intervention.

Why not try it - I think that you will be pleasantly surprised.

Good luck

---

### Post by CatKiller on 2020-01-02
> **camarillo-brillo said:**
> Thanks. 
OK, so I download what  need, then I install it. 


**You** don't need to do either of those things. [This](https://en.wikipedia.org/wiki/Package_manager) is the concept that you need to grasp. The package manager does all the downloading, installing and updating for you.

---

### Post by Autodave on 2020-01-02
Go to the software center and start browsing through the thousand upon thousands of free programs that are there.  I have been using 'buntu for about 12 years now across 10 - 13 machines and I have not installed ANYTHING from the 'net.

If you are not sure what an equivalent program in Linux is to what you were using in Win or Mac, just ask.  For instance, LibreOffice will do all of your MS Office chores.  Gimp will do what Paint Shop Pro will do.

---

### Post by sudodus on 2020-01-02
It is usually enough for me to install the 'restricted extras' package. I do it via the command (but you can also do it via some graphical program as the advice in the previous posts). Please try

```

sudo add-apt repository multiverse
sudo apt update
sudo apt install ubuntu-restricted-extras  # in standard Ubuntu
sudo apt install kubuntu-restricted-extras  # in Kubuntu
sudo apt install lubuntu-restricted-extras  # in Lubuntu
sudo apt install xubuntu-restricted-extras  # in Xubuntu

```

and after that I think you will have the necessary codecs to play most multimedia file types.

Tip:

When there is a screen with blue background you need to press the TAB key until the OK button is selected, and then press the Enter key to accept (getting the Microsoft fonts).

---

### Post by deadflowr on 2020-01-02
I would suggest either learning command line options to install software, or install Ubuntu's alternate package manager *synaptic* from Ubuntu's Software center.

I suggest this because Ubuntu's Software center is not good at listing any non-Desktop-centric related software.

(On top of that, the Software program also has the ability to install Ubuntu's new packaging format *snap*,
which are fairly restrictive by design and can cause a lot of pain and confusion if you do not know they exist and whether you installed a snap package or not)

Synaptic, on the other hand, will list all available software.
(And has no means to install snap packages, at least not at this time)


ftr, Ubuntu's Software center does have the ability, though, to install codecs, but they must be installed individually one at a time.
It's slow and tedious.
(Codec packages are found in Add-ons >> Codecs in Ubuntu Software or also known as the Software program)
> but they must be installed individually one at a time.
Another benefit of synaptic is that you can select and install all packages you want in one easy move.

That's my rambling 2 cents.

---

### Post by camarillo-brillo on 2020-01-02
> **CatKiller said:**
> **You** don't need to do either of those things. [This]("https://en.wikipedia.org/wiki/Package_manager") is the concept that you need to grasp. The package manager does all the downloading, installing and updating for you.

Thank you! I get it now. 
Wow, that really changes everything!

---

### Post by TheFu on 2020-01-02
> **camarillo-brillo said:**
> Thank you! I get it now. 
Wow, that really changes everything!

And if you want an all-in-one media player that isn't tied to external codecs, use **VLC**.  It is in the repos.  The way I see it, if vlc can't play it, then I really, really, don't want it.  The only exception would be commercial DVDs and commercia BluRay discs.  To get those working depends on the specific way vlc is installed.  snap packages have broken vlc for external DRM DVD support with 19.04 and 19.10 releases. It may have been fixed. IDK.

Package management is the primary reason I choose to use Linux the last 25+ yrs whenever possible.  Patching the OS and applications is all included within the package management.  

Snap packages have added some complexities and broke a few things. Hopefully, they will figure it out for production use that doesn't cause surprises, failures, or 10GB of wasted storage.  Many of us use systems with just 16G of storage total, so snaps wasting storage are a real problem.  Snaps aren't exactly new, but they weren't forced onto people until 19.10.  Some well-known applications moved to snap-only releases.

Even with these added complexities, Linux package management is still 1000x better than OSX or Windows methods.  The idea that an "app store" is new is simply wrong. Linux has had repositories since the 1990s.

---

### Post by camarillo-brillo on 2020-01-03
Thanks again to everyone that has offered some help & suggestions. 
I am very grateful for all the support I have received so far. 

I have somehow managed to use up about 18 GBs of space on my hard drive. 
I have not added anything to my new computer yet - no photos, no videos, no music, etc.  
Despite only having Ubuntu on my computer, it says it's taking up 7.2%

I must have done something wrong when I first tried to add applications. 
I've got Ubuntu 18.04
I have a 256 GB hard drive. 

Will I need to reinstall Ubuntu?
Do I have to reformat the drive? 
How do I recover the lost space?

---

### Post by deadflowr on 2020-01-03
Ubuntu ships with a disk usage program called Disk Usage Analyzer.
You can use that to see where space is being eaten up.

---

### Post by CatKiller on 2020-01-03
> **deadflowr said:**
> Ubuntu ships with a disk usage program called Disk Usage Analyzer.
You can use that to see where space is being eaten up.

And bear in mind that it shows *of the space that is used* where that space is being used. It will necessarily always add up to 100%. A lot of people get freaked out by that for some reason.

---

### Post by TheFu on 2020-01-03
The quick ways to share storage use is to use the CLI/shell.

**df -Th** will show the use on any mounted partition.
**lsblk -f**  will show the disk layout and partition, file system used, and logical volume sizes

Also, be aware that snap packages will eat storage faster than normal DEB packages because they bring dependencies along AND because they like to keep a few versions around even after an update happens.  There are commands to remove older snap packages.  I don't use snaps (and don't have any of those tools loaded), so don't know what those commands are.  **snap list** should show them.

Posting shell/CLI output here lets us see the data. We are used to seeing terminal commands and output.  It is important to show both. I avoid using GUI programs for things like this because every GUI programmer decides something different for showing allocations/used storage. My servers don't have a GUI, so why bother learning to use to methods?

On a fresh installed system, I'd be freaking out like you are if 18G was used!  I have entire desktops that don't use that amount even with the OS, HOME, and my programming files. Here's my main desktop system, as proof: 
```
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/vda1      ext4   20G   17G  1.9G  90% /

```
17G used and that is after 9 yrs of upgrades from 10.04 forward.  Small, light, fast. That's my motto.  Plus, if I don't keep the files, I don't need to back them up.

---

### Post by lwalper on 2020-01-08
You don't need to install anything from the net with the possible exception of Tor Browser. I've not been able to get the repository store version to work in 18.04. Downloaded the files from the torproject, followed the instructions there and all is good.

---

### Post by mastablasta on 2020-01-09
root (/) should have less on install (6-8 GB, maybe 10 GB at max if you added osme extra stuff).

i don't know how you looked at it, but /swap partition or the swap file could also reserve their space.

---

