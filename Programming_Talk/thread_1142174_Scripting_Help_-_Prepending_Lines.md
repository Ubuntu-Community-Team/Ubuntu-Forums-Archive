---
title: "Scripting Help - Prepending Lines"
date: 2009-04-28
forum: Programming Talk
---

### Post by PointyWombat on 2009-04-28
Hi,

I'm collecting statistics for a storage array and the data comes in the form of where the date and time is not on each line for each sample collected, but just the start of that iteration.. (data is captured every 5 minutes). In order to pump this into some graphing type solution, like cacti, each line should be prepended with the date time.

```
Capture Iteration: 2
Date/Time: 4/27/09 12:05:07 AM
CONTROLLER IN SLOT A,128077.0,28.5,24.7,2101.2,3868.4,162.6,263.4,

Volume LUN-01,54502.0,39.5,25.8,735.0,1957.5,51.6,129.7,

Volume LUN-03,21787.0,10.8,27.8,293.6,620.3,29.6,42.9,

CONTROLLER IN SLOT B,294606.0,64.4,25.9,5271.5,5271.5,470.8,509.6,

Volume LUN-02,38158.0,34.8,64.8,471.6,961.3,41.4,85.6,

Volume LUN-04,206221.0,83.3,22.3,2767.2,2767.2,333.9,352.4,

STORAGE ARRAY TOTALS,422683.0,53.5,25.7,7372.7,8091.3,633.4,773.0,

Capture Iteration: 3
Date/Time: 4/27/09 12:10:07 AM
CONTROLLER IN SLOT A,192892.0,29.3,29.4,2923.6,3868.4,215.3,263.4,

Volume LUN-01,77677.0,41.0,25.8,1147.2,1957.5,77.0,129.7,

Volume LUN-03,31578.0,9.3,31.7,322.3,620.3,32.5,42.9,

CONTROLLER IN SLOT B,438541.0,63.7,25.0,4768.3,5271.5,479.8,509.6,

Volume LUN-02,48491.0,28.7,65.1,261.2,961.3,34.4,85.6,

Volume LUN-04,308228.0,83.8,22.3,2446.9,2767.2,340.0,352.4,

STORAGE ARRAY TOTALS,631433.0,53.2,25.8,7691.9,8091.3,695.1,773.0,

Capture Iteration: 4
Date/Time: 4/27/09 12:15:08 AM
CONTROLLER IN SLOT A,248617.0,29.3,28.8,2442.0,3868.4,185.8,263.4,

Volume LUN-01,92837.0,39.3,27.2,718.0,1957.5,50.5,129.7,

Volume LUN-03,41212.0,10.2,36.9,298.3,620.3,32.1,42.9,

CONTROLLER IN SLOT B,566090.0,64.9,23.9,3908.4,5271.5,423.8,509.6,

Volume LUN-02,61391.0,28.0,64.1,638.1,961.3,42.9,85.6,

Volume LUN-04,403666.0,84.8,21.4,2740.8,2767.2,317.1,352.4,

STORAGE ARRAY TOTALS,814707.0,54.0,24.7,6350.4,8091.3,609.5,773.0,

Capture Iteration: 5
Date/Time: 4/27/09 12:20:08 AM
CONTROLLER IN SLOT A,299886.0,28.5,28.3,2364.5,3868.4,170.3,263.4,

Volume LUN-01,110209.0,39.7,26.6,931.4,1957.5,57.7,129.7,

Volume LUN-03,49205.0,9.6,39.0,227.8,620.3,26.6,42.9,

CONTROLLER IN SLOT B,693926.0,65.7,25.0,3368.9,5271.5,426.1,509.6,

Volume LUN-02,71039.0,24.8,64.3,342.4,961.3,32.2,85.6,

Volume LUN-04,502431.0,85.4,22.8,2475.2,2767.2,329.2,352.4,

STORAGE ARRAY TOTALS,993812.0,54.5,25.5,5733.4,8091.3,596.4,773.0,
```


I need to get it to form such as:

```

4/27/09 12:05:07 AM CONTROLLER IN SLOT A,128077.0,28.5,24.7,2101.2,3868.4,162.6,263.4,
4/27/09 12:05:07 AM Volume LUN-01,54502.0,39.5,25.8,735.0,1957.5,51.6,129.7,
4/27/09 12:05:07 AM Volume LUN-03,21787.0,10.8,27.8,293.6,620.3,29.6,42.9,
4/27/09 12:05:07 AM CONTROLLER IN SLOT B,294606.0,64.4,25.9,5271.5,5271.5,470.8,509.6,
4/27/09 12:05:07 AM Volume LUN-02,38158.0,34.8,64.8,471.6,961.3,41.4,85.6,
4/27/09 12:05:07 AM Volume LUN-04,206221.0,83.3,22.3,2767.2,2767.2,333.9,352.4,
4/27/09 12:05:07 AM STORAGE ARRAY TOTALS,422683.0,53.5,25.7,7372.7,8091.3,633.4,773.0,
4/27/09 12:10:07 AM CONTROLLER IN SLOT A,192892.0,29.3,29.4,2923.6,3868.4,215.3,263.4,
4/27/09 12:10:07 AM Volume LUN-01,77677.0,41.0,25.8,1147.2,1957.5,77.0,129.7,
4/27/09 12:10:07 AM Volume LUN-03,31578.0,9.3,31.7,322.3,620.3,32.5,42.9,
4/27/09 12:10:07 AM CONTROLLER IN SLOT B,438541.0,63.7,25.0,4768.3,5271.5,479.8,509.6,
4/27/09 12:10:07 AM Volume LUN-02,48491.0,28.7,65.1,261.2,961.3,34.4,85.6,
4/27/09 12:10:07 AM Volume LUN-04,308228.0,83.8,22.3,2446.9,2767.2,340.0,352.4,
4/27/09 12:10:07 AM STORAGE ARRAY TOTALS,631433.0,53.2,25.8,7691.9,8091.3,695.1,773.0,
4/27/09 12:15:08 AM CONTROLLER IN SLOT A,248617.0,29.3,28.8,2442.0,3868.4,185.8,263.4,
4/27/09 12:15:08 AM Volume LUN-01,92837.0,39.3,27.2,718.0,1957.5,50.5,129.7,
4/27/09 12:15:08 AM Volume LUN-03,41212.0,10.2,36.9,298.3,620.3,32.1,42.9,
4/27/09 12:15:08 AM CONTROLLER IN SLOT B,566090.0,64.9,23.9,3908.4,5271.5,423.8,509.6,
4/27/09 12:15:08 AM Volume LUN-02,61391.0,28.0,64.1,638.1,961.3,42.9,85.6,
4/27/09 12:15:08 AM Volume LUN-04,403666.0,84.8,21.4,2740.8,2767.2,317.1,352.4,
4/27/09 12:15:08 AM STORAGE ARRAY TOTALS,814707.0,54.0,24.7,6350.4,8091.3,609.5,773.0,
4/27/09 12:20:08 AM CONTROLLER IN SLOT A,299886.0,28.5,28.3,2364.5,3868.4,170.3,263.4,
4/27/09 12:20:08 AM Volume LUN-01,110209.0,39.7,26.6,931.4,1957.5,57.7,129.7,
4/27/09 12:20:08 AM Volume LUN-03,49205.0,9.6,39.0,227.8,620.3,26.6,42.9,
4/27/09 12:20:08 AM CONTROLLER IN SLOT B,693926.0,65.7,25.0,3368.9,5271.5,426.1,509.6,
4/27/09 12:20:08 AM Volume LUN-02,71039.0,24.8,64.3,342.4,961.3,32.2,85.6,
4/27/09 12:20:08 AM Volume LUN-04,502431.0,85.4,22.8,2475.2,2767.2,329.2,352.4,
4/27/09 12:20:08 AM STORAGE ARRAY TOTALS,993812.0,54.5,25.5,5733.4,8091.3,596.4,773.0,

```

Not even sure where to begin with this. I know some basic perl and ksh so that would be langs of choice.. 

Could someone give me a push in the right direction on how to prepend each line with the date/time for that round of stats...

Thanks,

---

### Post by PointyWombat on 2009-04-28
I'm also thinking that awk should be able to do it, but not sure how to construct it. I'm sure it would be an ugly one liner...  thoughts?

---

### Post by ghostdog74 on 2009-04-29
here you go
```
awk '/Date\/Time/{datetime=$2FS$3FS$4;next}!/Capture/&&!/^$/{ print datetime,$0}' file

```

---

### Post by PointyWombat on 2009-04-29
Nice... This will definately make my efforts of getting this data into cacti much easier.

Thanks ghostdog74!

---

