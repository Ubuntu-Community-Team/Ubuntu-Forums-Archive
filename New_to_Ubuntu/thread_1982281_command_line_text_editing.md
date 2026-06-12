---
title: "command line text editing"
date: 2012-05-18
forum: New to Ubuntu
---

### Post by z3nhakr on 2012-05-18
kk so im trying to make a gui to use with nmap that will detect the subnet and automate a basic scan but it all has to be in one line of code. here's what i have so far: ```
ifconfig | grep -m 1 -o -E '(0|1|2)*[0-9]?[0-9]?\.(0|1|2)?[0-9]?[0-9]?\.(0|1|2)*[0-9]?[0-9]?\.(0|1|2)*[0-9]?[0-9]?' | grep -m 1 -o -E '(0|1|2)*[0-9]?[0-9]?\.(0|1|2)?[0-9]?[0-9]?\.(0|1|2)*[0-9]?[0-9]?\.'
```this returns "10.0.1." and i need to add "0/24" before i send it to nmap. how can i do this without setting any variables?

---

### Post by ksprasad on 2012-05-18
I think this will do..
 
```
echo `your command`0/24
```
 
Regards,
ksprasad

---

