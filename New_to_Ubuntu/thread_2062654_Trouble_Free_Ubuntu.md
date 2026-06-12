---
title: "Trouble Free Ubuntu"
date: 2012-09-25
forum: New to Ubuntu
---

### Post by MathMcC on 2012-09-25
Hi,

I am currently installing Ubuntu 10.10 (Maverick Meerkat - I had to go with an older version because of a "this kernel requires the following features not present on the cpu: pae" warning on the latest version) on my boss's daughter's laptop (she's only 5 or so I think).

I want to make sure she doesn't get any bother, with updates, changes, configurations etc. Or if she does that her very non-techy parents can solve it easily.

All she needs to do is access the web: readingeggs.com

I wondered whether it would be wise to switch updates off so there is no risk of conflicts causing headaches.

Thanks!
Matt

---

### Post by jerrrys on 2012-09-25
You can [switch off updates]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=turn+off+updates&as_qdr=all&sa=Google+Search&lang=en") and just do a [manual updates]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=manual+updates&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F") when you feel like it :)

Myself, I have taken it a step further and do not have Update-Manager installed.

---

### Post by snowpine on 2012-09-25
10.10 has reached its end of support, so there will be no more updates or "hassle" for this obsolete release. It also means that your friend's underage daughter is surfing the web with an unsupported browser and no more security patches...

A better option is to install Xubuntu 12.04. This is a secure, long-term-support release (through April 2017!) that is designed for older hardware and therefore does not require a PAE kernel as described here: [http://askubuntu.com/questions/117744/how-can-i-install-12-04-on-a-non-pae-cpu-error-kernel-requires-features-not-p](http://askubuntu.com/questions/117744/how-can-i-install-12-04-on-a-non-pae-cpu-error-kernel-requires-features-not-p)

12.04 with a lightweight desktop environment and automatic updates turned *on* is my recommendation because a mature LTS release with 60 months of patches and bug fixes is the best path to "trouble free" in my opinion.

---

### Post by MathMcC on 2012-09-25
Good suggestion snowpine. Thanks.

> **snowpine said:**
> 10.10 has reached its end of support, so there will be no more updates or "hassle" for this obsolete release. It also means that your friend's underage daughter is surfing the web with an unsupported browser and no more security patches...

A better option is to install Xubuntu 12.04. This is a secure, long-term-support release (through April 2017!) that is designed for older hardware and therefore does not require a PAE kernel as described here: [http://askubuntu.com/questions/117744/how-can-i-install-12-04-on-a-non-pae-cpu-error-kernel-requires-features-not-p](http://askubuntu.com/questions/117744/how-can-i-install-12-04-on-a-non-pae-cpu-error-kernel-requires-features-not-p)

12.04 with a lightweight desktop environment and automatic updates turned *on* is my recommendation because a mature LTS release with 60 months of patches and bug fixes is the best path to "trouble free" in my opinion.

---

### Post by edeneen on 2012-09-25
I am a total nubie, I got that kernel error thing too on an older machine, I tried a different version of 12.04 and it worked perfectly, I agree with the above, go with 12.04

---

### Post by ssulaco on 2012-09-25
> **snowpine said:**
> 
A better option is to install Xubuntu 12.04. This is a secure, long-term-support release (through April 2017!)
Still 3 years on Xubuntu precise....
from Xubuntu.org > Below you’ll find a plethora of resources that will make getting help and resolving issues a snap. Getting help with Xubuntu is easy! The currently supported Xubuntu releases are:

Precise Pangolin 12.04 LTS, until April 2015
Oneiric Ocelot 11.10, until April 2013
Natty Narwhal 11.04, until October 2012
Lucid Lynx 10.04 LTS, until April 2013

> **snowpine said:**
> 12.04 with a lightweight desktop environment and automatic updates turned *on* is my recommendation because a mature LTS release with 60 months of patches and bug fixes is the best path to "trouble free" in my opinion.Totally agree on the Xubuntu Precise LTS being trouble free

---

### Post by HiImTye on 2012-09-26
> "this kernel requires the following features not present on the cpu: pae"
that is because you were using a 'pae' kernel, one that likely ended in 'generic-pae' such as '2.30.0.24-generic-pae' (I just randomly typed a kernel version number, don't take this is the literal version). switching to one that did not end in 'pae' would have fixed your problems.

that said, I would recommend using the latest stable version, which currently is 12.04

---

### Post by critin on 2012-09-26
Have you or the parents considered something especially for kids?  There are several that are supposed to be easy, and it gives them a chance to actually learn the computer too.

[http://www.brighthub.com/computing/linux/articles/43224.aspx](http://www.brighthub.com/computing/linux/articles/43224.aspx)

---

### Post by MathMcC on 2012-09-26
> **critin said:**
> Have you or the parents considered something especially for kids?  There are several that are supposed to be easy, and it gives them a chance to actually learn the computer too.

[http://www.brighthub.com/computing/linux/articles/43224.aspx](http://www.brighthub.com/computing/linux/articles/43224.aspx)

Brilliant. Thanks!

---

### Post by uzumakifahim on 2012-09-26
Overall, in my opinion Edubuntu 12.04 with disabled Update Manager is the perfect solution for you.

---

### Post by grahammechanical on 2012-09-26
Link to Edubuntu

[http://www.edubuntu.org/]("http://www.edubuntu.org/")

Notice that there is a weblive feature on the site where the OS can be tested for 2 hours (I think) without charge.

Regards.

---

