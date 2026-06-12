---
title: "[PYTHON] CSV Data Loss"
date: 2009-02-28
forum: Programming Talk
---

### Post by kjohansen on 2009-02-28
I have a list of lists called transactions.  Each list in the transaction contains words.  I am trying to print this out to a CSV, but I have 497 records and the CSV file is only getting 495 of them.  Is there any reason why this would be happening.

CSV code taken from the Python docs.
[php]
spamWriter = csv.writer(open('eggs.csv', 'w'), delimiter=',')
for et in transactions:
    spamWriter.writerow(et)

spamReader = csv.reader(open('eggs.csv','r'), delimiter=',')
l=[]
for et in spamReader:
    l.append(et)

len(transactions)
len(l)

[/php]

len(transactions)=497
len(l)=495

If I open the CSV, it has 495 lines.  


Edit: On further review, the last entry in l is half of the lat entry in transactions, so is there a limit of what can be written to CSV?  The cutoff is in the middle of the word and then the last two entries are completely missing.

[php]
>>> l[494]
['TOPIC_INTEREST', 'RAISE', 'GOVERNMENT', 'SIX', 'LEGISLATION', 'PCT', 'RATE', 'REUTERS', 'RATES', 'COMMUNITY', 'FIXED', 'LINE', 'SECRETARY', 'INDUSTRIES', 'DECREE', '"', 'FINANCE', 'DEPOSITS', 'ONE', 'ALSO', 'MEASURE', 'ECO']

>>> transactions[494]
[u'TOPIC_INTEREST', u'RAISE', u'GOVERNMENT', u'SIX', u'LEGISLATION', u'PCT', u'RATE', u'REUTERS', u'RATES', u'COMMUNITY', u'FIXED', u'LINE', u'SECRETARY', u'INDUSTRIES', u'DECREE', u'"', u'FINANCE', u'DEPOSITS', u'ONE', u'ALSO', u'MEASURE', u'ECONOMY', u'RECENT', u'STATE', u'EUROPEAN', u'DE', u'TAKES', u'SOME', u'TODAY', u'EC', u'BANKERS', u'SPOKESMAN', u'RESULT', u'BANKS', u'TOMORROW', u'PROFITS', u'UP', u'LIMITED', u'TOTAL', u'ASSETS', u'MINISTRY', u'OFFICIAL', u'YEAR', u'LOSSES', u'THIS']


[/php]

If you notice the word 'ECONOMY' in transactions is cut off as 'ECO'




-kj

---

### Post by kjohansen on 2009-02-28
I guess I should have read the *** manual.

> 
Note

This version of the csv module doesn&#8217;t support Unicode input. Also, there are currently some issues regarding ASCII NUL characters. Accordingly, all input should be UTF-8 or printable ASCII to be safe; see the examples in section Examples. These restrictions will be removed in the future.



---

