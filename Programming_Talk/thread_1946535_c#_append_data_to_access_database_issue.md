---
title: "c# append data to access database issue"
date: 2012-03-25
forum: Programming Talk
---

### Post by fullyunknown on 2012-03-25
Hello and thanks a head of time.

I just recently started learning C#. In Access Database I had a form where i clicked a button and slected my excel file and imported the results to a table called "tblBillingsData"

This table has a primary key called billingID. This ID is generated somewhere else and exported into the excel spreadsheet i am importing. Well sometimes when i download this data from the other source i might be downloading something i have already imported into my table "tblBillingsData" Well in VBA doing the

Docmd.Setwarnings False

would allow me to append the excel spreadsheet data into the table and every key violation would just not append. With c# though, when i try and append and it gets to a key violation, the catch statement stops the append process to tell me about the error and will not continue on with appending the data.

How do i get the below code to keep appending the data and not caring about the error that is popping up saying key violation?
```

OleDbDataReader dataReaderExcel = cmdExcel.ExecuteReader();
            try
            {
                while (dataReaderExcel.Read())
                {
                    //Assign all your values to the access command parameters
                    param1.Value = dataReaderExcel[0].ToString();
                    param2.Value = dataReaderExcel[1].ToString();
                    param3.Value = dataReaderExcel[2].ToString();
                    param4.Value = dataReaderExcel[3].ToString();
                    param5.Value = dataReaderExcel[4].ToString();
                    param6.Value = dataReaderExcel[5].ToString();
                    param7.Value = dataReaderExcel[6].ToString();
                    param8.Value = dataReaderExcel[7].ToString();
                    param9.Value = dataReaderExcel[8].ToString();
                    param10.Value = dataReaderExcel[9].ToString();
                    param11.Value = dataReaderExcel[10].ToString();
                    param12.Value = Left(dataReaderExcel[4].ToString(), 5);
                    
                    string x = Right(dataReaderExcel[4].ToString(), 3);
                    param13.Value = x.Replace("/","");
                    
                    double amount = double.Parse(dataReaderExcel[3].ToString()) * -1;
                    param14.Value = amount.ToString();
                    
                    if (Left(dataReaderExcel[4].ToString(), 1) == "9")
                        param15.Value = -1;
                    else
                        param15.Value = 0;
                    //Insert all the values into access
                    cmdAccess.ExecuteNonQuery();
                    
                }
            
            }
            catch (Exception ex)
            {

               
                    Console.WriteLine(ex.Message);
                    //return false;
       
            }

```

---

