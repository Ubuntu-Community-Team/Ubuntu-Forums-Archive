---
title: "Performing A Silly Logic In Gambas?"
date: 2011-08-09
forum: Programming Talk
---

### Post by etdsbastar on 2011-08-09
Hello friends,

I stuck in a simple coding in one project.  Actually I want to put a fine of 10% if the Tax Payment exceeds the  current financial year (i.e. 31st March).

For example:

Today is 09th of August 2011

If  someone pays the tax payment on 1st of April 2012 or on any above date  then I want to apply a surcharge of 10% on per year basis. Same will do for next year and so on...

How to do it.

Please help.

---

### Post by etdsbastar on 2011-08-09
anybody please help...

---

### Post by Arndt on 2011-08-09
> **etdsbastar said:**
> Hello friends,

I stuck in a simple coding in one project.  Actually I want to put a fine of 10% if the Tax Payment exceeds the  current financial year (i.e. 31st March).

For example:

Today is 09th of August 2011

If  someone pays the tax payment on 1st of April 2012 or on any above date  then I want to apply a surcharge of 10% on per year basis. Same will do for next year and so on...

How to do it.

Please help.

Apart from the fine, what does the program actually do? What is the input, and what is the output?

---

### Post by etdsbastar on 2011-08-09
Thanks for the reply.

Its just a financial year calculation of Tax (1st April) to (31st March) of any Financial year. I just want to add a % of tax to the payments which are paid after 31st March of current financial year.

Here is the sample code which I wrote:

```
PUBLIC SUB txtPaymentAmount_LostFocus()

  DIM finEndDay, finEndMonth, finEndYear AS Integer
  DIM dtVal AS String
  DIM finEndDate AS Date
  
  finEndDay = 1
  finEndMonth = 4
  finEndYear = Year(Now) 
  
  dtVal = finEndDay & "/" & finEndMonth & "/" & finEndYear
  
  finEndDate = Support.StringToDate(dtVal, FALSE)
  
  IF CDate(txtPaymentDate.Text) < finEndDate THEN 
    lblAmtAfterLateFee.Caption = CFloat(txtPaymentAmount.Text) * (CFloat(Support.GetConfigValue("Settings/lf", 6.25)) / 100)
  ELSE 
    lblAmtAfterLateFee.Caption = "0.00"
  ENDIF 
  
CATCH 
END
```

But the above code is not working properly.

---

### Post by etdsbastar on 2011-08-09
If anyone wants more information please intimate.

---

### Post by Arndt on 2011-08-10
> **etdsbastar said:**
> Thanks for the reply.

Its just a financial year calculation of Tax (1st April) to (31st March) of any Financial year. I just want to add a % of tax to the payments which are paid after 31st March of current financial year.

Here is the sample code which I wrote:

```
PUBLIC SUB txtPaymentAmount_LostFocus()

  DIM finEndDay, finEndMonth, finEndYear AS Integer
  DIM dtVal AS String
  DIM finEndDate AS Date
  
  finEndDay = 1
  finEndMonth = 4
  finEndYear = Year(Now) 
  
  dtVal = finEndDay & "/" & finEndMonth & "/" & finEndYear
  
  finEndDate = Support.StringToDate(dtVal, FALSE)
  
  IF CDate(txtPaymentDate.Text) < finEndDate THEN 
    lblAmtAfterLateFee.Caption = CFloat(txtPaymentAmount.Text) * (CFloat(Support.GetConfigValue("Settings/lf", 6.25)) / 100)
  ELSE 
    lblAmtAfterLateFee.Caption = "0.00"
  ENDIF 
  
CATCH 
END
```

But the above code is not working properly.

So what happens instead?

---

### Post by etdsbastar on 2011-08-11
The problem has been solved with the following code:

```
PRIVATE FUNCTION CalculateTax(amount AS Float) AS Float
  
  DIM $Fiscal AS String
  DIM $FiscalStart AS String
  DIM iDateDiff AS Integer
  DIM iDateDiffStart AS Integer
  DIM iYearDiff AS Integer
  DIM iYearDiffStart AS Integer

  $Fiscal = Date(Year(Now) + 1, 03, 31)
  $FiscalStart = Date(Year(Now), 04, 01)

  iDateDiff = DateDiff($Fiscal, CDate(txtPaymentDate.Text), gb.Day)

  IF iDateDiff > 0 THEN 
    amount = CFloat(txtPaymentAmount.Text) * (CFloat(Support.GetConfigValue("Settings/lf", 6.25)) / 100)
    IF Year(CDate(txtPaymentDate.Text)) > Year(Now) THEN 
      iYearDiff = Year(CDate(txtPaymentDate.Text)) - Year(Now)
      amount = amount * iYearDiff
    ELSE 
      amount = CFloat(txtPaymentAmount.Text) * (CFloat(Support.GetConfigValue("Settings/lf", 6.25)) / 100)
    ENDIF
  ELSE 
    IF Year(CDate(txtPaymentDate.Text)) < Year(Now) THEN 
      amount = CFloat(txtPaymentAmount.Text) * (CFloat(Support.GetConfigValue("Settings/lf", 6.25)) / 100)
      iYearDiffStart = Abs(Year(CDate(txtPaymentDate.Text)) - Year($FiscalStart))
      amount = amount * iYearDiffStart
    ELSE 
      amount = 0
    ENDIF 
  ENDIF 
  
  RETURN amount
  
END
```

Please suggest any corrections or modifications if needed.

---

