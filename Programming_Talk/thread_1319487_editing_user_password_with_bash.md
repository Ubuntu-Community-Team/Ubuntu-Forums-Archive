---
title: "editing user password with bash"
date: 2009-11-08
forum: Programming Talk
---

### Post by QsM on 2009-11-08
Hello all, I have an assignment which states:
1. Create username from a file called "user.txt". 
2. username should be the first two characters of the first name followed by the complete last name. (name in user.txt is in this format (ln,fn)
3. create user non-interactively
4. set password to some pre-determined string.

So far I have this:
```
#function to convert uppercase characters to lowercase
toLower() { echo $1 | tr "[:upper:]" "[:lower:]"; }

#lastName = first field of user.txt.
lastName=`cut -d',' -f1 user.txt`

#Store second field (firstname) into a temp file.
cut -d',' -f2 user.txt > temp.txt

#Retrieve first two characters of the firstname, and store into variable
firstName=`cut -c1-2 temp.txt`

#create username for new user.
userName=$firstName$lastName

#convert upper->lower
userName=`toLower $userName`

#test pw
password="foo"

#Create user
adduser --disabled-password --gecos "" $userName

#this line does not work
echo "$password" | passwd $userName

#clean up
rm temp.txt

```
I have been to unable to successfully change the password of our user. I have tried:
echo "$password" | passwd $userName
and
echo "$password" | passwd --stdin $userName                              

Neither work, could someone please point me in the right direction? Thank you!

---

### Post by geirha on 2009-11-08
```
man chpasswd
```

---

