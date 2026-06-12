---
title: "Using cURL to get data:need some help please"
date: 2010-03-30
forum: Programming Talk
---

### Post by wannabegeek on 2010-03-30
Hi folks,

I'm learning how to shell script and have a project for my research with which to practice.
I need to grab15 years of sea level data from the oldest water level meter on the West Coast, at
Crissy Field in San Francisco. The data would best be gotten from the database itself, but access is limited, it's a NOAA project....

Anyways, there's a website which allows one to fill in a form and get up to 30 days data at a time, which is good. I tried using cURL and got the html code, but don't see the rest of the data. I see it in the page source.

If you're interested in helping I really could use it, I would like to impress the people at my temporary job... :)

here's the address I'm messing with:

[http://tidesandcurrents.noaa.gov/data_menu.shtml?stn=9414290%20San%20Francisco,%20CA&type=Historic%20Tide%20Data]("http://tidesandcurrents.noaa.gov/data_menu.shtml?stn=9414290%20San%20Francisco,%20CA&type=Historic%20Tide%20Data")

I enter in a months time span, meters and GMT...then view data....

wbg

---

### Post by heikaman on 2010-03-31
[http://curl.haxx.se/docs/httpscripting.html]("http://curl.haxx.se/docs/httpscripting.html")

Also google sed and awk

---

### Post by wannabegeek on 2010-03-31
thanks for reply, this[ http://curl.haxx.se/docs/httpscripting.html is how]("http://curl.haxx.se/docs/httpscripting.html")
is how I got started...my problem is that I am not getting the complete source doe sent to my terminal....
the two line up, then there is a message that I did not enter a variable correctly, which is BS because I 
copied and pasted the entire link in the curl call.

> If you issue the command line
 
        curl [http://curl.haxx.se](http://curl.haxx.se)
 
 you get a web page returned in your terminal window. The entire HTML document
 that that URL holds.
 so that is not happening....I am wondering if the website is trying to disable people from using curl on it...

>  <P CLASS="error_message">Sorry, your request could not be completed due to the following: &lsquo;Station ID was not a valid.&rsquo;</P>
         <P CLASS="error_details">
         Details:<BR>
         Time = 03/31/2010 08:30:37<BR>
         Program = /var/www/vhosts/tidesandcurrents.noaa.gov/scripts/data_menu.pl<BR>
         Line = <BR>
         Program Error = Station ID was not a valid.<BR>
         OS Error = <BR></P>


I find it strange that the station ID is incorrect, since that state is chosen in the previous page and sent along  to the page I am trying to get.


wbg

---

### Post by falconindy on 2010-03-31
You probably need to wrap the URL you pass to curl in single quotes to avoid letting the shell get at it.

```
$ curl 'http://tidesandcurrents.noaa.gov/data_menu.shtml?bdate=20100101&edate=20100130&wl_sensor_hist=W1&relative=&datum=0&unit=1&shift=g&stn=9414290+San+Francisco,+CA&type=Historic+Tide+Data&format=View+Data' -o data.html
```
This worked just fine.

---

### Post by wannabegeek on 2010-03-31
Yeah !!

that's it ....thanks Falconindy
Lesson learned: pay attention to single quotes when using a program in terminal.....
need to look up the difference btw   ' '   and  " " 

cheers
wbg

---

### Post by geirha on 2010-03-31
> **wannabegeek said:**
> 
need to look up the difference btw   ' '   and  " " 

These explain it fairly well:
[http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)
[http://bash-hackers.org/wiki/doku.php/syntax/words](http://bash-hackers.org/wiki/doku.php/syntax/words)

---

### Post by wannabegeek on 2010-04-01
after spending a few hours writing a script for curl, I get the error:
curl: (3) [globbing] nested braces not supported at pos 62

  DO I  need to use another method of changing how curl calls up the web page data, 
or is this a syntax issue ?

thanks !
```
# script to get data from tides and currents web page
# need to loop thru YYYYDDMM
# $ in front of var. to call it
# Y  is begin and end  year
# M  is begin month
# ED  is end day array
  
readonly BD=01  #is a constant, begin day
ED=(31 28 31 30 31 30 31 31 30 31 30 31)
M=(01 02 03 04 05 06 07 08 09 10 11 12)
Y=1994  

for y in {0..14}  # years loop
  do  
   for m in {0..11}  # month loop
     do
     curl http://tidesandcurrents.noaa.gov/data_menu.shtml?bdate=$Y${M[m]}$BD'&edate='$Y${M[m]}${ED[m]}'&wl_sensor_hist=W1&relative=&datum=6&unit=0&shift=g&stn=9414290+San+Francisco%2C+CA&type=Historic+Tide+Data&format=View+Data'   
# need to pass the output to SED and write this that output  a file named with the date
# should probably pause      
  done
Y=$((Y+1))
done  
```

---

### Post by wannabegeek on 2010-04-01
this is working well...

just need to pipe output to file....

thanks to those who helped

wbg

---

