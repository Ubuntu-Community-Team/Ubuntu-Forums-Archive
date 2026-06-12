---
title: "Need autocomplete textfield in Netbeans java desktop app"
date: 2009-04-13
forum: Programming Talk
---

### Post by jabibi on 2009-04-13
Hi. I've searched all over the web but I havent got it

tried to code a swing jcombobox to behave like autocomplete but didnt make it.


anyways if anybody can help. it'll be appreciated

---

### Post by myrtle1908 on 2009-04-14
What have you tried?  What is your data source ie. what are you auto-completing against?  A dictionary, a database, a fixed list, what?  It should be simple to roll your own.

---

### Post by Ruhe on 2009-04-14
I wonder how do people use google that they can't find such things.

1. [http://www.jroller.com/santhosh/date/20050620](http://www.jroller.com/santhosh/date/20050620)
2. [http://swinglabs.java.sun.com/hudson/job/SwingX%20Continuous%20Build/javadoc/org/jdesktop/swingx/autocomplete/package-summary.html](http://swinglabs.java.sun.com/hudson/job/SwingX%20Continuous%20Build/javadoc/org/jdesktop/swingx/autocomplete/package-summary.html)

And lots of other stuff in forums

---

### Post by jabibi on 2009-04-14
Hi myrtle1908, what I tried before was so useless that I've erased the code hehe
I need to autocomplete from a PostgreSQL Database table

Ruhe, thanks, I'm using the swinglabs one right now and it's working but just not quite as I'd like to.

The flaw of this swinglabs autocomple is that it doesnt hide the options that are not related to the text entered in the Field. It permanently shows all items.

Maybe I just need to keep exploring this thing.

Thanks for your contribution, I still dont have all the functionality I'm looking for but I've made some advance thanks to you.




so right now this is what i got:
```

    public phonebookUI() {        
        initComponents();
        initdb();
        AutoCompleteDecorator.decorate(combo);        
    }

```

```

    private void formWindowOpened(java.awt.event.WindowEvent evt) {                                  
        combo.removeAllItems();
        try {
            resultset = statement.executeQuery("select namefield from tableperson");
            while(resultset.next()){
                combo.addItem(resultset.getObject(1));
            }
        }
        catch (SQLException ex) {System.out.println(ex.getMessage();}
}

```



So, this certainly autocompletes and shows the popup and selects and goes to the item most related to the text entered but it doesnt hide the items that dont have anything to do.

Example:

the autocomplete combo box is populated with:

abc
abcdef
abcdefghi
abc2345
xyz
vwxyz
xyz356



Now if I type in the combobox "abcd"
it will certainly autocomplete to "abcdef"
and the selected item in the combobox popup will be "abcdef" (2nd)
Now: it should only be showing the 2 choices that are related to the entered text:

abcdef
abcdefghi

And exclude the rest

abc
abc2345
xyz
vwxyz
xyz356


But it always shows all items.


I'm gonna keep experimenting with what I have so far but if you have a hint to make my pain end quicker please let me know.
Again, thank you.

---

### Post by ufis on 2009-04-15
> **jabibi said:**
> ```

    private void formWindowOpened(java.awt.event.WindowEvent evt) {                                  
        combo.removeAllItems();
        try {
            resultset = statement.executeQuery("select namefield from tableperson");
            while(resultset.next()){
                combo.addItem(resultset.getObject(1));
            }
        }
        catch (SQLException ex) {System.out.println(ex.getMessage();}
}

```

So, this certainly autocompletes and shows the popup and selects and goes to the item most related to the text entered but it doesnt hide the items that dont have anything to do.

Rather than using the resultset to populate your combo, read the results into an array or List or something. Then populate the combo from the array/List. Now every time the search string changes, repopulate the combo from the array/List but only using the values that match the search string.

---

