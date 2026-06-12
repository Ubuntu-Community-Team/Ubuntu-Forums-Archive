---
title: "Work project"
date: 2011-03-15
forum: Programming Talk
---

### Post by Drenriza on 2011-03-15
Hi all.

Im thinking about starting my own little project at work. In my normal day i work alot with linux servers, where im sitting in a administration group.

The project i would like to do is. Having an apache server, and something that can work along with it so i could take. Linux server outputs and put it into a html / something else page. And display

Free HDD space %
Processor utilization.
Network traffic.
With more.

Display this on either an internal or external webpage.
Making a system that can look in the logs, and post on the webpage page, if an known error occurs.

But what can do use to make this? I know an html / coldfusion combo can do this. But i havent found alot of usefull doc for this on linux, how to install and setup the coldfusion service. What would you use?

Thanks on advance.
Kind regards.

---

### Post by Shpongle on 2011-03-15
You could get the information from a bash script and write out the data with html tags around it , you could then set it as a cron job to overwrite the file periodically and when you call the page . You will have the latest results . Theres a few different ways you could do it.

bash has built in commands for what your looking for.

---

### Post by Drenriza on 2011-03-15
> **Shpongle said:**
> You could get the information from a bash script and write out the data with html tags around it , you could then set it as a cron job to overwrite the file periodically and when you call the page . You will have the latest results . Theres a few different ways you could do it.

bash has built in commands for what your looking for.

Have any guides, examples or where i can read about this?

---

### Post by Shpongle on 2011-03-15
> **Drenriza said:**
> Have any guides, examples or where i can read about this?

here is a guide for a bash tutorial. [http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)


you want to make a script that prints out a html page

like echo "<html>" 

text etc in here

echo "</html>"


you can either then echo it out to a file in the program or just pipe in to the file when you get it on screen

for example ./htmlInfoScript | info.html would put the html text into a html file called info which you could the view in your browser

you'll need to execute commands inside the script to get the info your after.
df -h will give you the disk space in a human readable format for example

you can look at the example for running commands in a bash script

eg echo `df -h`  note the ` (key beside the one on a qwerty keyboard) and not '

I would write it for you , just that I'm very busy at the minute writing my thesis

---

### Post by robots.jpg on 2011-03-15
There are some nice tools out there for monitoring servers.  But if you're doing it mostly for learning purposes:
  
  I would write a script to be called periodically by cron on each  of the servers. It would run your commands, pull out the useful  information, and then connect and save them to a database on the Apache server.  A  simple php script on the Apache server could generate a page each time you request it, with whatever  recent information you want to display for each reporting server.
 

You would have these parts to work out:
 
 - Run system commands from a script and extract the useful data
 - Set up a database and enable remote access
 - Connect and write to the remote database from your monitoring script
 - Connect to and read from the local database in php

---

