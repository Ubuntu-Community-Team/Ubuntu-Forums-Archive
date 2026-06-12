---
title: "saving bash arguments as their flags?"
date: 2010-11-23
forum: Programming Talk
---

### Post by M!K3_$ on 2010-11-23
Hello,
As the subject says, I want to save arguments as their respective flags.

For example:
If i type in 
```
./program.sh -i inputfile -o outputfile
```
How do I get "i = inputfile" and "o = outputfile"

The only thing I have been able to do is put the argument variables into an array using their $OPTIND
```

while getopts "i:o:" flag 
do
a[$OPTIND]=$OPTARG
done

```

---

### Post by Arndt on 2010-11-23
> **M!K3_$ said:**
> Hello,
As the subject says, I want to save arguments as their respective flags.

For example:
If i type in 
```
./program.sh -i inputfile -o outputfile
```
How do I get "i = inputfile" and "o = outputfile"

The only thing I have been able to do is put the argument variables into an array using their $OPTIND
```

while getopts "i:o:" flag 
do
a[$OPTIND]=$OPTARG
done

```

It seems like a dangerous thing to do - the user could get any variable set in your script just by using it as a flag, and it would crash mysteriously.

But maybe the builtin command "eval" will help.

---

### Post by M!K3_$ on 2010-11-23
This is just a script I'm writing for personal use, so I'm not too concerned about validating inputs at this time. But I would like to learn in the future. Thanks for the tip.

For now I am just looking for a basic way to assign variables to their respective flags.

---

### Post by mobilediesel on 2010-11-23
> **M!K3_$ said:**
> Hello,
As the subject says, I want to save arguments as their respective flags.

For example:
If i type in 
```
./program.sh -i inputfile -o outputfile
```
How do I get "i = inputfile" and "o = outputfile"

The only thing I have been able to do is put the argument variables into an array using their $OPTIND
```

while getopts "i:o:" flag 
do
a[$OPTIND]=$OPTARG
done

```

Something like this:
```
while getopts 'i:o:a:' OPTION; do
case "$OPTION" in
i) i="$OPTARG" ;;
o) o="$OPTARG" ;;
a) a="$OPTARG" ;;
*) echo Unknown option $OPTION; exit 1;;
esac
done
```

---

