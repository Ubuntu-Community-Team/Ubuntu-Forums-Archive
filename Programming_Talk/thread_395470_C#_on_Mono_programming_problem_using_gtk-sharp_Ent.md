---
title: "C# on Mono programming problem using gtk-sharp Entry boxes"
date: 2007-03-28
forum: Programming Talk
---

### Post by neilcavendish on 2007-03-28
I have written a peice of code that creates a form and loads a 3x3 table with 9 smaller 3x3 tables to create a sudoko grid. The program then loads entry boxes into each smaller table. The problem is i cant read from the entry boxes. Please help.
Here is the code that creates the form

```

using System;
using Gtk;

public class MainWindow: Gtk.Window
{
    protected Gtk.HBox hbox;
    protected Gtk.Button button;

    protected Gtk.Table MainTable;
    protected Gtk.Table[,] table;
    public Gtk.Entry[,] entry;


    public MainWindow (): base ("")
    {
        entry = new Gtk.Entry[9,9];
        MainTable = new Gtk.Table(3,3, false);
        table = new Gtk.Table[3,3];
        
        MainTable.ColumnSpacing = 3;
        MainTable.RowSpacing = 3;

        for(uint i = 0; i < 3; i++){

            for(uint j = 0; j < 3; j++)
            {
                table[i,j] = new Gtk.Table(3,3, false);
                table[i,j].ColumnSpacing = 0;
                table[i,j].RowSpacing = 0;
                MainTable.Attach(table[i,j], i, i+1, j, j+1);
                for(uint k = 0; k < 3; k++)
                {
                    for(uint l = 0; l < 3; l++)
                    {
                        entry[i*3+k,j*3+l] = new Gtk.Entry();
                        entry[i*3+k,j*3+l].MaxLength = 1;
                        entry[i*3+k,j*3+l].WidthChars = 1;
                        table[i,j].Attach(entryi*3+k,j*3+l],k,k+1,l,l+1);
                    }
                }
            }
        }
        hbox = new HBox();
        hbox.PackStart(MainTable);
        
        button = new Button("Go!!");
        hbox.PackEnd(button);
        button.Clicked += printArray;
        
        
        this.Add(hbox);
                

    }
    static void printArray(object obj, EventArgs args)
    {
        int [,]A = new int[9,9];
        for(int i = 0; i < 9; i++)
        {
            for(int j = 0; j < 9;j++)
            {
                //A[i,j] = entry[i,j].Text; this is were i wanna read the entry boxes to the array A. But it kicks out a error about not being able to index type object. 
                Console.Write (A[i,j]);
            }
            Console.WriteLine();
        }
    }
    
    protected void OnDeleteEvent (object sender, DeleteEventArgs a)
    {
        Application.Quit ();
        a.RetVal = true;
    }
}
In the code there is a cometed line this is were i would 


```

In the code there is a cometed line this is were i would like to read the values in the text box into a int array. But it gives a error when trying the code

int [,]A = new int[9,9];
A[i,j] = entry[i,j].text;

Says that it cant add indexing to a type object.
I am new to gtk. 
Please help 
Thanks again

---

### Post by mikalh on 2007-03-29
The problem is that you're trying to access an instance field from a static method. If you make "printArray" an instance method (i.e. nonstatic), or make  "entry" static, it'll work. You'll also need to use Int. TryParse or Int.Parse to convert the string into an int.

Wierd error message though. I suspect it was a knock-on effect of the first error message:
sudoku.cs(62,26): error CS0120: `MainWindow.entry': An object reference is required for the nonstatic field, method or property

---

### Post by neilcavendish on 2007-03-29
Thanks again. I have changed the static infront of print array to private and it now compiles. When i try and convet the text to int Convert.ToInt32 it segfalts and i dont really understand why. It says Input string was not in the correct format any ideas. Thanks

---

### Post by neilcavendish on 2007-03-29
I sorted it thanks for all the help

---

