---
title: "Sql: how much alike are two strings."
date: 2008-11-25
forum: Programming Talk
---

### Post by alek66 on 2008-11-25
I am trying to make a fucntion to compare two strings and see how much alike are the (levenshtein alg)

I found this one that was for mssql, but I dont know how to export it so I can use it in mysql.

I just want to compare two string and find tiping mistakes like "
banana" and "nanana" and the function returns a value thata makes me see that that might be the same word but with a tiping mistake.

I Used the levenshtein php function, using the hole list of words using a query but its too slow, and after 30segs i get a Maximum execution time of 30 seconds exceeded

so hope i can get some help
```
Public Function Similarity(FirstValue As Variant, SecondValue As Variant) As   
Single  
  
    Dim FArray() As String, SArray() As String  
    Dim intCounter As Integer, intMatches As Integer  
    Dim intLoop1 As Integer, intLoop2 As Integer  
      
    If IsNull(FirstValue) Or IsNull(SecondValue) Then  
        Similarity = 0  
        Exit Function  
    ElseIf FirstValue = SecondValue Then  
        Similarity = 99  
        Exit Function  
    End If  
      
    FArray() = Split(FirstValue, " ")  
    SArray() = Split(SecondValue, " ")  
      
    For intLoop1 = LBound(FArray) To UBound(FArray)  
        For intLoop2 = LBound(SArray) To UBound(SArray)  
            intCounter = intCounter + 1  
            If FArray(intLoop1) = SArray(intLoop2) Then  
                intMatches = intMatches + 2  
            ElseIf InStr(FArray(intLoop1), SArray(intLoop2)) > 0 Then  
                intMatches = intMatches + 1  
            ElseIf InStr(SArray(intLoop2), FArray(intLoop1)) > 0 Then  
                intMatches = intMatches + 1  
            End If  
        Next intLoop2  
    Next intLoop1  
      
    Similarity = IIf(intCounter = 0, 0, CSng(intMatches) / CSng(intCounter))  
      
End Function   
```

---

### Post by drubin on 2008-11-25
What data base server are you using? 

mysql supports [sounds like]("http://dev.mysql.com/doc/refman/5.0/en/string-functions.html#operator_sounds-like")

---

