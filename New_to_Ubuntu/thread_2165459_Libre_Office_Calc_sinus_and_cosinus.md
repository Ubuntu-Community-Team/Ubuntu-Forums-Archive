---
title: "Libre Office Calc sinus and cosinus"
date: 2013-08-05
forum: New to Ubuntu
---

### Post by Erik Kaiser on 2013-08-05
Hello !
The following problem has occurred : The functions 
sin and cos of the program libre office calc produce
wrong results if calculated through in steps of three
 ( 3,6,9,12,15,18, etc ). In an ankle span of 90 degrees the results
switch from positive to negative with every change of the calculated
degree rising upwards. This happens with Ubuntu taken from a CD which
was purchased in a newspaper shop and a Lenovo Thinkpad T 500 Laptop.
Unfortunately the topic could not be found in forum discussion yet.
Can you confirm this observation or do have any information about the
eventual cause of the problem ? The results were checked on an electronic 
calculator, they differ from the computer results, more functions were not tested.

Have a nice day
[COLOR=#888888]
Erik[/COLOR]

---

### Post by davetv on 2013-08-05
Are you sure the calculator is calculating the function with an argument of degrees and not radians?

---

### Post by rsgangr on 2013-08-06
By default, LibreOffice Calc works in Radians. Therefore if you want the SIN of 60 degrees, for example, it is necessary first to convert to radians and then apply the SIN function. In this case the formula would be =SIN(60*PI()/180).

---

### Post by bzsolt on 2013-08-31
[h=3]See here: [https://help.libreoffice.org/Calc/Mathematical_Functions#SIN](https://help.libreoffice.org/Calc/Mathematical_Functions#SIN)
*Syntax*[/h][COLOR=#000000][FONT=sans-serif]*SIN(Number)*[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]*Returns the (trigonometric) sine of **Number**, the angle in radians.*[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]*To return the sine of an angle in degrees, use the RADIANS function.*[/FONT][/COLOR]
[h=3]*Example*[/h][COLOR=#000000][FONT=sans-serif]*=SIN(PI()/2) returns 1, the sine of PI/2 radians.*[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif][I][COLOR=#ff0000]=SIN(RADIANS(30)) returns 0.5, the sine of 30 degrees.[/COLOR]
[/I]
[/FONT][/COLOR]

---

