---
title: "libavcodec2: broken packages"
date: 2005-02-28
forum: Repositories &amp; Backports
---

### Post by oceanelement on 2005-02-28
Recently I have been trying to install mplayer on Hoary amd64, but I run into a problem that is given below: 

[FONT=Courier New]
bash:~# apt-get install mplayer
Reading Package Lists... Done
Building Dependency Tree... Done
Note, selecting mplayer-amd64 instead of mplayer
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer-amd64: Depends: libavcodec2 but it is not installable
E: Broken packages[/FONT]

any ideas on what this could mean? Am I missing a synaptics link? Or is it that the libavcodec2 is not available at the moment for the Hoary amd64 dist.? Thanks in advance for any help.

Elijah

---

### Post by kokotero on 2005-05-16
Hi oceanelement

I found an libavcodec2 package for ubuntu googleing at this address:
[http://search.belnet.be/packages/ubuntu/ubuntu/pool/multiverse/f/ffmpeg/](http://search.belnet.be/packages/ubuntu/ubuntu/pool/multiverse/f/ffmpeg/)

You may require to fill some dependencies, in my case i executed:
$ sudo apt-get install libfaad2-0 libimlib2 liblame0 libungif4g

Install libavcodec2 (after downloading it). I get the one for x86, install what best fits your architecture:
sudo dpkg -i libavcodec2_0.4.9-pre1-0.2_i386.deb

Then you can install mplayer:
$ sudo apt-get install mplayer-custom

Note: You need to add multiverse to your sources.list:
$ sudo nano /etc/apt/sources.list
copy both lines ending with universe (uncomment then if needed) and change universe with multiverse.

Hope it helps

KoKo

---

