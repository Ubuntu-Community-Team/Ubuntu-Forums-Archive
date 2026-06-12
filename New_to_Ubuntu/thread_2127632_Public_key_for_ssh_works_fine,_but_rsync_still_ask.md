---
title: "Public key for ssh works fine, but rsync still askes for a password"
date: 2013-03-20
forum: New to Ubuntu
---

### Post by kramer65 on 2013-03-20
Hello,

I want to use rsync to sync a folder between two machines. Because I don't want to type in the password constantly I used [this guide]("https://blogs.oracle.com/jkini/entry/how_to_scp_scp_and") to create a key-pair, of which I put the public key in the destination machines ~/.ssh/authorized_keys

This seems to work fine for ssh: I can login without typing a password. When I run the following command however, the remote machine still askes for the password.

```
sudo rsync --delete -azvv -e ssh '/home/kramer65/mylocalfolder/' user@othermachine:/home/pi/myremotefolder
```

Does anybody know how this can be, and more importantly, how I can solve this? All tips are welcome!

---

### Post by Cheesemill on 2013-03-20
You're running your rsync command as the root user, whereas I'm guessing you set up ssh keys for your standard user.

Try running rsync as your normal user, it should pick up on the ssh keys you have setup.

---

### Post by kramer65 on 2013-03-20
That was indeed the problem!

Why I ran it as root in the first place? I have no clue..:confused:

Thanks a million!

---

