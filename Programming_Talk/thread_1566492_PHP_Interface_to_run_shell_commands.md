---
title: "PHP Interface to run shell commands"
date: 2010-09-02
forum: Programming Talk
---

### Post by Mr_G on 2010-09-02
Hi Guys,

I have implemented remote administration of servers via shell which includes viewing of log files.

The issue is that the logs are so big that the putty terminal seems to hang at times.

I wanted to do this via web and Hence needed to know how I can use PHP cli or cgi to achieve this.

Thanks

---

### Post by Hellkeepa on 2010-09-02
HELLo!

I recommend using "[proc_open ()](http://us3.php.net/manual/en/function.proc-open.php)" to start the process, as it'll allows for the process to run in the background. If that isn't what you want, then you'll need to use "exec ()" and make sure that all output is piped elsewhere than stdout. That'll allow PHP to start it in the background, and let it run completely independently.

Happy codin'!

---

### Post by Mr_G on 2010-09-03
Thanks for the reply.

I ll keep that in mind, But I did a bit of Googling and found cgi as a better alternative.

---

