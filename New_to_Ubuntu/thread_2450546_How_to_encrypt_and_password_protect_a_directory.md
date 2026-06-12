---
title: "How to encrypt and password protect a directory?"
date: 2020-09-16
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2020-09-16
Hello all,

What would be the best way to password protect a directory under "/home/<user>/"?

It doesn't need to be fort Knox but some authentication by password and a bit of encryption maybe in case I get hacked or something? I don't really know much about encryption beyond the basics but I believe authentication and encryption are not the same thing?

Any help is much appreciated!

---

### Post by sudodus on 2020-09-16
Is this for saving passwords (only) or for saving various data files?

I'm asking because there are special solutions for saving passwords (that are more convenient than a general solution).

Otherwise LUKS encryption can be used.

---

### Post by Dennis N on 2020-09-16
In Ubuntu, the file manager (Files) can encrypt a file or folder for you. When encryption is set up, you get an "Encrypt" option when you right-click on a file or folder. See this guide to setting up the ecryption:

[https://www.techrepublic.com/article/how-to-enable-encryptdecrypt-menu-option-in-the-ubuntu-file-manager/](https://www.techrepublic.com/article/how-to-enable-encryptdecrypt-menu-option-in-the-ubuntu-file-manager/)

(Note: simplest encryption is to use the 'shared passphrase' option instead of using encryption keys.)

---

### Post by jcdenton1995 on 2020-09-16
> **sudodus said:**
> Is this for saving passwords (only) or for saving various data files?

It's just for regular files, but I have also been considering a location in which I can store some of my less sensitive passwords, so I'd be interested to hear about that too :)

---

### Post by sudodus on 2020-09-16
This link: [KeePass Password Safe](https://keepass.info) should be useful for general information.

More specifically for Ubuntu, I think [KeePassXC](https://keepassxc.org/) is what you'd want. You can download it or install it from the repository Universe (version 2.3.1) or from a PPA (version 2.61) or snap.

---

### Post by scorp123 on 2020-09-16
> **jcdenton1995 said:**
>  What would be the best way to password protect a directory under "/home/<user>/"?

I use **Sirikali **for this. You will find it in the "Universe" repositories of recent Ubuntu releases.

The project's homepage is here:
[https://mhogomchungu.github.io/sirikali/]("https://mhogomchungu.github.io/sirikali/")

---

### Post by jcdenton1995 on 2020-09-21
Thanks, this looks good. I'll give it a whirl!

---

### Post by jcdenton1995 on 2020-09-21
Cheers, I'll give it a try as I'm awful with passwords and pretty much just change them every time I log into a site that I don't use often enough to have the password burned into my brain. I still think the best place for sensitive passwords is on a piece of paper kept in some obscure place around the house though :p

---

### Post by jcdenton1995 on 2020-09-21
> **Dennis N said:**
> In Ubuntu, the file manager (Files) can encrypt a file or folder for you. When encryption is set up, you get an "Encrypt" option when you right-click on a file or folder. See this guide to setting up the ecryption:

[https://www.techrepublic.com/article/how-to-enable-encryptdecrypt-menu-option-in-the-ubuntu-file-manager/](https://www.techrepublic.com/article/how-to-enable-encryptdecrypt-menu-option-in-the-ubuntu-file-manager/)

(Note: simplest encryption is to use the 'shared passphrase' option instead of using encryption keys.)

Thanks, I've just installed seahorse-nautilus and encrypted / decrypted with it, but what I can't understand is why when I encrypt a file with the shared passphrase option, it generates the encrypted file, however I can just decrypt it without using the passphrase? I don't think I fully understand how it works...

---

### Post by Dennis N on 2020-09-21
> **jcdenton1995 said:**
> Thanks, I've just installed seahorse-nautilus and encrypted / decrypted with it, but what I can't understand is why when I encrypt a file with the shared passphrase option, it generates the encrypted file, however I can just decrypt it without using the passphrase? I don't think I fully understand how it works...

I've noticed that too, and imagine it's a tradeoff between convenience and security. Suppose you had 20 files to decrypt.  Is it better to require the user to re-enter a long passphrase for each one, or allow the passphrase authentication persist during the same user session with Nautilus open? I would think if you closed Nautilus after decrypting a file, reopened it, and tried to decrypt another, you would have to re-enter the passphrase. That would be something to find out. There may be a time limitation too in any session.

---

### Post by peter235 on 2021-01-26
I installed sirikali on Ubuntu 20.04 and created a folder encrypted with cryfs. I was using gnome-encfs-manager on Ubuntu 18 but it is not available in Ubuntu 20.

---

