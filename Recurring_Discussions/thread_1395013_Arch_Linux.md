---
title: "Arch Linux"
date: 2010-01-31
forum: Recurring Discussions
---

### Post by KhRiZiZi on 2010-01-31
Hey guys, I'm here getting really tired of distros like Ubuntu, openSuSE, etc doing all the work for me, I know theres the option to just do it yourself in the terminal and stuff. The thing is if you don't need to use it, why use it? I don't know much about Linux in general maybe that's because I started with Ubuntu. Anyways I though I'd install Arch Linux and maybe try to actually learn something. I downloaded the Core ISO from their site by torrent. Burned it, etc. Installed it fine. But Post-Install, installing the GUI and everything I can't get. I found a guide that I was trying to follow over my PS3 browser. The Arch Linux beginners guide.

[http://wiki.archlinux.org/index.php/Beginners%27_Guide](http://wiki.archlinux.org/index.php/Beginners%27_Guide)

I got to Step 2, followed the instructions fine, @**Force pacman to refresh the package lists **I get stuck because when I do that it says something about me having no repositories to fetch from (pretty much)

I uncommented the Repositories, and I uncommented the Waterloo (Canadian) mirror and I uncommented all the mirrors in USA & Canada in the mirrorlist.backup like it said.

Does anyone know what's going on? Or a better guide that explains the whole post-install better? 

Thanks.
****

---

### Post by Skripka on 2010-01-31
Does a basic ping command work to google.com?

I'd guess your internet isn't working.

---

### Post by chucky chuckaluck on 2010-01-31
where exactly are you in the process? ("step 2" in that link is not what you're describing). also, what is the exact error message and to which command?

---

### Post by Eisenwinter on 2010-01-31
Did you sync your mirrors?

Try doing a pacman -Sy

---

### Post by ~sHyLoCk~ on 2010-01-31
Please ask for Arch support in [Arch forum]("http://bbs.archlinux.org/").

This will prevent any idiotic comments and hatred against Arch here.

---

### Post by fromthehill on 2010-01-31
arch can be a real pain to setup properly with a desktop environment (permission etc)

if you get stuck at this I wouldn't bother going any further

---

### Post by falconindy on 2010-01-31
> **KhRiZiZi said:**
> Hey guys, I'm here getting really tired of distros like Ubuntu, openSuSE, etc doing all the work for me, I know theres the option to just do it yourself in the terminal and stuff. The thing is if you don't need to use it, why use it? I don't know much about Linux in general maybe that's because I started with Ubuntu. Anyways I though I'd install Arch Linux and maybe try to actually learn something. I downloaded the Core ISO from their site by torrent. Burned it, etc. Installed it fine. But Post-Install, installing the GUI and everything I can't get. I found a guide that I was trying to follow over my PS3 browser. The Arch Linux beginners guide.

[http://wiki.archlinux.org/index.php/Beginners%27_Guide](http://wiki.archlinux.org/index.php/Beginners%27_Guide)

I got to Step 2, followed the instructions fine, @**Force pacman to refresh the package lists **I get stuck because when I do that it says something about me having no repositories to fetch from (pretty much)

I uncommented the Repositories, and I uncommented the Waterloo (Canadian) mirror and I uncommented all the mirrors in USA & Canada in the mirrorlist.backup like it said.

Does anyone know what's going on? Or a better guide that explains the whole post-install better? 

Thanks.
****
You uncommented mirrors in mirrorlist.backup, not the actual mirrorlist. Without looking at the guide, I suspect you're confusing this with the section that talks about installing Python and using the rankmirrors script in preparation for using powerpill. Uncomment mirrors in /etc/pacman.d/mirrorlist and then run `pacman -Syy`.

---

### Post by RiceMonster on 2010-01-31
> **~sHyLoCk~ said:**
> Please ask for Arch support in [Arch forum]("http://bbs.archlinux.org/").

This will prevent any idiotic comments and hatred against Arch here.

this.

---

### Post by KhRiZiZi on 2010-01-31
> **falconindy said:**
> You uncommented mirrors in mirrorlist.backup, not the actual mirrorlist. Without looking at the guide, I suspect you're confusing this with the section that talks about installing Python and using the rankmirrors script in preparation for using powerpill. Uncomment mirrors in /etc/pacman.d/mirrorlist and then run `pacman -Syy`.
I did both mirrorlist and mirrorlist.backup and I did pacman -Syy that's when I get the error.

---

### Post by Eisenwinter on 2010-01-31
> **fromthehill said:**
> arch can be a real pain to setup properly with a desktop environment (permission etc)
Give me a good enough connection, and I could set up Arch with a fully functioning desktop environment, and all my used programs, in 20 minutes.

---

### Post by KhRiZiZi on 2010-01-31
> **Skripka said:**
> Does a basic ping command work to google.com?

I'd guess your internet isn't working.
Yeah I pinged google.com and I got the ping which is why I skipped to the further steps like it told me to if I got a positive result.

---

### Post by KhRiZiZi on 2010-01-31
> **Eisenwinter said:**
> Give me a good enough connection, and I could set up Arch with a fully functioning desktop environment, and all my used programs, in 20 minutes.
:o

---

### Post by Barrucadu on 2010-01-31
List the uncommented mirrors in your /etc/pacman.d/mirrorlist file, and give the exact error output.

---

### Post by KhRiZiZi on 2010-01-31
> **Barrucadu said:**
> List the uncommented mirrors in your /etc/pacman.d/mirrorlist file, and give the exact error output.
Okay give me 10 mins or so I'm going to install it again.

---

### Post by chucky chuckaluck on 2010-01-31
> **fromthehill said:**
> arch can be a real pain to setup properly with a desktop environment (permission etc)

it's a far more detailed a process than ubuntu, but it's all very doable and the documentation is very clear. the first installation can be pretty unfamiliar, though, and i guess that's where people get into trouble.

---

### Post by fromthehill on 2010-01-31
> **Eisenwinter said:**
> Give me a good enough connection, and I could set up Arch with a fully functioning desktop environment, and all my used programs, in 20 minutes.
so can I
but not the first time I used it

---

### Post by Perfect Storm on 2010-01-31
As the other have mentioned. The best thing you can do is search for answers or ask questions at the Arch forums.
Thanks.

Thread closed.


Regards
A.I. Dude

---

