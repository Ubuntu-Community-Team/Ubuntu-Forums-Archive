---
title: "How To: Modify SSH Welcome Text"
date: 2009-05-25
forum: Outdated Tutorials &amp; Tips
---

### Post by BslBryan on 2009-05-25
Hello, everyone. :-)

If I ever want to connect through SSH, I receive this message:
```
2.6.24-24-generic #1 SMP Wed Apr 15 15:54:25 UTC 2009 i686 GNU/Linux

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

Last login: Mon May 25 02:52:46 2009
bryan@HAL_9000:~$
```

That's so boring.  Let's change it. :-)

We're going to do this by editing /etc/motd.  For your own security purposes, I'm not going to tell you how to disable the "last login" message.  If you're set on doing that, you can look up another how to. :-)

The /etc/motd file contains the Ubuntu warranty information and the Linux build information.  Let's delete that, and write whatever we'd like. :-)

```
I am a HAL_9000 computer.  I became operational at the H.A.L. plant in Chattanooga, 
Tennessee on the 12th of January 2008.  My instructor was Bryan Basil, and he taught 
me to sing a song.  If you'd like to hear it, I can sing it for you.

Last login: Mon May 25 03:29:14 2009
bryan@HAL_9000:~$
```

I hope that I've made someone's machine a lot cooler! :-)

---

