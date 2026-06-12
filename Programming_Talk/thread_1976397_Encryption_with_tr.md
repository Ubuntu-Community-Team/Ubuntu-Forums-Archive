---
title: "Encryption with tr"
date: 2012-05-08
forum: Programming Talk
---

### Post by bcooperizcool on 2012-05-08
Hello, I am trying to make a simple encryption tool, using tr, that takes a password in, and then, using that password, it gets the next letter, and then uses tr, in the code, to make any matching letter become the next letter in the password.

```
#!/bin/bash


#for the iphone, its a utility that gives a popup. Just need to know it will give an input into the shell.
password=`sbalert -m "Password" -d "ok" -p | sed 's/\(.\)/\1\n/g'`

#gives a not-so-random bunch of text/numbers.  I don't know if they are all a set size or not.  But lets go with not for now.
original=`sbdevice -u`


#for some reason, it didn't do it in the first place, so here we go.
list_password()
{
for i in $password; do
echo $i
done 
}
echo "Before:"
echo $original

#putting it into a loop
list_password | while read line
do

#getting the next charachter.
next=`list_password | awk "/$line/ { getline ; print }"`

#changing it, but it doesn't seem to be working :/
modded=`echo $original | tr "$line" "$next"`
original=$modded
export original

done

#annnnddd.... it didn't work.
echo "After:"
echo $original
```

Sorry if this doesn't make sense...   and please note, this will be running on an iPhone, not a computer ;) (but it is still the basic shell.)

If you have any ideas, or have any pointers, or know why it's not working, I welcome it all.  I'm kind of new to doing this sort of stuff, so go easy on me ;)

Thanks :)

---

