---
title: "Alternative to osascript for Gnome ?"
date: 2012-12-20
forum: New to Ubuntu
---

### Post by honeybear on 2012-12-20
Hi,

I look for an alternative to osascript for Gnome ? would you know any? 


```
skype () {
  number=`echo $1|sed 's/[\(\)\+ \-]//g'|sed 's/^1//'|sed 's/^/+1/'`
  osascript -e "tell application \"Skype\" to send command \"CALL $number\" script name \"CLIDIALER\""
}
```

Thanks

---

