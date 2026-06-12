---
title: "accessing ecryptfs contents"
date: 2015-07-16
forum: New to Ubuntu
---

### Post by sniper8752 on 2015-07-16
I setup ecryptfs on a folder.  I un-mounted it. and when I cat a file in the folder, it is encrypted.  How do I now decrypt it so I can read the file in plain text now?

---

### Post by Noah0504 on 2015-07-16
A quick search brought me here: [https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually)

Looks like you just need to mount it.

---

### Post by sniper8752 on 2015-07-17
The command that I found was this:
```
sudo mount -t ecryptfs sdtm ldm
```

But this encrypts the stuff.

---

### Post by sniper8752 on 2015-07-19
Anybody have any ideas?

---

### Post by yetimon_64 on 2015-07-19
> **sniper8752 said:**
> The command that I found was this:
```
sudo mount -t ecryptfs sdtm ldm
```

But this encrypts the stuff.

No it doesn't, the "stuff" is already encrypted before you ran the command and instead of using the actual paths involved on your install you left the example code in instead. Try replacing sdtm with the actual path of the source directory and ldm with the actual path of the location directory for the mount and run the command again.

From the link          Noah0504 posted.
> 
[LIST]
[*]sdtm = source directory to mount 
[*]ldm = location directory to mount at 
[/LIST]


Good luck, yeti.

---

### Post by sniper8752 on 2015-07-19
This is what I do: 
```
**user@host** **~ $** sudo mount -t ecryptfs /home/user/encrypt /home/user/encryptSelect key type to use for newly created files: 
 1) tspi
 2) passphrase
Selection: ^Cuser**@host** **~ $** 
```

I want to view the contents of the directory, "encrypt".  I can go inside there and it is mounted, but it is just that when I cat the contents of the txt file I have in there, it returns jibberish.  Isn't this a prompt to encrypt the directory?

---

### Post by sandyd on 2015-07-19
Have you tried typing 2 at the prompt and, typing in your passphrase.

---

### Post by sniper8752 on 2015-07-20
after I type my passphrase, it asks me for the cipher that I'd like to use.

---

### Post by Geoffrey_Arndt on 2015-07-20
Decided to delete my original response  . . . due to recent security/audit issues.

Comment:  the easiest file and directory encryption system I've come across lately is 7zip (it's in the repos), and is super easy to use.   Uses AES 256 bit cypher.    See youtube for use on Windows and Linux.[URL="https://www.youtube.com/watch?v=BaENd01bXUI"]

[https://www.youtube.com/watch?v=BaENd01bXUI](https://www.youtube.com/watch?v=BaENd01bXUI)



[/URL]

---

### Post by sandyd on 2015-07-20
Select the one with aes

---

### Post by sniper8752 on 2015-07-22
It then asks me for the key bits.  I already encrypted the folder.  I want to be able to unlock/decrypt it.

---

### Post by sandyd on 2015-07-22
This is part of the process, though it could be more user friendly as im just entering the defaults for ecryptfs-setup-private.

Type 128 at the prompt for bits

---

### Post by sniper8752 on 2015-07-28
This can't be right because when I enter a random wrong passphrase, it continues.

---

### Post by Geoffrey_Arndt on 2015-07-29
In addition to GPG, I've really enjoyed the simplicity of 7zip to provide directory and file encryption that is stronger than ecyptfs (256 vs 128 bit).  

7zip is in the Ubuntu repos, and is _integrated into the Nautilus file manager_.    Just right click the file or folder to see options.

Sometimes the best solution can also be the simplest.

[https://www.youtube.com/watch?v=U7UQpHDFPcI](https://www.youtube.com/watch?v=U7UQpHDFPcI)

---

### Post by kurt18947 on 2015-07-29
> **Geoffrey_Arndt said:**
> In addition to GPG, I've really enjoyed the simplicity of 7zip to provide directory and file encryption that is stronger than ecyptfs (256 vs 128 bit).  

7zip is in the Ubuntu repos, and is _integrated into the Nautilus file manager_.    Just right click the file or folder to see options.

Sometimes the best solution can also be the simplest.

[https://www.youtube.com/watch?v=U7UQpHDFPcI](https://www.youtube.com/watch?v=U7UQpHDFPcI)

7Zip is the simplest for sure. Only thing I know is to encrypt the files names as well as the contents. Gnome Disks works well to encrypt flash drives but it doesn't work on files AFAIK.  LibreOffice encryption is supposed to be pretty good for files that libreoffice handles. Doesn't help with media files and such though, nor folders.

Edit:  I've been messing with cryptkeeper. That seems like an option  for encrypting local files. A fly in the ointment for Unity users might be that cryptkeeper seems to rely on the gnome system tray. I don't know how that requirement would square with Unity (I haven't used Unity in quite some time)

---

