---
title: "C++ date"
date: 2009-09-14
forum: Programming Talk
---

### Post by matmatmat on 2009-09-14
Is there a function that gives just the date, I have looked at time.h but it seems to return the time & date.

---

### Post by Bachstelze on 2009-09-14
Look at strftime(3).

---

### Post by MindSz on 2009-09-14
You could use the time.h method and ignore the time. You can choose which format you want your output in.

---

### Post by matmatmat on 2009-09-14
Thanks

---

### Post by dwhitney67 on 2009-09-14
Or use Boost:
```

#include <boost/date_time/gregorian/gregorian.hpp>
#include <iostream>

int main()
{
   using namespace boost::gregorian;

   date now(day_clock::local_day());

   std::cout << "The date is: " << now << std::endl;
}

```

---

