---
title: "C programming with xcb, missing functions and typedef in randr.h"
date: 2017-04-12
forum: Programming Talk
---

### Post by cocodu13820 on 2017-04-12
Hello everyone,I am trying out elementaryOS right now (based on ubuntu 16.04 LTS) and tried to continue working on a project I have in C at the moment.Problem is:I was working on that project with an ArchLinux based distro before, and on now it seems like I am missing functions and typedefs in the randr.h file. [COLOR=#6897bb]0[/COLOR]) {        infoMonitor = monitorIterator.[COLOR=#9876aa]*data*[/COLOR][COLOR=#cc7832];[/COLOR]printf([COLOR=#6a8759]"Monitor name: [/COLOR][COLOR=#cc7832]%d\n[/COLOR][COLOR=#6a8759]"[/COLOR][COLOR=#cc7832], [/COLOR]infoMonitor->[COLOR=#9876aa]*name*[/COLOR])[COLOR=#cc7832];[/COLOR]printf([COLOR=#6a8759]"Monitor nbr: [/COLOR][COLOR=#cc7832]%d\n[/COLOR][COLOR=#6a8759]"[/COLOR][COLOR=#cc7832], [/COLOR]monitorIterator.[COLOR=#9876aa]*rem*[/COLOR])[COLOR=#cc7832];[/COLOR]printf([COLOR=#6a8759]"Primary: [/COLOR][COLOR=#cc7832]%d\n[/COLOR][COLOR=#6a8759]"[/COLOR][COLOR=#cc7832], [/COLOR]infoMonitor->[COLOR=#9876aa]*primary*[/COLOR])[COLOR=#cc7832];[/COLOR]printf([COLOR=#6a8759]"[/COLOR][COLOR=#cc7832]%d[/COLOR][COLOR=#6a8759]x[/COLOR][COLOR=#cc7832]%d\n[/COLOR][COLOR=#6a8759]"[/COLOR][COLOR=#cc7832], [/COLOR]infoMonitor->[COLOR=#9876aa]*width*[/COLOR][COLOR=#cc7832], [/COLOR]infoMonitor->[COLOR=#9876aa]*height*[/COLOR])[COLOR=#cc7832];[/COLOR]printf([COLOR=#6a8759]"x offset: [/COLOR][COLOR=#cc7832]%d[/COLOR][COLOR=#6a8759], y offset: [/COLOR][COLOR=#cc7832]%d\n\n[/COLOR][COLOR=#6a8759]"[/COLOR][COLOR=#cc7832], [/COLOR]infoMonitor->[COLOR=#9876aa]*x*[/COLOR][COLOR=#cc7832], [/COLOR]infoMonitor->[COLOR=#9876aa]*y*[/COLOR])[COLOR=#cc7832];[/COLOR]xcb_randr_monitor_info_next(&monitorIterator)[COLOR=#cc7832];[/COLOR]}    printf([COLOR=#6a8759]"---------------------------[/COLOR][COLOR=#cc7832]\n[/COLOR][COLOR=#6a8759]"[/COLOR])[COLOR=#cc7832];[/COLOR][COLOR=#cc7832][/COLOR][COLOR=#cc7832]**return **[/COLOR]xcb_randr_get_monitors_monitors_length(monitorsReply)[COLOR=#cc7832];[/COLOR][COLOR=#A9B7C6][FONT=&amp]}[/FONT][/COLOR][/CODE]Can this be because ArchLinux as a version of xcb that is higher ?(if you want to see the c file by yourself, it's [here]("https://github.com/SYCBWM/SYCBWM/blob/master/main.c"))

---

### Post by steeldriver on 2017-04-12
Yes it most likely is a versioning issue - the almighty google seems to suggest that the "monitors" feature is new in XRandR 1.5 and doesn't get supported in libxcb until version 1.12

---

### Post by cocodu13820 on 2017-04-12
> **steeldriver said:**
> Yes it most likely is a versioning issue - the almighty google seems to suggest that the "monitors" feature is new in XRandR 1.5 and doesn't get supported in libxcb until version 1.12I thank you very much, Ubuntu seems to be to much of a pain for me, I try to use it again and again but it always has something that doesn't work.It just seems like it's not the right distro for me.I am currently under Fedora 25 and have no problem at all, even with wayland.

---

