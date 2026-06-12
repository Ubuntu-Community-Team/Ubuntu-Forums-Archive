---
title: "GPG Error"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by kansasnoob on 2008-04-28
I just did my umpteenth dual boot with XP for a friend and all works well but in Hardy I get the following:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

Obviously I use the Medibuntu repo, but I know I'm installing Medibuntu the same (from the same source) as I have on my own three puters and I don't get that when I run apt-get update on them.

Just wondered if anyone else had encountered this. I have tried cut-n-pasting the GPG more than a few times.

While everything seems to be working great I hate to hand a computer back to someone while it shows an error code.

---

### Post by santaslittlehelper on 2008-04-28
Not sure but this might get you the key.
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by kansasnoob on 2008-04-28
That fixed it, many thanks!

Now, my second dumb question of the day, how do I mark this solved?

---

### Post by Oldsoldier2003 on 2008-04-28
the forum gurus haven't reimplemented solved yet, but I suppose you could always edit the title :)

---

