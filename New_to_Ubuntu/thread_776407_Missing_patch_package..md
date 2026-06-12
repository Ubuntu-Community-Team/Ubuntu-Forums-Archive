---
title: "Missing patch package."
date: 2008-04-30
forum: New to Ubuntu
---

### Post by El-Doble-O on 2008-04-30
I execute command "sudo apt-get install patch" and I get:

[I]Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package patch.[/I]

Help?

---

### Post by Het Irv on 2008-04-30
Are you connected to the internet? 
Do you have all the software sources enabled?

---

### Post by Alehbye on 2008-04-30
NVM. I'm an idiot.

---

### Post by El-Doble-O on 2008-04-30
> **Het Irv said:**
> Are you connected to the internet? 
Do you have all the software sources enabled?

1) No, I am not connected to the internet. Is that necessary?
2) I never disabled them, but I'm not sure.

*I connected myself to the internet and it still did not work.

---

### Post by Het Irv on 2008-04-30
Yes, you need an internet connection to use apt-get.  Apt-get checks the online repo's to find your package, and then download and installs it.

When I try to install patch on my computer, It says that it is already installed. That may be because it is a dependency of another package, but I don't think so. Why do you need to install it?

---

### Post by AgDon92 on 2008-05-16
I'm getting the same error. The problem is that I'm trying to patch a file so that my network card will work. Is there anyway I can download the patch program on another computer and install it on my other computer?

Thanks.

don

---

### Post by Het Irv on 2008-05-18
Yeah, you can download .deb and run them from a local source.  Just google for the package and you should be able to find it on an ubuntu site somewhere.

---

### Post by mohsen88 on 2011-03-11
I want  to download patch package in windows and install it into linux ubuntu 
who can help me?
please say

---

