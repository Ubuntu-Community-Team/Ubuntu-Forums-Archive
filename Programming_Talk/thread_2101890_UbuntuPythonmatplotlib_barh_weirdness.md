---
title: "Ubuntu/Python/matplotlib barh weirdness"
date: 2013-01-05
forum: Programming Talk
---

### Post by Rich_S on 2013-01-05
I'm working my way through the examples in the O'Reilly Python Data Analysis book.

The following code snippet is giving me an issue:

```

tz_counts[:10].plot(kind='barh', rot=0)  
plt.show()

```

On Ubuntu 12.04, it displays a blank plot (axes are there but no data series).  If I change the 'barh' to 'bar', it displays a regular bar chart correctly.

On WIndows 7, it works just fine.

I have tried a few different backends in matplotlibrc and have also tried having the code save to a file instead of displaying, with *plt.savefig('figpath.svg')* - I tried png as a format as well.

Same result every time - bar works fine, barh displays an empty plot.

Any ideas?

---

### Post by Lux Perpetua on 2013-01-06
You'll need to provide more context for that code.  If possible, post a minimal but complete code example that demonstrates the issue.

---

### Post by Rich_S on 2013-01-06
> **Lux Perpetua said:**
> You'll need to provide more context for that code.  If possible, post a minimal but complete code example that demonstrates the issue.

Here is a running example:

```

import json 
from pandas import DataFrame, Series
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

#read in records one line at a time
path = '/home/rich/code/sample.txt'
records = [json.loads(line) for line in open(path)] 
frame = DataFrame(records)

#get counts by time zone and fill in missing and NA records
tz_counts = frame['tz'].value_counts()
clean_tz = frame['tz'].fillna('Missing')
clean_tz[clean_tz == ''] = 'Unknown'
tz_counts = clean_tz.value_counts()

#create and display bar chart
tz_counts[:10].plot(kind='barh', rot=0)  
plt.show()

```

Then this is what displays:

[img]http://i.imgur.com/qjEPn.png[/img]

Now if I change 'barh' in the next to last line of code to 'bar' then it works fine and I get:

[img]http://i.imgur.com/Ifhop.png[/img]

On a Windows 7 box, I ran the exact same code in the first instance and it worked correctly, drawing a horizontal bar chart.

---

### Post by Rich_S on 2013-01-06
Solved.  I had pandas 0.7 installed (the latest version in the Ubuntu repository).  Uninstalling that and manually installing the latest pandas (0.10) fixed this issue and another one I was having.

---

