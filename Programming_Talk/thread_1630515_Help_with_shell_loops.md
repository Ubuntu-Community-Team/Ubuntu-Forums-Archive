---
title: "Help with shell loops"
date: 2010-11-25
forum: Programming Talk
---

### Post by msjones on 2010-11-25
Hi

I have written an automated twitter script for work, posting business updates etc submitting information from a database. Its all working fine. Providing the information is 140 characters or below.

```

TWEET=`databasefile`
COUNT=`echo $TWEET | wc -m`

if [ $COUNT -gt 140 ]
  then
    echo "Tweet is $COUNT characters long"
    else
    `twidge update "$TWEET"`
    echo "Tweet posted"
fi

```

As you can see, if COUNT is greater than 140 it reports error. If less than posts TWEET using twidge cli app.

I want it to loop so if COUNT is greater than 140, run the TWEET variable, and the check to see if less than or equal to 140. So i tried this:

```

until [ $COUNT -gt 140 ]
 do
  `twidge update "$TWEET"`
  echo "Tweet posted"
   break
done

```

Which does pretty much the same thing.

Go easy, I have no idea why I thought the second would work.... Blonde moment.

---

### Post by msjones on 2010-11-28
bump.

Still not go this one figured out. Any help will be greatly appreciated.

---

### Post by Arndt on 2010-11-28
> **msjones said:**
> Hi

I have written an automated twitter script for work, posting business updates etc submitting information from a database. Its all working fine. Providing the information is 140 characters or below.

```

TWEET=`databasefile`
COUNT=`echo $TWEET | wc -m`

if [ $COUNT -gt 140 ]
  then
    echo "Tweet is $COUNT characters long"
    else
    `twidge update "$TWEET"`
    echo "Tweet posted"
fi

```

As you can see, if COUNT is greater than 140 it reports error. If less than posts TWEET using twidge cli app.

I want it to loop so if COUNT is greater than 140, run the TWEET variable, and the check to see if less than or equal to 140. So i tried this:

```

until [ $COUNT -gt 140 ]
 do
  `twidge update "$TWEET"`
  echo "Tweet posted"
   break
done

```

Which does pretty much the same thing.

Go easy, I have no idea why I thought the second would work.... Blonde moment.

Shouldn't something change COUNT inside the loop?

Besides, you don't need ` ` quotes if you don't use the result of the command.

---

### Post by debsankha on 2010-11-28
I'm not sure what you mean by
> loop so if COUNT is greater than 140, run the TWEET variable.

But in case all you want to do is tweet the first 140 characters, this will do the job:
```

TWEET=`echo $TWEET | head -c 140`

```

---

### Post by SecretCode on 2010-11-28
Does the first version work?

What are you trying to do in the loop? Read the database repeatedly, check the length and tweet if < 140 ch? You're not doing those things in the loop. So I'm confused.

---

### Post by msjones on 2010-11-30
The first script is working fine. But if TWEET is greater than 140 the script just exits.

What I want it to do is re-run the TWEET variable again until the COUNT variable is less than or equal to 140 characters, then send the TWEET variable to the twidge application.

---

### Post by SecretCode on 2010-11-30
How will the TWEET variable change? Do you need to truncate it in the script - or do you just want to wait until `databasefile` results in a short enough message?

Try something like this (untested!)
```

while true; do
  TWEET=`databasefile`
  COUNT=`echo $TWEET | wc -m`
  if [ $COUNT -gt 140 ]; then
    echo "Not tweeting, message is $COUNT characters long"
  else
    `twidge update "$TWEET"`
    echo "Tweet posted"
  fi
done

```

_while true_ creates an infinite loop that's terminated only when you terminate the program (control-C)

---

### Post by epicoder on 2010-11-30
I am going to assume here that you want to loop until the TWEET variable is 140 characters or less, then tweet and exit.
In Bash:
```
COUNT=150 # To make the loop start
until [ $COUNT -le 140 ] # -le stands for less than or equal to
do
  TWEET=$(databasefile)
  COUNT=$(echo "$TWEET" | wc -m)
done
twidge update $TWEET
EXIT=$?
echo "Tweet posted"
exit $EXIT
```

---

