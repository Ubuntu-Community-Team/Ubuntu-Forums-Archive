---
title: "Problems with debmirror"
date: 2017-06-14
forum: New to Ubuntu
---

### Post by Nigel_Pain on 2017-06-14
I'm managing a number of Ubuntu machines, all recently upgraded to 14.04 LTS. One is a mirror which has been holding 12.04 and 14.04 packages. I have now changed this to 14.04 and 16.04 packages, in preparation for upgrading the machines to 16.04 LTS. However, when the mirror update job runs (using debmirror) it gets so far and then fails on a particular package. The message I'm getting is:

> [  0%] Getting: pool/main/g/gcc-4.8/gcj-4.8-source_4.8.4-2ubuntu1~14.04.3_all.deb... read failed: Connection reset by peer at /usr/share/perl5/LWP/Protocol/http.pm line 460. at /usr/share/perl5/LWP/UserAgent.pm line 916.
WARNING: releasing 1 pending lock...

It always seems to be the same package.

Can anyone help?

Thanks.

---

### Post by Rocket2DMn on 2017-06-15
This could have been a transient problem with the mirror you're fetching from.  Has the problem resolved itself?  If not, what remote repository are you mirroring?

---

### Post by Nigel_Pain on 2017-06-15
Thanks for your help.

No, it hasn't resolved itself. I'm using gb.archive.ubuntu.com, which is the only repository that we have access to through the proxy server. 

However I have found a way around the problem (I think!) We have another repository mirror in our development network and that particular package was there. So I managed to use scp to copy it across. As far as I can see, it fixes the symptom, but not the cause. But hopefully, if it's transient it shouldn't be a problem in the long run.

---

### Post by Rocket2DMn on 2017-06-15
That's strange, because I'm able to access the file directly at [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.8/gcj-4.8-source_4.8.4-2ubuntu1~14.04.3_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.8/gcj-4.8-source_4.8.4-2ubuntu1~14.04.3_all.deb)

Are you able to access it directly?  I didn't realize you're using a proxy - it could that your proxy is dropping the connection.

---

### Post by Nigel_Pain on 2017-06-16
Yes, it looks like it could be a proxy issue. I was able to download both using a machine that's not on our network. Also happened with [http://gb.archive.ubuntu.com/ubuntu/pool/universe/g/gcc-4.9/gcj-4.9-source_4.9.3-13ubuntu2_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/universe/g/gcc-4.9/gcj-4.9-source_4.9.3-13ubuntu2_all.deb) so I think there's a pattern there. Our Systems Management are going to take a look at the proxy logs. 
Thanks for your advice. I'll mark this thread as Solved.

---

