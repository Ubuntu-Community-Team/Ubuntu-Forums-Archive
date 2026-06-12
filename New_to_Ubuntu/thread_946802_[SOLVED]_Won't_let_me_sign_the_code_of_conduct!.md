---
title: "[SOLVED] Won't let me sign the code of conduct!"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by Lorelei- on 2008-10-13
So now that my PGP key is set up and working, I was going to sign the Ubuntu code of conduct on Launchpad, only to find that it won't let me. I'm following the Launchpad instructions and everytime I run the command in the terminal I get the following:

> gpg: can't open `UbuntuCodeofConduct.txt': No such file or directory
gpg: UbuntuCodeofConduct.txt: clearsign failed: file open error

what the heck is going on/am I not doing here so that this well let me sign it and upload it?

Help please (as this is starting to annoy the hell out of me!).

---

### Post by Keen101 on 2008-10-13
It's been a while since i've signed the code of conduct and even then i ha a lot of trouble.

You are probably not browsing to the file location in your terminal.

cd ~/Desktop

---

### Post by Lorelei- on 2008-10-13
thank you, after changing the file location it seems to have worked now!

---

