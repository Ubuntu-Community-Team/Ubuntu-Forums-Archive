---
title: "Bash - password cracking"
date: 2019-09-27
forum: New to Ubuntu
---

### Post by 0N3 on 2019-09-27
Sorry if this is in the wrong place. I am trying to legally crack passwords as part of an assignment using three files....... 1) A file containing salted hashed passwords filename = ds_passwd  2) A file with dictionary words where one of the hashed passwords matches filename = dictionary  3) bash file to crack the passwords.

Here is my bash file

```
#!/bin/bashinput="ds_passwd"
input2="dictionary"
while IFS= read -r passwordline
do
  echo "$passwordline"
  salt=${passwordline:0:2}
  echo $salt
  while IFS= read -r dictword
  do
    output=$(openssl passwd -crypt -salt $salt $dictword 2> /dev/null)
    if [ "$output" = "$passwordline" ] ; then
      echo "Password found!"
      echo $dictword
      exit
    fi
  done < "$input2"
done < "$input"
```

When run this prints out the first hashed password in my dictionary file and on a new line in a terminal the first two letters of this hashed password. 

I'm not sure why it's not running and telling me password found.

Any help guidance appreciated

---

### Post by Irihapeti on 2019-09-27
Sorry, we don't allow discussion of cracking, legal or illegal, on these forums. It's too easy for the wrong kind of people to read the discussions and make nefarious use of the information.

***Thread closed.***

---

