---
title: "I used Mono Installer,but i have some troubles"
date: 2006-04-28
forum: Programming Talk
---

### Post by Zonkle on 2006-04-28
Hello,

Today I download the Mono installer 1.1.15 and installed it and it didn't show any errors.

But when I open the mono directory and try to open Mono Develop it doesn't open, why ?
Do I have to download Mono Develop also ?

And do I have to do anything extra to get the Glade GUI ?

Thanks.

---

### Post by malavar on 2006-04-28
did you download it from the website? if so give the repos a try.

sudo apt-get install monodevelop

---

### Post by Zonkle on 2006-04-29
Thanks for your reply.

I downloaded only the installer from mono project web site.

But after i installed it, i saw in its folder like an icon for mono develop .... i thought it is installed.

So do i have to download it ?

---

### Post by kaamos on 2006-04-29
If you downloaded mono from the website you really should NOT install any mono-stuff with apt. They are completely different versions by now, as breezy is 6 months old and mono developement is quite fast.

Monodevelop should start just by typing "monodevelop" in a terminal. If it say command not found or some other error, your path is probably wrong and you should add these to your /home/username/.bashrc
> 
export PATH="$PATH:/opt/mono/bin"
export PKG_CONFIG_PATH="$PKG_CONFIG_PATH:/opt/mono/lib/pkgconfig:/usr/local/lib/pkgconfig"
export MANPATH="/opt/mono/share/man:$MANPATH"
export LD_LIBRARY_PATH="/usr/lib:/opt/mono/lib:$LD_LIBRARY_PATH"

Note that if you did not install mono to /opt you have to tweak to paths to match you install.

---

