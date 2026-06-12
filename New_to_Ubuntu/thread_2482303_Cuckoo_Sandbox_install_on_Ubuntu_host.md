---
title: "Cuckoo Sandbox install on Ubuntu host"
date: 2022-12-27
forum: New to Ubuntu
---

### Post by pjans123 on 2022-12-27
Hello everyone,

I'm new to this forum and also quite new to malware analysis, so I hope you can help me. I'm in the process of installing Cuckoo Sandbox in a virtual environment (Ubuntu 20.04 is the host, the guest is a Windows 7 VM). However, when I run the prerequisites, I get stuck. When I follow the official documentation [https://cuckoo.sh/docs/installation/host/requirements.html](https://cuckoo.sh/docs/installation/host/requirements.html), I get an error (see screenshot below). I have tried many things to fix the problem (so many things that I don't even know what I tried and what not), e.g. installing Python 2 (2.7, since Cuckoo doesn't support Python 3 yet, etc.), but I can't solve the problem.

Does anyone know how I can fix this? Thank you in advance.

---

### Post by Holger_Gehrke on 2022-12-27
Unless you've got a **very** good reason to use this, I would avoid Cuckoo Sandbox. If you look at the main page of the site you'll see that the last news post was from September of 2016. I'd classify it as a dead project, especially since their SSL-certificate has expired in November and nobody has bothered to get and install a new one.

Holger

P.S.: please don't post screenshots of a terminal, they are usually hard to read. Just copy and paste the text in a code-block.

---

### Post by ActionParsnip on 2022-12-28
Why Windows 7?its not supported by anyone so you aren't really testing anything worthwhile.

---

### Post by pjans123 on 2022-12-30
Thank you very much and I was already a little bit afraid of getting this answer.

Do you have a recommendation for setting up a lab to analyse malware / ransomware? There are types of ransomware that can escape from the virtual environment. For this reason, I wanted to install a sandbox, also because previous studies have done this (however, they used the additional information of the sandbox (dynamic behaviour analysis of ransomware, e.g. API calls, registry key operations). For me this is not very relevant, as I will be developing an anti-ransomware system myself (so I don't really need the information Cuckoo provides). The only thing I want to make sure is that ransomware cannot spread to the network and/or infect my host machine (it should, however, be able to connect with to the internet, as it should communicate with command-and-control servers).

---

### Post by pjans123 on 2023-01-01
anyone?

---

