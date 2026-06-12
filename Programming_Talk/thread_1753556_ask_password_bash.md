---
title: "ask password bash"
date: 2011-05-09
forum: Programming Talk
---

### Post by chukchuck on 2011-05-09
In your opinion is it safe to ask password in this way:

```
zenity --entry --title="Password root" --text="Scrivi la password:" --entry-text "" --hide-text
```

or if it isn't safe what is the best way?

---

### Post by ssam on 2011-05-09
you could just call gksu from your script

---

### Post by hakermania on 2011-05-09
```
gksudo --message "Hello" program_name
```

---

### Post by chukchuck on 2011-05-10
thanks a lot :)

and...if i want to do only from terminal?
For example if i want to crypt a lot of files i'll do a for cycle and if i don't want to write every time the pwd i'll have to set the pwd in this way:

```

echo -n "Insert pwd: "
read p
list=`zenity --file-selection --multiple --title="Choose files"`
for file in $elenco; do echo $p | gpg --encrypt --passphrase-fd 0 $file
```

but it doesn't work...

---

### Post by ssam on 2011-05-10
so it is not actually the root/admin password that you want?

---

### Post by chukchuck on 2011-05-10
Yes, the first question i wanted to know that!
However i have solved, the code i've pasted before is wrong xD 
The correct code is:

```

stty -echo
echo -n "Insert pwd: "
read p
stty echo
list=`zenity --file-selection --multiple --title="Choose files"`
for f in $list; do echo $p | gpg -c --passphrase-fd 0 $f
```

---

