---
title: "How to check DSL status?"
date: 2008-07-15
forum: Programming Talk
---

### Post by rivalslayer on 2008-07-15
Can anyone help me with this? I want to check if the DSL connection is on or off. How can I check that using shell? Please help!

:)

---

### Post by ErusGuleilmus on 2008-07-15
```
ping www.google.com
```

---

### Post by tinny on 2008-07-15
> **ErusGuleilmus said:**
> ```
ping www.google.com
```

Yeah, those guys are always up! Man they are good.

---

### Post by ghostdog74 on 2008-07-15
> **tinny said:**
> Yeah, those guys are always up! Man they are good.

if it so happens that [www.google.com](www.google.com) is down, then you would have false positive. 2 other ways
1) check more sites
2) contact your DSL provider and see if they provide DSL checking service?

---

### Post by Mickeysofine1972 on 2008-07-15
type:

```
tail -f /var/log/messages
```

if your dsl is up you will see the connection messages and line speed etc.

Mike

---

### Post by themusicwave on 2008-07-15
> **Mickeysofine1972 said:**
> type:

```
tail -f /var/log/messages
```

if your dsl is up you will see the connection messages and line speed etc.

Mike

I just get a bunch of bluetooth messages with that command.  My DSL is up, but the blue tooth messages must be more recent.  This way may not always work.

Although it is a good way to see what my pesky bluetooth mouse is up to!

---

### Post by themusicwave on 2008-07-15
Look in /proc/net/dev

There are lots of info in there about networking.  I was able to write a script using them to be me my average bandwidth of all my connections o a 2 seconds update.

What you need is probably in there.

Other files in /proc/net may be helpful too.

---

### Post by Mickeysofine1972 on 2008-07-15
Its best to run that command whilst you unplug and replug the dsl router then you will see the messages.

once you know what the messages look like you could use grep to filter the /var/log/messages to only show those messages.

I would like to be more specific but each DSL device might have differing log output

Mike

EDIT:

```
tail -20 /var/log/messages |grep '[ADSL]'
```

that might do the trick but  *havent tested it :D*

---

