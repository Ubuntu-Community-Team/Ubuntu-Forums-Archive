---
title: "c# return statement"
date: 2011-11-30
forum: Programming Talk
---

### Post by Drenriza on 2011-11-30
Hi all.
 
I have a C# ASP.NET site where i run a methode
 
```
[FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]
protected[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]void[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] Page_Load([/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]object[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] sender, [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]EventArgs[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] e)
{
tbu.TableCreationOne(); [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]//this is to replace TableCreationOne
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]//TableCreationOne();
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]TableCreationAction();
}
[/SIZE][/FONT][/SIZE][/FONT]
```
the tbu.TableCreationOne(); has a return statement saying
```
return tb1;
```
tb1 = table1.
But when i return tb1 how do i "grab" it and add it to my form. In my "old" way i do it like this
```
[FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]
form1.Controls.Add(tb1);
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]
```
But here i don't return it from another class.
 
A little code dump. The "old" way of doing it.
```
[FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]
//public void TableCreationOne()
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]//{
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// //more information on forms visit: http://forums.devx.com/archive/index.php/t-99981.html
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// //Create the table
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// Table tb1 = new Table();
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// //Set table width
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// tb1.BorderWidth = 1;
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// //create tabel cells
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// TableRow row = new TableRow();
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// TableCell cell1 = new TableCell();
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// TableCell cell2 = new TableCell();
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// TableCell cell3 = new TableCell();
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// TableCell cell4 = new TableCell();
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// TableCell cell5 = new TableCell();
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// TableCell cell6 = new TableCell();
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// TableCell cell7 = new TableCell();
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// TableCell cell8 = new TableCell();
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// TableCell cell9 = new TableCell();
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// TableCell cell10 = new TableCell();
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// //Add cells to the row
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// row.Cells.Add(cell1);
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// row.Cells.Add(cell2);
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// row.Cells.Add(cell3);
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// row.Cells.Add(cell4);
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// row.Cells.Add(cell5);
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// row.Cells.Add(cell6);
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// row.Cells.Add(cell7);
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// row.Cells.Add(cell8);
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// row.Cells.Add(cell9);
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// row.Cells.Add(cell10);
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// tb1.Rows.Add(row);
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// //Set cells border width
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell1.BorderWidth = 1;
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell1.Style["Text-Align"] = "center";
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// //cell1.Width = 70;
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell1.Width = Unit.Pixel(70);
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell2.BorderWidth = 1;
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell2.Style["Text-Align"] = "center";
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// //cell2.Width = 250;
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell2.Width = Unit.Pixel(250);
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell3.BorderWidth = 1;
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell3.Style["Text-Align"] = "center";
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// //cell3.Width = 100;
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell3.Width = Unit.Pixel(100);
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell4.BorderWidth = 1;
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell4.Style["Text-Align"] = "center";
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// //cell4.Width = 70;
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell4.Width = Unit.Pixel(80);
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell5.BorderWidth = 1;
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell5.Style["Text-Align"] = "center";
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// //cell5.Width = 90;
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell5.Width = Unit.Pixel(90);
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell6.BorderWidth = 1;
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell6.Style["Text-Align"] = "center";
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// //cell6.Width = 70;
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell6.Width = Unit.Pixel(80);
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell7.BorderWidth = 1;
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell7.Style["Text-Align"] = "center";
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// //cell7.Width = 100;
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell7.Width = Unit.Pixel(100);
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell8.BorderWidth = 1;
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell8.Style["Text-Align"] = "center";
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// //cell8.Width = 200;
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell8.Width = Unit.Pixel(200);
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell9.BorderWidth = 1;
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell9.Style["Text-Align"] = "center";
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// //cell9.Width = 100;
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell9.Width = Unit.Pixel(100);
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell10.BorderWidth = 1;
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell10.Style["Text-Align"] = "center";
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// //cell10.Width = 100;
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell10.Width = Unit.Pixel(100);
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// //Add static content to the cells
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell1.Text = getAndSet._removed;
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell2.Text = getAndSet._removed;
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell3.Text = getAndSet._removed;
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell4.Text = getAndSet._removed;
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell5.Text = getAndSet._removed;
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell6.Text = getAndSet._removed;
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell7.Text = getAndSet._removed;
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell8.Text = getAndSet._removed;
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell9.Text = getAndSet._removed;
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// cell10.Text = getAndSet._removed;
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// //Add table to the page
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// form1.Controls.Add(tb1);
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]//}[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]
[FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT] 
[FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]the "new" way has replaced form1.controls.add(tb1) witn return tb1;
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]
```
 
Hope someone can help me. If you need more info, please don't hesitate to ask.
Also i would like to add. That i'm no C# expert at all, im learning. So i apologise for obivious mistakes.
 
Thanks on advance.
Kind regards.

---

### Post by CryptAck on 2011-11-30
I'm sorry, I'm having a difficult time in comprehending what you are attempting to achieve. 

If you are still using form1, you could do, 

form1.Controls.Add(tbu.TableCreationOne());

---

### Post by Drenriza on 2011-11-30
> **CryptAck said:**
> I'm sorry, I'm having a difficult time in comprehending what you are attempting to achieve. 
 
If you are still using form1, you could do, 
 
form1.Controls.Add(tbu.TableCreationOne());
 
Thanks, it does exactly what i was looking for.
I'm sorry if i wasn't crystal clear in my description of the problem.

---

### Post by CryptAck on 2011-11-30
> **Drenriza said:**
> Thanks, it does exactly what i was looking for.
I'm sorry if i wasn't crystal clear in my description of the problem.

Not a problem, I'm glad it works as expected! :)

---

### Post by Drenriza on 2011-11-30
I also have another issue, in the same area. These are two (for me) not major but bigger problems. Where now the first one was resolved :p
 
I have a class in my ASP.NET site, called listManagementClass. Where i wan't to keep all of my arrays and arraylists. I don't have a problem getting my Table, from my Form to my class and adding it to the correct ArrayList.
 
My problem is when i need to get the (multiple) Table / Tabels from the ArrayList in the listManagementClass.
 
At the moment i got the arraylists and the methode to get the Table in the arraylist in the same webform. So at the moment it works as such.
 
```
[FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]
[SIZE=2][FONT=Consolas][COLOR=#0000ff]static[/COLOR][/FONT][/SIZE][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]ArrayList[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] tableList = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]ArrayList[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]();[/SIZE][/FONT]
[/SIZE][/FONT]
```
```
[FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]
[SIZE=2][FONT=Consolas][COLOR=#0000ff]foreach[/COLOR][/FONT][/SIZE][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] (System.Web.UI.[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Control[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] i [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]in[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] tableList)[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]{[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]form1.Controls.Add(i);[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]}[/FONT][/SIZE]
[/SIZE][/FONT]
```
 
But when i take the
```
[FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]
[SIZE=2][FONT=Consolas][COLOR=#0000ff]static[/COLOR][/FONT][/SIZE][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]ArrayList[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] tableList = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]ArrayList[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]();[/SIZE][/FONT]
[/SIZE][/FONT]
```
and place it in another class, how do i then still call the content of the ArrayList?
 
Again, i try to explain my issue the best i can. If you find it fuzzy, or you don't understand how i want it to work or where im headed. Please dont hesitate to say so and i try to elaborate.
 
Thanks on advance.
Kind regards.
 
EDIT. Please not the foreach loop is part of a methode. If u need to se the entire methode, please say so and i will post it.

---

### Post by Petrolea on 2011-12-01
The easiest method would probably be to make a constructor in other class (where you want that arraylist to appear) and make it accept an arraylist as an argument. Then save that arraylist to a local variable in the second class.

It would look something like this (this is not correct code, I'm just trying to show you how it should look like)

Let's say you keep your data in arraylist named **one**

```

class second
{
    ArrayList **two** //this is where you want to store your data from arraylist **one**

    public second(ArrayList a) //constructor that takes Arraylist as an argument
    {
        two = a; //put contents of 'a' in 'two'
    }

}

```

Now to transfer the data:

```

//now the contents of arraylist **two** will be the same as arraylist **one**
second my_object = new second(**one**);

```

Hope I got the question right and that this will help :)

---

### Post by Drenriza on 2011-12-02
Hi Prtrolea.
 
Thanks for your reply. But from what i can see, you show how i can add my Table to my arraylist (which is in another class), but how do i "get it back"?
 
This was how i took my table and placed it in my arraylist before.
Create the table and call the methode to place it in arraylist
```

public[FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]partial[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]class[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]WebForm1[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] : System.Web.UI.[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Page << where TableCreationTwo reside.[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][SIZE=2][FONT=Consolas][COLOR=#0000ff][SIZE=2][FONT=Consolas][COLOR=#0000ff]public[/COLOR][/FONT][/SIZE][/COLOR][/FONT][/SIZE][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]void[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] TableCreationTwo()[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]//creates user defined tabels[/COLOR][/SIZE][/FONT]
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]{[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]//Create the table[/COLOR][/SIZE][/FONT]
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Table[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] tb2 = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Table[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]();[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]//Set table width[/COLOR][/SIZE][/FONT]
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]tb2.BorderWidth = 1;[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]//create tabel cells[/COLOR][/SIZE][/FONT]
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableRow[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] row = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableRow[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]();[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] cell1 = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]();[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] cell2 = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]();[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] cell3 = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]();[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] cell4 = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]();[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] cell5 = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]();[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] cell6 = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]();[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] cell7 = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]();[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] cell8 = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]();[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] cell9 = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]();[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] cell10 = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]();[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]//Add cells to the row[/COLOR][/SIZE][/FONT]
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]row.Cells.Add(cell1);[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]row.Cells.Add(cell2);[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]row.Cells.Add(cell3);[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]row.Cells.Add(cell4);[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]row.Cells.Add(cell5);[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]row.Cells.Add(cell6);[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]row.Cells.Add(cell7);[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]row.Cells.Add(cell8);[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]row.Cells.Add(cell9);[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]row.Cells.Add(cell10);[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]tb2.Rows.Add(row);[/FONT][/SIZE]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]//Set cells border width[/COLOR][/SIZE][/FONT]
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]cell1.BorderWidth = 1;[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]cell1.Style[[/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Text-Align"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]] = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"center"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]cell1.Width = [/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Unit[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].Pixel(70);[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]cell1.BackColor = [/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Color[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].PaleGoldenrod;[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]cell2.BorderWidth = 1;[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]cell2.Style[[/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Text-Align"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]] = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"center"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]cell2.Width = [/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Unit[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].Pixel(250);[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]cell2.BackColor = [/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Color[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].PaleGoldenrod;[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]cell3.BorderWidth = 1;[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]cell3.Style[[/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Text-Align"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]] = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"center"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]cell3.Width = [/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Unit[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].Pixel(100);[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]cell3.BackColor = [/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Color[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].PaleGoldenrod;[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]cell4.BorderWidth = 1;[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]cell4.Width = [/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Unit[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].Pixel(80);[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]cell4.Style[[/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Text-Align"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]] = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"center"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]cell4.BackColor = [/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Color[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].PaleGoldenrod;[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]cell5.BorderWidth = 1;[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]cell5.Width = [/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Unit[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].Pixel(90);[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]cell5.Style[[/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Text-Align"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]] = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"center"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]cell5.BackColor = [/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Color[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].PaleGoldenrod;[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]cell6.BorderWidth = 1;[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]cell6.Style[[/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Text-Align"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]] = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"center"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]cell6.Width = [/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Unit[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].Pixel(80);[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]cell6.BackColor = [/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Color[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].PaleGoldenrod;[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]cell7.BorderWidth = 1;[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]cell7.Style[[/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Text-Align"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]] = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"center"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]cell7.Width = [/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Unit[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].Pixel(100);[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]cell7.BackColor = [/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Color[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].PaleGoldenrod;[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]cell8.BorderWidth = 1;[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]cell8.Style[[/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Text-Align"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]] = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"center"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]cell8.Width = [/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Unit[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].Pixel(200);[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]cell8.BackColor = [/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Color[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].PaleGoldenrod;[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]cell9.BorderWidth = 1;[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]cell9.Style[[/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Text-Align"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]] = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"center"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]cell9.Width = [/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Unit[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].Pixel(100);[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]cell9.BackColor = [/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Color[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].PaleGoldenrod;[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]cell10.BorderWidth = 1;[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]cell10.Style[[/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Text-Align"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]] = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"center"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]cell10.Width = [/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Unit[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].Pixel(100);[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]cell10.BackColor = [/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Color[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].PaleGoldenrod;[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]//Add static content to the cells[/COLOR][/SIZE][/FONT]
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]cell1.Text = getAndSet.CellOne;[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]cell2.Text = getAndSet.CellTwo;[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]cell3.Text = getAndSet.CellThree;[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]cell4.Text = getAndSet.CellFour;[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]cell5.Text = getAndSet.CellFive;[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]cell6.Text = getAndSet.CellSix;[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]cell7.Text = getAndSet.CellSeven;[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]cell8.Text = getAndSet.CellEight;[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]cell9.Text = getAndSet.CellNine;[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]cell10.Text = getAndSet.CellTeen;[/FONT][/SIZE]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]//Add table to arraylist[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]
[FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]lmc.addToTableList(tb2);[/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]}[/SIZE][/FONT]
[/SIZE][/FONT]
```
 
[FONT=Consolas][SIZE=2]addToTableList methode.[/SIZE][/FONT]
```

[SIZE=2][FONT=Consolas][COLOR=#0000ff][SIZE=2][FONT=Consolas][COLOR=#0000ff][SIZE=2][FONT=Consolas][COLOR=#0000ff]public[/COLOR][/FONT][/SIZE][/COLOR][/FONT][/SIZE][/COLOR][/FONT][/SIZE][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]class[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]ListManagmentClass[/COLOR][/SIZE][/FONT]
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]{[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]public[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]static[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]ArrayList[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] tableList = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]ArrayList[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]();[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]public [/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]void[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] addToTableList([/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Table[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] x)[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]{[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]tableList.Add(x);[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]}[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]}[/FONT][/SIZE]
[/SIZE][/FONT]
```
 
But my issue was, when i later call the following methode, which is in another class then the ListManagmentClass. I codent figure out how to get the Table,s back and add them to form 1. As seen in the bottom of the methode in the foreach loop.
 
```
 
[SIZE=2][FONT=Consolas][COLOR=#0000ff][SIZE=2][FONT=Consolas][COLOR=#0000ff][SIZE=2][FONT=Consolas][COLOR=#0000ff]public[/COLOR][/FONT][/SIZE][/COLOR][/FONT][/SIZE][/COLOR][/FONT][/SIZE][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]void[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] TableCreationAction()[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]{[/FONT][/SIZE]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]if[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] (![/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]File[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].Exists(getAndSet.PathOne))[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]{[/FONT][/SIZE]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]using[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] ([/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]FileStream[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] fs = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]File[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].Create(getAndSet.PathOne)) { }[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]}[/FONT][/SIZE]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]int[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] Num = 1;[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]using[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] ([/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]StreamReader[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] sr = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]StreamReader[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2](getAndSet.PathOne))[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]{[/FONT][/SIZE]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]while[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] (sr.Peek() >= 0)[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]{[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]getAndSet.Lala = sr.ReadLine();[/FONT][/SIZE]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]String[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][] lines = getAndSet.Lala.Split([/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]'#'[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]);[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]tableListTwo.Add(lines);[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]}[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]}[/FONT][/SIZE]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]foreach[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] ([/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]String[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][] line [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]in[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] tableListTwo)[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]{[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]getAndSet.CellOne = line[0];[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]getAndSet.CellTwo = line[1];[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]getAndSet.CellThree = line[2];[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]getAndSet.CellFour = line[3];[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]getAndSet.CellFive = line[4];[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]getAndSet.CellSix = line[5];[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]getAndSet.CellSeven = line[6];[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]getAndSet.CellEight = line[7];[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]getAndSet.CellNine = line[8];[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]getAndSet.CellTeen = line[9];[/FONT][/SIZE]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]if[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] (Num % 2 == 0)[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]//modulus forklaring http://en.wikipedia.org/wiki/Modulo_operation[/COLOR][/SIZE][/FONT]
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]{[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]TableCreationTwo();[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]}[/FONT][/SIZE]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]else[/COLOR][/SIZE][/FONT]
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]{[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]TableCreationThree();[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]}[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]Num++;[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]}[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]Num = 0;[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]tableListTwo.Clear();[/FONT][/SIZE]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]foreach[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] (System.Web.UI.[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Control[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] i [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]in[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] tableList)[/SIZE][/FONT]
[SIZE=2][FONT=Consolas]{[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]form1.Controls.Add(i);[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]}[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]tableList.Clear();[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]}[/FONT][/SIZE][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]//tableCreationAction Ends[/COLOR][/SIZE][/FONT]
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]
```
 
Hope it makes sense, or else please tell me :D thanks all.

---

### Post by Petrolea on 2011-12-02
I would have to see how you built your code to be able to tell you how to take the tables back and forth.

Can you show the problem whit some kind of pseudo-code? I don't understand the question, is the problem moving table between classes or what?

---

### Post by Drenriza on 2011-12-02
```
is the problem moving table between classes or what?
```
Short answer yes.
 
Long answer.
I can get the Table from the first class and into the arraylist in another class. But i have trouble getting the Table back. And add it to form1. Because the arraylist contains multiple tabels. Which all needs to be added to [FONT=Consolas][SIZE=2]form1.Controls[/SIZE][/FONT]

---

### Post by Petrolea on 2011-12-03
> **Drenriza said:**
> ```
is the problem moving table between classes or what?
```
Short answer yes.
 
Long answer.
I can get the Table from the first class and into the arraylist in another class. But i have trouble getting the Table back. And add it to form1. Because the arraylist contains multiple tabels. Which all needs to be added to [FONT=Consolas][SIZE=2]form1.Controls[/SIZE][/FONT]

Ah I think I get it now. That's very easy to achieve. Use get/set methods and you can call those ArrayLists like variables, for example: FirstClass.MyTable1 = something;

Otherwise you'd have to make functions to save them for you.

```

class One
{
    double x;
    public double X 
    {
            get { return x; }
            set { x = value; }
    }
}

```

Now when you create your object, you set variables like this:

```

One my_object = new One();
my_object.X = 35.223;

```

Same thing can be done with ArrayLists.

---

### Post by Drenriza on 2011-12-03
So i thought about what you sayd. And tryed working from a new point of view (noob detection).
 
And i figured out something like this, it seams to work but is it the "correct" way of doing it, or is their a better way.
 
_**Please note. Im not sure i understod above post 100%.**_
 
Adding table to arraylist
```
[FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]
public[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]void[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] TableCreationTwo()[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]//creates user defined tabels
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]{
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]//Create the table
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Table[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] tb2 = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Table[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]();
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]//Set table width
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]tb2.BorderWidth = 1;
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]//create tabel cells
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableRow[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] row = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableRow[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]();
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] cell1 = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]();
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] cell2 = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]();
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] cell3 = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]();
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] cell4 = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]();
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] cell5 = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]();
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] cell6 = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]();
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] cell7 = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]();
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] cell8 = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]();
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] cell9 = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]();
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] cell10 = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]TableCell[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]();
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]//Add cells to the row
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]row.Cells.Add(cell1);
row.Cells.Add(cell2);
row.Cells.Add(cell3);
row.Cells.Add(cell4);
row.Cells.Add(cell5);
row.Cells.Add(cell6);
row.Cells.Add(cell7);
row.Cells.Add(cell8);
row.Cells.Add(cell9);
row.Cells.Add(cell10);
tb2.Rows.Add(row);
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]//Set cells border width
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]cell1.BorderWidth = 1;
cell1.Style[[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Text-Align"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]] = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"center"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];
cell1.Width = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Unit[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].Pixel(70);
cell1.BackColor = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Color[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].PaleGoldenrod;
cell2.BorderWidth = 1;
cell2.Style[[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Text-Align"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]] = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"center"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];
cell2.Width = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Unit[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].Pixel(250);
cell2.BackColor = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Color[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].PaleGoldenrod;
cell3.BorderWidth = 1;
cell3.Style[[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Text-Align"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]] = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"center"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];
cell3.Width = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Unit[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].Pixel(100);
cell3.BackColor = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Color[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].PaleGoldenrod;
cell4.BorderWidth = 1;
cell4.Width = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Unit[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].Pixel(80);
cell4.Style[[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Text-Align"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]] = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"center"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];
cell4.BackColor = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Color[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].PaleGoldenrod;
cell5.BorderWidth = 1;
cell5.Width = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Unit[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].Pixel(90);
cell5.Style[[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Text-Align"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]] = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"center"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];
cell5.BackColor = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Color[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].PaleGoldenrod;
cell6.BorderWidth = 1;
cell6.Style[[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Text-Align"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]] = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"center"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];
cell6.Width = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Unit[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].Pixel(80);
cell6.BackColor = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Color[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].PaleGoldenrod;
cell7.BorderWidth = 1;
cell7.Style[[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Text-Align"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]] = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"center"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];
cell7.Width = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Unit[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].Pixel(100);
cell7.BackColor = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Color[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].PaleGoldenrod;
cell8.BorderWidth = 1;
cell8.Style[[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Text-Align"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]] = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"center"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];
cell8.Width = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Unit[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].Pixel(200);
cell8.BackColor = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Color[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].PaleGoldenrod;
cell9.BorderWidth = 1;
cell9.Style[[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Text-Align"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]] = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"center"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];
cell9.Width = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Unit[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].Pixel(100);
cell9.BackColor = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Color[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].PaleGoldenrod;
cell10.BorderWidth = 1;
cell10.Style[[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Text-Align"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]] = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"center"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];
cell10.Width = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Unit[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].Pixel(100);
cell10.BackColor = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Color[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].PaleGoldenrod;
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]//Add static content to the cells
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]cell1.Text = getAndSet.CellOne;
cell2.Text = getAndSet.CellTwo;
cell3.Text = getAndSet.CellThree;
cell4.Text = getAndSet.CellFour;
cell5.Text = getAndSet.CellFive;
cell6.Text = getAndSet.CellSix;
cell7.Text = getAndSet.CellSeven;
cell8.Text = getAndSet.CellEight;
cell9.Text = getAndSet.CellNine;
cell10.Text = getAndSet.CellTeen;
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]//Add table to arraylist[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]
lmc.addToTableList(tb2); //<<<< calls methode
}
[/SIZE][/FONT][/SIZE][/FONT]
```
 
```
[FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]
public[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]class[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]ListManagmentClass
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]{
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]public[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]static[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]ArrayList[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] tableList = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]ArrayList[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]();
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]public[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]void[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] addToTableList([/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Table[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] x)
{
tableList.Add(x);
}[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]
}
[/SIZE][/FONT][/SIZE][/FONT]
```
 
Now towards getting the table back to the other class.
```
[FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]
System.Collections.[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]ArrayList[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] something = lmc.returnTablelist();
[/SIZE][/FONT][/SIZE][/FONT]
```
calls
```
[FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]
public[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]class[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]ListManagmentClass
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]{[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]public[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] System.Collections.[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]ArrayList[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] returnTablelist()
{
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]return[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] tableList;
}
}
[/SIZE][/FONT][/SIZE][/FONT]
```
adding to form1
```
[FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]
foreach[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] (System.Web.UI.WebControls.[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Table[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] p [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]in[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] something)
{
form1.Controls.Add(p);
}
[/SIZE][/FONT][/SIZE][/FONT]
```
 
But is their a better way of doing it?
 
Thanks all.

---

### Post by Petrolea on 2011-12-03
That's pretty much I had in mind. But with using get/set it's very easy to move the table between classes, you don't have to use any methods for returning values, you just call it like it was a public variable.

```

class One
{
    //table creation methods and other stuff
    Table first;

    public Table First
    {
        get { return first; }
        set { first = value; }
    }
}

class Two
{
    One my_object = new One();
    
    Table second; //you want your table here
    second = my_object.First; //table second gets data from first table

    //now the reverse operation
    my_object.First = second; //transfer data from table second to first
}

```

Hope this explains it.

---

### Post by Drenriza on 2011-12-04
Thanks guys, i worked out my two issues.
 
Kind regards.

---

