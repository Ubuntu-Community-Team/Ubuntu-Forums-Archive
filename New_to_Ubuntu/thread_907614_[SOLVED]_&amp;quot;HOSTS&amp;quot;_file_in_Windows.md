---
title: "[SOLVED] &amp;quot;HOSTS&amp;quot; file in Windows = &amp;quot;?&amp;quot; in Xubuntu?"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by ExWindowsDude on 2008-09-01
In windows, I use the HOSTS file as loopback for unwanted adaware sites, etc. (i.e. Spybot adds badsitename 127.0.0.1) to loop back.

Is there a similar security mechanism I can use in Xubuntu?

I *HATE* surfing without at least that minimal protection.

Thanks!!

---

### Post by OutOfReach on 2008-09-01
I'm sure that it is /etc/hosts.

---

### Post by doas777 on 2008-09-01
> **ExWindowsDude said:**
> In windows, I use the HOSTS file as loopback for unwanted adaware sites, etc. (i.e. Spybot adds badsitename 127.0.0.1) to loop back.

Is there a similar security mechanism I can use in Xubuntu?

I *HATE* surfing without at least that minimal protection.

Thanks!!

you may be able to copy the contents of a spybot modified hosts file from windows (%windir%\System32\Drivers\etc\hosts). the basic contents of the file are the same, if you don;t have any old lanman config defined.

OutOfReach is correct on the location of the file in ubuntu.

good luck,
frank

---

### Post by cariboo on 2008-09-01
You may get some unexpected results if you put your block list in /etc/hosts, you would be better off putting the list in /etc/hosts.deny

Jim

---

### Post by caljohnsmith on 2008-09-01
> **cariboo907 said:**
> You may get some unexpected results if you put your block list in /etc/hosts, you would be better off putting the list in /etc/hosts.deny

Jim
Actually, /etc/hosts.deny is for *incoming* networking requests like ssh, ftp, etc and not outgoing requests such as from your web browser. So unfortunately, using /etc/hosts.deny wouldn't work for blocking access to websites. :)

---

### Post by ExWindowsDude on 2008-09-02
> **OutOfReach said:**
> I'm sure that it is /etc/hosts.

REALLY Dumb question, but I gotta ask it just because I'm new to Linux and want to make sure.

The "Loopback" address is the same in Linux, correct?
127.0.0.1

(I'm *assuming* Linux/Xubuntu does not have it's own IP Protocol universe..*grin*, but just making noob sure).

:-)

---

### Post by caljohnsmith on 2008-09-02
> **ExWindowsDude said:**
> REALLY Dumb question, but I gotta ask it just because I'm new to Linux and want to make sure.

The "Loopback" address is the same in Linux, correct?
127.0.0.1

(I'm *assuming* Linux/Xubuntu does not have it's own IP Protocol universe..*grin*, but just making noob sure).

:-)
Yes, Linux does not have its own "IP protocol universe", so loopback or "LOCALHOST" is still 127.0.0.1 :)

Hmmmm.... having your own IP protocol universe... Just don't give Microsoft any ideas here! :D

---

### Post by ExWindowsDude on 2008-09-02
> **cariboo907 said:**
> You may get some unexpected results if you put your block list in /etc/hosts, you would be better off putting the list in /etc/hosts.deny

Jim

Hey Jim,
Just want to clarify what you mean by "unexpected" results.

If,  for example you mean I might get a (blank box) with HOSTS denied, on my screen as I'm surfing (in lieu of the Ad itself), that's o.k. I'm use to that.

For example, pick "Adware FARM!!!"--myspace.com
if I ever have the (temporary insanity) to want to visit that AD FARM CESSPOOL...lots of links are broken (and I'll have blank boxes....and/or will have to 'open' my hosts file--i.e. revert to empty HOSTS to surf the site)....I"m o.k. with those "unexpected" results.


If, however you mean there are SYSTEM related issues (native to my Desktop Xubuntu environment) I could screw up...please let me know....as I'm noob to Xubuntu and trying to be "safe" with experimenting....


Thanks!

---

