---
title: "Weather Script help"
date: 2010-04-28
forum: Programming Talk
---

### Post by yoshi445511 on 2010-04-28
I have a weather script that i need to pass an argument to, and then have curl fetch a URL with that argument variable in it. It doesn't give me any errors, but there is no output.
Here's the script
```
ZIPCODE=
while getopts "z" OPTION; do
	case $OPTION in
		z) 
			ZIPCODE=$OPTARG
			;;
	esac
done
curl --silent -o weather.html "http://www.wunderground.com/cgi-bin/findweather/getForecast?query="$ZIPCODE"&wuSelect=WEATHER"
grep '<span class="nobr"><span class="b">.*</span>&nbsp;°F</span>' weather.html | sed ' s@<span class="nobr"><span class="b">@@' | sed ' s@</span>&nbsp;°F</span>@@'
```

EDIT: Oh, Gosh. I seem to have mistakingly posted in the wrong section. Can an Admin Please close this?

---

### Post by yoshi445511 on 2010-04-28
I have a weather script that i need to pass an argument to, and then have curl fetch a URL with that argument variable in it. It doesn't give me any errors, but there is no output.
Here's the script
```
ZIPCODE=
while getopts "z" OPTION; do
	case $OPTION in
		z) 
			ZIPCODE=$OPTARG
			;;
	esac
done
curl --silent -o weather.html "http://www.wunderground.com/cgi-bin/findweather/getForecast?query="$ZIPCODE"&wuSelect=WEATHER"
grep '<span class="nobr"><span class="b">.*</span>&nbsp;°F</span>' weather.html | sed ' s@<span class="nobr"><span class="b">@@' | sed ' s@</span>&nbsp;°F</span>@@'
```

---

### Post by lisati on 2010-04-28
Threads merged & tidied.

Please do not start multiple threads on the same question.

---

### Post by gmargo on 2010-04-29
You need to append a colon to indicate that the -z option takes an argument.
```

while getopts "z:" OPTION; do

```

---

