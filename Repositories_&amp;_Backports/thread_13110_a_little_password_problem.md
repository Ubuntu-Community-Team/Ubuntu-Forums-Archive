---
title: "a little password problem"
date: 2005-01-28
forum: Repositories &amp; Backports
---

### Post by memnon on 2005-01-28
k so this is prolly in the wrong section, i did look around first and did a search for the only thing i could come up with, password, the stuff i was doing had the word Repository in it so i posted here, now the problem.

i wanna do this: [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

but when i get asked for the passwd i cant type, nothing on keyboard works but the enter key, how do i fix that???

only thing i done after installation is this: [http://ubuntuguide.org/#disableinteractiveeditinggrub](http://ubuntuguide.org/#disableinteractiveeditinggrub)

and not even all of it since i couldnt type passwd
```
 $ grub

grub> md5crypt
Password: ****** (ubuntu)
Encrypted: $1$ZWnke0$1fzDBVjUcT1Mpdd4u/T961 (encrypted password)

grub> quit
```

i did that part but couldnt do next cos of passwd problem  ](*,) 

now i am all new to any distro of linux at all, first time i tried today so ive been a linux user for about 3 hours.

hope someone can help me with this problem :D

and sorry to the mod who prolly had to move this thread :lol:

---

### Post by Rancoras on 2005-01-28
The password you type after the sudo commands is the password for the account you created during installation.  You won't see any feedback on the screen that you are typing anything until you press the enter key.

---

### Post by memnon on 2005-01-29
oh thx for the help

as i said i know nothing about linux

---

