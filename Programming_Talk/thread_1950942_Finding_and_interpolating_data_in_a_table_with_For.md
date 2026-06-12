---
title: "Finding and interpolating data in a table with Fortran"
date: 2012-04-01
forum: Programming Talk
---

### Post by Marlonsm on 2012-04-01
Hi, I'm in the middle of a Fortran project and need some help.

I have a table in a text file. It has 3 columns, one for height, one for air pressure and one for air density.
I need the program to read that table and, given a height, find pressure and density for it, interpolating values that are not in the table (linear interpolation is good enough).
It will be done multiple times during the execution, so it'd be nice to have it to read the file just once and keep it in memory for the other times.

Thanks!

---

### Post by CynicRus on 2012-04-02
[http://people.sc.fsu.edu/~jburkardt/f_src/table_io/table_io.html]("http://people.sc.fsu.edu/~jburkardt/f_src/table_io/table_io.html") - may this help you.

---

### Post by Marlonsm on 2012-04-02
Thank you! I'll take a look at it.

EDIT: I looked all those functions, but didn't find what I need. There is one that reads the Nth line of the table, but I don't know in which line the information I need will be.

---

### Post by ofnuts on 2012-04-02
> **Marlonsm said:**
> Hi, I'm in the middle of a Fortran project and need some help.

I have a table in a text file. It has 3 columns, one for height, one for air pressure and one for air density.
I need the program to read that table and, given a height, find pressure and density for it, interpolating values that are not in the table (linear interpolation is good enough).
It will be done multiple times during the execution, so it'd be nice to have it to read the file just once and keep it in memory for the other times.

Thanks!
Several questions:

First, I don't see if you must fetch/interpolate "related" values of pressure & density of if you can output a pressure value and a density value. 

Second, whatever the answer to the first question, what insures that the height/density and height/pressure function are monotonous. Sort you table on height: are the corresponding pressure and density monotonously increasing?

Third (which may be expanding on the first)  it may depend a lot on the data you have: if the data you have defines a surface then there are an infinity of values of pressure and density for a given height (think about contour line). It's even worse if the surface has "bumps" (non-contiguous sets of answer values). If it does not then pressure is a function of density (or vice versa) and you are back  to very simple independent interpolations of the two values.

---

### Post by Marlonsm on 2012-04-02
> **ofnuts said:**
> Several questions:

First, I don't see if you must fetch/interpolate "related" values of pressure & density of if you can output a pressure value and a density value. 

Second, whatever the answer to the first question, what insures that the height/density and height/pressure function are monotonous. Sort you table on height: are the corresponding pressure and density monotonously increasing?

Third (which may be expanding on the first)  it may depend a lot on the data you have: if the data you have defines a surface then there are an infinity of values of pressure and density for a given height (think about contour line). It's even worse if the surface has "bumps" (non-contiguous sets of answer values). If it does not then pressure is a function of density (or vice versa) and you are back  to very simple independent interpolations of the two values.

Both pressure and density decrease as the altitude increases.
The table I have is in the following format with more entries:

alt	press	dens
km	N/sq.m	kg/cu.m
-2	1.28E+05	1.48E+00
0	1.01E+05	1.23E+00
2	7.95E+04	1.01E+00
4	6.17E+04	8.19E-01
6	4.72E+04	6.60E-01
8	3.57E+04	5.26E-01
10	2.65E+04	4.14E-01
12	1.94E+04	3.12E-01
16	1.04E+04	1.67E-01
20	5.53E+03	8.89E-02
22	4.05E+03	6.45E-02
26	2.19E+03	3.43E-02
30	1.20E+03	1.84E-02

Later, I might also need to work with temperature, which is not a monotonous function.

I'll need the function or subroutine to find the pressure and density for a given altitude.
For example, I enter h = 9.5 km, the output should be an estimative of pressure and density for it (likely based on the interpolated values at 8 km and 10 km)

Thanks!

---

### Post by ofnuts on 2012-04-03
> **Marlonsm said:**
> Both pressure and density decrease as the altitude increases.
The table I have is in the following format with more entries:

alt    press    dens
km    N/sq.m    kg/cu.m
-2    1.28E+05    1.48E+00
0    1.01E+05    1.23E+00
2    7.95E+04    1.01E+00
4    6.17E+04    8.19E-01
6    4.72E+04    6.60E-01
8    3.57E+04    5.26E-01
10    2.65E+04    4.14E-01
12    1.94E+04    3.12E-01
16    1.04E+04    1.67E-01
20    5.53E+03    8.89E-02
22    4.05E+03    6.45E-02
26    2.19E+03    3.43E-02
30    1.20E+03    1.84E-02

Later, I might also need to work with temperature, which is not a monotonous function.

I'll need the function or subroutine to find the pressure and density for a given altitude.
For example, I enter h = 9.5 km, the output should be an estimative of pressure and density for it (likely based on the interpolated values at 8 km and 10 km)

Thanks!
- Load you table in three arrays: Heights/Pressures/Densities:
  - read line (likely using some FORMAT)
  - split
  - store values at same index in the three arrays
  - next line

Given a height
- iterate array of heights while Heights[i]<height
- interpolation=(height-Heights[i-1])/(Heights[i]-heights[i-1])
- pressure=Pressures[i-1]+interpolation*(Pressures[i]-Pressures[i-1]
- same for density

---

### Post by bouncingwilf on 2012-04-03
I suggest you investigate simple multi-linear regression analysis - There have been subroutines out there written in fortran for at least 45 years to my certain knowledge. (part of IBM fortssp comes to mind as an old one). This would have the advantage that you can add large numbers of additional variables to your model (given sufficient observations of course). Non linear variables can also be added after linearizing.

Bouncingwilf

---

### Post by Marlonsm on 2012-04-03
> **ofnuts said:**
> - Load you table in three arrays: Heights/Pressures/Densities:
  - read line (likely using some FORMAT)
  - split
  - store values at same index in the three arrays
  - next line

Given a height
- iterate array of heights while Heights[i]<height
- interpolation=(height-Heights[i-1])/(Heights[i]-heights[i-1])
- pressure=Pressures[i-1]+interpolation*(Pressures[i]-Pressures[i-1]
- same for density

Thanks! It seems to be just what I needed, I'll give it a try.

EDIT: I've done that and it's working. Thanks!

---

