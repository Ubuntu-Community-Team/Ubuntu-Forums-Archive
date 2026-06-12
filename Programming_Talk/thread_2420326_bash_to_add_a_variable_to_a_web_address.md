---
title: "bash to add a variable to a web address"
date: 2019-06-03
forum: Programming Talk
---

### Post by cazz on 2019-06-03
This have to be simple but I guess I'm very tired right now so I can't see the error

I have in a bash file

$dd = date +%Y-%m-%d
$fd = date +%Y-%m-%d --date='-7 day'

dd is to show todays date 
fd is to show a week ago date.

that work fine but when I trying to add it to a wget address

```
sudo wget "https://mysite.com/show?timeUnit=DAY&endDate=${dd}&startDate=${fd}&api_key=XXXXXXXXXXXXX" --output-document=file.xm
```

then dd and fd goes emty and I get.
```
sudo wget "https://mysite.com/show?timeUnit=DAY&endDate=&startDate=&api_key=XXXXXXXXXXXXX" --output-document=file.xm
```

---

### Post by spjackson on 2019-06-03
> **cazz said:**
> 
$dd = date +%Y-%m-%d
$fd = date +%Y-%m-%d --date='-7 day'

dd is to show todays date 
fd is to show a week ago date.

that work fine but when I trying to add it to a wget address

That's puzzling because it is absolutely NOT fine bash syntax. You probably mean something like this:
```

dd=$(date +%Y-%m-%d)
fd=$(date +%Y-%m-%d --date='-7 day')

```

---

### Post by kpatz on 2019-06-03
Is there a reason you're using sudo on your wget?  Is it to write the output to a folder that isn't writable by your regular user?

I would do the wget without sudo.  Not only is it more secure, but it will also make your newly created variables available to the command as they're running in the same shell--they aren't passed through sudo by default to the shell running the wget.  Wget into a temp file, then use sudo to move/copy it to the desired location as needed.

But if you **have **to wget with sudo, pass your variables on the sudo line:

```
dd="$(date +%Y-%m-%d)"
fd="$(date +%Y-%m-%d --date='-7 day')"
sudo dd="$dd" fd="$fd" wget "https://mysite.com/show?timeUnit=DAY&endDate=${dd}&startDate=${fd}&api_key=XXXXXXXXXXXXX" --output-document=file.xm
```

---

### Post by cazz on 2019-06-03
Ahh it was that simple (I have now sleep a little so I'm fine now :) )

Yes right now I have sudo on my webserver (the xml file is going to be on a website) but when I move it to a friend server I do not going to use sudo at all.

---

