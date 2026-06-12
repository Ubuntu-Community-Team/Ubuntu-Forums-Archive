---
title: "wget/lftp script problem"
date: 2008-10-02
forum: Programming Talk
---

### Post by Omega2Four on 2008-10-02
Hey all,
Im trying to write a shell script that will grab data from a http directory and download it to my local machine. My first problem is that I dont know which of the above commands will help me the most. I need to download the files from this archive :  [HTML]http://metfs1.agron.iastate.edu/data/gempak/images/sat/GOES-12/4km/IR/[/HTML] it is meteorological data so the file names are relatively uniform..Ok HERE is my real problem, there are 600 or so files there and when I use lftp to download the directory it takes _forever_ to 'get the files information', way longer than the update cycle of that data (every 15 mins). I can't use wget because it wont allow me to specify a regex for how long I want to go back (I really only want data for the last 2 days, not the last 10 like that archive has) Any suggestions? Thanks in advance for any help.

---

### Post by aeiah on 2008-10-02
well the file names have the date in, so with a bash script, or python or whatever, you should be able to get today's date, and download everything that has todays date in its filename and everything that has todays date - 1 day in its filename.

the problem will come when you cross months. ie, how do you easily tell it that one day before 1st of october is 30th september? perhaps a python module would be useful for that or a big if else statement.

once you've got a mechanism that'll identify all files that contain todays date and todays date - 1 you can iterate over them with wget, or if you're using python, you could multithread it so it downloads them all at once (or 5 at a time or something). im not sure if bash does anything resembling multithreading, i dont really use it im afriad.

---

### Post by Omega2Four on 2008-10-02
First off, thank you for your quick response. 

> **aeiah said:**
> 
once you've got a mechanism that'll identify all files that contain todays date and todays date - 1 you can iterate over them with wget, or if you're using python, you could multithread it so it downloads them all at once (or 5 at a time or something). im not sure if bash does anything resembling multithreading, i dont really use it im afriad.

This is the part I'm confused about. How do you make the mechanism to do that, and how do you iterate over it with wget? I'm relatively new to scripting so I dont know the language to use to do that. I know how commands and options work and can write simple scripts, you know, ones that will rename all files and move them somewhere automatically, trivial stuff like that. If you could help me out or point me to a link that adresses what I need to learn that would be great. Thanks again.

---

### Post by iponeverything on 2008-10-02
easy enough. I hope you have a fast connection.

watch this space

---

### Post by iponeverything on 2008-10-02
Put this in a file called "time"

```

0015
0045
0115
0145
0215
0245
0315
0645
0715
0745
0815
0845
0915
0945
1015
1045
1115
1145
1215
1245
1315
1345
1415
1445
1515
1545
1615
1645
1715
1745
1815
1845
1915
1945
2015
2045
2115
2145
2215
2245
2315
2345

```

cat time | awk '{print "date --date  \47 2 days ago\47 \47+%Y%m%d_"$1"\47"}'| sh | awk '{print "wget http://metfs1.agron.iastate.edu/data/gempak/images/sat/GOES-12/4km/IR/IR_"$1}' > script

cat time | awk '{print "date --date  \47 1 day ago\47 \47+%Y%m%d_"$1"\47"}'| sh | awk '{print "wget http://metfs1.agron.iastate.edu/data/gempak/images/sat/GOES-12/4km/IR/IR_"$1}'>> script

 cat time | awk '{print "date \47+%Y%m%d_"$1"\47"}'| sh | awk '{print "wget http://metfs1.agron.iastate.edu/data/gempak/images/sat/GOES-12/4km/IR/IR_"$1}' >> script

sh script

---

### Post by Omega2Four on 2008-10-02
Thanks a lot, at the station now but I'll try it on my pc when I get home.

---

