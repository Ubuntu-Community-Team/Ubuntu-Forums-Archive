---
title: "python newb: how to combine tuples into dictionaries"
date: 2011-01-27
forum: Programming Talk
---

### Post by pharubu on 2011-01-27
Any clues would be appreciated

foFname = ['John', 'Mary', 'Fred']
foLname = ['Smith', 'Jones', 'Dagg']
foAge = [10, 21, 23]

foKeys = ['FNAME', 'LNAME', 'AGE']

**magic happens to produce the below result**

foList = [
        {'FNAME':'John', 'LNAME':'Smith', 'AGE':10},
        {'FNAME':'Mary', 'LNAME':'Jones', 'AGE':21},
        {'FNAME':'Fred', 'LNAME':'Dagg', 'AGE':23},
]

**Note:** to make it really tricky the magic must happen on one line
i.e. [x for x... ] or lambda...
as genshi wont allow 

for i in item: 
  print i

---

### Post by StephenF on 2011-01-28
```

foFname = ['John', 'Mary', 'Fred']
foLname = ['Smith', 'Jones', 'Dagg']
foAge = [10, 21, 23]
foKeys = ['FNAME', 'LNAME', 'AGE']

foList = [dict((key, val) for key, val in zip(foKeys, record)) for record in zip(foFname, foLname, foAge)]

```

---

