---
title: "Help With Bash Script"
date: 2011-08-22
forum: Programming Talk
---

### Post by jlacroix on 2011-08-22
This is probably a quick question for you experts out there, but I'm not able to find the answer. 

Basically, I have a set of instructions in my bash script I want to execute only if the hostname of the machine is Athena OR Polaris. Is there an if statement that would incorporate this?

---

### Post by cgroza on 2011-08-22
You can get the host name with the command:
```

hostname

```
An if statement would look like:
```

if [ $(hostname) = "myHostname"; 
      then
      # do something
fi

```

---

### Post by Bachstelze on 2011-08-22
> **cgroza said:**
> You can get the host name with the command:
```

hostname

```
An if statement would look like:
```

if [ $(hostname) = "myHostname" ]; 
      then
      # do something
fi

```

Fixed. Seriously, test your code before pasting it...

---

### Post by jlacroix on 2011-08-22
> **Bachstelze said:**
> Fixed. Seriously, test your code before pasting it...

I will try that very soon. Thanks guys! But how do I make it still execute the statements if the $hostname is either Athena or Polaris? This script will be run on several machines but there are a few lines that only apply to the aforementioned hosts.

Thanks again!

---

### Post by cgroza on 2011-08-22
> **Bachstelze said:**
> Fixed. Seriously, test your code before pasting it...
Sorry, it was a square bracket anyway, nothing the OP can't handle.
Thanks for correcting it.

---

### Post by cgroza on 2011-08-22
I use the || operator here. I am sure there are other and possibly better  ways to do it.
```

#!/bin/bash
HNAME=$(hostname)
if [[ $HNAME = "Athena" || $HNAME = "Polaris" ]];
     then
     echo "True"
fi


```

---

### Post by sisco311 on 2011-08-22
In bash, I would try something like:
```

HOSTS='^(Athena|Polaris)$'
if [[ $(hostname) =~ $HOSTS ]]
then
    :
else
    :
fi
```

a case statement should work in other shells as well:
```

case $(hostname) in
    Athena|Polaris)
        echo 'do something'
        ;;
    *)
        echo 'do something else'
        ;;
esac
```

---

### Post by jlacroix on 2011-08-22
> **sisco311 said:**
> In bash, I would try something like:
```

HOSTS='^(Athena|Polaris)$'
if [[ $(hostname) =~ $HOSTS ]]
then
    :
else
    :
fi
```

a case statement should work in other shells as well:
```

case $(hostname) in
    Athena|Polaris)
        echo 'do something'
        ;;
    *)
        echo 'do something else'
        ;;
esac
```
Thank you everyone! The if statements wouldn't work for some reason, but the case statement posted worked fine. :)

---

### Post by sisco311 on 2011-08-22
You are welcome! Don't forget to mark this thread as solved.

---

### Post by jlacroix on 2011-08-22
> **sisco311 said:**
> You are welcome! Don't forget to mark this thread as solved.

Actually, I'm having a slight problem now that I tried it again. Here is the code in the relevant section of my script:

```

case $HNAME in
	Athena|Polaris)
	read -p "Press ENTER to set up emulators." arg
	rm -r /home/jlacroix/.zsnes
	rm -r /home/jlacroix/.mednafen
	rm -r /home/jlacroix/.mame
	scp -r -P $HOSTPORT $HOST:"$SYSPATH/$HOSTNAME/$SNESPATH/" $HOMEPATH
	scp -r -P $HOSTPORT $HOST:"$SYSPATH/$HOSTNAME/$MAMEPATH/" $HOMEPATH
	scp -r -P $HOSTPORT $HOST:"$SYSPATH/$HOSTNAME/$MEDPATH/" $HOMEPATH
	## Below checks to see if the /etc/mame directory exists, and creates it if it doesn't. ##
		folderName="mame"
		cd /etc
		if ! test -d folderName
		then
			sudo mkdir /etc/mame
		fi
	sudo scp -P $HOSTPORT $HOST:"$SYSPATH/$HOSTNAME/$MAMEPATH/mame.ini.etc" $MAMEETC
esac
```

The problem is that it tries to make the /etc/mame directory without checking whether or not it exists. It still runs just fine, but it just gives an error message.

---

### Post by sisco311 on 2011-08-22
```

...
#folderName is a variable ;)
if ! test -d "**$**folderName"
...

```

If you are `lazy' to do an extra check, you can use mkdir's -p option (no error if existing).

---

### Post by dave01945 on 2011-08-22
i think your if statement needs to look like this

```
 if [ ! -d $folderName ];
         then
```

---

### Post by jlacroix on 2011-08-22
> **sisco311 said:**
> ```

...
#folderName is a variable ;)
if ! test -d "**$**folderName"
...

```


If you are `lazy' to do an extra check, you can use mkdir's -p option (no error if existing).

D'oh! I can't believe after all this I didn't notice that. LOL Thanks!

And about the second point, that was a very clever (and much more simpler) idea.

Now this is definitely solved.

---

### Post by sisco311 on 2011-08-22
No problem. 

You can use the Thread Tools menu at the top of the page to mark this thread as [SOLVED].

---

