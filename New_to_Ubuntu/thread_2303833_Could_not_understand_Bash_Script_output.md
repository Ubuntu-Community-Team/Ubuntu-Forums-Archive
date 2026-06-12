---
title: "Could not understand Bash Script output"
date: 2015-11-21
forum: New to Ubuntu
---

### Post by Chanikya_Desu on 2015-11-21
Hi,

I have written a bash script which gets the weather data from OpenWeatherMap.org and process to give sunrise and sunset times onto stdout. This is a start. The following file is stored in potlightssunsetcopy.sh

```
#!/bin/bash 

TEMP=""
SUNRISE=""
SUNSET=""
OUTPUT="" 
TEMP=$(curl -s "http://api.openweathermap.org/data/2.5/weather?id=5884260&mode=xml&units=metric&appid=83dfad037778ee7c6f5bea304d62e492"|grep -o -i "sun rise=.*sun"|awk -F\" '{print $2 $4}')
SUNRISE=$(echo $TEMP|sed 's/....................$//')
SUNSET=$(echo $TEMP|sed 's/^...................//')
OUTPUT=$(echo "SUNRISE" & $SUNRISE & "SUNSET" & $SUNSET) 
echo $OUTPUT

```


But the output what I am seeing on the screen is....

```
chanikya@chanikya-minipc:~/Downloads$ sh potlightssunsetcopy.sh
: not foundnsetcopy.sh: 2: potlightssunsetcopy.sh: 
: not foundnsetcopy.sh: 10: potlightssunsetcopy.sh: 2015-11-22T22:41:37
potlightssunsetcopy.sh: 10: potlightssunsetcopy.sh: SUNSET: not found
: not foundnsetcopy.sh: 10: potlightssunsetcopy.sh: 2015-11-22T13:50:40
SUNRISE
: not foundnsetcopy.sh: 12: potlightssunsetcopy.sh: 
: not foundnsetcopy.sh: 13: potlightssunsetcopy.sh: 
: not foundnsetcopy.sh: 14: potlightssunsetcopy.sh: 

```
Can somebody help me where I went wrong?

Thanks

---

### Post by ian-weisser on 2015-11-21
You aren't using any special bash functions, you can use ordinary sh.
You don't need to declare all the empty variables.
Variables don't need to be all uppercase.

The biggest problem is on Line 10.
'&' means something different from what you seem to expect, and it's causing lots of errors.
'&' means to background the command, not to concatenate output.

Example using wget instead of curl:
```
#!/bin/sh 
url="http://api.openweathermap.org/data/2.5/weather?id=5884260&mode=xml&units=metric&appid=83dfad037778ee7c6f5bea304d62e492"
str=$(wget -O - $url | grep -o -i "sun rise=.*sun")
sr=$(echo $str | awk -F\" '{print $2}')
ss=$(echo $str | awk -F\" '{print $4}')
echo "Sunrise:" $sr ", Sunset:" $ss
```

---

### Post by nerdtron on 2015-11-22
And also note that using "sh" to run a bash script on Ubuntu is different than "bash". Try also running the script as "bash potlightssunsetcopy.sh" since it is a bash script.

---

### Post by Chanikya_Desu on 2015-11-22
> And also note that using "sh" to run a bash script on Ubuntu is  different than "bash". Try also running the script as "bash  potlightssunsetcopy.sh" since it is a bash script.
I tried this but it gives errors of line return "/r" command not found. I do not know what exactly means.
> You aren't using any special bash functions, you can use ordinary sh.
You don't need to declare all the empty variables.
Variables don't need to be all uppercase.

The biggest problem is on Line 10.
'&' means something different from what you seem to expect, and it's causing lots of errors.
'&' means to background the command, not to concatenate output.

Example using wget instead of curl:
Based on this I tried, but the response was no username/password authentication failed. I raised a ticket on openweathermap.org for their suggestion about the output. I have to wait until they come back.

Thanks to both @ian-weisser and @nerdtron for their valuable suggestions.

Thanks

---

### Post by Lars Noodén on 2015-11-22
The data is fine, and ian-weisser's variant of the script produces a date and time for sunrise and sunset.  If you want the output in the format you are trying to have, you need to escape the ampersands in some way.  Either precede them with a backslash or put them in quotes.  I expect it is the latter you are aiming for:

```

echo "SUNRISE $SUNRISE  SUNSET $SUNSET";

```

---

### Post by Chanikya_Desu on 2015-11-22
> Lars Noodén                   [INDENT]                              Re: Could not understand Bash Script output
                          The data is fine, and ian-weisser's variant of the script produces a  date and time for sunrise and sunset.  If you want the output in the  format you are trying to have, you need to escape the ampersands in some  way.  Either precede them with a backslash or put them in quotes.  I  expect it is the latter you are aiming for:

     Code:
     echo "SUNRISE $SUNRISE  SUNSET $SUNSET"; 
         [/INDENT]
    


I used the orginal script and changed the last portion on the statement as you said, that is , I need to concatenate the strings. The response is like this...

```
chanikya@chanikya-minipc:~/Downloads$ sh potlightssunsetcopy.sh
: not foundnsetcopy.sh: 2: potlightssunsetcopy.sh: 
: not foundnsetcopy.sh: 6: potlightssunsetcopy.sh: 
: not foundnsetcopy.sh: 10: potlightssunsetcopy.sh: 

chanikya@chanikya-minipc:~/Downloads$ 

```

Now there is no output. Intially I used the option -S --raw options in curl, I see that there is no data. I think the data is not transferred or there is no data.

I could not understand what  is " not foundnsetcopy.sh" means.....

Thanks for your help as well....

---

### Post by Chanikya_Desu on 2015-11-22
Hi,

If you observe the url, it has options and it may not be correct using wget, if there are options in the url. I just do not know.

Thanks

---

### Post by Chanikya_Desu on 2015-11-22
OK! Got some good news.

There is some syntax problems and I got it thorugh to some extent.

There are two spaces at the end of lines and so it is displacing "not foundnsetcopy" issues. I removed those spaces and everything went but fine. But last echo command is not displaying the concatenate strings. Does it have any fixed string width to display, as I see it is overwriting on the dispay whole valves. But I requested the individual valves the values are displayed fine but could not handle the whole valve. Right now I am OK with the variables and I do not need the echo display.

Any more help will be fine and Thanks.

---

### Post by ian-weisser on 2015-11-23
You don't need to explicity concatenate the strings on the output line.
The 'echo' command is already concatenating the strings.

---

### Post by Chanikya_Desu on 2015-11-23
But echo command is overwriting at the same spot, could not differentiate two separate values.

---

### Post by Lars Noodén on 2015-11-23
Did you try echo with the quotes?

---

