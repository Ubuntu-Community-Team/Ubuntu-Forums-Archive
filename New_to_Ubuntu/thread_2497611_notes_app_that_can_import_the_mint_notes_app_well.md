---
title: "notes app that can import the mint notes app well"
date: 2024-05-12
forum: New to Ubuntu
---

### Post by ronjjjg8885 on 2024-05-12
i'm planning to switch to ubuntu
i want to ask..
is there a notes app in ubuntu similar to the one that mint has?

i want to import all my notes well in such app..

is there such thing?

if not, is it risky installing ppa for the mint app to be installed on ubuntu?

tnks
and love from israel..

---

### Post by TheFu on 2024-05-12
Do you mean _Linux Mint_?  If so, just use the same program. [https://www.omgubuntu.co.uk/2021/12/install-linux-mint-sticky-notes-app-ubuntu](https://www.omgubuntu.co.uk/2021/12/install-linux-mint-sticky-notes-app-ubuntu)

I was running Ubuntu as my desktop from about 2006 - 2022, when I switched to Linux Mint to avoid some of the choices Canonical had made to force certain package types onto users.  I still have lots of Ubuntu systems around, just not my desktop. 

You are the first I've heard even considering going from Mint --> Ubuntu.  At my LUG, about 30% use Linux Mint. Oddly, the 2nd most popular distro there is MXLinux (a type of debian without systemd).  Then we have a few Arch and Fedora guys.

---

### Post by ronjjjg8885 on 2024-05-12
yes,
so am i safe to go with this link that you added? it requires a new ppa..
tnx

---

### Post by TheFu on 2024-05-12
> **ronjjjg8885 said:**
> yes,
so am i safe to go with this link that you added? it requires a new ppa..
tnx

Safe is a judgement call.  Only you can decide if the PPA is reputable for your needs.  Every repo or PPA effectively has root access to your system.  If you are running code from a project already and they have a PPA, there is already *some level of trust*. After all, running software under your userid gives that software all the same access that you have on the system already.

I stick with core repos from Canonical and PPAs only from the specific project team responsible for the software.  Some say that I'm overly cautious.  With all the 3rd parties trying to corrupt the software development on F/LOSS project teams (especially Java, Javascript, and php libraries), I'm happy to choose tools that are available from the core places.

I use vim for taking notes and vim-wiki to keep them organized.  I tried about 20 different methods before deciding that vim-based tools were best for my needs.  To each their own.  Lots of people seem to like CherryTree. [https://opensource.com/article/19/5/cherrytree-notetaking](https://opensource.com/article/19/5/cherrytree-notetaking)

---

### Post by ronjjjg8885 on 2024-05-12
ok..
would it be very simple to import notes from the linux mint app to cherrytree?

---

### Post by TheFu on 2024-05-12
> **ronjjjg8885 said:**
> 
would it be very simple to import notes from the linux mint app to cherrytree?

Does the Linux Mint notes application have any Export capability?  If so, what formats does it support?

Does the CherrTree  application have any Import capability?  If so, what formats does it support?

Are any of the Export ---> Import formats the same?  Use one of those.  You know, you can load CherryTree on Mint and try it BEFORE you swap OSes.

---

### Post by ronjjjg8885 on 2024-05-14
at the end i copied and pasted manually into the new notes app [cherrytree]

i didn't see any way to import json files..

---

### Post by TheFu on 2024-05-14
Why didn't you stick with the Mint Notes application?  
Did CherryTree seem like a better tool for your needs?

CherryTree supports about 20 different import methods: [https://www.giuspen.com/cherrytreemanual/#_importing](https://www.giuspen.com/cherrytreemanual/#_importing)
Export support is less impressive.  Will you be stuck with a new tool that can't easily export to the next tool you choose?  Whenever I'm picking a new tool, I look for how trapped my data will be BEFORE I transition.  After the transition, it is too late.

I'm curious.

---

### Post by ronjjjg8885 on 2024-05-15
>  Did CherryTree seem like a better tool for your needs?

yes
i don't have many notes.
i can switch manually

---

