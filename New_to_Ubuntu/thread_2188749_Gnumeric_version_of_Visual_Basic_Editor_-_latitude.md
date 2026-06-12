---
title: "Gnumeric version of Visual Basic Editor - latitude decimals"
date: 2013-11-18
forum: New to Ubuntu
---

### Post by Kevin McCready on 2013-11-18
Is there a gnumeric version of Microsoft Excel's Visual Basic Editor (VBE)?

I have to convert a bunch of latitudes and longitudes from degrees seconds minutes (DSM) to decimal.

I've been given these instructions for Excel and VBE, but would like to do it in gnumeric:
-------------
Converting Degrees/Minutes/Seconds to Decimal Degrees
The following Microsoft Visual Basic for Applications custom function accepts a text string of degrees, minutes and seconds formatted in the exact same format that the Convert_Degree function returns (for example, 10° 27' 36") and converts it to an angle formatted as a decimal value. This is exactly the reverse of the Convert_Degree custom function.

WARNING: This custom function fails if the Degree_Deg argument is not in the following format
<degrees>° <minutes>' <seconds>"
even if the seconds value is 0.

Function Convert_Decimal(Degree_Deg As String) As Double
   ' Declare the variables to be double precision floating-point.
   Dim degrees As Double
   Dim minutes As Double
   Dim seconds As Double
   ' Set degree to value before "°" of Argument Passed.
   degrees = Val(Left(Degree_Deg, InStr(1, Degree_Deg, "°") - 1))
   ' Set minutes to the value between the "°" and the "'"
   ' of the text string for the variable Degree_Deg divided by
   ' 60. The Val function converts the text string to a number.
   minutes = Val(Mid(Degree_Deg, InStr(1, Degree_Deg, "°") + 2, _
             InStr(1, Degree_Deg, "'") - InStr(1, Degree_Deg, _
             "°") - 2)) / 60
    ' Set seconds to the number to the right of "'" that is
    ' converted to a value and then divided by 3600.
    seconds = Val(Mid(Degree_Deg, InStr(1, Degree_Deg, "'") + _
            2, Len(Degree_Deg) - InStr(1, Degree_Deg, "'") - 2)) _
            / 3600
   Convert_Decimal = degrees + minutes + seconds
End Function
                

To use this function, create a conversion formula, as in the following example:

    Start Excel and press ALT+F11 to start the Visual Basic Editor.
    On the Insert menu, click Module.
    Enter the sample code for the Convert_Decimal custom function described above into the module sheet.
    Press ALT+F11 to return to excel.
    In cell A1 type the following formula:
    =Convert_Decimal("10° 27' 36""")
    NOTE: You are required to type three quotation marks (""") at the end of the argument of this formula to balance the quotation mark for the seconds and the quotation mark for the text string. A cell reference will not require a quotation mark.
    The formula returns 10.46

---

### Post by oldfred on 2013-11-19
If just the numbers you do not need a function, just the math. The function is just to convert a string to numbers so you can do the math.

If a formated csv or text file that you import, then python, java or bash might be a better solution.

---

### Post by Lars Noodén on 2013-11-19
> **oldfred said:**
> ... python, java or bash might be a better solution.

In LibreOffice, you can write macros in java, javascript or python.  I don't know about Gnumeric.

But it would be best to stick to the built-in functions if you can.  It is possible to build them out quite well.  Lattitude conversion should be a fairly simple formula and should lend itself to the functions and any formulas you would write, without resorting to macros.  Macros would be overkill.

---

### Post by Lars Noodén on 2013-11-19
I'm not up on geography, but looking around the conversion formula seems very, very simple.  One place with it in detail is (ugh) Wikipedia:

[http://en.wikipedia.org/wiki/Decimal_degrees](http://en.wikipedia.org/wiki/Decimal_degrees)

Conversion back requires modulo but is not much more complex.  

You can very easily use regular formulas, not macros, for either conversion.

Edit: If degrees, minutes, seconds are in A1, B1 and C1 then the formula is =A1+B1/60+C1/3600

---

