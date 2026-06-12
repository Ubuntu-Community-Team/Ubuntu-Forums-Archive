---
title: "Python pyhtmltable and easygui issue"
date: 2009-01-29
forum: Packaging and Compiling Programs
---

### Post by Cornbreadly on 2009-01-29
I am new and trying to change a simple script into something I can change into a self contained .exe that I can email around at work to co-workers who could care less what python is.

The programs work.  I just need the out put from the pyhtmltable module to be a string so that easygui can spit it out in a codebox() with an ok button.

[Pyhtmltable]("http://www.pasko.net/PyHtmlTable/")
[Easygui codebox]("http://easygui.sourceforge.net/easygui.html#-codebox")

Here is my program I have been getting help on.

```

#c:/python25/working/trans_list/
# transaction posting on available balance in HTML output
import PyHtmlTable
from easygui import *

posting_trans = [] #creating a list of posting debits here

#getting the starting balance
print 'What is the balance available to pay transactions? '
avail_bal = float(raw_input('Value: ')) 

while True:  #building up the list of transactions
    print 'Please enter the debits in order of posting one at a time.'
    print 'If there is no more, please enter 0:'
    ans = float(raw_input('Value: '))
    if ans == 0:
        break # to get out of loop
    posting_trans.append(ans)

# start of the html table


print "<b> Beginning available balance of %.2f</b>" % avail_bal

tabledict = {'width': '400', 'border': 2, 'bgcolor': 'white'}
t  = PyHtmlTable.PyHtmlTable(2, 1, tabledict)

t.setCellcontents(0, 0, "Transaction Value")  #header cells
t.setCellcontents(0, 1, "Available Balance")


for line, trans in enumerate(posting_trans):
    avail_bal -= trans
    t.setCellcontents(line + 1, 0, '%.2f' % trans)
    t.setCellcontents(line + 1, 1, '%.2f' % avail_bal)   

t.return_html() #t.display here outputs the html I need perfectly.  
#But I need it in a window that can be highlighted and copied.  
#the py2exe conversion I did works in a way but the program immediately closes when I tested the exe after I input the info.  
#Having a window pop-pup with an "ok" button will be great.
#return_html returns just a string the easygui codebox will use supposedly

codebox("Beginning available balance of %.2f" % avail_bal, t.return_html)

```

---

### Post by Cornbreadly on 2009-01-30
This has been posted to the wrong area.  Thanks to those who took a look.  I moved it over to Programming Talk.

---

