---
title: "Mono installation is fudged, related to beryl"
date: 2006-11-24
forum: Programming Talk
---

### Post by skelooth on 2006-11-24
note: I tried posting this once but I don't see it on the thread listing, so I apologize if there's a duplicate floating around.

I asked this on the Desktop environment's board, but after 2 days it's gotten no responses. Since I think the problem is pertaining to mono I thought maybe I'd have a better chance asking here. Here's the original post.

--------

Really quick history:

I have an Nvidia 7950gt and wanted to try beryl, so I followed the guide in the wiki. Basically add the repos then apt-get the packages and run beryl-manager.

Well... that worked and worked great.

My friend recently ported and added to a game we had written a while back to C# but I couldn't run it because the mono in the repositories wasn't new enough. So I apt-get autoremoved mono and installed mono 1.2 to /opt/ right from the official site. Then I deleted the link in bin with sudo rm /usr/bin/mono

Well, all was well and fine... until I went to restart my box and it told me that my x config file was no good. I tried restoring my back up config w/ just the nvidia drivers but it didn't help, nor did replacing it with my original vga configuration and running nvidia-xconfig... so I had to recompile and reinstall the driver.

Now forward to the present, I'd really like to have beryl back on my desktop. Installing it goes fine, I follow the instructions from the wiki guide. But when I type in beryl-manager the screen locks up and I have to ctrl-alt-backspace out of it.

Sometimes it will lock up after spitting out errors, sorry i can't copy and paste them... BUT.....

it complains about mono 1.2.1 not having version information for libpng12.so.0

I tried using synaptic to remove everything beryl related and reinstalled, no go. I tried sudo apt-get install mono and mono-runtime but... it doesn't seem to actually be installing it? (It does not add ANYTHING executable named just "mono" anywhere on my system, even after deleting my 1.2.1 installation).

---

