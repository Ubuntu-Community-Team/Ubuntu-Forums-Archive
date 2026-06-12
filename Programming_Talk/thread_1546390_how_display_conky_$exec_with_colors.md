---
title: "how? display conky $exec *with colors*"
date: 2010-08-05
forum: Programming Talk
---

### Post by betlog on 2010-08-05
How do I output each text element with a different color?
eg: localPort=green remoteIP=orange remotePort=red protocol=white...etc
The catch: This is a shell script that is being displayed in conky.. so various obvious answers are probably going to be inappropriate.

**netstat-colored.sh**```
#!/bin/bash
netstat -nutp | sed 1,2d | awk '{gsub(/:/," ");print $5,$6,$7,"\t",$1"/"$9}'
```Completely different approaches welcome.. so long as its displayable by conky

Also; is there a way to specify which tab column a text element will jump to?
Because the length of a given field can vary quite a bit using regular tabs to space the columns doesnt work. Any ideas?

---

### Post by betlog on 2010-08-15
${execpi}

---

### Post by geirha on 2010-08-15
You can use printf to format the output
```

netstat -nulp | awk -F'[ :]+' 'NR>2{printf "%5d %-15s %5d   %s/%s\n", $5, $6, $7, $1, $9}'

```

As for coloring, I guess you'd have to have the awk print ${color foo} in front of each field as well, and use it with the execpi as betlog suggested.

---

### Post by betlog on 2010-08-15
interesting...
I ended up doing this 
```
lsof -n -i | sed 1,2d | awk '!/127.0.0.1/' | awk '/ESTABLISHED/' | awk '{gsub(/->/," ");print $0}' | awk '{gsub(/:/," ");print $1"${goto 110}${color green}"$8"${goto 140}"$10"${color}${goto 180}${color orange}"$11"${goto 280}:${goto 290}"$12"${color}"}'
```

which i am sure is ugly and inelegant.... i need to spend more time figuring out how to use sed etc properly

---

### Post by geirha on 2010-08-15
I'd consider looking into awk; you only need one.

```
lsof -n -i | awk -F '[ :]+|->' '$NF == "(ESTABLISHED)" && $11 != "127.0.0.1" {printf "${color}%-10s ${color green}%-3s  %5d  ${color orange}%-16s : %s\n", $1, $8, $10, $11, $12}'
```

You can probably do some more filtering with lsof too.

---

### Post by betlog on 2010-08-15
thanks
yeah, this was my first attempt to use any sed/awk/grep, and since then I have found some decent references/tutorials/manuals. I guess I just need to work on it a bit to get over that first hurdle where I have to overcome the frustration of not knowing anyhting about bash/perl/awk/sed/grep/etc.

---

