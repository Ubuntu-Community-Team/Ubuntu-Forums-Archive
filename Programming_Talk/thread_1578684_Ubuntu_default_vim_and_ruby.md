---
title: "Ubuntu default vim and ruby?"
date: 2010-09-20
forum: Programming Talk
---

### Post by Kurtosis on 2010-09-20
Edit:  I just installed vim-gui-common (and its dependency vim-gnome) and that added Ruby, including to terminal vim.

I see Ubuntu's default vim is compiled without ruby support.  Is there another way to get ruby support besides compiling and installing a new vim?  

For example, I see vim-gnome and vim-gtk packages both include ruby support, is there any issue with installing one of these instead?

---

### Post by lloyd_b on 2010-09-21
> **Kurtosis said:**
> Edit:  I just installed vim-gui-common and vim-gnome and that added Ruby, including to terminal vim.

I see Ubuntu's default vim is compiled without ruby support.  Is there another way to get ruby support besides compiling and installing a new vim?  

For example, I see vim-gnome and vim-gtk packages both include ruby support, is there any issue with installing one of these instead?
Ubuntu's default vim ("vim-tiny") is very stripped down.  Have you tried installing the package "vim-full"?  It contains support for just about everything...

Lloyd B.

---

### Post by Kurtosis on 2010-09-21
I tried, but that package doesn't seem to exist.  I searched both Synaptic and Aptitude, and tried to install via Aptitude, but got nothing.  Is there really such a package?

---

### Post by lloyd_b on 2010-09-22
> **Kurtosis said:**
> I tried, but that package doesn't seem to exist.  I searched both Synaptic and Aptitude, and tried to install via Aptitude, but got nothing.  Is there really such a package?
Oops.  Looks like the "vim-full" package was dropped after Jaunty (I upgrade my machine from release to release, so it's probably been that long since I did a clean install).  I would expect the full version to be in the package "vim" - did you try installing that?

Lloyd B.

---

### Post by Kurtosis on 2010-09-22
Thanks, vim is what I had originally, but it was compiled with -ruby instead of +ruby.  

Installing vim-gui-common (and its dependency vim-gnome) solved it though.  Maybe there are three levels now - vim-tiny, vim, and vim-gui-common.

---

