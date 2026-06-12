---
title: "Sorting strings in C++"
date: 2015-03-09
forum: Programming Talk
---

### Post by Bresser on 2015-03-09
Ok I have a program that needs to sort Homeland security Warnings by most urgent to least. I have an array of Alert Objects. How can I sort them from Red to Green?

This is the formatting of the input:

------------------------------------------------
NATIONAL SECURITY WARNING LEVEL INDICATORS
RED     Severe risk of terrorist attacks
ORANGE  High risk of terrorist attacks
YELLOW  Significant risk of terrorist attacks
BLUE    General risk of terrorist attack
GREEN   Low risk of terrorist attacks
------------------------------------------------

I have no problem inputting from the file just having trouble sorting it.

---

### Post by alena3 on 2015-03-09
Hi Bresser!

Add a field for A[COLOR=#000000]lert type into Alert class. 
Compare first symbol of sentences with R,O,Y,B,G and assign accordingly 1|2|3|4 or 5. ([/COLOR][COLOR=#000000]In case with binary tree, you can compare and assign type of alert directly into the algo)[/COLOR][COLOR=#000000]
Sort your array using quick sort or binary tree.

Hope it will help.[/COLOR]

---

### Post by Bresser on 2015-03-09
Do you see where I messed up. I did just that compared the first digit to the codes I also have code for 'W', 'y', 'A' or Warning, Watch, and Advisory.

Heres the code:


```

    void alertList::sort() 
    {
        int i = 0, numElems;
        Alert temp;


        while (alertlist[i].getCity() != "INVALID")
        {
            string warn;


            warn = alertlist[i].getWarningType();


            if (warn.substr(0, 1) == "R")
            {
               alertlist[i].setWarningNumber(0);
            }
            else if (warn.substr(0, 1) == "O")
            {
                alertlist[i].setWarningNumber(1);
            }
            else if (warn.substr(0, 2) == "YE")
            {
                alertlist[i].setWarningNumber(2);
            }
            else if (warn.substr(0, 1) == "B")
            {
                alertlist[i].setWarningNumber(3);
            }
            else if (warn.substr(0, 1) == "G")
            {
                alertlist[i].setWarningNumber(4);
            }
            else if (warn.substr(0, 1) == "W")
            {
                alertlist[i].setWarningNumber(5);
            }
            else if (warn.substr(0, 1) == "Y")
            {
                alertlist[i].setWarningNumber(6);
            }
            else
                alertlist[i].setWarningNumber(7);
            cout << endl << "Assigned: " << alertlist[i].getWarningNumber();
            i++;
        }


        numElems = i;
        // Start of bubble sort
        for (i = 0; i < numElems; i++)
        {
            if (alertlist[i].getWarningNumber() > alertlist[i].getWarningNumber())
            {
                temp = alertlist[i];
                alertlist[i] = alertlist[i + 1];
                alertlist[i + 1] = temp;
            }
          }
    }


```

---

### Post by spjackson on 2015-03-10
I'm guessing this is homework and that's why you are coding a sorting algorithm.

> 
```

        if (alertlist[i].getWarningNumber() > alertlist[i].getWarningNumber()) 

```

What are you comparing here? An item with itself!

> 
```

        // Start of bubble sort
        for (i = 0; i < numElems; i++)


```

A bubble sort has a loop within a loop [http://en.wikipedia.org/wiki/Bubble_sort](http://en.wikipedia.org/wiki/Bubble_sort) . Where is your inner loop?

---

### Post by mörgæs on 2015-03-10
It does indeed look like homework. People don't normally code their own sorting algorithms, there are many available to choose from.

Closing the thread.

---

