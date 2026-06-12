---
title: "Need help with perl regex expression"
date: 2007-07-17
forum: Programming Talk
---

### Post by Amon_Re on 2007-07-17
Hi guys,

At work we have a squid transparent proxy that we use to cache Mac  & Windows updates, and since recently the Windows updates seem to fail.

I managed to trace the problem to a file that is getting cached that should not be cached, however, i am unable to edit the regex appropriatly to exclude the file

This is the regex in question:
```
m#^http://(.*?\.microsoft\.com\S+(?:(?!(wuredir|wusetup|wuweb)).......|^.{0,6})\.(cab|exe|idx|dat|img|dmg|tar))\b#i
```

The file that should be excluded is wuweb_setup.cab

If anyone can tell me what i'm doing wrong, i'd appreciate it

---

### Post by wvalters on 2007-07-17
m#^[http://(.*?\.microsoft\.com\](http://(.*?\.microsoft\.com\)[COLOR="Red"]S+[/COLOR]

That S+ in there means ANYTHING but whitespace, so wuweb_setup.cab will match in along with the [http://www.microsoft.com](http://www.microsoft.com).

since your next section is an OR that has one part that can match 0 times, it passes.

---

### Post by Amon_Re on 2007-07-17
> **wvalters said:**
> m#^[http://(.*?\.microsoft\.com\](http://(.*?\.microsoft\.com\)[COLOR="Red"]S+[/COLOR]

That S+ in there means ANYTHING but whitespace, so wuweb_setup.cab will match in along with the [http://www.microsoft.com](http://www.microsoft.com).

since your next section is an OR that has one part that can match 0 times, it passes.

Huh, then why is it not downloading the other files mentioned? As far as i know it doesn't download the files wuredir.cab and wusetup.cab

Mind you, this ain't my code, i inherited this, let's see if i understand

```
m#^http://(.*?\.microsoft\.com\S+
```
This will match anything containing microsoft.com, regardless of what comes before & as long as there's no "whitespace"?

```
(?:(?!(wuredir|wusetup|wuweb)).......|^.{0,6})
```

This... i can't figure out at all, i don't know perl at all, and the bits of info i found online made me even more confused then i already am.

Don't even know where to start

```
\.(cab|exe|idx|dat|img|dmg|tar))\b#i
```

This i take it is just an OR matching any of those extensions

---

### Post by McNils on 2007-07-17
Your expression is designed to find names with an extension cab|exe|idx|dat|img|dmg|tar that is not prefixed with wuredir|wusetup. wuweb failes because it doesn't match the number of dots after (?!(wuredir|wusetup|wuweb)).


I did manage to weed out wuweb_setup.cab with this expression ```
m#^http://(\S+microsoft\.com\S+(?:(?!(wuweb_setup))...........|^.{0,10})\.(cab|exe|idx|dat|img|dmg|tar))\b#i
```

If you can combine the two expressions you have a solution to yor problem...

---

### Post by Amon_Re on 2007-07-18
So doing the following should work?

```
m#^http://(\S+microsoft\.com\S+(?:(?!(wuweb_setup))...........|^.{0,10})\.(cab|exe|idx|dat|img|dmg|tar))\b#i
|| m#^http://(.*?\.microsoft\.com\S+(?:(?!(wuredir|wusetup|wuweb)).......|^.{0,6})\.(cab|exe|idx|dat|img|dmg|tar))\b#i
```
 Or would that be to simple? :P

---

### Post by Amon_Re on 2007-07-18
> **Amon_Re said:**
> So doing the following should work?

```
m#^http://(\S+microsoft\.com\S+(?:(?!(wuweb_setup))...........|^.{0,10})\.(cab|exe|idx|dat|img|dmg|tar))\b#i
|| m#^http://(.*?\.microsoft\.com\S+(?:(?!(wuredir|wusetup|wuweb)).......|^.{0,6})\.(cab|exe|idx|dat|img|dmg|tar))\b#i
```
 Or would that be to simple? :P

Meh, that was too simple indeed, but i finally managed to figure out the code (i think) so i came up with this:
```
 m#^http://(.*?\.microsoft\.com\S+((?:(?!(wuredir|wusetup)).......|^.{0,6})&(?:(?!(wuweb_site))..........|^.{0,10}))\.(cab|exe|idx|dat|img|dmg|tar))\b#i
```

Blah, perl just isn't my thing, it looks like obfuscated code to me

---

