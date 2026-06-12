---
title: "Awk Help - duplicates in $1 that match x &amp; y in $2"
date: 2011-12-22
forum: Programming Talk
---

### Post by jamesjwilsonsr on 2011-12-22
I'm primarily a "Windows" systems administrator whose been getting his toes in the Linux waters.  I am new to programming and advanced scripting so please bear with me and my incomplete example below.

I have exported all entries from our DNS zones.  I used sed to remove everything other than the fqdn from the files.  We have a few hundred hosts across a few dozen zones.  Some hosts are not in all zones though.

I would like to use something like awk to determine which hosts are (or are not) in the domains I specify.  Bonus might also be to accept input from a file (with the various domain names) but the simpler the better.

the file looks something like this:

host1.domain1.com
host1.domain2.com
host1.domain3.com
host1.domain4.com
host2.domain1.com
host2.domain2.com
host2.domain3.com
host2.domain4.com

and so on.  And again, some hosts are not in all zones.

I would like to do something like:
```
awk -F"." '($2 == "domain2" && $2 == "domain3") {print $1}' filename
```
to figure out which hosts are (or maybe, are not) in the zones specified.

Obviously this script is incomplete.  I can't figure out how to find duplicates from $1 and then search $2 for domain2 and domain3.
I want all hosts from $1 that match a few possible domain inputs from $2 to return, and nothing else.  Since I may have the same host returned per domain a few times, if the result could be truncated to just the host once, even better.

I am not necessarily looking to be spoon fed a few completed examples.  If you have a few ideas for me, I'd appreciate being pointed closer in the right direction.

---

### Post by Vaphell on 2011-12-22
not awk but an abomination in bash
```
#!/bin/bash

if (( $# < 2 )); then echo "usage: script.sh <input_file> <domain1.com> <domain2.co.uk>..."; exit 1; fi
h_file=$1
shift
echo domains: $@ "($#)"

rgx=$( echo $@ | sed -r 's/ /|/g' | sed -r 's/[.]/[.]/g' )
h_list=$( grep -oE '^[^.]+' "${h_file}" | sort -u )

for h in ${h_list}
do
  match=$( grep -E '^'${h}'[.]('${rgx}')$' "${h_file}" | sort -u )
  n=$( echo "${match}" | wc -w )
  if (( n == $# ));   then echo "${h}"
  elif (( n == 0 ));  then echo "! ${h}"; fi
done | sort -u
```
example:
```
$ ./hosts.sh hosts.txt domain1.com domain2.com domain3.com
domains: domain1.com domain2.com domain3.com (3)
host1
host2
! host666

```
listed hosts belong to all listed domains, ! means they don't belong to none. Script to find 'belongs to ABC' but ' not belongs to DEF' would be more complicated.

---

### Post by jamesjwilsonsr on 2011-12-22
> **Vaphell said:**
> not awk but an abomination in bash
```
#!/bin/bash

if (( $# == 0 )); then echo "usage: script.sh <input_file> <domain1.com> <domain2.co.uk>..."; exit 1; fi
h_file=$1
shift
echo domains: $@ "($#)"

rgx=$( echo $@ | sed -r 's/ /|/g' | sed -r s/[.]/[.]/g )
h_list=$( grep -oE '^[^.]+' "${h_file}" | sort -u )

for h in ${h_list}
do
  match=$( grep -E '^'${h}'[.]('${rgx}')$' "${h_file}" | sort -u )
  n=$( echo "${match}" | wc -w )
  if (( n == $# ));   then echo "${h}"
  elif (( n == 0 ));  then echo "! ${h}"; fi
done | sort -u
```
example:
```
$ ./hosts.sh hosts.txt domain1.com domain2.com domain3.com
domains: domain1.com domain2.com domain3.com (3)
host1
host2
! host666

```
listed hosts belong to all listed domains, ! means they don't belong to none. Script to find 'belongs to ABC' but ' not belongs to DEF' would be more complicated.
Ha, it worked!  Thank you very much.  I'd love to see if this looks any different/simpler in awk if any lurkers care to take a stab.  

Thanks a lot, this solved my immediate need.  I appreciate your time.

---

### Post by jamesjwilsonsr on 2011-12-22
I also post on unix.com and a guy there (ahamed101) came back with this awk script/code which also did the trick.  

```
awk -F"." '$2 ~ "domain2|domain3" {print $1}' input_file | sort | uniq
```

---

### Post by Vaphell on 2011-12-22
but does it cover the case when host belongs to domain2 but not to domain3?
i see simple OR here (unless awk treats | differently). imho this will print $1 if $2 is (domain2 OR domain3) which means that (h1.d2, h2.d3) will produce (h1, h2)

```
$ echo $'h1.d1.com\nh2.d2.com'
h1.d1.com
h2.d2.com


echo $'h1.d1.com\nh2.d2.com' | awk -F"." '$2 ~ "d1|d2" {print $1}' | sort | uniq
h1
h2

```

another question is whether domain.com is logically equal to domain.co.uk or not

---

