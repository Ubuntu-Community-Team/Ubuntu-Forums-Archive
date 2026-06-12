---
title: "TEMPer USB to MySQL with graphs?"
date: 2014-11-10
forum: Programming Talk
---

### Post by solitaire on 2014-11-10
Hi guys!

Just picked up a TEMPer1f USB temp sensor
What's the best way to get the data from the sensor into nice looking graphs?

I've got the PCSensor software from [https://github.com/petechap/usb-thermometer](https://github.com/petechap/usb-thermometer)  and it outputs to the command line fine.
I've set up a cron job to send the temperature info to a log file every 5 mins.

Now I'm terrible at programming and don't know where to start getting the info from the sensor into mySQL let alone into a graph.

any help or pointers on where to look gratefully received.

---

### Post by solitaire on 2014-11-10
**duplicate post **

---

### Post by oldfred on 2014-11-10
Threads merged.
Please do not post duplicate threads. Those who may be able to help need to know what others have already posted to prevent duplication of effort. We all are volunteers.

---

### Post by Matthew_Harrop on 2014-11-10
How does the data come down?

Can you modify the sensor program you've got there to output not only to the Command line but also to something else?

Why do you want to use MySql? Is it important you use it or was it just the first database that sprung to mind?

---

### Post by solitaire on 2014-11-10
The command line program just prints the following:

```
bill@zotac:~$ pcsensor
2014/11/10 21:36:26 Temperature 64.85F 18.25C

```

I could possibly tinker with the program to change the output. But i'm not good at programming and so it would be mainly cosmetic changes to the output, rather than anything more difficult.

As for logging MySQL was the first thing that came to mind as the machine is already running the mySQL for Wordpress. 
I think it's a bit neater than having to phrase text log files if I want to push the data into something to create graphs.

---

### Post by Matthew_Harrop on 2014-11-10
> [TABLE="class: highlight tab-size-8 js-file-line-container"]
[TR]
[TD="class: blob-code js-file-line"]           if (mrtg) {[/TD]
       [/TR]
       [TR]
                  [TD="class: blob-code js-file-line"]              if (formato==2) {[/TD]
       [/TR]
       [TR]
                  [TD="class: blob-code js-file-line, bgcolor: #F8EEC7"]                  printf("%.2f\n", (9.0 / 5.0 * tempc + 32.0));[/TD]
       [/TR]
       [TR]
                  [TD="class: blob-code js-file-line"]                  printf("%.2f\n", (9.0 / 5.0 * tempc + 32.0));[/TD]
       [/TR]
       [TR]
                  [TD="class: blob-code js-file-line"]              } else {[/TD]
       [/TR]
       [TR]
                  [TD="class: blob-code js-file-line"]                  printf("%.2f\n", tempc);[/TD]
       [/TR]
       [TR]
                  [TD="class: blob-code js-file-line"]                  printf("%.2f\n", tempc);[/TD]
       [/TR]
       [TR]
                  [TD="class: blob-code js-file-line"]              }[/TD]
       [/TR]
       [TR]
                  [TD="class: blob-code js-file-line"]              
[/TD]
       [/TR]
       [TR]
                  [TD="class: blob-code js-file-line"]              printf("%02d:%02d\n", [/TD]
       [/TR]
       [TR]
                  [TD="class: blob-code js-file-line"]                          local->tm_hour,[/TD]
       [/TR]
       [TR]
                  [TD="class: blob-code js-file-line"]                          local->tm_min);[/TD]
       [/TR]
       [TR]
                  [TD="class: blob-code js-file-line"] 
[/TD]
       [/TR]
       [TR]
                  [TD="class: blob-code js-file-line"]              printf("pcsensor\n");[/TD]
       [/TR]
       [TR]
                  [TD="class: blob-code js-file-line"]           } else {[/TD]
       [/TR]
       [TR]
                  [TD="class: blob-code js-file-line"]              printf("%04d/%02d/%02d %02d:%02d:%02d ", [/TD]
       [/TR]
       [TR]
                  [TD="class: blob-code js-file-line"]                          local->tm_year +1900, [/TD]
       [/TR]
       [TR]
                  [TD="class: blob-code js-file-line"]                          local->tm_mon + 1, [/TD]
       [/TR]
       [TR]
                  [TD="class: blob-code js-file-line"]                          local->tm_mday,[/TD]
       [/TR]
       [TR]
                  [TD="class: blob-code js-file-line"]                          local->tm_hour,[/TD]
       [/TR]
       [TR]
                  [TD="class: blob-code js-file-line"]                          local->tm_min,[/TD]
       [/TR]
       [TR]
                  [TD="class: blob-code js-file-line"]                          local->tm_sec);[/TD]
       [/TR]
       [TR]
                  [TD="class: blob-code js-file-line"] 
[/TD]
       [/TR]
       [TR]
                  [TD="class: blob-code js-file-line"]              if (formato==2) {[/TD]
       [/TR]
       [TR]
                  [TD="class: blob-code js-file-line"]                  printf("Temperature %.2fF\n", (9.0 / 5.0 * tempc + 32.0));[/TD]
       [/TR]
       [TR]
                  [TD="class: blob-code js-file-line"]              } else if (formato==1) {[/TD]
       [/TR]
       [TR]
                  [TD="class: blob-code js-file-line"]                  printf("Temperature %.2fC\n", tempc);[/TD]
       [/TR]
       [TR]
                  [TD="class: blob-code js-file-line"]              } else {[/TD]
       [/TR]
       [TR]
                  [TD="class: blob-code js-file-line"]                  printf("Temperature %.2fF %.2fC\n", (9.0 / 5.0 * tempc + 32.0), tempc);[/TD]
       [/TR]
       [TR]
                  [TD="class: blob-code js-file-line"]              }[/TD]
       [/TR]
       [TR]
                  [TD="class: blob-code js-file-line"]              fflush(stdout);[/TD]
       [/TR]
       [TR]
                  [TD="class: blob-code js-file-line"]           }[/TD]
[/TR]
[/TABLE]


That's the part you're looking to modify in main()

If you open the pcsensor.c file in your favorite text editor/IDE (Make a backup before you do mind) and shunt the outputs that you see there into a basic SQL insert query. 

It'll look something like this:

> INSERT INTO "MYTABLE" VALUES(NULL, (9.0 / 5.0 * tempc + 32.0))

If MySql is already running on your computer then that would be the most appropriate product to use. 
Of course you'll need to start the database and write all the tables and stuff first, but SQL isn't to difficult to pick up.

If you need help learning it (From scratch) go here:
[http://www.w3schools.com/sql/default.asp](http://www.w3schools.com/sql/default.asp)

For MySql specific stuff, look here:
[http://dev.mysql.com/doc/](http://dev.mysql.com/doc/)

That should enter the data into a sql database :)

---

### Post by solitaire on 2014-11-11
Thanks for your help.

I'll take a look, I'm so-so with setting up a basic databases in MySQL so it will not be a huge problem for me.

---

### Post by Matthew_Harrop on 2014-11-11
Cool, you need any other help, don't hesitate to ask :)

---

