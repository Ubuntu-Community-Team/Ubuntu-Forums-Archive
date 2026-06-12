---
title: "How to easily downgrade from 8.04 (Wubi) to 7.10 (Wubi) and still keep all my apps?"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Watchtow3r on 2008-06-12
I installed 8.04 with Wubi on my laptop. The only thing is, it severely heats it up and supposedly this is a known bug in 8.04. I have heard from a few people that 7.10 doesn't do this. Is there an easy way to downgrade to 7.10 (with Wubi) and still keep all my apps/settings? I don't even really care so much about the apps, but I had to put a lot of energy into making things work in Ubuntu like my printer and sound, and I really don't want to do that again. Thanks.

---

### Post by Watchtow3r on 2008-06-12
any help?

---

### Post by bumanie on 2008-06-12
As far as I know there is no way to downgrade form one distro to an earlier one - reinstallation of the earlier version is the only way.

---

### Post by Paqman on 2008-06-12
You'll need to reinstall, but don't worry, all is not lost.

To save all your settings, just make a copy of the contents of your /home/username folder. Restore it onto the new system and take ownership of it with:
```

sudo chown -R username:username /home/username

```

See here for how to [automatically reinstall all your apps](http://ubuntuforums.org/showthread.php?t=261366). Not everything is guaranteed to work, since 7.10 and 8.04 have different repos (things could have different names, for example)

---

### Post by Watchtow3r on 2008-06-12
Where can I download the livecd for 7.10 with Wubi? I'm not very experienced with Ubuntu, and I really don't want to partition my hd. Thanks.

---

### Post by hyper_ch on 2008-06-12
I don't think 7.10 has wubi

---

### Post by Watchtow3r on 2008-06-12
I have read some things about it and it sounds like Wubi was independant from Ubuntu in 7.04 and 7.10, but was still there. It was just actually put on the livecd in 8.04 (I got that from the wikipedia entry [here]("http://en.wikipedia.org/wiki/Wubi_(Ubuntu)")). But how do I download Wubi and use it to install 7.10?

---

