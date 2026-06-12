---
title: "General Python Questions"
date: 2010-04-14
forum: Programming Talk
---

### Post by goseph on 2010-04-14
Hi everyone,

I have a couple of tasks to perform in Python and I wonder, what is the best way to complete them? I could do these tasks manually by a series of tedious for loops but there must be a better way?

1) having read in a line from a config file, of the form:

param = ' string value'  # comment

where white space could appear anywhere in the line and the value may or may not be quoted.

How could I best extract the value? If quotes appear, what lies between the first two (non-comment, after the '='), quote characters should be extracted

If quotes do not appear, the first sequence of alphanumeric characters should be extracted after the '=' (unless in quotes)

---

### Post by Pyro.699 on 2010-04-14
Do you have to write your own? If not, try using this: [http://docs.python.org/library/configparser.html](http://docs.python.org/library/configparser.html)

Side note, use this:
[php]
def GetBetween(zStr, zStart, zEnd):
    z1 = zStr.find(zStart)
    z2 = zStr.find(zEnd, z1+len(zStart));
    
    if(z2 > z1 and z1 > -1):
        return zStr[z1+len(zStart):z2]
    else:
        return "";

myStr = "param = ' string value'  # comment"
print GetBetween(myStr, "'", "'")
[/php]

I left it as a function, because i copied and pasted it out of one of my other programs, quite the useful tool ^^

---

### Post by raydeen on 2010-04-14
Is the first part of each line always 'param = '? That is, is the usage of whitespace consistent? If so, you could just read each line in using the standard file commands and split each string into a list. After that, you would know that list[2] would always be the string value you were looking for which you could then check to see if it had the quotes or not and strip them out as needed.

"param = 'value'" when converted to a list would be 
list[0] = 'param'
list[1] = '='
list[2] = 'value'

Hope that helps with your answer. By default, the split function should interpret whitespace as a separator for the string to list conversion.

I'm a newbie too so if that info is wrong someone please correct me.

---

### Post by Pyro.699 on 2010-04-14
Slightly off topic, but i made my own config parser which has a config file that looks like this:

```

bank_Current,integer=374301 
bank_InitiateBankTransfer,boolean=False 
bank_StartTransferAt,integer=5000000 
bank_TransferAmountLeft,integer=0 
bank_TransferPurchaseCost,integer=50000 
bank_TransferPurchaseID,integer=2788  
main_AlternateAccount,string= 
main_EnableAlternateAccount,boolean=False 
main_HandCurrent,integer=13143 
main_Password,string=hidden:P 
main_SentDailyAt,date=20100330000000 
main_Username,string=somename 
 
more_Item,boolean=False 
 
qitem_AuctionDuration,string=6 
 
stocks_Bought,boolean=True 
stocks_BuyAt,integer=15 
stocks_PersonalAlert,integer=60 
stocks_PersonalList,list=[''] 
stocks_SellAt,integer=60 
 
two_TimesToToss,integer=500 
two_TossAmount,string=1 

```

I find it useful, theres alot more in my config file, i just chose not to post the full file xD

---

### Post by wmcbrine on 2010-04-14
I'd use the ConfigParser, but failing that:

```
comment = line.find('#')
if comment > -1:
    line = line[:comment]
key, value = [x.strip() for x in line.split('=')]
```

etc. It's actually really easy to deal with this sort of thing in Python. But I fear that this is homework.

---

