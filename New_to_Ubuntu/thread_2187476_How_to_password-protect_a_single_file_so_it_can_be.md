---
title: "How to password-protect a single file so it can be opened on a different OS?"
date: 2013-11-12
forum: New to Ubuntu
---

### Post by kmajaa on 2013-11-12
I want to send a password-protected file to someone who uses Windows/Mac OS on a shared computer (it's not theirs) and I don't want anyone else but that person to be able to open this file (easily!) but **I don't want to make it an archive**.
Is there a way to do it?


I know there are already a lot of similar threads but they don't include the solution to my problem.

---

### Post by Impavidus on 2013-11-12
Some file formats allow for encryption. PDF, libreoffice, maybe some others. Else you need a separate program to encrypt the file, like gpg. The reciever shouldn't store the decrypted file on the hard disk of the shared computer, but keep it on a usb stick. You also need a safe way to transfer the encryption key.

---

### Post by Dennis N on 2013-11-12
You asked about "password protected", but this is a typical use case for gpg public key encryption. Using gpg, A creates a public and private (or secret) key. A sends B his public key. B uses A's public key to encrypt a file, then sends the encrypted file to A. Only A can decrypt that file. To do this, he uses his private key (which he shares with no one).

To learn how, google "gpg tutorial"

In Ubuntu, after you get the public key, you can use Nautilus and the seahorse-nautilus plugin to do the work, or you can use the command line gnupg program. Windows and Mac have gpg programs that are compatable.

---

### Post by shabuboy on 2013-11-12
If the program itself does not provides password protection, as the others mentioned, [COLOR=#000000]gpg is the option. However, to me, that is similar to archive. For beginners, unless you are really want to read/learn gpg, I would recommend sticking with zip/rar password protected.

I see you also posted here...
[/COLOR]http://ubuntuforums.org/showthread.php?t=2169295

---

