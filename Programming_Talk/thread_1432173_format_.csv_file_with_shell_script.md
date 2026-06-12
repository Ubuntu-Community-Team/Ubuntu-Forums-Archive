---
title: "format .csv file with shell script"
date: 2010-03-17
forum: Programming Talk
---

### Post by choco420 on 2010-03-17
Hello, 

I wanted to a graph our daily network health report on cacti and so i came up with a shell script to extract data from a .csv which resides in the path /etc/cacti/scripts/data (its a network health report) and the shell script i wrote lies in the path /etc/cacti/scripts. 
Here is the script: 

cat data/network_health* | cut -d "|" -f 1,4 

Now this shell script diplays the data in two columns as this : 

WINDOW                            |Y_CHANGE 
|03/12 - 03/11 (%) 
00:00:00 - 08:00:00      | 
AD_REQUESTS                 |-1.22 
PAID_REVENUE                |15.01 
QUATTRO_REVENUE      |15.75 
PAGE_VIEWS                    |-4.46 
PAID_IMPRESSIONS        |-8.22 
PAID_CLICKS                   |3.46 
PAID_ECPM                     |25.32 
PAID_CTR                       |12.50 
PAID_FILL_RATE            |-7.15 
07:00:00 - 08:00:00 | 
AD_REQUESTS               |-3.25 
PAID_REVENUE              |19.68 
ABC_REVENUE               |20.33 
PAGE_VIEWS                  |-5.65 
PAID_IMPRESSIONS      |-7.99 
PAID_CLICKS                 |5.19 
PAID_ECPM                   |30.08 
PAID_CTR                     |14.81 
PAID_FILL_RATE          |-4.82 
06:00:00 - 07:00:00 | 
AD_REQUESTS             |-3.61 
PAID_REVENUE            |11.16 
ABC_REVENUE             |11.87 
PAGE_VIEWS                |-5.62 
PAID_IMPRESSIONS    |-7.45 
PAID_CLICKS               |1.47 
PAID_ECPM                  |20.12 
PAID_CTR                    |7.41 
PAID_FILL_RATE         |-3.93 

Now when i try graph this it just doesnt come up. So i am assuming i have to get the result in a format readable for cacti which should be as such; 
AD_REQUESTS: -3.61 PAID_REVENUE:11.16 ABC_REVENUE:11.87 PAGE_VIEWS: -5.62 PAID_IMPRESSIONS: -7.45 PAID_CLICKS:1.47 PAID_ECPM: 20.12 PAID_CTR: 7.41 PAID_FILL_RATE:-3.93 

Could someone please help me with the shell script for doing so? I am just starting to learn shell scripting while i am working on it. 

Any help is appreciated.

---

### Post by geirha on 2010-03-17
If I understand correctly, this should do the trick:
```
awk -F'|' '{printf "%s: %f\n", $1, $4}' data/network_health*
```

EDIT: there seems to be some odd lines in there that you probably don't want, like
```
07:00:00 - 08:00:00 |
```

Assuming all the lines you want start with a capital letter, you can extend the awk to only act on such lines.
```
awk -F'|' '/^[A-Z]/{printf "%s: %f\n", $1, $4}' data/network_health*
```

---

### Post by lloyd_b on 2010-03-17
> **geirha said:**
> If I understand correctly, this should do the trick:
```
awk -F'|' '{printf "%s: %f\n", $1, $4}' data/network_health*
```

EDIT: there seems to be some odd lines in there that you probably don't want, like
```
07:00:00 - 08:00:00 |
```

Assuming all the lines you want start with a capital letter, you can extend the awk to only act on such lines.
```
awk -F'|' '/^[A-Z]/{printf "%s: %f\n", $1, $4}' data/network_health*
```

From reading the data, I think it's a case of multiple periods, with the data associated with each period, and he wants it with one line of output per period.

Here's what I came up with:```
awk ' {if ($1 ~ /[0-9]+:[0-9]+:[0-9]+/) {printf "\nPeriod:%s-%s ", $1, $3} else {printf "%s:%s ", $1, substr($2, 2, 99)+ 0}} ' data/network_health*
```

Using the sample data provided, this produces the following:```
WINDOW:0 |03/12:0 
Period:00:00:00-08:00:00 AD_REQUESTS:-1.22 PAID_REVENUE:15.01 QUATTRO_REVENUE:15.75 PAGE_VIEWS:-4.46 PAID_IMPRESSIONS:-8.22 PAID_CLICKS:3.46 PAID_ECPM:25.32 PAID_CTR:12.5 PAID_FILL_RATE:-7.15 
Period:07:00:00-08:00:00 AD_REQUESTS:-3.25 PAID_REVENUE:19.68 ABC_REVENUE:20.33 PAGE_VIEWS:-5.65 PAID_IMPRESSIONS:-7.99 PAID_CLICKS:5.19 PAID_ECPM:30.08 PAID_CTR:14.81 PAID_FILL_RATE:-4.82 
Period:06:00:00-07:00:00 AD_REQUESTS:-3.61 PAID_REVENUE:11.16 ABC_REVENUE:11.87 PAGE_VIEWS:-5.62 PAID_IMPRESSIONS:-7.45 PAID_CLICKS:1.47 PAID_ECPM:20.12 PAID_CTR:7.41 PAID_FILL_RATE:-3.93
```Is this what's desired?

Note: I included the "Period" info because you've got overlapping periods in the data.  For instance, the first line is "00:00:00 - 08:00:00", while the second line is "07:00:00 - 08:00:00" and the third is "07:00:00 - 06:00:00".  There's also a little garbage at the beginning because of the date.  Does that need to be worked into the output data?

Lloyd B.

---

### Post by choco420 on 2010-03-17
Hello,

Thanks for the help here. I will exactly explain what i am trying to do over here. The code that you gave me outputs three time periods which need to be graphed in cacti.So ideally i would require to chart 3 graphs for three time periods but i dont think that will be possible.  And i do not require to have the garbage data on the top. so my out put should be looking like this.

 
AD_REQUESTS:-1.22 PAID_REVENUE:15.01 QUATTRO_REVENUE:15.75 PAGE_VIEWS:-4.46 PAID_IMPRESSIONS:-8.22 PAID_CLICKS:3.46 PAID_ECPM:25.32 PAID_CTR:12.5 PAID_FILL_RATE:-7.15 
 AD_REQUESTS:-3.25 PAID_REVENUE:19.68 ABC_REVENUE:20.33 PAGE_VIEWS:-5.65 PAID_IMPRESSIONS:-7.99 PAID_CLICKS:5.19 PAID_ECPM:30.08 PAID_CTR:14.81 PAID_FILL_RATE:-4.82 
 AD_REQUESTS:-3.61 PAID_REVENUE:11.16 ABC_REVENUE:11.87 PAGE_VIEWS:-5.62 PAID_IMPRESSIONS:-7.45 PAID_CLICKS:1.47 PAID_ECPM:20.12 PAID_CTR:7.41 PAID_FILL_RATE:-3.93

Note that i have kept the out for different time periods on different lines.

I really appreciate the help again.

---

### Post by lloyd_b on 2010-03-17
Okay, this command```
awk ' {if ($1 == "PAID_FILL_RATE") printf "%s:%d\n", $1, substr($2, 2, 99); else if ($1!="WINDOW" && $1~/^[^\|]/ && $1~/^[^0-9]/) printf "%s:%d ", $1, substr($2, 2, 99)} ' data/network_health*
``` produces ```
AD_REQUESTS:-1 PAID_REVENUE:15 QUATTRO_REVENUE:15 PAGE_VIEWS:-4 PAID_IMPRESSIONS:-8 PAID_CLICKS:3 PAID_ECPM:25 PAID_CTR:12 PAID_FILL_RATE:-7
AD_REQUESTS:-3 PAID_REVENUE:19 ABC_REVENUE:20 PAGE_VIEWS:-5 PAID_IMPRESSIONS:-7 PAID_CLICKS:5 PAID_ECPM:30 PAID_CTR:14 PAID_FILL_RATE:-4
AD_REQUESTS:-3 PAID_REVENUE:11 ABC_REVENUE:11 PAGE_VIEWS:-5 PAID_IMPRESSIONS:-7 PAID_CLICKS:1 PAID_ECPM:20 PAID_CTR:7 PAID_FILL_RATE:-3
```One caveat - the last line for each entry must be the "PAID_FILL_RATE", as I'm using that to determine when to stick in a newline.

Lloyd B.

---

### Post by lloyd_b on 2010-03-17
Oops - goofed on the last one (float vs int issue).  Here's the command```
awk ' {if ($1 == "PAID_FILL_RATE") printf "%s:%-3.2f\n", $1, substr($2, 2, 99); else if ($1!="WINDOW" && $1~/^[^\|]/ && $1~/^[^0-9]/) printf "%s:%-3.2f ", $1, substr($2, 2, 99)} ' data/network_health*
``` and the output ```
AD_REQUESTS:-1.22 PAID_REVENUE:15.01 QUATTRO_REVENUE:15.75 PAGE_VIEWS:-4.46 PAID_IMPRESSIONS:-8.22 PAID_CLICKS:3.46 PAID_ECPM:25.32 PAID_CTR:12.50 PAID_FILL_RATE:-7.15
AD_REQUESTS:-3.25 PAID_REVENUE:19.68 ABC_REVENUE:20.33 PAGE_VIEWS:-5.65 PAID_IMPRESSIONS:-7.99 PAID_CLICKS:5.19 PAID_ECPM:30.08 PAID_CTR:14.81 PAID_FILL_RATE:-4.82
AD_REQUESTS:-3.61 PAID_REVENUE:11.16 ABC_REVENUE:11.87 PAGE_VIEWS:-5.62 PAID_IMPRESSIONS:-7.45 PAID_CLICKS:1.47 PAID_ECPM:20.12 PAID_CTR:7.41 PAID_FILL_RATE:-3.93
```

Lloyd B.

---

### Post by geirha on 2010-03-17
You're also grabbing the wrong fields. If you see the first post, the initial code cuts out field 1 and 4, not 1 and 2.

---

### Post by lloyd_b on 2010-03-17
> **geirha said:**
> You're also grabbing the wrong fields. If you see the first post, the initial code cuts out field 1 and 4, not 1 and 2.

Have you looked at the data?  There *aren't* 4 fields there...

Okay, I get it.  I'm working from the data that he's posted, which is *after* it's been 'cut'.  But since I haven't seen the base data, that's pretty much all I can do.  He can change the field numbers to suit (or post samples of the actual data before the 'cut').

Lloyd B.

---

### Post by choco420 on 2010-03-17
Hey Llyod,

The script that you provided works great except for two glitches:

I modified the script a bit to cut the data from the fourth column instead of 2nd (which was not your fault, i should have mentioned it before)

So here is the modfication:
awk ' {if ($1 == "PAID_FILL_RATE") printf "%s:%-3.2f\n", $1, substr($4, 2, 99); else if ($1!="WINDOW" && $1~/^[^\|]/ && $1~/^[^0-9]/) printf "%s:%-3.2f ", $1, substr($4, 2, 99)} ' data/network_health*

And here is the output  i get:

:0.00 AD_REQUESTS:0.00 PAID_REVENUE:15.01 QUATTRO_REVENUE:15.75 PAGE_VIEWS:-4.46 PAID_IMPRESSIONS:-8.22 PAID_CLICKS:3.46 PAID_ECPM:25.32 PAID_CTR:12.50 PAID_FILL_RATE:-7.15
AD_REQUESTS:-3.25 PAID_REVENUE:19.68 QUATTRO_REVENUE:20.33 PAGE_VIEWS:-5.65 PAID_IMPRESSIONS:-7.99 PAID_CLICKS:5.19 PAID_ECPM:30.08 PAID_CTR:14.81 PAID_FILL_RATE:-4.82
AD_REQUESTS:-3.61 PAID_REVENUE:11.16 QUATTRO_REVENUE:11.87 PAGE_VIEWS:-5.62 PAID_IMPRESSIONS:-7.45 PAID_CLICKS:1.47 PAID_ECPM:20.12 PAID_CTR:7.41 PAID_FILL_RATE:-3.93


As you notice in the output, i get :0:00 and the AD_REQUEST in the first line has a value of 0.00. I tried to change a few things in the script but due to my limited knowledge i couldnt figure it out. Could you give me a short explanation of how this script actually works for my learning purposes?

Thanks again,

choco

---

### Post by geirha on 2010-03-17
A sample of the input would really help.

Does this give you the needed output?
```
awk -F\| '/^[0-9]/{print "";next} {printf "%s:%.2f ",$1,$4} END {print ""}' data/network_health*
```

EDIT: Oh and please use code-tags (# icon in the toolbar above the textbox) for terminal output. Makes it much easier to read.

---

### Post by lloyd_b on 2010-03-18
> **geirha said:**
> A sample of the input would really help.

Does this give you the needed output?
```
awk -F\| '/^[0-9]/{print "";next} {printf "%s:%.2f ",$1,$4} END {print ""}' data/network_health*
```

EDIT: Oh and please use code-tags (# icon in the toolbar above the textbox) for terminal output. Makes it much easier to read.

Agreed - it's very hard to debug this without seeing what the input data looks like.

Lloyd B.

---

### Post by choco420 on 2010-03-18
Hey Guys,

The script that was posted earlier doesnt work well. It gives wrong space allocations. I am again posting the output from Llyod's script earlier.

#:0.00 AD_REQUESTS:0.00 PAID_REVENUE:15.01 QUATTRO_REVENUE:15.75 PAGE_VIEWS:-4.46 PAID_IMPRESSIONS:-8.22 PAID_CLICKS:3.46 PAID_ECPM:25.32 PAID_CTR:12.50 PAID_FILL_RATE:-7.15
AD_REQUESTS:-3.25 PAID_REVENUE:19.68 QUATTRO_REVENUE:20.33 PAGE_VIEWS:-5.65 PAID_IMPRESSIONS:-7.99 PAID_CLICKS:5.19 PAID_ECPM:30.08 PAID_CTR:14.81 PAID_FILL_RATE:-4.82
AD_REQUESTS:-3.61 PAID_REVENUE:11.16 QUATTRO_REVENUE:11.87 PAGE_VIEWS:-5.62 PAID_IMPRESSIONS:-7.45 PAID_CLICKS:1.47 PAID_ECPM:20.12 PAID_CTR:7.41 PAID_FILL_RATE:-3.93

The problem is that cacti is not recognizing the data due to the 0.00 read in front of the data, and thats why the trouble.

Just for your reference, here is the input data:

WINDOW             |TODAY     |YESTERDAY |Y_CHANGE         
                   |2010-03-12|2010-03-11|03/12 - 03/11 (%)
00:00:00 - 08:00:00|          |          |                 
AD_REQUESTS        |76,712,939|77,664,044|-1.22            
PAID_REVENUE       |24257.70  |21092.30  |15.01            
ABC_REVENUE    |23007.95  |19876.68  |15.75            
PAGE_VIEWS         |1608304   |1683381   |-4.46            
PAID_IMPRESSIONS   |43567950  |47472365  |-8.22            
PAID_CLICKS        |117688    |113747    |3.46             
PAID_ECPM          |0.5568    |0.4443    |25.32            
PAID_CTR           |0.0027    |0.0024    |12.50            
PAID_FILL_RATE     |0.5792    |0.6238    |-7.15            
07:00:00 - 08:00:00|          |          |                 
AD_REQUESTS        |9,309,473 |9,621,876 |-3.25            
PAID_REVENUE       |3183.77   |2660.34   |19.68            
ABC_REVENUE    |3020.16   |2509.90   |20.33            
PAGE_VIEWS         |255484    |270772    |-5.65            
PAID_IMPRESSIONS   |4555517   |4951013   |-7.99            
PAID_CLICKS        |14085     |13390     |5.19             
PAID_ECPM          |0.6989    |0.5373    |30.08            
PAID_CTR           |0.0031    |0.0027    |14.81            
PAID_FILL_RATE     |0.4981    |0.5233    |-4.82            
06:00:00 - 07:00:00|          |          |                 
AD_REQUESTS        |7,917,841 |8,214,757 |-3.61            
PAID_REVENUE       |2487.94   |2238.26   |11.16            
ABC_REVENUE    |2345.53   |2096.60   |11.87            
PAGE_VIEWS         |183887    |194846    |-5.62            
PAID_IMPRESSIONS   |3902349   |4216501   |-7.45            
PAID_CLICKS        |11363     |11198     |1.47             
PAID_ECPM          |0.6376    |0.5308    |20.12            
PAID_CTR           |0.0029    |0.0027    |7.41             
PAID_FILL_RATE     |0.5013    |0.5218    |-3.93  

As you see the script is calling the 1st and the 4th row after i did the modification to llyod's script, except for that 0.00 in the front.

Thanks,

---

### Post by lloyd_b on 2010-03-18
Okay, here's a command:```
awk ' BEGIN {FS="|"} {gsub(/ /, "", $1); if ($1=="PAID_FILL_RATE") printf "%s:%s\n", $1, $4; else if ($1!="" && $1!="WINDOW" && $1~/^[A-Z].*/) printf "%s:%s ", $1, $4} ' data/network_health*
``` and the results of running it on your test data:```
AD_REQUESTS:-1.22 PAID_REVENUE:15.01 ABC_REVENUE:15.75 PAGE_VIEWS:-4.46 PAID_IMPRESSIONS:-8.22 PAID_CLICKS:3.46 PAID_ECPM:25.32 PAID_CTR:12.50 PAID_FILL_RATE:-7.15
AD_REQUESTS:-3.25 PAID_REVENUE:19.68 ABC_REVENUE:20.33 PAGE_VIEWS:-5.65 PAID_IMPRESSIONS:-7.99 PAID_CLICKS:5.19 PAID_ECPM:30.08 PAID_CTR:14.81 PAID_FILL_RATE:-4.82
AD_REQUESTS:-3.61 PAID_REVENUE:11.16 ABC_REVENUE:11.87 PAGE_VIEWS:-5.62 PAID_IMPRESSIONS:-7.45 PAID_CLICKS:1.47 PAID_ECPM:20.12 PAID_CTR:7.41 PAID_FILL_RATE:-3.93
```

Now, for what it all means:

The BEGIN block is executed before any lines are processed, to perform any intitialization.  In this case, I'm setting the FS variable (Field Separator).  This can also be done with the "-F" command line parameter.

Everything between the next set of {}'s is executed once for each line.

gsub(/ /, "", $1) 
This is a search/replace command, removing any spaces from the first field (without this, there'll be a trailing space, which messes up the output format.

if ($1=="PAID_FILL_RATE") - 
Execute this only if the first field is "PAID_FILL_RATE"

printf "%s:%s\n", $1, $4 - prints two strings (the %s's), putting the first field into the first, and the fourth field into the second,  The "\n" is a newline - it forces a <return>

else if ($1!="" && $1!="WINDOW" && $1~/^[A-Z].*/)
Execute this if the first "if" failed, and the following criteria are met.
    The first field is not equal to null ("").  This suppresses lines that start with "|"
        AND
    The first field is not equal to "WINDOW".  This suppresses that header line
        AND
    The first field matches the pattern above, which means the first character is A-Z.  This suppresses those period lines ("08:00:00 - 07:00:00")

printf "%s:%s ", $1, $4 - same as the first printf, but with a space afterwards, instead of a newline.

Lloyd B.

---

### Post by choco420 on 2010-03-18
THANKSSS LLYODD...your the best :)

---

