---
title: "zenity question"
date: 2014-08-12
forum: Programming Talk
---

### Post by jimmyh1972 on 2014-08-12
Hi
I wrote a script uses "zenity --question"
how do I catch the output of yes / no click?
I want to put an if statment uses the output 
Thank's ahead
Jimmi

---

### Post by cariboo on 2014-08-12
This really has nothing to do with Utopic. Moved.

---

### Post by steeldriver on 2014-08-12
You should be able to use the return code e.g.

```

zenity --timeout 3 --question
case $? in 
  0) echo "Yes"
  ;; 
  1) echo "No"
  ;; 
  *) echo "Timeout"
  ;; 
esac

```

See **man zenity**

```

       For example, zenity --question will return either 0, 1 or 5,  depending
       on  whether  the  user  pressed OK, Cancel or timeout has been reached.

```

---

### Post by rhss6-2011 on 2014-08-13
From my use of zenity you need to use a mix between shell/bash scripting and zenity itself. I did a Yes/No script once that worked properly (even though it's been a couple years) and here's the code for that.
I'm not saying it's the answer, I just think that it will help point you in the right direction.

```

#!/bin/sh
zenity --question --text="QUESTION" --ok-label="Yes" --cancel-label="No"
if [ $? = 0 ] ; then
command=$()
else
command=$()
fi

```


**EDITED TO ADD THIS:**

As an example, I created a script using Zenity for changing your keyboard layout. I'm giving you the code so that might help you piece together what you're trying to do...

```

#!/bin/sh
ans=$(zenity --width="600" --height="600" --title="LXDE Keymap Configuration" --text="Please select your keymap" --print-column="3" --radiolist --list \
          --column="" --column="Country" --column='Keyboard Entry Code' \
""    "USA"                       'us' \
""    "Andorra"                 'ad' \
""    "Afghanistan"                 'af' \
""    "Arabic"                 'ara' \
""    "Albania"                 'al' \
""    "Armenia"                 'am' \
""    "Azerbaijan"                 'az' \
""    "Belarus"                 'by' \
""    "Belgium"                 'be' \
""    "Bangladesh"                 'bd' \
""    "India"                 'in' \
""    "Bosnia and Herzegovina"         'ba' \
""    "Brazil"                 'br' \
""    "Bulgaria"                 'bg' \
""    "Morocco"                 'ma' \
""    "Myanmar"                 'mm' \
""    "Canada"                 'ca' \
""    "Congo, Democratic Republic of the"    'cd' \
""    "China"                 'cn' \
""    "Croatia"                 'hr' \
""    "Czechia"                 'cz' \
""    "Denmark"                 'dk' \
""    "Netherlands"                 'nl' \
""    "Bhutan"                 'bt' \
""    "Estonia"                 'ee' \
""    "Iran"                     'ir' \
""    "Iraq"                     'iq' \
""    "Faroe Islands"             'fo' \
""    "Finland"                 'fi' \
""    "France"                 'fr' \
""    "Ghana"                 'gh' \
""    "Guinea"                 'gn' \
""    "Georgia"                 'ge' \
""    "Germany"                 'de' \
""    "Greece"                 'gr' \
""    "Hungary"                 'hu' \
""    "Iceland"                 'is' \
""    "Israel"                 'il' \
""    "Italy"                 'it' \
""    "Japan"                 'jp' \
""    "Kyrgyzstan"                 'kg' \
""    "Cambodia"                 'kh' \
""    "Kazakhstan"                 'kz' \
""    "Laos"                     'la' \
""    "Latin American"             'latam' \
""    "Lithuania"                 'lt' \
""    "Latvia"                 'lv' \
""    "Maori"                 'mao' \
""    "Montenegro"                 'me' \
""    "Malta"                 'mt' \
""    "Mongolia"                 'mn' \
""    "Norway"                 'no' \
""    "Poland"                 'pl' \
""    "Portugal"                 'pt' \
""    "Romania"                 'ro' \
""    "Russia"                 'ru' \
""    "Serbia"                 'rs' \
""    "Slovenia"                 'si' \
""    "Slovakia"                 'sk' \
""    "Spain"                 'es' \
""    "Sweden"                 'se' \
""    "Switzerland"                 'ch' \
""    "Syria"                 'sy' \
""    "Tajikistan"                 'tj' \
""    "Sri Lanka"                 'lk' \
""    "Thailand"                 'th' \
""    "Turkey"                 'tr' \
""    "Ukraine"                 'ua' \
""    "United Kingdom"             'gb' \
""    "Uzbekistan"                 'uz' \
""    "Vietnam"                 'vn' \
""    "Korea, Republic of"             'kr' \
""    "Japan (PC-98xx Series)"         'jp' \
""    "Ireland"                 'ie' \
""    "Pakistan"                 'pk' \
""    "Maldives"                 'mv' \
""    "South Africa"                 'za' \
""    "Esperanto"                 'epo' \
""    "Nepal"                 'np' \
""    "Nigeria"                 'ng' \
""    "Ethiopia"                 'et' ); echo "" ; setxkbmap $ans 

```

---

### Post by Vaphell on 2014-08-13
> **rhss6-2011 said:**
> 

**EDITED TO ADD THIS:**

As an example, I created a script using Zenity for changing your keyboard layout. I'm giving you the code so that might help you piece together what you're trying to do...


Y U NO USE BASH AND ARRAYS!

```
#!/bin/bash

kb=(   us:USA 
       ad:Andorra
       af:Afghanistan
      ara:Arabic
       al:Albania
       am:Armenia
       az:Azerbaijan
       by:Belarus
       be:Belgium
      etc:"Et cetera, et cetera" )

zen_opts=( --width="600" --height="600"
           --title="LXDE Keymap Configuration"
           --text="Please select your keymap"
           --print-column="3"
           --radiolist --list 
           --column="" --column="Country" --column='Keyboard Entry Code' )

for k in "${kb[@]}"
do
  zen_opts+=( "" "${k#*:}" "${k%%:*}" )
done
           
ans=$( zenity "${zen_opts[@]}" )
```

---

### Post by fugu2 on 2014-08-14
An example that can be tested right from the command line...
```
$ (zenity --question) && echo YES || echo NO
YES
$ (zenity --question) && echo YES || echo NO
NO

```

---

