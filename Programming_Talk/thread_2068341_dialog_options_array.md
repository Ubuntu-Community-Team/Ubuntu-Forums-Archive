---
title: "dialog options array"
date: 2012-10-08
forum: Programming Talk
---

### Post by conradin on 2012-10-08
Hi everyone, 
I have a bash script that launches a dialog interface. I want to read values from a .csv file to build the options selection but it is just not working right. Maybe someone can point out what Im doing wrong. 

```
			
#!/bin/bash
ar=()
	while read FName NName PN Email Comments
	 do
	ar+=($FName)
        done < contacts.csv
dialog  --menu "Latest news " 20 50 30 "${ar[@]}"
```

a sample from contacts.csv
```
@work,"",207-123-1234,"",Personnel services
AJ Whitney,,207-581-1234,,"Network Tech professional  "
Andrea,"",787-123-1234,"",Researcher, Fort Group
```

ordinarily when reading a csv, i would use the IFS=, flag to indicate that the script should parse on the comma.
but when I include that, it fails to even produce a dialog.
on the other hand, the while loop below gives the correct values, but no nifty interface.
```

#!/bin/bash
while IFS=, read FName NName PN Email Comments
do
	echo "$FName : $PN"
	done < contacts.csv

```

---

### Post by Vaphell on 2012-10-08
potential problem
```
ar+=([COLOR="Red"]"[/COLOR]$FName[COLOR="Red"]"[/COLOR])

AJ[COLOR="Red"]_[/COLOR]Whitney,,207-581-1234,,"Network Tech professional  "
```

in case of unshielded $FName the following code
```
for x in "${ar[@]}"; do echo "- '$x'"; done
```
 will produce
```
- '@work'
[COLOR="Red"]- 'AJ'
- 'Whitney'[/COLOR]
- 'Andrea'
```
i don't think you expect 4 parameters

---

