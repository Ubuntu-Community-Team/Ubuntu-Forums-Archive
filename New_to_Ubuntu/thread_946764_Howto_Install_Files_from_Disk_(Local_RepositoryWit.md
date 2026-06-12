---
title: "Howto: Install Files from Disk (Local Repository/Without Internet)"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by RealG187 on 2008-10-13
I made a guide [here]("http://bestwikiever.wikidot.com/ubuntu:local-repository") on how to take the files from the repository and put them on a device and move them to a computer without internet, or just as a way to save [bandwidth]("http://bestwikiever.wikidot.com/bandwidth").

I also am uploading packages for people to download.

I am just sharing this, if anyone can find a way to improve it then you are welcome to. Hope I helped.

---

### Post by aeiah on 2008-10-13
quite useful, although did you know that you dont need to install the packages on the initial system that you're downloading them on? there's a tickbox to 'download packages only' in synaptic, and if you use apt-get, you can use the -d option to download only
```

sudo apt-get install -d files you want
```

with apt-get, you can also delete all the stuff from the /var/cache/apt/ folder before starting it with
```

sudo apt-get clean
```

---

### Post by RealG187 on 2008-10-13
so apt-get clean deltes everything in the /var/cache/apt/archives folder (except the two file/folder I mentioned)?

If I would use "sudo apt-get install -d files you want" how would I install then later, just use "sudo apt-get install  files you want" and it will use the files already there?

---

