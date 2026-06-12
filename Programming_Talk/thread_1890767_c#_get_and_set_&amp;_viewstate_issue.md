---
title: "c# get and set &amp; viewstate issue"
date: 2011-12-04
forum: Programming Talk
---

### Post by Drenriza on 2011-12-04
Hi all.
 
I am working on a ASP.NET site, where i have some trouble with some of my get and set methodes.
 
I currently have 3 classes, to seperate the different methodes and to give a good overview.
 
In my WebForm1.aspx.cs class i add my values to my get and set
```

[SIZE=2][FONT=Consolas][COLOR=#0000ff][SIZE=2][FONT=Consolas][COLOR=#0000ff][SIZE=2][FONT=Consolas][COLOR=#0000ff]foreach[/COLOR][/FONT][/SIZE][/COLOR][/FONT][/SIZE][/COLOR][/FONT][/SIZE][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] ([/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]String[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][] line [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]in[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] tableListTwo)[/SIZE][/FONT]
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
[/SIZE][/FONT]
```
 
And the values get added to the get and set, no trouble so far.
```

[SIZE=2][FONT=Consolas][COLOR=#0000ff][SIZE=2][FONT=Consolas][COLOR=#0000ff][SIZE=2][FONT=Consolas][COLOR=#0000ff]public[/COLOR][/FONT][/SIZE][/COLOR][/FONT][/SIZE][/COLOR][/FONT][/SIZE][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]String[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] _CellOne = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Removed"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]public[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]String[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] _CellTwo = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Removed"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]public[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]String[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] _CellThree = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Removed"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]public[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]String[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] _CellFour = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Removed"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]public[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]String[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] _CellFive = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Removed"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]public[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]String[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] _CellSix = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Removed"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]public[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]String[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] _CellSeven = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Removed"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]public[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]String[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] _CellEight = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Removed"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]public[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]String[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] _CellNine = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Removed"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];[/SIZE][/FONT]
[/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]public[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]String[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] _CellTeen = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Removed"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];[/SIZE][/FONT]
[/SIZE][/FONT]
```
 
The problem is when i call for the values. Then i don't get the value that i've added to the get and set. I get the static value "Removed"
 
For example i add the value 2, to _CellOne, but i retrive the value Removed.
 
```

[SIZE=2][FONT=Consolas][SIZE=2][FONT=Consolas]cell1.Text = getAndSet.CellOne;[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]cell2.Text = getAndSet.CellTwo;[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]cell3.Text = getAndSet.CellThree;[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]cell4.Text = getAndSet.CellFour;[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]cell5.Text = getAndSet.CellFive;[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]cell6.Text = getAndSet.CellSix;[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]cell7.Text = getAndSet.CellSeven;[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]cell8.Text = getAndSet.CellEight;[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]cell9.Text = getAndSet.CellNine;[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]cell10.Text = getAndSet.CellTeen;[/FONT][/SIZE]
[/FONT][/SIZE]
```
 
Is this because i need to use a viewstate to save the values in? For some reason they get lost when retrived them into a different class then the WebForm1.aspx.cs class.
 
Hope you understand what i mean. I am not a C# shark ,) im quite new at it.
 
If their is something that sounds fuzzy, please dont hesitate to ask and i will try to elaborate.
 
Thanks all on advance.
Kind regards.
 
Edit.
is their someone who can explain to me when to use a viewstate and when to use a get and set methode?
 
Edit 2.
Well i have read a little up on what a viewstate is. So my question is more focused on. When i from my page.aspx.cs file, add a value to a get&set methode in a C# class. And then call that same value to another C# class, why do i then "loose" the value. Resulting in getting the static value, when i defined the get&set methode. And how can i prevent "loosing" the value?

---

### Post by Drenriza on 2011-12-04
No one? :( :)

---

### Post by Petrolea on 2011-12-04
The problem might occur in two places:

1. When you put strings into cells with your foreach loop
2. When you try to retrieve them with get statement. You might return a wrong value and that's why you get that weird string over and over again.

Please tell me if the values of cells are correct right after the foreach part.

---

### Post by Drenriza on 2011-12-04
> Please tell me if the values of cells are correct right after the foreach part.
 
Right after the foreach loop (to where i place the value inside the get&set methode) the values in the get&set are correct. But when i leave the
 
Form1.aspx.cs class and try to retrive the values in another xxxx.cs i get the wrong value. Meaning i get the static value i give the String when i create it. And somehow the value inside the get&set methode vanishes.

---

### Post by Petrolea on 2011-12-04
> **Drenriza said:**
> Right after the foreach loop (to where i place the value inside the get&set methode) the values in the get&set are correct. But when i leave the
 
Form1.aspx.cs class and try to retrive the values in another xxxx.cs i get the wrong value. Meaning i get the static value i give the String when i create it. And somehow the value inside the get&set methode vanishes.

Please show the code that you use within your get/set function.

Edit: And briefly describe what the values are that you get and return.

---

### Post by Drenriza on 2011-12-04
example of my get and set methode
```
[FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]
public[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]String[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] _CellOne = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Removed"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2];
[/SIZE][/FONT][/SIZE][/FONT] 
[FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]public[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]String[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] CellOne
{
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]get[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] { [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]return[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] _CellOne; }
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]set[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] { _CellOne = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]value[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]; }
}
[/SIZE][/FONT][/SIZE][/FONT]
```
 
The values i add to for example CellOne is a series of numbers. Like 1, 2, 3, 451, 622, 1901 and so on and so forth. Where the values (in this case numbers) are read from a text file. But when i try and retrive them i get the static value of in this case "Removed". And that gets placed into the table.
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
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]//Add table to arraylist[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]
[FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]lmc.addToTableList(tb2);
}
[/SIZE][/FONT][/SIZE][/FONT]
```
 
Where the Table then is added to the form.
```
[FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]
public[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]void[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] TableCreationAction()
{
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]if[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] (![/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]File[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].Exists(getAndSet.PathOne))
{
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]using[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] ([/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]FileStream[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] fs = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]File[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].Create(getAndSet.PathOne)) { }
}
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]int[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] Num = 1;
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]using[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] ([/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]StreamReader[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] sr = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]StreamReader[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2](getAndSet.PathOne))
{
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]while[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] (sr.Peek() >= 0)
{
getAndSet.Lala = sr.ReadLine();
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]String[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][] lines = getAndSet.Lala.Split([/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]'#'[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]);
tableListTwo.Add(lines);
}
}
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]foreach[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] ([/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]String[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][] line [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]in[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] tableListTwo)
{
getAndSet.CellOne = line[0];
getAndSet.CellTwo = line[1];
getAndSet.CellThree = line[2];
getAndSet.CellFour = line[3];
getAndSet.CellFive = line[4];
getAndSet.CellSix = line[5];
getAndSet.CellSeven = line[6];
getAndSet.CellEight = line[7];
getAndSet.CellNine = line[8];
getAndSet.CellTeen = line[9];

[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]if[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] (Num % 2 == 0)[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]//modulus forklaring http://en.wikipedia.org/wiki/Modulo_operation
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]{
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]//TableCreationTwo();
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]tbu.TableCreationTwo();
}
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]else
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]{
TableCreationThree();
}
Num++;
}
Num = 0;
tableListTwo.Clear();
System.Collections.[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]ArrayList[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] something = lmc.returnTablelist();
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]foreach[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] (System.Web.UI.WebControls.[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Table[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] p [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]in[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] something)
{
form1.Controls.Add(p);
}
lmc.clearTableList();
}[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]//tableCreationAction Ends
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]
```
 
The get and set methode is placed in class GetAndSetMethodes.cs.
[FONT=Consolas][SIZE=2]TableCreationTwo() is placed in class TableBuildUp.cs[/SIZE][/FONT]
[FONT=Consolas][SIZE=2]TableCreationAction() is placed in WebForm1.aspx.cs[/SIZE][/FONT]
[FONT=Consolas][SIZE=2][/SIZE][/FONT] 
[FONT=Consolas][SIZE=2]If i place the [FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]TableCreationTwo() methode in the WebForm1.aspx.cs class, i have no trouble getting the correct value from the get and set methode. But when i place [FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]TableCreationTwo() in another class, in this case TableBuildUp.cs i get the wrong value.[/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT]
[FONT=Consolas][SIZE=2][/SIZE][/FONT] 
[FONT=Consolas][SIZE=2]Hope i explained it well enough.[/SIZE]
[/FONT]

---

### Post by Petrolea on 2011-12-04
You might also want to post your getset class and I will analyse it tomorrow.

Can't find any errors in these two classes.

---

### Post by Drenriza on 2011-12-05
> **Petrolea said:**
> You might also want to post your getset class and I will analyse it tomorrow.

Can't find any errors in these two classes.

You want me to post my entire get/set class?

---

### Post by Petrolea on 2011-12-05
> **Drenriza said:**
> You want me to post my entire get/set class?

Actually, you don't have to. I can't seem to think of why this error might occur. Try asking on some Windows forum, more people will probably be able to help you there since this is Windows related.

---

