---
title: "How to set gnuplot automatically for max-min margin"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by ahjiefreak on 2008-08-13
Hi,

I have written a script to automatically generate plots . However, I have two problems here:-

i) Given my plot of data points, I am not sure what is the best way to automate plot at its best where there's no redundant empty space range. 

By default, the plots would automatically adjust the margin of y-axis. However, I observed there are some problem in some plots where redundant space is wasted without any plot. 

I would like to set yrange using the max and min of the data but im not sure how.

My data is something like below:-

file1	file2	file3	file4	file5	file6	file7	
38	143	0	408	113	391	29	
3	48	38	28	150	186	28	
0.0731707	0.251309	1	0.0642202	0.570342	0.322357	0.491228	
0.0681818	0.24	1	0.0642202	0.517241	0.321244	0.444444	
0.0810811	0.24	1	0.0646651	0.535714	0.322357	0.451613	
0.0731707	0.226415	1	0.0648148	0.539568	0.321799	0.509091	
0.0666667	0.235294	1	0.0643678	0.557621	0.324042	0.444444	

I plot them from 3rd field onwards; 
plot 'myfile.txt' u 0:$i every ::3 w li

But Im not sure how to set yrange for the dataset as the value varies across N files.

ii) For the legend, I try explore in gnuplot demo and tried option like set key bottom, set key box..etc..but it still doesnt optimize the location of the legend in some plots. I would like to have the legend automatically adjusted to any empty space (top, middle or bottom).


Please advise. Thanks.

---

