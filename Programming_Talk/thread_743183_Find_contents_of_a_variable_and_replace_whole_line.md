---
title: "Find contents of a variable and replace whole line"
date: 2008-04-02
forum: Programming Talk
---

### Post by primal100 on 2008-04-02
I have a specific problem on a project I am working on. Any help would be greatly appreciated as this has frustrated me for a while.

Overview of project: I'm working on a file which contains timetable information for a class. Included in this timetable, among a lot of other information, are a series of dates, contained on certain lines.
Each entry is like this:

3962

Mon

14:00

15:00

KE - 3-003

{28-01-2008, 04-02-2008, 11-02-2008, 18-02-2008, 25-02-2008, 03-03-2008, 10-03-2008, 31-03-2008, 07-04-2008, 14-04-2008, 21-04-2008, 28-04-2008, 05-05-2008}

ITCD1109

Information Tech. & Communications Development 1.1

Lecture

Timetable Event

I can't use days of the week to identify what class is on today because the timetable changes slightly every week. So I must use the exact date.

My method is to declare a variable and store it as today's date. Then later in the file I must find any line (series of dates for that entry) containing today's date and replace the whole line with the word TRUE. All other lines containing a series of dates must go to FALSE. I am then planning to run a cron job so that the timetable updates itself every day assigning true to any subjects which are on today, and false to all others 

These are the lines of the file that are important:

#1 declare today's date as a variable in correct format
today=$(date +"%d-%m-%Y")

#2 find all lines containing data stored in "today" and replace whole line with the word true
sed 's/^.*$today.*$/True/' partk > partl

#3 find all other lines with dates and replace with word false
sed 's/^.*[0-3][0-9]-[0-1][0-9]-[0-9][0-9][0-9][0-9].*$/False/' partl > partm

The data is then entered into MySQL but unfortunately the relevant column has false on each entry and no true. Therefore #3 worked but #2 or #1 failed. Any ideas?

This is the full file:

 wget --output-document=temp.html --save-cookies=cookie.txt --keep-session-cookies --post-data "reqtype=login&type=null&appname=unknown&appversion=unknown&username=Student%20Engineering&userpassword=engineering" [http://webtimetables.dit.ie/TTSuiteRBLIVE/PortalServ](http://webtimetables.dit.ie/TTSuiteRBLIVE/PortalServ)


wget --output-document=DT0092.html --cookies=on --load-cookies=cookie.txt --keep-session-cookies --save-cookies=cookie.txt "http://webtimetables.dit.ie/TTSuiteRBLIVE/PortalServ?reqtype=timetable&action=getgrid&sType=class&sKey=200708%7CDT009%7CDT009/2%7C2&sTitle=BEngTech%20in%20Electrical%20%26%20Control%20Systems&sYear=2&sWeeks=&namevalue=BEngTech%20in%20Electrical%20%26%20Control%20Systems&instCode=-2&instName="

***today=$(date +"%d-%m-%Y")***
sed '1,155d' DT0092.html > parta
sed -n -e :a -e '1,13!{P;N;D;};N;ba' parta > partb
sed 's/<td class="gridData">//g' partb > partc
sed 's/<\/td>//g' partc > partd
grep -v '^<' partd > parte
grep -v '<tr class="gridHeader">' parte > partf
grep -v 'Mon' partf > partg 
grep -v 'Tue' partg > parth
grep -v 'Wed' parth > parti
grep -v 'Thu' parti > partj
grep -v 'Fri' partj > partk
[B][I]sed 's/^.*$today.*$/True/' partk > partl
sed 's/^.*[0-3][0-9]-[0-1][0-9]-[0-9][0-9][0-9][0-9].*$/False/' partl > partm[/I][/B]
sed 's/^.*[0-9][0-9][0-9][0-9].*$//g' partm > partn
sed 's/Lab //g' partn > parto
sed 's/DT009\/2//g' parto > partp
grep -v '^Timetable' partp > partq
sed '/^$/d' partq > partr
sed 'n;n;n;n;n;G;' partr > parts
	mysql --user=mysql --password=kashmir \
	-e "Use BTIDs;" \
	-e "DROP Table IF EXISTS DT0092;" \
	-e "CREATE TABLE DT0092 (StartTime time, FinishTime time, Room varchar(10), ValidToday varchar(5), ModuleName varchar(29), ActivityType varchar(10));" \
	-e "LOAD DATA LOCAL INFILE 'parts' INTO TABLE DT0092  FIELDS TERMINATED BY '\n' LINES TERMINATED BY '\n\n';"

---

### Post by WW on 2008-04-02
There is a problem in #2, where you used single quotes.  The following is from  the QUOTING section of the bash man page:
> 
       Enclosing  characters  in  single quotes preserves the literal value of
       each character within the quotes.  A single quote may not occur between
       single quotes, even when preceded by a backslash.

       Enclosing  characters  in  double quotes preserves the literal value of
       all characters within the quotes, with the exception of $,  `,  and  \.
       The  characters  $  and  `  retain  their special meaning within double
       quotes.  The backslash retains its special meaning only  when  followed
       by one of the following characters: $, `, ", \, or <newline>.  A double
       quote may be quoted within double quotes by preceding it with  a  back-
       slash.

So change
```

sed 's/^.*$today.*$/True/'  partk > partl

```
to
```

sed "s/^.*$today.*\$/True/"  partk > partl

```

---

