---
title: "bash if [ ] &amp;&amp; [ ] problem"
date: 2014-09-28
forum: Programming Talk
---

### Post by sgofferj on 2014-09-28
Hi,

why does that

```
AWAY=$(asterisk -rx "devstate list" | grep "Custom:PRIVAWAY" | sed "s/.*State: '\(.*\)'.*/\1/g")
SIPSTATUS=$(asterisk -rx "sip show peer sgofferj" | grep "Status" | sed "s/.*Status.*: \(.*\)/\1/g" | sed "s/ (.*).*//g")

if [ "${AWAY}" == "NOT_INUSE" ] && [ "${SIPSTATUS}" == "UNREACHABLE" ]; then
  asterisk -rx "devstate change Custom:PRIVAWAY INUSE"
fi

if [ "${AWAY}" == "INUSE" ] && [ "${SIPSTATUS}" == "OK" ]; then
  asterisk -rx "devstate change Custom:PRIVAWAY NOT_INUSE"
fi
```

Result in
```
/exec/pingphone.sh: line 14: [: missing `]'
/exec/pingphone.sh: line 10: [: missing `]'
```

:confused:

If I create a similar construction with [ ... ] || [ ... ], it works as expected...

-s

---

### Post by Vaphell on 2014-09-28
are you using bash or sh to run that?
if i copypaste your if into sh i get some error, apparently it has a problem with == and wants =

in bash you should use superior [[ ]]

---

### Post by sgofferj on 2014-09-28
Bash - as the title says. I usually try to stick to POSIX compatibility, just in case...
The absurd thing is that it works with || but not with &&, although it should...

---

