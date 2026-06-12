---
title: "awk, merge colums from different files"
date: 2010-10-10
forum: Programming Talk
---

### Post by Leonardo2887 on 2010-10-10
Hello to everybody. 

I need to merge three different files, which are structured as follows:

```
#Temperature		 298.3643 K
#Angle			 90 deg
#Viscosity		 0.8904 mPas
#Refractive Index	 1.33
#Wavelength		 532 nm
#Duration		 99.82444 s
#Scattering Vector	 0.0222144 1/nm
#tau/ms	 g(2)	 ln(g(1))	 t/s	 I
     0.00020000	      1.54655100	     -0.30206383	     0.00000000	     2.20743800
     0.00040000	      1.93848500	     -0.03174420	     0.19611874	     2.20743800
     0.00060000	      1.85374200	     -0.07906312	     0.39223749	     2.45666500
     0.00080000	      1.99144900	     -0.00429388	     0.58835623	     2.31425000
     0.00100000	      1.74781400	     -0.14530050	     0.78447497	     2.17183400
     0.00120000	      1.81137100	     -0.10451493	     0.98059371	     2.42106100
     0.00140000	      1.83255600	     -0.09162740	     1.17671246	     2.10062700
     0.00160000	      1.99144900	     -0.00429388	     1.37283120	     2.20743800
     0.00180000	      1.74781400	     -0.14530050	     1.56894994	     2.38545700
     0.00200000	      1.85374200	     -0.07906312	     1.76506868	     2.06502300
.....................
```

All three files have the same identical first column (tau/ms). Now, I'd like to have a new file, which has the following structure:

tau/ms g(2)1
tau/ms g(2)2
tau/ms g(2)3

where g(2)1, g(2)2 and g(2)3 are the respective second columns from the three input files. 

I hope somebody here can give me some useful advides. 

Kind regards,
Leonardo

PS: the first lines, those marked with # are not needed in the new file.

---

