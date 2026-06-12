---
title: "New Chrome install - start without terminal?"
date: 2014-06-13
forum: New to Ubuntu
---

### Post by BeachBuddah on 2014-06-13
It's funny - the first 6 answers on Google all tell me how to start Chrome VIA the command line.

Running 14.04 on an HP laptop.  Had Chrime and wanted to update with newer more secure version.

When I download from Google, I have the choice to open via the Software Center or just save.  Either way, the Software Center is utilized and when done on the Chrome page I am told to start the program via the terminal.  There is a Chrome icon but if I connect it to the launcher it does nothing except throb a few times and then subside.  If I close the terminal, I am reminded that a process is running and closing the terminal blablabla.

What I would like is to download a new version of the Chrome browser that can run from an icon in the launcher and not require the terminal to commence,

Any help?

---

### Post by deadflowr on 2014-06-13
I'm not getting this.
When you installed chrome, it adds the chrome repos to your system, and so it will always get updated to the latest version, as long as you install your updates.
No need to reinstall it.

Other then that, perhaps remove the launcher icon for chrome, open the dash, search "Chrome", launch that, then look at the launcher-dock and locate the chrome icon, then right-click and re-lock it to the launcher.

---

### Post by squakie on 2014-06-14
I'm probably going to show my stupidity here, but is there some sort of difference between "Chrome browser" and chromium?  I know you can install chromium from the repositories themselves.

---

### Post by squakie on 2014-06-14
Ok, I downloaded the 32-bit deb for Chrom from Google and installed it via the software center.  I'm running xubuntu, and Chome just shows and executes via the menus.

I had 14.04 running on a new 64-bit laptop, but I just broke the dang thing (my fault and I can't afford to fix it right now), so I'm trying to remember things.  I *think* if you go to /usr/share/applications you find the desktop launcher for Chrome.  Copy the launcher to your desktop folder, then see if it works.

---

### Post by deadflowr on 2014-06-14
> **squakie said:**
> I'm probably going to show my stupidity here, but is there some sort of difference between "Chrome browser" and chromium?  I know you can install chromium from the repositories themselves.

The difference is that chromium is Free software, mostly. So it doesn't include parts like flash.
Chrome does include flash, and other stuff you can deem non-free.
If you want those nonfree items on chromium, then you have to install them yourself.
Chrome has them ready-made out of the box.

---

### Post by squakie on 2014-06-15
Thanks for that explanation! ;)   to the OP:  did you try finding the desktop launcher and copying it to your Desktop folder?

---

### Post by BeachBuddah on 2014-06-15
> **squakie said:**
> Thanks for that explanation! ;)   to the OP:  did you try finding the desktop launcher and copying it to your Desktop folder?

I did, but that didn't work either.  It appears I was merely ahead of the curve, as deaflower suggested.  While I was mucking around with all the possibilities, I was notified there were updates to be had and went along with that.  Lo and behold, the update to Chrome 35.x was part of it all.  By now, this is solved by dint of time passing, not 'doing' anything to resolve the issue.

---

