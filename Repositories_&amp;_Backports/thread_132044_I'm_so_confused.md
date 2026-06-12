---
title: "I'm so confused"
date: 2006-02-17
forum: Repositories &amp; Backports
---

### Post by lzfy on 2006-02-17
Can someone explain me how the Ubuntu repository works? What's Universe and Multiverse? I'm sorry if this has been asked before, but i really need to know this. thanks...

---

### Post by skierkegaard on 2006-02-17
If you are really confused, this would be a good place to start:
[https://wiki.ubuntu.com/AddingRepositoriesHowto?action=show&redirect=HowToEnableTheMultiverseRepositoryInUbuntu]("https://wiki.ubuntu.com/AddingRepositoriesHowto?action=show&redirect=HowToEnableTheMultiverseRepositoryInUbuntu")

---

### Post by lzfy on 2006-02-17
Thanks skierkegaard, that helped me a lot. But I still don't know the difference between Universe and Multiverse.

---

### Post by az on 2006-02-17
[QUOTE=lzfy]Thanks skierkegaard, that helped me a lot. But I still don't know the difference between Universe and Multiverse.[/QUOTE]

Ubuntu is free-libre software.  You need to provide the source code for the software as well as the ability to change it and redistribute those changes for it to be considered free software.

This is why there are repositories.  Since it is a pain to compiloe everything yourself (and uneccesary) the apps are compiled for you.  The interface through which they are developed is at the source code level, and not at the precompiled binary level.  This may seem limiting, but it actually gives you a ton of freedom since you can pretty much compile anything you want to if you have the source code.

The down side is that not all precompiled packages work well together.  You would need to recompile them to work together.

That's what the software is seperated into repositories.  Ubuntu uses "main" for everything that is officially supported.  Everything else that is packaged for debian is in "universe" which works, but is not supported by as many developers.

What is not free-libre software (no source code, or a licence that is not free) is in the restricted or multiverse repositories. 

So, the difference between universe and multiverse is that some of the multiverse packages are illegal or unlicenced in some parts of the world whereas everything in universe is DFSG (Debian free software guidelines) compatible.

---

### Post by lzfy on 2006-02-17
Thank you for the great explanation, it's simple but i had to ask because it's very important for me to understand how Ubuntu works :)

---

