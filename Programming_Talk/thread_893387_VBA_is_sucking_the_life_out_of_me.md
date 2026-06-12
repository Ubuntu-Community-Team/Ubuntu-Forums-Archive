---
title: "VBA is sucking the life out of me"
date: 2008-08-18
forum: Programming Talk
---

### Post by lordhaworth on 2008-08-18
Hey all

Im using VBA to display the dates of the first of the month for a number of months determined by the user. This is not a problem, The rather embarresing trouble I am actually having is with my nested DO loop! It wont stop running despite trying different VBA DO and FOR styles... here is my code (ps i know the code in the middle of this is bad but thats because if I correct it my computer feels the effects of a never ending do loop in Excel - and dies)


```

Public Sub Auto_Date()
Dim x, i, j, Default, months_req, temporary As Integer
Dim Title As String
Dim Start, Ending As Date

 Message = "Enter a value between 1 and 6"    ' Set prompt.
    Title = "How many months required?"    ' Set title.
    Default = "3"    ' Set default.
    months_req = InputBox(Message, Title, Default, 800, 500)
    On Error GoTo errorhandler
     If months_req > 6 Or months_req < 1 Then months_req = 3 'error trap
    Application.ScreenUpdating = False
    
i = 1

Do While (i <= months_req)

    j = 1
        Do While (j <= 4)
    
            If (j = 2 And i = 1) Then
            Cells(j, i).FormulaR1C1 = "=DATE(YEAR(TODAY()),MONTH(TODAY()), 1)"
            End If
            
            If (j = 2 And i > 1) Then
            Cells(j, i) = "=R[-1]C[1]"
            End If
        
            If (j = 3) Then
            Cells(j, i).FormulaR1C1 = "=DATE(YEAR(RC[-1]), MONTH(RC[-1]) + 1, 1)"
            End If
            
            Cells(10, i) = i
            Cells(11, i) = j
            
            j = j + 1

            Loop
    i = i + 1
Loop


errorhandler:
    Exit Sub


End Sub

```

The reason I use a nested loop is to print the dates row by row. There will eventually be 4 columns but at the moment I am focusing on just the middle 2.

Again the only problem I have with this at the mo is that the loops wont stop. 

This bit of code

```

Cells(10, i) = i
Cells(11, i) = j

```

I put in to display the values of i and j... according to this i increases (1, 2, 3, 4, 5...) whereas j is always equal to 4! (4, 4, 4, 4, 4 ...)

What is up!?!?! im hardly the best programmer, but not exactly new - Ive not had trouble like this with a loop afor a long while!

Cheers in advance

Tom

---

### Post by ghostdog74 on 2008-08-18
put some debug.print statements in various places to actually see what's going on.

---

### Post by lordhaworth on 2008-08-18
Ok this is strange, I put in 
```

Debug.Print j
Debug.Print i

```

And get 

 1 
 255 
 2 
 255 
 3 
 255 
 4 
 255 
 1 
 256 
 2 
 256 
 3 
 256 
 4 
 256 
 1 
 257 

Etc... 

however the lines directly beneath
```

Debug.Print j
Debug.Print i
Cells(10, i) = i
Cells(11, i) = j

```
Still give
1, 2, 3, 4, 5, 6, 7, 8, 9, 10 ...
4, 4, 4, 4, 4, 4, 4, 4, 4, 4

---

### Post by ghostdog74 on 2008-08-18
show where you put those debug statements!

---

### Post by lordhaworth on 2008-08-18
Sorry i thought id implied it with my second code quote in my last post - heres the whole lot again


> 
Public Sub Auto_Date()
Dim x, i, j, Default, months_req, temporary As Integer
Dim Title As String
Dim Start, Ending As Date

 Message = "Enter a value between 1 and 6"    ' Set prompt.
    Title = "How many months required?"    ' Set title.
    Default = "3"    ' Set default.
    months_req = InputBox(Message, Title, Default, 800, 500)
    On Error GoTo errorhandler
     If months_req > 6 Or months_req < 1 Then months_req = 3 'error trap
    Application.ScreenUpdating = False 'use to prevent eyes strain refreshes after all done
    
i = 1

Do While (i <= months_req)

    j = 1
        Do While (j <= 4)
    
            If (j = 2 And i = 1) Then
            Cells(j, i).FormulaR1C1 = "=DATE(YEAR(TODAY()),MONTH(TODAY()), 1)"
            End If

            If (j = 2 And i > 1) Then
            Cells(j, i) = "=R[-1]C[1]"
            End If
        
            If (j = 3) Then
            Cells(j, i).FormulaR1C1 = "=DATE(YEAR(RC[-1]), MONTH(RC[-1]) + 1, 1)"
            End If
            
            Debug.Print j
            Debug.Print i
            Cells(10, i) = i
            Cells(11, i) = j
            
            j = j + 1

        Loop

    i = i + 1
Loop



errorhandler:
    Exit Sub


End Sub


Thanks

---

### Post by lordhaworth on 2008-08-18
For those interested it somehow works now, it seems you cant nest a do loop in a do loop in VBA. I did a Do loop within a FOR loop and it worked

```

Public Sub Auto_Date()
Dim x, i, j, Default, months_req, temporary As Integer
Dim Title As String
Dim Start, Ending As Date

 Message = "Enter a value between 1 and 6"    ' Set prompt.
    Title = "How many months required?"    ' Set title.
    Default = "3"    ' Set default.
    months_req = InputBox(Message, Title, Default, 800, 500)
    On Error GoTo errorhandler
     If months_req > 6 Or months_req < 1 Then months_req = 3 'error trap
    Application.ScreenUpdating = False 'use to prevent eyes strain refreshes after all done
    
    Debug.Print months_req
    
i = 1

For i = 1 To months_req
    j = 1
        Do While j <= 4
        
            If (j = 1 And i = 1) Then
            Cells(i, j).NumberFormat = "General"
            Cells(i, j).FormulaR1C1 = "=DATE(YEAR(TODAY()),MONTH(TODAY()), 1)"
            End If
            
            If (j = 1 And i > 1) Then
            Cells(i, j).NumberFormat = "General"
            Cells(i, j) = "=R[-1]C[+3]"
            End If
            
            If (j = 2 And i = 1) Then
            Cells(i, j).NumberFormat = "dd/mm/yyyy"
            Cells(i, j).FormulaR1C1 = "=DATE(YEAR(TODAY()),MONTH(TODAY()), 1)"
            End If

            If (j = 2 And i > 1) Then
            Cells(i, j).NumberFormat = "dd/mm/yyyy"
            Cells(i, j) = "=R[-1]C[1]"
            End If
        
            If (j = 3) Then
            Cells(i, j).NumberFormat = "dd/mm/yyyy"
            Cells(i, j).FormulaR1C1 = "=DATE(YEAR(RC[-1]), MONTH(RC[-1]) + 1, 1)"
            End If
            
            If (j = 4) Then
            Cells(i, j).NumberFormat = "General"
            Cells(i, j) = "=R[1]C[-1]"
            End If
            
            j = j + 1
        Loop

    Next i



errorhandler:
    Exit Sub


End Sub


```


One more piece of advice, get away from VBA - far away

---

### Post by ghostdog74 on 2008-08-18
convert your months_req to integer
```
months_req = CInt(InputBox(Message, Title, Default, 800, 500))

```

---

### Post by ghostdog74 on 2008-08-18
> **lordhaworth said:**
> 

One more piece of advice, get away from VBA - far away

i beg to differ. Its has its uses.

---

### Post by grenyg on 2008-08-18
When you declare:
Dim x, i, j, Default, months_req, temporary As Integer

Only "temporary" is declared as Integer, the others will be of type Variant. The problem is where you compare a string to an integer.

---

### Post by lordhaworth on 2008-08-18
Thanks all, at least the true nature of the problem is now known!
Well... a lot of the problem is my inexperience with vba

> Quote:
Originally Posted by lordhaworth  

One more piece of advice, get away from VBA - far away 

i beg to differ. Its has its uses. 

Fair enough - I have got it to do some cool things in the past. However there has not been a single project Ive done with VBA where ive thought things just seem fairly stupid making life, and learning the language, difficult. I

---

