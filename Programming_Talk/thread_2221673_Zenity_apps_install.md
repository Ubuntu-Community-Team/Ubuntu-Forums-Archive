---
title: "Zenity apps install"
date: 2014-05-03
forum: Programming Talk
---

### Post by xxvirusxx on 2014-05-03
Hello


I try to make my own script to install my favorite application but do nothing. What is wrong?

Here is what I try

```
#!/bin/bash

choicess=`/usr/bin/zenity --title="Apps install" --width=520 --height=400 \
                         --text="Select to install" \
                         --list --column="Select" --column="Name" --column="Description" \
                         --checklist FALSE "Kopete" "For chat" FALSE "Inkscape" "vectors" `

if [ $? -eq 0 ]
then
        IFS="|"
        for choice in $choicess
        do
              if [ "$choice" = "Kopete" ];
                   then
                           sudo apt-get -y install kopete
             elif [ "$choice" = "Inkscape" ];
                   then
                           sudo apt-get -y install inkscape
  fi
done
```


Tks for help

---

### Post by Habitual on 2014-05-03
use
```

#!/bin/bash
set -xv
....
```

Run it in terminal.
Examine output.

---

### Post by Vaphell on 2014-05-03
typo in choices**s**

that said, a more general solution based on arrays would be something like this
```
#!/bin/bash

# [Program_name]=package_name:description
declare -A apps=(
                   ["Kopete"]="kopete:For chat"
                   ["Inkscape"]="inkscape:Vectors" 
                )

chklist=()
for k in "${!apps[@]}"; do chklist+=( "FALSE" "$k" "${apps[$k]#*:}" ); done

choices=$( zenity --title="Apps install" --width=520 --height=400 \
                  --text="Select to install" \
                  --list --column="Select" --column="Name" --column="Description" \
                  --checklist "${chklist[@]}" )

[[ -z $choices ]] && { echo 'sum-ting wong'; exit 1; }

pkg=()
IFS='|' read -a choices <<< "$choices"
for k in "${choices[@]}"; do pkg+=( "${apps[$k]%%:*}" ); done

sudo apt-get -y install "${pkg[@]}"
```

---

### Post by xxvirusxx on 2014-05-03
**@**Habitual

```

line 22: syntax error: unexpected end of file
```


@Vaphell
Is a PRO code but work. Tks
I will try to adapt for adding PPA :)

---

