---
title: "Have I installed thunderbird correctly?"
date: 2012-04-10
forum: New to Ubuntu
---

### Post by kapi on 2012-04-10
Hi, Just downloaded the tar file for thunderbird and extracted the directory to my home directory. Then I added a new icon to the applications menu and pointed the command to:

/home/me/thunderbird/thunderbird

Thunderbird opens fine but I can't help thinking that I should be doing stuff with chmod and permissions.

Is this all I have to do?

Thanks

---

### Post by MG&amp;TL on 2012-04-10
Rule (IMHO) is:

"If it ain't broke, don't fix it"

But why not simply install thunderbird from the repositories?

Sometimes you might have to set execution permmisions on an executable (chmod +x), but only if you installed from a tarball.

---

### Post by kapi on 2012-04-10
I kept getting messages saying it's unsupported and that a newer version was available so I thought I'd give it a go.

---

### Post by MG&amp;TL on 2012-04-10
> **kapi said:**
> I kept getting messages saying it's unsupported and that a newer version was available so I thought I'd give it a go.

Is your profile information regarding your Ubuntu version correct? If it is, you might consider updating or adding a PPA for thunderbird. According to wikipedia, 10.10's support runs out April this year.

---

### Post by QIII on 2012-04-10
EOL for 10.10 is today.

OP:  this means a couple of things to you.

1.  The way you have installed Thunderbird keeps you from getting updates from the repositories, no matter which version of Ubuntu you have.

2.  You will not get updated versions of any other software you have through the repos.

3.  You can add the PPA as suggested above, or...

4.   You can upgrade your version of Ubuntu.

Be aware that the upgrade path for 10.10 is only to 11.04.  You can upgrade to 11.10 from 11.04 without waiting.
  
Even at 11.04, I'm not sure Tbird 11.0.1 is available in the repo yet, although it seems that is the plan.  So the PPA may still be the way to go.

---

