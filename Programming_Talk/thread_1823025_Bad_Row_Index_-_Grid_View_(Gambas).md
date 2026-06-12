---
title: "Bad Row Index - Grid View (Gambas)"
date: 2011-08-11
forum: Programming Talk
---

### Post by etdsbastar on 2011-08-11
Hi,

I am programming in Gambas for my Visual Basic needs. I stuck in the code given below which is giving me bad row index error. Please anyone help me to resolve this issue:

```
PUBLIC SUB loadData()
  DIM i AS Integer, rst AS Result
  TRY rst = Support.myDB.Exec("select * from taxdetails where demandno=&1", txtDemandNo.Text)
  
  WITH gvPayments
    .Clear
    .Columns.Count = 5
    .Columns[0].Width = 70
    .Columns[0].Title = "S. No."
    .Columns[1].Width = 100
    .Columns[1].Title = "D. No."
    .Columns[2].Width = 120
    .Columns[2].Title = "Date"
    .Columns[3].Width = 120
    .Columns[3].Title = "Amount"
    .Columns[4].Width = 120
    .Columns[4].Title = "Late Fee"
  END WITH 

  FOR i = 0 TO rst.Max
    gvPayments[i, 0].Text = rst!id
    gvPayments[i, 1].Text = rst!demandno
    gvPayments[i, 2].Text = rst!date
    gvPayments[i, 3].Text = rst!amount
    gvPayments[i, 4].Text = rst!latefee
    rst.MoveNext
  NEXT 

CATCH 
  Message.Error("Unable to open table\n" & Error.Text & "\n" & Error.Where)
END
```

---

