---
title: "bash scripting question - reading and formatting data"
date: 2009-04-08
forum: Programming Talk
---

### Post by japhyr on 2009-04-08
Hello everyone,

I have been wanting to learn bash scripting for a while, so I decided to learn by writing a script that will help a friend with a [research project]("http://www.sitkanature.org/wordpress/2009/03/16/starrigavan-temperatures/") he is involved in.  The project is to compare temperature data from specific places around our town to the temperatures that are recorded at the local airport.  We are in a small coastal mountain town, so the airport temperature is the only one that is ever reported.  We would like to know how much temperatures around town vary from this reported temperature.

The script should accept a start date and end date.  It should then download the weather data from weather underground for all dates between these two dates, and write them to one text file.

My script so far collects the right data, but I am getting lost in how to use regular expressions in bash to pick out the right lines and write the data neatly to a text file.  I get lost in all the reading about sed, awk, pipes, formatting, etc.  I have used regexp's before in some other languages, so they are not brand new to me.  Can someone clarify:
[LIST]
[*]How should I use regexp's to pick out the right lines?
[*]How can I rewrite the lines to a text file, with the date added at the beginning of each line?
[*]How can I format the output so it is comma-separated but also tabbed so it is visually simple?
[/LIST]

I know I will need to add some logic dealing with days of the month, and some logic to accept input rather than hard-coding the start and end dates.  That I can take care of later.

There is no rush on this project.  Right now it is mostly for my own learning, but the end product will be useful to my friend who is doing the project.  Thank you very much for any feedback.

My script looks like this:
```
#!/bin/sh

# Script for downloading weather history

# Set first day to retrieve data
day="1"
month="4"
year="2009"

# Set last day to retrieve data
last_day="3"

# Set start and end date, build filename, and create file
start_date=$year/$month/$day
end_date=$year/$month/$last_day
wxhx_filename="wxhx_$month-$day-${year}_$month-$last_day-$year.txt"

echo "Data will be stored in file: $wxhx_filename"
> $wxhx_filename


# Create temp file for day data
> wx_day_data.txt

# Begin retrieval loop
while [ $day -lt $(($last_day+1)) ]
do
   # Build date
   date=$year/$month/$day

   # Set url for weatherunderground
   url="http://www.wunderground.com/history/airport/PASI/$date/DailyHistory.html?req_city=Sitka&req_state=AK&req_statename=Alaska&format=1"

   # Get the data from the url
   wget $url -o wx_log.txt -O wx_day_data.txt


   # Print date in data file
   echo "$month/$day/$year" >> $wxhx_filename


   while read inputline
   do
      echo $inputline
      grep ^.*[,],*[,] $inputline | awk 'BEGIN { FS="," } { print " " $1 "\t" $2 }' >> $wxhx_filename
      
   done < wx_day_data.txt

   echo "Processed data for $date"
   day=$(($day+1))


done
```

Each day's data looks like this:
```

TimeAKDT,TemperatureF,Dew PointF,Humidity,Sea Level PressureIn,VisibilityMPH,Wind Direction,Wind SpeedMPH,Gust SpeedMPH,PrecipitationIn,Events,Conditions<br />
12:53 AM,30.0,25.0,82,30.15,10.0,East,5.8,-,N/A,,Clear<br />
1:53 AM,28.9,25.0,85,30.15,10.0,ESE,3.5,-,N/A,,Clear<br />
2:53 AM,28.0,25.0,88,30.16,10.0,East,3.5,-,N/A,,Clear<br />
3:53 AM,28.9,24.1,82,30.15,10.0,East,5.8,-,N/A,,Clear<br />
4:53 AM,28.9,24.1,82,30.14,10.0,SE,3.5,-,N/A,,Clear<br />
5:53 AM,28.9,23.0,78,30.13,10.0,East,5.8,-,N/A,,Clear<br />
6:53 AM,28.9,21.9,75,30.11,10.0,East,3.5,-,N/A,,Clear<br />
7:53 AM,30.9,21.9,69,30.09,10.0,ESE,4.6,-,N/A,,Clear<br />
8:53 AM,34.0,19.9,56,30.08,10.0,East,6.9,-,N/A,,Clear<br />
9:53 AM,36.0,19.9,52,30.06,10.0,ESE,11.5,-,N/A,,Partly Cloudy<br />
10:53 AM,37.0,21.0,52,30.04,10.0,ESE,10.4,-,N/A,,Clear<br />
11:53 AM,37.9,21.0,51,30.02,10.0,East,9.2,-,N/A,,Mostly Cloudy<br />
12:53 PM,39.0,21.0,49,30.00,10.0,East,10.4,-,N/A,,Overcast<br />
1:53 PM,39.0,21.0,49,29.98,10.0,ESE,12.7,-,N/A,,Overcast<br />
2:53 PM,39.9,21.0,47,29.97,10.0,East,13.8,-,N/A,,Mostly Cloudy<br />
3:53 PM,39.0,21.0,49,29.94,10.0,ESE,15.0,20.7,N/A,,Scattered Clouds<br />
4:53 PM,39.0,21.9,50,29.88,10.0,ESE,19.6,28.8,N/A,,Scattered Clouds<br />
5:53 PM,39.0,23.0,53,29.86,10.0,ESE,19.6,27.6,N/A,,Overcast<br />
6:53 PM,39.0,24.1,55,29.85,10.0,ESE,11.5,23.0,N/A,,Overcast<br />
7:53 PM,37.9,25.0,60,29.84,10.0,ESE,18.4,25.3,N/A,,Overcast<br />
8:53 PM,37.0,27.0,67,29.82,10.0,ESE,17.3,-,N/A,,Overcast<br />
9:53 PM,37.9,27.0,65,29.80,10.0,SE,20.7,26.5,N/A,,Overcast<br />
10:53 PM,37.0,28.0,70,29.79,10.0,ESE,20.7,28.8,N/A,,Overcast<br />
11:01 PM,37.4,28.4,70,29.79,10.0,ESE,17.3,28.8,N/A,,Overcast<br />
11:22 PM,37.4,28.4,70,29.78,10.0,ESE,16.1,28.8,N/A,,Overcast<br />
11:53 PM,37.0,28.0,70,29.76,10.0,ESE,17.3,27.6,N/A,,Overcast<br />
<!-- 0.151:0 -->
```

The current output looks like this:
```
4/1/2009
 4:53 AM	34.0
 5:53 AM	34.0
 6:53 AM	34.0
 7:53 AM	34.0
 8:53 AM	37.0
 9:53 AM	37.0
 10:53 AM	39.0
 11:53 AM	39.9
 12:53 PM	41.0
 1:53 PM	43.0
 2:53 PM	42.1
 3:53 PM	41.0
 4:53 PM	39.9
 5:53 PM	39.0
 6:53 PM	39.0
 7:53 PM	37.0
 8:53 PM	37.0
 9:53 PM	36.0
 10:53 PM	36.0
4/2/2009
 12:24 AM	33.8
 3:00 AM	33.8
 3:53 AM	34.0
 5:53 AM	33.1
 6:53 AM	34.0...
```

---

### Post by ghostdog74 on 2009-04-08
if you want to do string processing, just use awk. the rest like grep, and the while loop to read the input file are redundant
```

awk -F"," '{print $1,$2}' inputfile

```

> 
    * How should I use regexp's to pick out the right lines?
    * How can I rewrite the lines to a text file, with the date added at the beginning of each line?
    * How can I format the output so it is comma-separated but also tabbed so it is visually simple?


depending on what you are getting, you may not need to use regular expressions, especially since the weather data you get is a csv. its better to use fields and field separators. To rewrite to new text file, use >>. to format the output, there is printf.

---

### Post by japhyr on 2009-04-08
That helps.  I did not know I could use printf within the awk statement, so I will add that shortly.  I got rid of the while loop for reading line-by-line, so the relevant section of code now looks like this:

```
# Get the data from the url
   wget $url -o wx_log.txt -O wx_day_data.txt

   grep ^.*[,],*[,] wx_day_data.txt |awk -F"," -v date="$date_mdy" '{print date,$1,$2}' >> $wxhx_filename
      
   echo "Processed data for $date_mdy"
```

Output now looks like this, which is exactly what I'm after:
```
4/1/2009 8:53 PM 37.0
4/1/2009 9:53 PM 36.0
4/1/2009 10:53 PM 36.0
4/2/2009 12:24 AM 33.8
4/2/2009 3:00 AM 33.8
4/2/2009 3:53 AM 34.0
4/2/2009 5:53 AM 33.1
```

I have kept the grep and regex in there, because without it awk includes elements of every line.  I do not want the first and last lines included, because they always consist of a full set of column headers and a closing tag.  Those do not need to be mixed in with each day's data.

Is there a better way to ignore those lines?

---

### Post by ibuclaw on 2009-04-08
Awk can do it all by itself:
```
awk -F"," -v date="$date_mdy" '$0 ~ /^.*[,],*[,]/ {print date,$1,$2}' wx_day_data.txt >> $wxhx_filename
```
Just shift the grep regexp into the awk single quotes, and encapsulate them in /forward slashes/

Regards
Iain

---

### Post by ghostdog74 on 2009-04-08
> **japhyr said:**
> 

I have kept the grep and regex in there, because without it awk includes elements of every line.  I do not want the first and last lines included, because they always consist of a full set of column headers and a closing tag.  Those do not need to be mixed in with each day's data.

Is there a better way to ignore those lines?

no need for grep. if you want to exclude header, use NR>1
```

awk 'NR>1{ print $1,$2 }' file

```

---

### Post by japhyr on 2009-04-08
Thanks, that is some of the cleanliness I was looking for.  I know there are other issues to address, but I should be able to take care of most of those.

---

