---
title: "touch command confusion with &quot;&amp;&amp; \&quot;"
date: 2014-02-15
forum: New to Ubuntu
---

### Post by epikvision on 2014-02-15
I am currently setting up mutt on my Ubuntu 12.04 machine. I want to verify something about the following commands, used to set up msmtp.

```

touch $HOME/.msmtprc && \
touch $HOME/.msmtp.log && \
chmod 0600 $HOME/.msmtprc

```

What does "&& \" do?  I don't know if they're relevant.

---

### Post by Lars Noodén on 2014-02-15
The && will run the next command if the first one was successful.  .So if the first touch was successful, run the second touch.  If that was successful, too, then do the chmod.

The \ means that it continues on the next line.  So this is equivalent to the above:

```

touch $HOME/.msmtprc && touch $HOME/.msmtp.log && chmod 0600 $HOME/.msmtprc

```

You can see && and || in action:

```

/bin/true && echo OK || echo fail
/bin/false && echo OK || echo fail

```

/bin/true always succeeds, /bin/false always fails.

---

### Post by sisco311 on 2014-02-15
EDIT: D'oh! Lars Noodén beat me to it.  :)

&& is a control or list operator; it represents a logical AND:
```
command1 && command2
```
command2 is executed if, and only if, the execution of command1 was successful.

The sequence \<newline> is treated as a line continuation:
 
See:
[http://mywiki.wooledge.org/BashGuide/TestsAndConditionals](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals)
and
[http://wiki.bash-hackers.org/syntax/quoting](http://wiki.bash-hackers.org/syntax/quoting)

---

### Post by epikvision on 2014-02-15
Ah ok, I see that the commands are meant to be "copy-pasted." Thanks!

---

### Post by andrew.46 on 2014-02-27
I suspect that you are following an old guide of mine:

[https://help.ubuntu.com/community/MuttAndGmail](https://help.ubuntu.com/community/MuttAndGmail)

Good to see it still is useful :)

---

### Post by BlinkinCat on 2014-02-27
> **andrew.46 said:**
> I suspect that you are following an old guide of mine:

[https://help.ubuntu.com/community/MuttAndGmail](https://help.ubuntu.com/community/MuttAndGmail)

Good to see it still is useful :)

Hi andrew.46

Might I suggest you do a minor update to your page to retain it within NewDocs which has an 18 month edit  limit at present.

Perhaps you could check the URL on your external Link which came up with a 404 error on my check.

Regards,

BlinkinCat

---

### Post by andrew.46 on 2014-02-27
> **BlinkinCat said:**
> Might I suggest you do a minor update to your page to retain it within NewDocs which has an 18 month edit  limit at present.

Perhaps you could check the URL on your external Link which came up with a 404 error on my check.

The 404 is from old website which is now defunct unfortunately. I only really maintain a vlc guide on these Forums at the moment, but that page is a wiki so anybody can jump in and alter things as they see fit. The basic information should be pretty sound still...

---

### Post by BlinkinCat on 2014-02-27
> **andrew.46 said:**
> The 404 is from old website which is now defunct unfortunately. I only really maintain a vlc guide on these Forums at the moment, but that page is a wiki so anybody can jump in and alter things as they see fit. The basic information should be pretty sound still...

If I remove the link that should retain an up to date edit if that is O.K. with you.

---

### Post by andrew.46 on 2014-02-27
> **BlinkinCat said:**
> If I remove the link that should retain an up to date edit if that is O.K. with you.

Thanks for going to the trouble :)

---

### Post by BlinkinCat on 2014-02-27
> **andrew.46 said:**
> Thanks for going to the trouble :)

It is no trouble whatsoever!

The main issue is that you still consider the page relevant today.

Cheers - :)

---

