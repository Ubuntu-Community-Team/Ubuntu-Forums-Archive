---
title: "While loop inside while loop."
date: 2011-02-21
forum: Programming Talk
---

### Post by bcooperizcool on 2011-02-21
Is this possible?
I have a script that generates text files, using names from inside another text file
```

ls /home/ubuntu > names.txt
while read names; do
ls /home/ubuntu/$names > $names.txt
done < names.txt

```
See?  It lists the contents of each folder into a text file with the folder name.
This is where I am stuck at how to proceed.
I need to read each text file, and its contents file, but I don't know the names of the contents file.

Any help?
it would be something like this I'm thinking
```
while read -u3 names && read -u4 contents; do
if [[ -f "/home/ubuntu/$names/$contents" && -f /OtherLocation/$names/$contents ]];
then cp "/home/ubuntu/$names/$contents" "/OtherLocation/$name/$contents";
else echo "It doesn't exist!;
fi
done u3< names.txt u4< $names.txt  
```
See?  I don't know the files name.
I could just read it all into one big file I suppose....
```

while read names; do
ls "/home/ubuntu/$names" > bigfile.txt;
done
```

and then just do this...:
```

while read -u3 names && read -u4 contents; do
if [[ -f "/home/ubuntu/$names/$contents" && -f "/OtherLocation/$names/$contents";
then cp "/home/ubuntu/$names/$contents" "/OtherLocation/$names/$contents";
else echo "It doesn't exist!";
fi
done u3< names.txt u4< bigfile.txt

```

Which one is better?
And back to my main question, how do I get the first one to work?  (a loop within a loop)

Thanks!

---

### Post by bcooperizcool on 2011-02-22
I just went with the big file one.```
while read names; do
ls "/home/ubuntu/$names" >> bigfile.txt;
done
```

Note the ">>" rather than the ">"

---

