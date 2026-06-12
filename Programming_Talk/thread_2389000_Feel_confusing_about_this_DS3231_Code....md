---
title: "Feel confusing about this DS3231 Code..."
date: 2018-04-10
forum: Programming Talk
---

### Post by joshua1203 on 2018-04-10
[COLOR=#3B3B3B][FONT=Arial]I'm using a Maxim DS3231 Real Time Clock IC. 
[/FONT][/COLOR]
[COLOR=#3B3B3B][FONT=Arial]See:[http://www.kynix.com/Detail/99971/DS3231.html](http://www.kynix.com/Detail/99971/DS3231.html)
[/FONT][/COLOR]
[COLOR=#3B3B3B][FONT=Arial]Datasheet: [http://www.alldatasheet.com/datasheet-pdf/pdf/112132/DALLAS/DS3231.html](http://www.alldatasheet.com/datasheet-pdf/pdf/112132/DALLAS/DS3231.html)
[/FONT][/COLOR]
[COLOR=#3B3B3B][FONT=Arial]I found a working code on google:
[/FONT][/COLOR]
[COLOR=#3B3B3B][FONT=Arial]```
[COLOR=#222222][FONT=&amp]Wire.beginTransmission(DS3231_I2C_ADDRESS);[/FONT][/COLOR]
```[/FONT][/COLOR]```

[FONT=&amp]  Wire.write(0); // set DS3231 register pointer to 00h[/FONT]
[FONT=&amp]  Wire.endTransmission();[/FONT]
[FONT=&amp]  Wire.requestFrom(DS3231_I2C_ADDRESS, 7);[/FONT]
[FONT=&amp]  // request seven bytes of data from DS3231 starting from register 00h[/FONT]
[FONT=&amp]  *second = bcdToDec(Wire.read() & 0x7f);[/FONT]
[FONT=&amp]  *minute = bcdToDec(Wire.read());[/FONT]
[FONT=&amp]  *hour = bcdToDec(Wire.read() & 0x3f);[/FONT]
[FONT=&amp]  *dayOfWeek = bcdToDec(Wire.read());[/FONT]
[FONT=&amp]  *dayOfMonth = bcdToDec(Wire.read());[/FONT]
[FONT=&amp]  *month = bcdToDec(Wire.read());[/FONT]
[COLOR=#3B3B3B][FONT=Arial][COLOR=#222222][FONT=&amp]  *year = bcdToDec(Wire.read());[/FONT][/COLOR][/FONT][/COLOR]
```[COLOR=#3B3B3B][FONT=Arial]
in the line
```
[COLOR=#222222][FONT=&amp]*second = bcdToDec(Wire.read() & 0x7f);[/FONT][/COLOR]
```
[/FONT][/COLOR]
is a 0x7f added,
and in the line

```
[FONT=&amp]*hour = bcdToDec(Wire.read() & 0x3f);[/FONT]
```

a 0x3f.


I think the 0x3f for hour, is because of the am/pm 12/24 thing, if you look at the datasheet. 


But im wondering what this 0x7f is doing there? Why is is it needed? If you look at the datasheet, minutes and seconds in the register map are looking complete the same. 


Any idea what 0x7f is for?  Thanks in advance.


P.S. The code works fine, i just wanna understand it...

---

### Post by steeldriver on 2018-04-10
The & is not an addition - it's a [bitwise logical AND]("https://en.wikipedia.org/wiki/Bitwise_operations_in_C") and it is being used to apply a [mask]("https://en.wikipedia.org/wiki/Mask_(computing)") to the register contents

---

### Post by Frogs Hair on 2018-04-10
Moved to* Programing Talk*.

---

