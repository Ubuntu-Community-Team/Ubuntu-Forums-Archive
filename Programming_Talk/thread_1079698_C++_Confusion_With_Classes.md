---
title: "C++ Confusion With Classes"
date: 2009-02-24
forum: Programming Talk
---

### Post by tdrusk on 2009-02-24
This would not be a problem if I didn't have to use a switch statement, but I would need to learn anyway.

Basically I need to use a class that is outside of a switch statement in a switch statement. For example

```
#include<iostream>
using namespace std;
#include<string>
int main()
{
        for (int dc = 1; dc <=4; dc++)
        {
                switch (dc)
                {
                        case 1:
                        {
                                 CollegeCourse myMondayClass;
                         }
                         break;
                   }
            }
}
class CollegeCourse
{
        private:
                string department;
                int courseNum;
                int seats;
        public:
                void setDepartmentAndCourse(string, int);
                void setSeats(int);
                void displayCourseData();
};


```

This returns the error
```

error: ‘CollegeCourse’ was not declared in this scope

```

What do I do to declare it in the scope?

):P

---

### Post by Can+~ on 2009-02-24
In C and C++, any { } declares a new scope.

I guess you'll need to use new and delete, and that's what the assignment is about, so I won't say anything else.

---

### Post by PandaGoat on 2009-02-24
You need to declare and define the class before the main method.  Do the following:
```

#include<iostream>
using namespace std;
#include<string>

class CollegeCourse
{
        private:
                string department;
                int courseNum;
                int seats;
        public:
                void setDepartmentAndCourse(string, int);
                void setSeats(int);
                void displayCourseData();
};

int main()
{
        for (int dc = 1; dc <=4; dc++)
        {
                switch (dc)
                {
                        case 1:
                        {
                                 CollegeCourse myMondayClass;
                         }
                         break;
                   }
            }
}

```

---

### Post by tdrusk on 2009-02-24
Thanks guys. 

Works great. :p

---

