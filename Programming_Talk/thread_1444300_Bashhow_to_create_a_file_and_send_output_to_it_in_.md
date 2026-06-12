---
title: "Bash:how to create a file and send output to it in a loop"
date: 2010-04-01
forum: Programming Talk
---

### Post by wannabegeek on 2010-04-01
Hi all,

I've got myself a task to learn shell scripting in bash, that is coming together well.

I am using curl to get data and need to store it in a file whose name will be made from 
variables in the for loop.

So I guess I need empty files created first in the loop, then and have the output sent to them.

I am having trouble finding out how to do this...
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

for y in {0..1}  # years loop
  do
   for m in {0..1}  # month loop
     do
      curl -s http://tidesandcurrents.noaa.gov/data_menu.shtml?bdate=$Y${M[m]}$BD'&edate='$Y${M[m]}${ED[m]}'&wl_sensor_hist=W1&relative=&datum=6&unit=0&shif$
     grep -e '^9414290[[:space:]]' |   > ClevelcurlDATA/stageGetData$Y${M[m]}     
  done
Y=$((Y+1))
done
```


tia
wbg

---

### Post by wannabegeek on 2010-04-01
never mind...I shouldn't post anymore tonight...

peace

---

