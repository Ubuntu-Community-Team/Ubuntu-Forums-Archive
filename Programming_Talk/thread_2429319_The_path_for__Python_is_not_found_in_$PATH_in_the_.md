---
title: "The path for  Python is not found in $PATH in the Arduino-IDE - on my Ubuntu"
date: 2019-10-16
forum: Programming Talk
---

### Post by dilbert_one on 2019-10-16
[COLOR=#000000][FONT=&amp]Hello, good day dear Ubuntu-experts - good day dear Community, 

[/FONT][/COLOR]

**the topic of today: **The path for Python is not found in $PATH in the Arduino-IDE - on my Ubuntu



[COLOR=#000000][FONT=&amp]I'm running Ubuntu 18.04.02 - and i like it very much. 
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]I'm trying to work with esp8266.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]
therefore: I have downloaded and installed the board for the esp8266 in the Arduino IDE; so far so good:  but when I try to compile a sketch I have this message :[/FONT][/COLOR]

```
[COLOR=#000000][FONT=&amp]
exec: "python": executable file not found in $PATH[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Error compiling for board Generic ESP8266 Module.[/FONT][/COLOR]

```[COLOR=#000000][FONT=&amp]

**btw**:... It's the same message for every esp8266 board. If I choose another board (Genuino etc.) it works without any issues.[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]I have checked the $PATH and it seems that python is included :[/FONT][/COLOR]

```
[COLOR=#000000][FONT=&amp]
echo $PATH[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][...]:/usr/bin/python[/FONT][/COLOR]
```


[COLOR=#000000][FONT=&amp]Python is installed correctly  see the corresponding data [/FONT][/COLOR]

```
[COLOR=#000000][FONT=&amp]
>python[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Python 2.7.15rc1 (default, Nov 12 2018, 14:31:15) [/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][GCC 7.3.0] on linux2[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Type "help", "copyright", "credits" or "license" for more information.[/FONT][/COLOR]

```

[COLOR=#000000][FONT=&amp]Well i look forward to hear  from you  ?[/FONT][/COLOR]

---

### Post by lutz-muellerrs on 2020-03-02
Hi,

did you find a solution? Where can I find to set the path in arduino ide?

---

### Post by Skaperen on 2020-03-04
try:
```

ls -dl /usr/bin/python*

```
python version 2 became end-of-life on 1 Jan 2020.  minimal systems perhaps no longer include python version 2 which used the command name "python".  python version 3 (the only version any supported software should be using) uses the command name "python3".

---

