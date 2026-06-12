---
title: "how to implement sorting on custom Python class?"
date: 2012-10-11
forum: Programming Talk
---

### Post by fokuslee on 2012-10-11
Here is my custom class, they will be used to build up more complex objects

```

class RIMSheet:
    def __init__(self, PageNum, PageName):
        """
        This DocString is returned by calling help
        """
        self.PageNum = int(PageNum)
        self.PageName = PageName
    def getPageName(self):
        return self.pageName
    def getPageNum(self):
        return str(self.PageNum)

```

if i have a list of these sheets, i want to be able to sort the list based on PageNum.
How do i enable that?

---

### Post by Bachstelze on 2012-10-11
See [http://wiki.python.org/moin/HowTo/Sorting/#Key_Functions](http://wiki.python.org/moin/HowTo/Sorting/#Key_Functions)

---

