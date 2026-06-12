---
title: "bash: greater than"
date: 2010-07-29
forum: Programming Talk
---

### Post by takayuki on 2010-07-29
Hi,

trying to create a bash script that will shrink jpegs that are larger than 50kb in a directory on my server.  

Here's what I've got so far, very early in the process...   

the if line errors out with a "command not found".  oops. 

anyone have any thoughts here for the noob bash scripter?

thanks :)

[PHP]for FILENAME in *.jpg  #traverse filenames...

	do
	FILESIZE=$(stat -c%s "$FILENAME")

		if ["$FILESIZE" > 50000]
		then
		echo "$FILENAME is too large = $FILESIZE bytes."
		fi

	done

exit 0[/PHP]

---

### Post by seungwon on 2010-07-29
I think you should change > with -gt.

---

### Post by ghostdog74 on 2010-07-29
```

if [[ $FILESIZE > 50000 ]] ;then
  ...
fi

```

---

### Post by seungwon on 2010-07-29
How about this?

```

if [ "$FILESIZE" -gt 50000 ]
then
        echo "$FILENAME is too large = $FILESIZE bytes."
fi

```

---

### Post by takayuki on 2010-07-29
thanks!

if [[ $FILESIZE > 50000 ]] ;then

did the trick.

syntax!

---

