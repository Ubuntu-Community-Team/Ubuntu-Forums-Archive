---
title: "Won't Install Laptop-Mode-Tools"
date: 2012-08-20
forum: New to Ubuntu
---

### Post by coloreporter on 2012-08-20
I tried installing Laptop-Mode-Tools and got this error message:

Selecting previously unselected package laptop-mode-tools. 
dpkg: regarding .../laptop-mode-tools_1.52-1ubuntu2_all.deb containing laptop-mode-tools: 
 pm-utils conflicts with laptop-mode-tools (<< 1.55) 
  laptop-mode-tools (version 1.52-1ubuntu2) is to be installed. 
dpkg: error processing /home/hans/Downloads/laptop-mode-tools_1.52-1ubuntu2_all.deb (--install): 
 conflicting packages - not installing laptop-mode-tools

It seems I need to uninstall "pm utils" to be able to install laptop-mode-tools.  Is that a wise thing to do?

Thanks.

---

### Post by Daveth on 2012-08-20
"pm-utils is a small collection of scripts that handle suspend and resume on behalf of HAL."

so I would imagine uninstalling makes those 2 functions difficult to pull off!

---

