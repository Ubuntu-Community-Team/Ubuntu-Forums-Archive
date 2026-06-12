---
title: "could someone send me the source code of ffmpeg please?"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by njsfzj on 2008-06-10
Hi,
would someone not mind sending me the source code of ffmpeg please? I can't download it through SVN in the college. My email is
[email]njsfzj@gmail.com[/email]

Thank you very much!

---

### Post by Martje_001 on 2008-06-10
Done.

---

### Post by hyper_ch on 2008-06-10
you could get the source also through apt

---

### Post by Martje_001 on 2008-06-10
```
apt-get source ffmpeg
```
Like that.

---

### Post by njsfzj on 2008-06-10
Get it. Thank you, Martje!
hyper_ch, if I download it through apt, what folder will the source be downloaded in?
Thank you!

---

### Post by exile on 2008-06-10
by default it will set up the source code in the directory that you executed the apt-get source in.

eg.

cd /tmp
apt-get source ffmpeg
cd ffmpeg-0.cvs20070307

---

### Post by FakeOutdoorsman on 2008-06-10
ffmpeg devlopment is active and the source from the repos is old.  Nightly snapshots from subversion are available. From: [http://ffmpeg.mplayerhq.hu/download.html]("http://ffmpeg.mplayerhq.hu/download.html")
> We also provide nightly Subversion snapshots. You can choose between a [full checkout]("http://ffmpeg.mplayerhq.hu/ffmpeg-checkout-snapshot.tar.bz2") that you can update with Subversion or [bare sources]("http://ffmpeg.mplayerhq.hu/ffmpeg-export-snapshot.tar.bz2") that are smaller but don't come with Subversion metadata.
You might also be interested in:  [HOWTO: Compile the latest ffmpeg and x264 from source]("http://ubuntuforums.org/showthread.php?t=786095")

---

