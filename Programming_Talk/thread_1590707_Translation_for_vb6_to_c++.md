---
title: "Translation for vb6 to c++"
date: 2010-10-08
forum: Programming Talk
---

### Post by eric65 on 2010-10-08
Hello i need a help on translation from this code in vb6 to c++ .
 
If it's possible i need to translate in to a function.
 
thanks
 
Eric
 
code:
 

'This Filter computes the default Band-Pass-Filter 
'This Filter assumes a Randome-Walk time-series with drift'
'data = time-series'
'pl   = minimum period'
'pu   = maximum period'
'Quarterly data: pl=6, pu=32 returns component with periods between 1.5 and 8 yrs.
'Monthly data:   pl=2, pu=24 returns component with all periods less than 2 yrs.'
 
-----------------------------------------------------------
Function bpass(data As Range, pl As Double, pu As Double)
Dim nobs As Integer, k As Integer, drift As Double, a As Double, b As Double
Dim bnot As Double, bhat As Double, AA() As Double, AAt() As Double
Dim l As Integer
Const pi As Double = 3.14159265358979
Dim datanew() As Double, BB() As Double
nobs = data.Rows.Count
ReDim datanew(nobs, 1)
    
For k = 1 To nobs Step 1
    datanew(k, 1) = data(k, 1)
Next k
    
'Drift wird entfernt'
'Removing drift'
    
drift = (datanew(nobs, 1) - datanew(1, 1)) / (nobs - 1)
For k = 1 To nobs Step 1
    datanew(k, 1) = datanew(k, 1) - (k - 1) * drift
Next k
'Create the ideal B's then construct the AA matrix'
b = 2 * pi / pl
a = 2 * pi / pu
bnot = (b - a) / pi
bhat = bnot / 2
ReDim BB(nobs, 1)
For k = 1 To nobs - 1 Step 1
    BB(k + 1, 1) = (Sin(k * b) - Sin(k * a)) / (k * pi)
Next k

BB(1, 1) = bnot
ReDim AAt(2 * nobs, 2 * nobs)
ReDim AA(nobs, nobs)
For k = 1 To nobs Step 1
    For l = 1 To nobs Step 1
        AAt(k, l + k - 1) = BB(l, 1)
           
        AAt(k + l - 1, k) = BB(l, 1)
    Next l
Next k
For k = 1 To nobs Step 1
    For l = 1 To nobs Step 1
        AA(k, l) = AAt(k, l)
    Next l
Next k

AA(1, 1) = bhat
AA(nobs, nobs) = bhat
For k = 1 To nobs - 1 Step 1
    AA(k + 1, 1) = AA(k, 1) - BB(k, 1)
    AA(nobs - k, nobs) = AA(k, 1) - BB(k, 1)
Next k
            
        
ReDim BB(nobs, 1)
        

'Computes the Filter using AA'
For k = 1 To nobs Step 1
    For l = 1 To nobs Step 1
        BB(k, 1) = BB(k, 1) + AA(k, l) * datanew(l, 1)
    Next l
Next k
bpass = BB
End Function

---

### Post by Zugzwang on 2010-10-08
Doesn't look too complicated.

Here is a high-level view of what to do:
[LIST]
[*]Think about where the "translated" function should be used. In your example, you have this data type "Range" which is non-standard. What is the [signature]("http://en.wikipedia.org/wiki/Method_signature") of the new function to write?
[*]Then, try to find out which data structures you want to use in C++ for this function.
[*]After these steps, translating won't look so hard anymore.
[/LIST]

---

