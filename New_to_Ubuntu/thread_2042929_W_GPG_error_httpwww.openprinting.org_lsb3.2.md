---
title: "W: GPG error: http://www.openprinting.org lsb3.2"
date: 2012-08-15
forum: New to Ubuntu
---

### Post by cejack on 2012-08-15
I get the following message when updating now:

W: GPG error: [http://www.openprinting.org](http://www.openprinting.org) lsb3.2 Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7A4B44C2D2A2203E

Is there something wrong with the repository for "www.openprinting.org".  I think this has been in my software sources list for some time now and it is all of a sudden becoming a problem.  Seems to not be updating because of some key problem I guess.  

Any fixes or is there a new repository or something?

I'm still on Ubuntu 10.04 LTS...

---

### Post by oldos2er on 2012-08-15
That's just a warning that you're missing the gpg key. ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 7A4B44C2D2A2203E

sudo apt-get update
``` should work.

---

### Post by cejack on 2012-08-19
Thank you very much.  

Worked fabulously.  

Us Ubuntu nincompoops don't know much about keyserver commands and stuff like that.

---

### Post by kennyhendrick on 2012-11-24
Wow...gotta love this Linux community~! :popcorn:

Thanks

---

### Post by vigyani on 2013-05-20
Hi

Thanks it worked.

---

### Post by sddfdds on 2013-06-02
Did this fully work for you?  For me it ended up with a similar but new error:

W: GPG error: [http://www.openprinting.org](http://www.openprinting.org) lsb3.1 Release: The following signatures were invalid: BADSIG 7A4B44C2D2A2203E OpenPrinting (OpenPrinting Test Key) <webmaster@openprinting.org>

---

### Post by Blackbart42 on 2013-06-09
> **sddfdds said:**
> Did this fully work for you?  For me it ended up with a similar but new error:

W: GPG error: [http://www.openprinting.org](http://www.openprinting.org) lsb3.1 Release: The following signatures were invalid: BADSIG 7A4B44C2D2A2203E OpenPrinting (OpenPrinting Test Key) <webmaster@openprinting.org>

I ended up with this same error. Is it because we have "lsb3.1" rather than "lsb3.2"? If so, how can we update? Thanks!

---

### Post by gosh7001 on 2013-06-14
Getting the same error when trying to update and cannot find a solution. I was reading on a german thread that the key needed to be updated on the package itself so there maybe little we can do. That was on May 10th though and still the error is there. I wonder if support knows about this. I am new to Ubuntu but if someone knows how to contact Ubuntu support and can get them to update the keys in the package, that would be wonderful. Thanks!

---

### Post by stronghenge on 2013-06-16
> **Blackbart42 said:**
> I ended up with this same error. Is it because we have "lsb3.1" rather than "lsb3.2"? If so, how can we update? Thanks!

I had the same issue.  Turns out the repo entry in /etc/apt/sources.list for openprinting.org was incorrect.  This is what I changed mine to:

```
deb http://www.openprinting.org/download/printdriver/debian/ lsb3.2 main
```

And it works now!

---

### Post by rsmeineke on 2013-06-17
> **stronghenge said:**
> I had the same issue.  Turns out the repo entry in /etc/apt/sources.list for openprinting.org was incorrect.  This is what I changed mine to:

```
deb http://www.openprinting.org/download/printdriver/debian/ lsb3.2 main
```

And it works now!

---------------------------------
Thanks for this.

I changed this:
deb [http://www.openprinting.org/download/printdriver/debian/](http://www.openprinting.org/download/printdriver/debian/) lsb3.1 gutenprint

to this:
deb [http://www.openprinting.org/download/printdriver/debian/](http://www.openprinting.org/download/printdriver/debian/) lsb3.2 main

And the error went away for me as well.

Regards,
Robert M.

---

### Post by bodie-ci5 on 2013-08-10
> **stronghenge said:**
> I had the same issue.  Turns out the repo entry in /etc/apt/sources.list for openprinting.org was incorrect.  This is what I changed mine to:

```
deb http://www.openprinting.org/download/printdriver/debian/ lsb3.2 main
```

And it works now!

Sensational! Thanks heaps, stronghenge!

---

### Post by lionslair on 2013-12-19
> **rsmeineke said:**
> ---------------------------------
Thanks for this.

I changed this:
deb [http://www.openprinting.org/download/printdriver/debian/](http://www.openprinting.org/download/printdriver/debian/) lsb3.1 gutenprint

to this:
deb [http://www.openprinting.org/download/printdriver/debian/](http://www.openprinting.org/download/printdriver/debian/) lsb3.2 main

And the error went away for me as well.

Regards,
Robert M.

Your step resolved mine too thank you

---

### Post by Paul_Maki on 2014-01-05
This was driving me nuts, Thanks!

---

### Post by eflester on 2014-01-05
Allow me to add my thanks. I have had this little error nagging me for a while on this 13.04 Lubuntu install. Fixing the repository name was the key for me.

---

