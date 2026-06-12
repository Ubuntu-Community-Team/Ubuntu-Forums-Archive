---
title: "See total uploaded / downloaded and average speed over time"
date: 2012-06-13
forum: New to Ubuntu
---

### Post by yeehi on 2012-06-13
I would like to know a nifty application that would show me a record of the total amount downloaded and uploaded over a period of a year, or a month. It would be nice if it also could show average up and download speeds during this time period, too.

System monitor measures that for you but it is in real time. It doesn't build up a record over time, as far as I know.

---

### Post by ajgreeny on 2012-06-13
Look at vnstat

```
vnstat -d
```will give output like
```
eth0  /  daily

         day         rx      |     tx      |    total    |   avg. rate
     ------------------------+-------------+-------------+---------------
      05/15/12    484.21 MiB |   21.24 MiB |  505.45 MiB |   47.92 kbit/s
      05/16/12    196.12 MiB |   11.88 MiB |  208.01 MiB |   19.72 kbit/s
      05/17/12      1.33 GiB |   43.98 MiB |    1.37 GiB |  133.15 kbit/s
      05/18/12     33.27 MiB |   26.04 MiB |   59.31 MiB |    5.62 kbit/s
      05/19/12     49.85 MiB |   34.66 MiB |   84.51 MiB |    8.01 kbit/s
      05/20/12      1.17 GiB |   45.01 MiB |    1.21 GiB |  117.58 kbit/s
      05/21/12    906.95 MiB |   47.12 MiB |  954.06 MiB |   90.46 kbit/s
      05/22/12    599.12 MiB |   23.66 MiB |  622.78 MiB |   59.05 kbit/s
      05/23/12     43.01 MiB |    4.06 MiB |   47.07 MiB |    4.46 kbit/s
      05/24/12     64.76 MiB |    3.34 MiB |   68.11 MiB |    6.46 kbit/s
      05/25/12    276.54 MiB |   19.58 MiB |  296.12 MiB |   28.08 kbit/s
      05/26/12     54.29 MiB |    6.62 MiB |   60.92 MiB |    5.78 kbit/s
      05/27/12    949.69 MiB |   26.88 MiB |  976.57 MiB |   92.59 kbit/s
      05/28/12    310.05 MiB |   13.61 MiB |  323.66 MiB |   30.69 kbit/s
      05/29/12    415.65 MiB |   21.92 MiB |  437.57 MiB |   41.49 kbit/s
      05/30/12    649.38 MiB |   52.13 MiB |  701.51 MiB |   66.51 kbit/s
      05/31/12    204.58 MiB |   11.26 MiB |  215.84 MiB |   20.46 kbit/s
      06/01/12    683.35 MiB |   27.60 MiB |  710.95 MiB |   67.41 kbit/s
      06/02/12    223.10 MiB |    8.39 MiB |  231.50 MiB |   21.95 kbit/s
      06/03/12    151.81 MiB |    7.44 MiB |  159.25 MiB |   15.10 kbit/s
      06/04/12     47.64 MiB |   12.65 MiB |   60.29 MiB |    5.72 kbit/s
      06/05/12     96.17 MiB |    6.56 MiB |  102.73 MiB |    9.74 kbit/s
      06/06/12    278.76 MiB |   10.41 MiB |  289.17 MiB |   27.42 kbit/s
      06/07/12     65.80 MiB |    3.05 MiB |   68.85 MiB |    6.53 kbit/s
      06/08/12     73.88 MiB |    7.80 MiB |   81.69 MiB |    7.74 kbit/s
      06/09/12    178.97 MiB |   10.00 MiB |  188.97 MiB |   17.92 kbit/s
      06/10/12    281.97 MiB |   13.21 MiB |  295.18 MiB |   27.99 kbit/s
      06/11/12    118.93 MiB |    8.38 MiB |  127.31 MiB |   12.07 kbit/s
      06/12/12     46.82 MiB |    3.97 MiB |   50.80 MiB |    4.82 kbit/s
      06/13/12     57.75 MiB |    3.41 MiB |   61.16 MiB |    6.68 kbit/s
     ------------------------+-------------+-------------+---------------
     estimated        65 MiB |       3 MiB |      68 MiB |

``````
vnstat -l
``` will give you live output which changes as speed changes, etc etc, like this
```
Monitoring eth0...    (press CTRL-C to stop)

   rx:        0 kbit/s     0 p/s          tx:        0 kbit/s     0 p/s^C


 eth0  /  traffic statistics

                           rx         |       tx
--------------------------------------+------------------
  bytes                      196 KiB  |          45 KiB
--------------------------------------+------------------
          max             628 kbit/s  |       76 kbit/s
      average            5.09 kbit/s  |     1.17 kbit/s
          min               0 kbit/s  |        0 kbit/s
--------------------------------------+------------------
  packets                        297  |             256
--------------------------------------+------------------
          max                 70 p/s  |          62 p/s
      average                  0 p/s  |           0 p/s
          min                  0 p/s  |           0 p/s
--------------------------------------+------------------
  time                  5.13 minutes
```mostly showing low figures as I was not downloading anything when I copied it here.  This is useful for d/l speeds of, for example a download of a specific single file, where you can start the vnstat when the d/l starts and stop it when the d/l stops, showing you how much was transfered and the average d/l speed.

---

### Post by yeehi on 2012-06-13
When I try to use vnstat -d, I get command not found

:(

Is something not installed?

It would be nice if there were a GUI for vnstat.

---

### Post by Cheesemill on 2012-06-13
+1
You need to install [vnstat]("apt://vnstat") first.
```
sudo apt-get install vnstat
```
I use it on all of my machines.

---

