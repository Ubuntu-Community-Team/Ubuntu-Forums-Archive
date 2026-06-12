---
title: "Synaptic error"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by MachSpire on 2008-09-29
As an absolute beginner, I'm puzzled by the message I'm getting when trying to load synaptic. Where do I start? How do I do the correction, and how do I make this report. I'm using the latest Hardy Heron:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Some help and advice would be most welcome.

Many thanks.

:confused:

---

### Post by arochester on 2008-09-29
It tells you what to do. Open a terminal and input:> sudo dpkg --configure -a

---

### Post by oldsoundguy on 2008-09-29
also make sure you have enabled and installed the repositories:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by MachSpire on 2008-09-29
Sorry, I meant to post to all and got a quote instead.

I was using su instead of sudo - however the synaptic problem is fixed thanks to the advice given by arochester. But, I can't get synaptic to accept the repositories address old sound guy gives - [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu). Am I doing wrong to try to add the address on the 3rd party tab?

Please advise.

Thanks.

---

### Post by Elfy on 2008-09-29
> sudo dpkg --configure -a is a command not a repository address

---

### Post by MachSpire on 2008-09-30
> **oldsoundguy said:**
> also make sure you have enabled and installed the repositories:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Well,

I did what you said and now have the following error:

E: Malformed line 58 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

Where is the repository dialogue, now that synaptic is not working? Then what do I do there?

Please help.

Many thanks.

:confused::confused::confused:

---

### Post by Elfy on 2008-09-30
What exactly have you added to the sources list - please post your sources list

```
cat /etc/apt/sources.list
```

If though you have added [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) to your sources list - it isn't a repo.

---

