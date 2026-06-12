---
title: "conky theme IP doesnt show up"
date: 2014-04-30
forum: Programming Talk
---

### Post by tomasvdmeer on 2014-04-30
Hi all

in my theme file of conky i have this code:
```

${color}public IP: $alignr${execi 60 ~/.conky/ip.sh}

```

and in the ip.sh i have this code
```

#!/bin/bash
wget http://checkip.dyndns.org/ -q -O - |
grep -Eo '\<[[:digit:]]{1,3}(\.[[:digit:]]{1,3}){3}\>'

```
And still the ip adress doesnt show up, whats the mistake i made?
thxalot

---

### Post by tomasvdmeer on 2014-04-30
Fixed it, execi wont work

---

