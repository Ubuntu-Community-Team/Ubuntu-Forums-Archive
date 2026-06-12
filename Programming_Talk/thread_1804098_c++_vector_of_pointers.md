---
title: "c++ vector of pointers"
date: 2011-07-14
forum: Programming Talk
---

### Post by muteXe on 2011-07-14
hiya,
I just want to check i've cleared up any memory leaks properly.  I have a class that holds a vector of pointers (to a CPosition type):

```

std::vector<CPosition*> m_waypointList;

```

In the class d'tor I call this method to free up stuff:
```

void CTrajectory::ClearList(void)
{
    if(m_waypointList.empty() != true)
    {
        for(size_t i = 0; i < m_waypointList.size(); ++i)
        {
            delete m_waypointList[i];
        }
        m_waypointList.clear();
    }
}

```

Is this ok?  Also, on a side note, how would I implement this using iterators?  I am comfortable with using iterators to loop over the list, just not sure how to call delete when using iterators.

Many thanks,

Tom

---

### Post by PaulM1985 on 2011-07-14
Looks ok to me.  You would use an iterator in the same was as you would when using an iterator normally... If you are unsure, create a pointer to the CPosition in your loop and then delete that.

```

CPosition *pPos = (*iter);
delete pPos;

```

Or you could just do

```

delete (*iter);

```

Paul

---

### Post by muteXe on 2011-07-14
Cheers mate.
I was going to use your second iter suggestion, but it didnt look right for some reason.  I guess it's fine though :)

Thanks again,

Tom

---

### Post by dwhitney67 on 2011-07-14
> **muteXe said:**
> ... I am comfortable with using iterators to loop over the list, just not sure how to call delete when using iterators.


```

for (std::vector<CPosition*>::iterator it = m_waypointList.begin(); it != mywaypointList.end(); ++it)
{
   delete *it;
}

```

---

