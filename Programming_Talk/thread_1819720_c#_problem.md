---
title: "c# problem"
date: 2011-08-06
forum: Programming Talk
---

### Post by Drenriza on 2011-08-06
Hi all.

I am getting the following error, **Unable to cast object of type 'System.String[]' to type 'System.String'.** But i don't understand how to solve the issue.

I am in asp.net trying to create a list with tables, containing different information. I get the information from a text file, where each word is isolated by #word#, when i read the file i then remove the "#". I succeed in doing this with only a single entry in the file, but when i get multiple entries, i ran into issues since the code, wasn't able handle multiple entries. So i had to edit it.

The code that i am currently working with is as follows
```
using (StreamReader sr = new StreamReader(path))
             {
                 while (sr.Peek() >= 0)
                 {
                     lala = sr.ReadLine();
                     String[] lines = lala.Split('#');
                     test.Add(lines);
                 }
             }
 
             foreach (String line in test) <<------i get the error here..
             {
                 for (int z = 0; z < test.Count; z++)
                 {
                     if (z == 0 && txtbox_test1.Text == "test1")
                     {
                         txtbox_test1.Text = line;
                         break;
                     }
                     if (z == 1 && txtbox_test2.Text == "test2")
                     {
                         txtbox_test2.Text = line;
                         break;
                     }
                     if (z == 2 && txtbox_test3.Text == "test3")
                     {
                         txtbox_test3.Text = line;
                         break;
                     }
                     if (z == 3 && txtbox_test4.Text == "test4")
                     {
                         txtbox_test4.Text = line;
                         break;
                     }
                     if (z == 4 && txtbox_test5.Text == "test5")
                     {
                         txtbox_test5.Text = line;
                         break;
                     }
                     if (z == 5 && txtbox_test6.Text == "test6")
                     {
                         txtbox_test6.Text = line;
                         break;
                     }
                     if (z == 6 && txtbox_test7.Text == "test7")
                     {
                         txtbox_test7.Text = line;
                         break;
                     }
                     if (z == 7 && txtbox_test8.Text == "test8")
                     {
                         txtbox_test8.Text = line;
                         break;
                     }
                 }
             }
```

My arraylist "test" is below
```
static ArrayList test = new ArrayList();
```

Hope someone can give me a point in the right direction, since i have ran into a brick wall and i cannot get through :p

Kind regards.

---

### Post by ve4cib on 2011-08-06
What line specifically are you getting the error on?

---

### Post by Drenriza on 2011-08-06
Edited my post to show the error on the line in the code.

Sorry :)

---

### Post by cgroza on 2011-08-06
I do not know much C#. so I will use my Java skills. Hope it works. :D
Here is what I think the problem is.
It appears that the variable "test" is a String[][]. And you are trying to iterate through it with a String, it should be a String[].

---

### Post by ve4cib on 2011-08-06
When you declare test, try declaring it as **ArrayList<String> test = new ArrayList<String>()**

I think the problem may be that at some point you've stored a string array inside test, which is causing the problem when you try to iterate through the list.  Explicitly setting the type of object you're storing in test (the "<String>" part) you should be able to catch where that's happening.


EDIT:

I found where that's actually happening:

```
lala = sr.ReadLine();
String[] lines = lala.Split('#');
test.Add(lines);
```

Rather than adding the String[] to test, you need to add each individual string separately.  The ArrayList class may have a function built in that will merge an array into itself, or you may have to manually do this with a simple loop on your own.

---

### Post by mendhak on 2011-08-07
Change the type to List<string>

```

static List<string> test = new List<string>();

```


And then change how you're adding:

```

                 while (sr.Peek() >= 0)
                 {
                     lala = sr.ReadLine();
                     List<string> lines = new List<string>(lala.Split('#'));
                     test.AddRange(lines);
                 }


```

---

### Post by Drenriza on 2011-08-07
Hi all.

Thanks for all your replies and suggestions. I got the suggestion in #6 to work with a single entry in the text file, to be written in the 8 cells of the table. The code needs to be fitted to be able to write multiple lines, havnt gotten to that.

However their is a small issue. My issue before, was that when i added my Strings to my arraylist, it became (as far as i know) an object. And i could not figure out how to read the content of the object in the arraylist. But this gave me one object in my arraylist pr one line in the text file.

The method in #6 gives me 32 entries in my arraylist because i have 8 cells and four lines in my text file. 8*4=32. This becomes quite huge when i add all of the 400+ lines which will give me 3200+ entries in the list.

Isn't their a way that i can add the String to the arraylist as i do now (where it becomes an object, as far as i know) and then read the content of each object? This would make it much easier to manage.

Thanks all on advance.

Kind regards.

---

### Post by mendhak on 2011-08-07
So basically, you want to process them in logical groups rather than all in one go.  Alright, going back to the code in your first post, you need to process each string array in your ArrayList.  (You thought it was an object, but it's actually a string array you are adding per line of your text file).  And I assume each line has 8 'elements' that you want to assign to various textboxes.  

Since it's already an array per line, you needn't loop through it, just assign the values.  

```

             foreach (String[] line in test) 
             {

                     txtbox_test1.Text = line[0];               
                     txtbox_test2.Text = line[1];
                     txtbox_test3.Text = line[2];
                     txtbox_test4.Text = line[3];
                     txtbox_test5.Text = line[4];
                     ......
                     
              }


```

---

### Post by Drenriza on 2011-08-07
> **mendhak said:**
> So basically, you want to process them in logical groups rather than all in one go.  Alright, going back to the code in your first post, you need to process each string array in your ArrayList.  (You thought it was an object, but it's actually a string array you are adding per line of your text file).  And I assume each line has 8 'elements' that you want to assign to various textboxes.  

Since it's already an array per line, you needn't loop through it, just assign the values.  

```

             foreach (String[] line in test) 
             {

                     txtbox_test1.Text = line[0];               
                     txtbox_test2.Text = line[1];
                     txtbox_test3.Text = line[2];
                     txtbox_test4.Text = line[3];
                     txtbox_test5.Text = line[4];
                     ......
                     
              }


```

Hi Mendhak

Again thanks for your help. I'm still new to the "world" of C# but i am trying to learn.
I will definitely try you second suggestion, and see how it works out.

Kind regards.

---

### Post by Drenriza on 2011-08-08
Thanks #8 i got it working :p

Thanks for the solution along with the short explanation of what i was doing. I was not aware that i simple could extract the info that already was in the array, the way you showed.

Kind regards.

---

### Post by Drenriza on 2011-08-08
I don't know if you guys can help me with something else but still related to this project.

When i read my arraylist and creates the table with the cells to my asp.net page. Then if i hit the refresh button, it will post the same tabels, that was last read from the arraylist. Does the tabels get putted in some temp file that the refresh button can access or something?

To try and elaborate. If my arraylist contains two arraystrings? :p and i create two tabels with 8 elements in each table. If i hit refresh, the same tabels are shown on the screen, so i have four. But only two lies in the arraylist. O.o confusing.

Hope you know what i mean, or else i will try to explain better.

EDIT: Maybe this example explains my problem better.
[http://aspalliance.com/687_preventing_duplicate_record_insertion_on_page_refresh](http://aspalliance.com/687_preventing_duplicate_record_insertion_on_page_refresh)

---

### Post by mendhak on 2011-08-08
Depends on how you're binding your page controls.  It sounds like you need a 

if(!Page.IsPostBack)

check around the bit where you bind your values.

Yes, the values do get persisted in what's known as viewstate.  Viewstate stores various values that the controls/page can use to know if something has changed and what events it should raise.  Because it persists your values, you get to see the values across reloads.  

If none of that helped, you'll need to show how you're binding your values, maybe even the entire codebehind.

---

### Post by Drenriza on 2011-08-08
What do you mean with "binding your values," i need more details to know what i should be looking for :D noob alert.

Edit.
Based on #12 i found this
> Hello, i want to add a row to an asp table every time i click on a button. What is happenning with me is that each time i click on the button a row is added as if it is the first row, but i want to append each row to the others.
My problem in a nutshell.

The solution to this problem is
> To make this work, you need to create a function that adds your rows based on an integer value (how many times you have clicked that button. The best way to keep this value is in a Session value, Session("RowsAdded"), then in the Page_Init method re-add your dynamic controls on each post back.
But im not sure i understand the solution.

The website i found this on
[http://www.dreamincode.net/forums/topic/33647-postbackc%23/](http://www.dreamincode.net/forums/topic/33647-postbackc%23/)

---

### Post by mendhak on 2011-08-08
Can you post your ASPX and codebehind (and sample text file)?  I understand the main issue but I'm trying to see what data you want the button to add - you've presumably already made your table by populating it from the text file.  What extra data will the button add?

---

### Post by Drenriza on 2011-08-09
> **mendhak said:**
> Can you post your ASPX and codebehind (and sample text file)?  I understand the main issue but I'm trying to see what data you want the button to add - you've presumably already made your table by populating it from the text file.  What extra data will the button add?

When i click my button to add my tables to the asp.net page i run the following code.
```
protected void readTableList_Click(object sender, EventArgs e)
        {
            using (StreamReader sr = new StreamReader(path))
            {
                while (sr.Peek() >= 0)
                {
                    lala = sr.ReadLine();
                    String[] lines = lala.Split('#');
                    tableListTwo.Add(lines);
                }
            }

            foreach (String[] line in tableListTwo)
            {
                _cellOne = line[0];
                _cellTwo = line[1];
                _cellThree = line[2];
                _cellFour = line[3];
                _cellFive = line[4];
                _cellSix = line[5];
                _cellSeven = line[6];
                _cellEight = line[7];
                wwwa();
            }

            foreach (System.Web.UI.Control i in tableList)
            {
                form1.Controls.Add(i);
            }

        }//readTableList button, metode ends
```
wwwa(); is as follows
```
public void wwwa()//creates user defined tabels
        {
            //Create the table
            Table tb2 = new Table();
            //Set table width
            tb2.BorderWidth = 1;
            //create tabel cells
            TableRow row = new TableRow();
            TableCell cell1 = new TableCell();
            TableCell cell2 = new TableCell();
            TableCell cell3 = new TableCell();
            TableCell cell4 = new TableCell();
            TableCell cell5 = new TableCell();
            TableCell cell6 = new TableCell();
            TableCell cell7 = new TableCell();
            TableCell cell8 = new TableCell();
            //Add cells to the row
            row.Cells.Add(cell1);
            row.Cells.Add(cell2);
            row.Cells.Add(cell3);
            row.Cells.Add(cell4);
            row.Cells.Add(cell5);
            row.Cells.Add(cell6);
            row.Cells.Add(cell7);
            row.Cells.Add(cell8);
            tb2.Rows.Add(row);
            //Set cells border width
            cell1.BorderWidth = 1;
            cell1.Width = 150;
            cell2.BorderWidth = 1;
            cell2.Width = 150;
            cell3.BorderWidth = 1;
            cell3.Width = 150;
            cell4.BorderWidth = 1;
            cell4.Width = 150;
            cell5.BorderWidth = 1;
            cell5.Width = 150;
            cell6.BorderWidth = 1;
            cell6.Width = 150;
            cell7.BorderWidth = 1;
            cell7.Width = 150;
            cell8.BorderWidth = 1;
            cell8.Width = 150;
            //Add static content to the cells
            cell1.Text = _cellOne;
            cell2.Text = _cellTwo;
            cell3.Text = _cellThree;
            cell4.Text = _cellFour;
            cell5.Text = _cellFive;
            cell6.Text = _cellSix;
            cell7.Text = _cellSeven;
            cell8.Text = _cellEight;
            //Add table to arraylist
            tableList.Add(tb2);
        }
```

My aspx looks like
```
<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <title></title>

</head>
<body>
    <form id="form1" runat="server">
    <div>
    
        <asp:Button ID="btn_readTableList" runat="server" onclick="readTableList_Click" 
            Text="Read Table List" />
        <asp:Button ID="btn_createTableList" runat="server" 
            onclick="btn_createTableList_Click" Text="Create New Table" />
        <br />
        <asp:TextBox ID="txtbox1" runat="server" Width="73px"></asp:TextBox>
        <asp:TextBox ID="txtbox2" runat="server"></asp:TextBox>
        <asp:TextBox ID="txtbox3" runat="server"></asp:TextBox>
        <asp:TextBox ID="txtbox4" runat="server"></asp:TextBox>
        <asp:TextBox ID="txtbox5" runat="server"></asp:TextBox>
        <asp:TextBox ID="txtbox6" runat="server"></asp:TextBox>
        <asp:TextBox ID="txtbox7" runat="server"></asp:TextBox>
        <asp:TextBox ID="txtbox8" runat="server"></asp:TextBox>
    
        <br />
    
    </div>
    </form>
</body>
</html>
```

And its like if it hit the refresh button, it looks like that this part is ran again and just appended to the asp.net site along with what is already their
```
foreach (System.Web.UI.Control i in tableList)
            {
                form1.Controls.Add(i);
            }
```

My sample text file is just a normal text file where words are seperated by #, example
```
cell1#cell2#cell3#cell4#cell5#cell6#cell7#cell8#
```

Need more?
Thanks for the help.

---

### Post by mendhak on 2011-08-09
From what I see, it's very likely that you click the button, it adds the row, and when you refresh, it is simply resubmitting the form - which means that it's raising that button click event once more.

To test this, set a breakpoint anywhere in that click event.  Run the website.  Click the button.  It'll hit the breakpoint.  Let it do its things.  Then when you hit F5, it will hit that breakpoint again.  Since the viewstate is preserved, when you call form1.Controls.Add, it's adding to the form *which already contains the first table*. 

At the moment, you are mixing your data operation with your rendering operation.  You're attempting to deal with them together.  If you, instead, using an ASP.NET Repeater, you would first read your data from the file and put it in your 'data model'.  You would then give that data model to your repeater.  This way, even if you refresh the page and it were to reread and rebind to the repeater, you'll still see only what you give it.

---

### Post by Drenriza on 2011-08-09
> At the moment, you are mixing your data operation with your rendering operation. You're attempting to deal with them together. If you, instead, using an ASP.NET Repeater, you would first read your data from the file and put it in your 'data model'. You would then give that data model to your repeater. This way, even if you refresh the page and it were to reread and rebind to the repeater, you'll still see only what you give it.

Thanks for your insight Mendhak. Do you have an example of a repeater i can work from to solve my issue? :D

Edit.
Yes your right, i sat a break point in the
```
foreach (System.Web.UI.Control i in tableList)
            {
                form1.Controls.Add(i);
            }
```
and when i then refresh my page, it ends at the break point again.

---

### Post by Drenriza on 2011-08-14
Hi mendhak.

Thanks for all your help so far. I have read about a little about what your talking about (rendering and data operations) and it gives a good insight. But i am not closer about the repeater. Do you have an example you can show me i can work from, to try and solve my issue?

Kind regards.

---

