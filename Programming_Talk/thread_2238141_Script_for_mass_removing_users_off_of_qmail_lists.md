---
title: "Script for mass removing users off of qmail lists"
date: 2014-08-06
forum: Programming Talk
---

### Post by Damonion on 2014-08-06
So basically I am trying to make a script that will firstly ask for the name of a user, then continues to search for every list that user is on, and remove them from said list. Honestly I'm still fairly new to ubuntu, let alone making scripts for it. Apologies if the logic is all wrong, you've got to start somewhere, right ?

Anyway here it is: 

```
#!/bin/bash
Confirm = No
Returned = 0
while( $confirm = no) 
do
echo ""
echo "Enter name to Search and Destroy: "
read NAME
echo "The specified name is found in the following qmail aliases:"
echo ""
grep -i -H -d skip -l $NAME .qmail* | Returned
echo "Do you wish to delete them from these lists? (y/n)"
read Confirm
if(confirm = yes)
  {
    while ($Returned = >1)
    {
        sudo rvim $Returned | rm $NAME .qmail*
        :wq
    }
  }
done

```

Hopefully someone can give me some insight to where it would go wrong! I can't test it because it's for work use, and I don't want to mess things up on this end.

---

### Post by Vaphell on 2014-08-06
if it's supposed to be bash, the syntax is wrong

```
while [[ $confirm = no ]]
do
   ...

   if [[ $confirm = yes ]]
   then
      while (( Returned >= 1 ))
      do
         ...
      done
   fi
done
```

either way i have trouble understanding the train of thought and the goal from the code.
what is *grep ... | Returned* supposed to do?

---

### Post by Damonion on 2014-08-06
Right, thanks.

I was hoping that the returned answer would be able to be piped into the integer 'Returned' ? So that then later on in the script it could come back to finding each item returned into the integer and get to removing the user from each of the lists as included in the while loop.

Apologies for the bad code, it would seem I have some learning to do. The reason the syntax is jumbled is because this script is somewhat similar to another script that I know of that does indeed work.

Thanks for the input though, much appreciated.

---

### Post by Vaphell on 2014-08-06
capturing output of commands is done with *returned=$( command )*
but grep with such parameters would return text not a number so that kinda doesn't make sense.

can you describe the desired algorithm in plain words?

---

### Post by Damonion on 2014-08-06
Ah, right.

Basically I am wanting this script to firstly ask for a name and then search for every instance where the name is mentioned alongside '.qmail'

Then when this has been found I want it to open up each list, remove the user, and write-quit. Until the user is no longer in any of the email lists.

Is this even possible ? If so I'll need to work on my near to none existent bash skills.

---

### Post by Vaphell on 2014-08-06
If that's all then it sounds rather trivial. Are these .qmail* files nothing more than lists of users in plain text? Do they have some special format?

---

### Post by Damonion on 2014-08-06
Trivial, yes. It's just something I was looking at for work, to make the process a little bit easier.

The .qmail* files are nothing more than text laid out in this format

&t.user@workplace.com

---

### Post by Vaphell on 2014-08-06
```
#!/bin/bash

(( UID )) && { echo 'This script requires root privileges, use sudo'; exit 1; }

col=$'\e[1;36m'
rst=$'\e[0m'

while :
do
  qmail=()
  read -p "Enter name to Search and Destroy: " user

  while read -rd $'\0' f
  do
    qmail+=( "$f" )
  done < <( grep -ZHilF "$user" .qmail* )

  (( ${#qmail[@]} )) || { printf 'Specified name not found\n\n'; continue; }

  (( ${#qmail[@]} == 1 )) && als='alias' || als='aliases'
  printf '%s%s%s is found in %d qmail %s:\n' "$col" "$user" "$rst" ${#qmail[@]} "$als"
  printf '%s\n' "${qmail[@]}" 

  (( ${#qmail[@]} == 1 )) && als='this list' || als='these lists'
  until [[ ${confirm,,} = [yn] ]]
  do
    printf 'Delete %s%s%s from %s? (y/n) ' "$col" "$user" "$rst" "$als"
    read confirm
  done
  
  if [[ ${confirm,,} = y ]]
  then
    sed -i "/$user/d" .qmail*
    printf 'User %s%s%s deleted\n' "$col" "$user" "$rst"
  fi
  confirm=
  printf '\n'
done

```

should fit the bill, though test it first in some junk directory on dummy data. Detection and deletion with straightforward grep/sed are kind of stupid and not foolproof enough for my taste, so you shouldn't enter things like 'a' or 'john' that would match boatloads of records.

---

### Post by Damonion on 2014-08-07
Wow, thanks a lot!

I'll take this, learn from it and test it.

You seem like quite the dedicated user to this forum, very helpful, very friendly.

---

