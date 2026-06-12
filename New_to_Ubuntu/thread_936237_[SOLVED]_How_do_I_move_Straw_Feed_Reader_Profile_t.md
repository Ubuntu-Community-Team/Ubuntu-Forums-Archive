---
title: "[SOLVED] How do I move Straw Feed Reader Profile to second disk?"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by bornagainpenguin on 2008-10-02
I use the Straw Feed Reader on Ubuntu Hardy (8.04) Heron, on my EeePC 901 because it is the only true **offline** feed reader for Linux.

I'm not looking for suggestions on replacing it because I don't honestly think any exist with the important **OFFLINE** feature--and if it doesn't display images **OFFLINE** I don't consider it an **OFFLINE** feed reader--if you honestly know differently please PM me with that information, don't derail this thread.  Thank you.

Now my issue is Straw has been freezing and hanging really badly on my EeePC 901 and I'm starting to think the issue is caused by my /home living on the secondary 16GB SSD drive, which is known to be slower than the primary 4GB SSD drive where my / lives.

On my Inspiron 5100 Straw would occasionally hang but never as badly as it has been with my EeePC 901!

So my question is can someone please tell me how to move the folder Straw writes to from the secondary disk to the primary one?

Currently I have:
```
/dev/sdb1/home/bornagainpenguin/.straw/
```

I want have something like:
```
/dev/sda1/**something goes here**/.straw/
```

Can someone give me instructions to follow to do this?  Thanks!

--bornagainpenguin

---

### Post by bornagainpenguin on 2008-10-02
I got help on this just a bit ago on the Eeeuser.com forums, so I'm marking this thread solved.  Here's the answer in case anyone else needs it:

[quote=themono]I'm pretty sure this string of commands should work, obviously don't include the stuff in brackets:

sudo mkdir /.straw (Making a straw directory on the main drive)
sudo chown bornagainpenguin:bornagainpenguin /.straw (Giving ownership of that directory to your user)
mv /home/bornagainpenguin/.straw/* /.straw/ (Moving contents of the old straw directory to the new one)
rm -r /home/bornagainpenguin/.straw (Removing the old straw directory)
ln -s /.straw /home/bornagainpenguin/.straw (Linking the old straw directory to point to the new one)

Not using straw, I can't be totally sure, but that should be fine.[/quote]

Thanks themono again!

I knew that symbolic links would have to be involved somehow but I wasn't quite sure exactly where or whether what I was asking was even a good idea, etc....

I just executed the commands you listed and I'm already seeing an improvement.  I know it'll still be a bit slow--it's still in v0.27 so I know better than to expect miracles but I really do think the faster disk is making a difference.  If only there were some activity on the part of the straw developers...but this is working well enough for now, so thanks again!

--bornagainpenguin

---

