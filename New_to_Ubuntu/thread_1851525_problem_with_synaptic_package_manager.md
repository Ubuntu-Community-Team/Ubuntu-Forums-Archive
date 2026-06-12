---
title: "problem with synaptic package manager"
date: 2011-09-28
forum: New to Ubuntu
---

### Post by technoob on 2011-09-28
I have added the repositories for firefox 7 but then when I tried to update my package manager it returns the following error:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ppa.mozillateam_firefox-stable_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

as soon as it shows this msg it terminates and I can not do anything.please provide me the solution

thanx in advance..!!

---

### Post by amjjawad on 2011-09-28
> **technoob said:**
> I have added the repositories for firefox 7 but then when I tried to update my package manager it returns the following error:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ppa.mozillateam_firefox-stable_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

as soon as it shows this msg it terminates and I can not do anything.please provide me the solution

thanx in advance..!!

Hello there,

What release of Ubuntu are you using?
How did you added Firefox 7 PPA?

Thanks!

---

### Post by technoob on 2011-09-28
i added them using the gui of synaptic.
btw

when i try to update it using sudo apt-get update it shows decoder error..!!

---

### Post by technoob on 2011-09-28
I am using ubuntu natty narwhal

---

### Post by amjjawad on 2011-09-28
You need to add the PPA either from Synaptic and Update it from there "Reload" or add it from the Terminal and use "sudo apt-get update".
Whatever works for you or whatever easier for you.

Can you double check whether you have added it twice or something? can you please remove it and install the PPA from Terminal?

```
sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install firefox
```

---

### Post by technoob on 2011-09-28
can u please tell me how to remove the repositories using terminal..
btw I have ubuntu tweak installed so if anything I can do using it!

synaptic's GUI is not working for now..

---

### Post by amjjawad on 2011-09-28
> **technoob said:**
> can u please tell me how to remove the repositories using terminal..
btw I have ubuntu tweak installed so if anything I can do using it!

synaptic's GUI is not working for now..

I'm sorry, don't know the command to remove PPA from Terminal but if Synaptic doesn't work, please run this from Terminal:

```
gksudo synaptic

```

You can use Synaptic to remove Firefox PPA and then re-install it form Terminal.

---

### Post by Elfy on 2011-09-28
I've deleted the posts you made - twice - in the Re: Firefox 4, 5 & Beyond Mega Thread - please do no duplicate your posts or threads.

---

### Post by technoob on 2011-09-28
> **forestpiskie said:**
> I've deleted the posts you made - twice - in the Re: Firefox 4, 5 & Beyond Mega Thread - please do no duplicate your posts or threads.
my apologies..!!

---

### Post by Elfy on 2011-09-28
You can use ```
sudo ppa-purge ppa:*nameofppa*
``` to remove ppa by command line

---

### Post by technoob on 2011-09-28
> **amjjawad said:**
> I'm sorry, don't know the command to remove PPA from Terminal but if Synaptic doesn't work, please run this from Terminal:

```
gksudo synaptic

```

You can use Synaptic to remove Firefox PPA and then re-install it form Terminal.

It is showing the same error msg.and I'm unable to open it anyhow..

---

### Post by amjjawad on 2011-09-28
> **technoob said:**
> It is showing the same error msg.and I'm unable to open it anyhow..

forestpiskie has posted the command so please try and report back :)

---

### Post by technoob on 2011-09-28
Seems like the structures are becoming corrupt..
I removed the ppa's from /etc/apt/sources.list and it worked.!!):P

---

### Post by amjjawad on 2011-09-28
> **technoob said:**
> Seems like the structures are becoming corrupt..
I removed the ppa's from /etc/apt/sources.list and it worked.!!):P

Ok, well done and glad you managed to fix it :)

Edit: If you have Ubuntu 11.04, I don't think you need to add the PPA anyway :)

---

