---
title: "conntrack -m"
date: 2020-11-28
forum: New to Ubuntu
---

### Post by skybird182 on 2020-11-28
What does the -m argument before conntrack indicate ? I have looked on different web sites but have not found the answer.

 [FONT=Arial, sans-serif][SIZE=2][B]iptables –A INPUT –p tcp –m multiport --dports 80,443[COLOR=#ff0000]_ –m_ conntrack [/COLOR]–cstate RELATED, ESTABLISHED –j ACCEPT

[/B]Thanks[/SIZE][/FONT]

---

### Post by The Cog on 2020-11-28
It's telling iptables to use the conntrack module, to which the --cstate argument then applies.
This is unusual - most examples you find looking for RELATED,ESTABLISHED use "-m state --state RELATED,ESTABLISHED" instead.

P.S. Please use code tags when posting console text. Click Go Advanced and use the # editor button.

---

### Post by TheFu on 2020-11-28
The iptables manpage says this:
```
       -m, --match *match*
              Specifies a match to use, that  is,  an  extension  module
              that  tests  for  a  specific property. The set of matches
              make up the condition under which  a  target  is  invoked.
              Matches  are  evaluated  first to last as specified on the
              command line and work in short-circuit  fashion,  i.e.  if
              one extension yields false, evaluation will stop.

```

Lots of good information in manpages, especially when using non-beginner tools.

---

### Post by skybird182 on 2020-11-29
Thanks. I should have looked in iptables and not for conntrack as a stand alone command but I am still learning.

---

### Post by TheFu on 2020-11-29
> **skybird182 said:**
> Thanks. I should have looked in iptables and not for conntrack as a stand alone command but I am still learning.

We all are. That's a good thing compared to the alternative. ;)

---

