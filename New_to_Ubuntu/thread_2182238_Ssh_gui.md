---
title: "Ssh gui"
date: 2013-10-20
forum: New to Ubuntu
---

### Post by HonorableFool on 2013-10-20
Hello I'm sorry if this thread has already been covered I was unable to find any such topic. I feel ridiculous because Im almost certain this is user misunderstanding and I am simply missing a step. However it seems my SSH GUI is different and in my case, less capable then what I've been instructed to use

my interface: [http://imgur.com/kdvdinw](http://imgur.com/kdvdinw)

what I believe I am supposed to be working in: [http://imgur.com/KEek8i2](http://imgur.com/KEek8i2)

Operating Linux Box: Ubuntu 13.10 Gnome (however I ran into this same issue with standard Unity Desktop 13.04)

any insight is much appreciated thanks so much

---

### Post by Lars Noodén on 2013-10-20
Where it says 'server address' you can enter the URI to what you want to connect to.

```

sftp://honorablefool@server.example.org/home/honorablefool/

```

You can adjust the path given as needed.

---

### Post by newb85 on 2013-10-20
That's the difference in file browsers.  The one you think you should be working in is probably Konqueror, as it looks like that's a picture of a KDE-based setup.

Anyways, if I remember right those other options (username, folder, password, etc.) will appear once you click the "Connect" button in Nautilus (the default file browser for Ubuntu).

---

### Post by HonorableFool on 2013-10-20
Thanks Lars for that info. I have attempted to do this with the path shfs://vincent@168.192.1.113/home/vincent:22/ and ssh://vincent@168.192.1.113/home/vincent:22/ I must entering the incorrect values though.

---

### Post by HonorableFool on 2013-10-20
Thanks newb85, would you suggest I install Konquerer and if I do I wouldnt need Kubuntu would I?

---

### Post by Lars Noodén on 2013-10-20
> **HonorableFool said:**
> Thanks Lars for that info. I have attempted to do this with the path shfs://vincent@168.192.1.113/home/vincent:22/ and ssh://vincent@168.192.1.113/home/vincent:22/ I must entering the incorrect values though.

Did you try with **sftp://** yet?  The underlying protocol the file manager is using is SFTP, which goes over SSH.

---

### Post by HonorableFool on 2013-10-20
> **Lars Noodén said:**
> Did you try with **sftp://** yet?  The underlying protocol the file manager is using is SFTP, which goes over SSH.

Perfect Thank you lars issue resolved :D  thanks for taking an interest and assisting me. Cheers!

---

