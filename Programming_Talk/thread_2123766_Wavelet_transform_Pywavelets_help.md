---
title: "Wavelet transform Pywavelets help"
date: 2013-03-08
forum: Programming Talk
---

### Post by flyingsliverfin on 2013-03-08
Hi there, I need to incorporate a wavelet transform into a program that I'm writing. I know basically what it does, but I don't know much of the math behind it and the complex math (for instance, haven't taken linear algebra or anything, only calculus so far). So, I was wondering if someone could provide a setup for how I would use the pyWavelets library to do what I want. Basically what I have is data, and an associated timestamp. I want the frequency spectra at each moment (or just which frequencies exist at the moments).

For instance, here's a sample input:
```
2862	0
2865	60
2862	124
2864	180
2864	236
2860	292
2855	344
2859	408
2856	468
2857	528
2860	636
2851	660
2848	684
2848	708
2847	732
2847	760
2848	784
2847	808
2844	832
2844	860
2847	884
2855	908
2870	932
2883	960
2892	984
2887	1008
2864	1032
2828	1056
2791	1084
2764	1108
2763	1132
2772	1156
2791	1184
2817	1208
2854	1232
2879	1256
2903	1284
2953	1308
3027	1332
3040	1356
2904	1384
2599	1408
2294	1432
2211	1456
2521	1480
2835	1508
3057	1532
3215	1564
2632	1588
2052	1612
1651	1636
1708	1664
2236	1688
2627	1712
2908	1736
2896	1764
2324	1788
1844	1812
1816	1836
2323	1864
2691	1888
2953	1912
3139	1936
3047	1960
2368	1988
1863	2012
1499	2036
1465	2060
2023	2088
2467	2112
2792	2136
2303	2160
1815	2188
1463	2212
1209	2236
1201	2260
1875	2288
2360	2312
2713	2336
2968	2360
3150	2384
3278	2412
3367	2436
3431	2460
3473	2484
3500	2512
2968	2536
2284	2560
1806	2592
1683	2616
2199	2640
2601	2668
2889	2692
3096	2716
3239	2740
3278	2764
2556	2792
1995	2816
1593	2840
1308	2864
1108	2892
953	2916
957	2940
1181	2964
1384	2992
1718	3016
1847	3040
1718	3064
1526	3092

```

Where the first number is the value, and second is the timestamp (in microseconds)

Any help is greatly appreciated!
Thanks!

---

