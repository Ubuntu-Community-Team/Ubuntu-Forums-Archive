---
title: "dangerdeep"
date: 2012-06-28
forum: New to Ubuntu
---

### Post by auspot on 2012-06-28
can someone help me with this problem with step by step instructions please?

bill@bill-ET1831:~$ svn co [https://dangerdeep.svn.sourceforge.n...nk/dangerdeep/]("https://dangerdeep.svn.sourceforge.net/svnroot/dangerdeep/trunk/dangerdeep/") dangerdeep
svn: Working copy 'dangerdeep' locked

Thanks
auspot

---

### Post by ubudog on 2012-06-29
Hi auspot, try running the following command while in the directory you checked out dangerdeep.

```
svn cleanup
```

Did you recently cancel an svn checkout of dangerdeep?

---

### Post by auspot on 2012-06-30
this is what I get:

bill@bill-ET1831:~/dangerdeep$ svn cleanup
svn: Can't remove directory 'build/linux/.svn/tmp/props': Permission denied
bill@bill-ET1831:~/dangerdeep$

no but I would like to clean the whole mess dangerdeep off puter and start
over

Thanks for the reply
auspot

---

### Post by ubudog on 2012-06-30
> **auspot said:**
> this is what I get:

bill@bill-ET1831:~/dangerdeep$ svn cleanup
svn: Can't remove directory 'build/linux/.svn/tmp/props': Permission denied
bill@bill-ET1831:~/dangerdeep$

no but I would like to clean the whole mess dangerdeep off puter and start
over

Thanks for the reply
auspot

You could remove the dangerdeep directory, and then check it out again.

To remove the directory (when cd'd to the directory one up from dangerdeep):
```
rm -rf dangerdeep
```

And then to check it out again:
```
svn co https://dangerdeep.svn.sourceforge.n...nk/dangerdeep/ dangerdeep

```

Hope that helps!

---

### Post by auspot on 2012-06-30
bill@bill-ET1831:~$ rm -rf dangerdeep
rm: cannot remove `dangerdeep/utils/.svn/tmp/prop-base': Permission denied
rm: cannot remove `dangerdeep/utils/.svn/tmp/text-base': Permission denied
rm: cannot remove `dangerdeep/utils/.svn/tmp/props': Permission denied
rm: cannot remove `dangerdeep/src/tinyxml/.svn/tmp/prop-base': Permission denied
rm: cannot remove `dangerdeep/src/tinyxml/.svn/tmp/text-base': Permission denied
rm: cannot remove `dangerdeep/src/tinyxml/.svn/tmp/props': Permission denied
rm: cannot remove `dangerdeep/src/dftdtester/.svn/tmp/prop-base': Permission denied
rm: cannot remove `dangerdeep/src/dftdtester/.svn/tmp/text-base': Permission denied
rm: cannot remove `dangerdeep/src/dftdtester/.svn/tmp/props': Permission denied
rm: cannot remove `dangerdeep/src/.svn/tmp/prop-base': Permission denied
rm: cannot remove `dangerdeep/src/.svn/tmp/text-base': Permission denied
rm: cannot remove `dangerdeep/src/.svn/tmp/props': Permission denied
rm: cannot remove `dangerdeep/src/tools/.svn/tmp/prop-base': Permission denied
rm: cannot remove `dangerdeep/src/tools/.svn/tmp/text-base': Permission denied
rm: cannot remove `dangerdeep/src/tools/.svn/tmp/props': Permission denied
rm: cannot remove `dangerdeep/src/oglext/.svn/tmp/prop-base': Permission denied
rm: cannot remove `dangerdeep/src/oglext/.svn/tmp/text-base': Permission denied
rm: cannot remove `dangerdeep/src/oglext/.svn/tmp/props': Permission denied
rm: cannot remove `dangerdeep/src/Mac/.svn/tmp/prop-base': Permission denied
rm: cannot remove `dangerdeep/src/Mac/.svn/tmp/text-base': Permission denied
rm: cannot remove `dangerdeep/src/Mac/.svn/tmp/props': Permission denied
rm: cannot remove `dangerdeep/src/test/.svn/tmp/prop-base': Permission denied
rm: cannot remove `dangerdeep/src/test/.svn/tmp/text-base': Permission denied
rm: cannot remove `dangerdeep/src/test/.svn/tmp/props': Permission denied
rm: cannot remove `dangerdeep/data/models/.svn/tmp/prop-base': Permission denied
rm: cannot remove `dangerdeep/data/models/.svn/tmp/text-base': Permission denied
rm: cannot remove `dangerdeep/data/models/.svn/tmp/props': Permission denied
rm: cannot remove `dangerdeep/data/convoys/.svn/tmp/prop-base': Permission denied
rm: cannot remove `dangerdeep/data/convoys/.svn/tmp/text-base': Permission denied
rm: cannot remove `dangerdeep/data/convoys/.svn/tmp/props': Permission denied
rm: cannot remove `dangerdeep/data/maps/.svn/tmp/prop-base': Permission denied
rm: cannot remove `dangerdeep/data/maps/.svn/tmp/text-base': Permission denied
rm: cannot remove `dangerdeep/data/maps/.svn/tmp/props': Permission denied
rm: cannot remove `dangerdeep/data/maps/terrain/.svn/tmp/prop-base': Permission denied
rm: cannot remove `dangerdeep/data/maps/terrain/.svn/tmp/text-base': Permission denied
rm: cannot remove `dangerdeep/data/maps/terrain/.svn/tmp/props': Permission denied
rm: cannot remove `dangerdeep/data/textures/explosion01/.svn/tmp/prop-base': Permission denied
rm: cannot remove `dangerdeep/data/textures/explosion01/.svn/tmp/text-base': Permission denied
rm: cannot remove `dangerdeep/data/textures/explosion01/.svn/tmp/props': Permission denied
rm: cannot remove `dangerdeep/data/textures/explosion02/.svn/tmp/prop-base': Permission denied
rm: cannot remove `dangerdeep/data/textures/explosion02/.svn/tmp/text-base': Permission denied
rm: cannot remove `dangerdeep/data/textures/explosion02/.svn/tmp/props': Permission denied
rm: cannot remove `dangerdeep/packaging/.svn/tmp/prop-base': Permission denied
rm: cannot remove `dangerdeep/packaging/.svn/tmp/text-base': Permission denied
rm: cannot remove `dangerdeep/packaging/.svn/tmp/props': Permission denied
rm: cannot remove `dangerdeep/packaging/ubuntu/.svn/tmp/prop-base': Permission denied
rm: cannot remove `dangerdeep/packaging/ubuntu/.svn/tmp/text-base': Permission denied
rm: cannot remove `dangerdeep/packaging/ubuntu/.svn/tmp/props': Permission denied
rm: cannot remove `dangerdeep/packaging/ubuntu/daily/.svn/tmp/prop-base': Permission denied
rm: cannot remove `dangerdeep/packaging/ubuntu/daily/.svn/tmp/text-base': Permission denied
rm: cannot remove `dangerdeep/packaging/ubuntu/daily/.svn/tmp/props': Permission denied
rm: cannot remove `dangerdeep/packaging/ubuntu/daily/src/.svn/tmp/prop-base': Permission denied
rm: cannot remove `dangerdeep/packaging/ubuntu/daily/src/.svn/tmp/text-base': Permission denied
rm: cannot remove `dangerdeep/packaging/ubuntu/daily/src/.svn/tmp/props': Permission denied
rm: cannot remove `dangerdeep/packaging/ubuntu/daily/src/debian/.svn/tmp/prop-base': Permission denied
rm: cannot remove `dangerdeep/packaging/ubuntu/daily/src/debian/.svn/tmp/text-base': Permission denied
rm: cannot remove `dangerdeep/packaging/ubuntu/daily/src/debian/.svn/tmp/props': Permission denied
rm: cannot remove `dangerdeep/packaging/ubuntu/daily/terrain/.svn/tmp/prop-base': Permission denied
rm: cannot remove `dangerdeep/packaging/ubuntu/daily/terrain/.svn/tmp/text-base': Permission denied
rm: cannot remove `dangerdeep/packaging/ubuntu/daily/terrain/.svn/tmp/props': Permission denied
rm: cannot remove `dangerdeep/packaging/ubuntu/daily/data/.svn/tmp/prop-base': Permission denied
rm: cannot remove `dangerdeep/packaging/ubuntu/daily/data/.svn/tmp/text-base': Permission denied
rm: cannot remove `dangerdeep/packaging/ubuntu/daily/data/.svn/tmp/props': Permission denied
rm: cannot remove `dangerdeep/packaging/ubuntu/daily/data/debian/.svn/tmp/prop-base': Permission denied
rm: cannot remove `dangerdeep/packaging/ubuntu/daily/data/debian/.svn/tmp/text-base': Permission denied
rm: cannot remove `dangerdeep/packaging/ubuntu/daily/data/debian/.svn/tmp/props': Permission denied
rm: cannot remove `dangerdeep/packaging/suse/.svn/tmp/prop-base': Permission denied
rm: cannot remove `dangerdeep/packaging/suse/.svn/tmp/text-base': Permission denied
rm: cannot remove `dangerdeep/packaging/suse/.svn/tmp/props': Permission denied
rm: cannot remove `dangerdeep/packaging/win32/.svn/tmp/prop-base': Permission denied
rm: cannot remove `dangerdeep/packaging/win32/.svn/tmp/text-base': Permission denied
rm: cannot remove `dangerdeep/packaging/win32/.svn/tmp/props': Permission denied
rm: cannot remove `dangerdeep/build/.svn/tmp/prop-base': Permission denied
rm: cannot remove `dangerdeep/build/.svn/tmp/text-base': Permission denied
rm: cannot remove `dangerdeep/build/.svn/tmp/props': Permission denied
rm: cannot remove `dangerdeep/build/default/.svn/tmp/prop-base': Permission denied
rm: cannot remove `dangerdeep/build/default/.svn/tmp/text-base': Permission denied
rm: cannot remove `dangerdeep/build/default/.svn/tmp/props': Permission denied
rm: cannot remove `dangerdeep/build/win32/.svn/tmp/prop-base': Permission denied
rm: cannot remove `dangerdeep/build/win32/.svn/tmp/text-base': Permission denied
rm: cannot remove `dangerdeep/build/win32/.svn/tmp/props': Permission denied
rm: cannot remove `dangerdeep/build/linux/.svn/tmp/prop-base': Permission denied
rm: cannot remove `dangerdeep/build/linux/.svn/tmp/text-base': Permission denied
rm: cannot remove `dangerdeep/build/linux/.svn/tmp/props': Permission denied
rm: cannot remove `dangerdeep/debian/.svn/tmp/prop-base': Permission denied
rm: cannot remove `dangerdeep/debian/.svn/tmp/text-base': Permission denied
rm: cannot remove `dangerdeep/debian/.svn/tmp/props': Permission denied

looks like it don't like me

---

### Post by ubudog on 2012-06-30
Strange, did you check it out as root?

You can always:
```
sudo rm -rf dangerdeep
```

---

### Post by auspot on 2012-06-30
don't know how to use root

does this mean its gone?

bill@bill-ET1831:~$ ls
Desktop    Downloads     examples.desktop       Music     Public  Templates
Documents  electric.log  Firefox_wallpaper.png  Pictures  squeak  Videos
bill@bill-ET1831:~$

I believe that dangerdeep no longer exists on this system

Thank you for all you help
auspot

---

### Post by ubudog on 2012-06-30
Yep, dangerdeep is gone.

Now you can check it out from svn again, like so:
```
svn co https://dangerdeep.svn.sourceforge.net/svnroot/dangerdeep/trunk/dangerdeep/ dangerdeep
```

Be warned that this could take a good while, and that cancelling it could result in the same problem as last time.

---

### Post by rosswmcgee on 2012-06-30
Do you like this better than Silent Sevice 2 ?

---

### Post by auspot on 2012-07-01
never tried Silent Sevice 2
auspot

---

### Post by rosswmcgee on 2012-07-02
Runs great in Dosbox, I think it is way better than danger deep.

---

