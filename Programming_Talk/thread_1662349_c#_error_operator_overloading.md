---
title: "c# error: operator overloading"
date: 2011-01-07
forum: Programming Talk
---

### Post by varshasharat on 2011-01-07
using System;
using System.Collections;

class school
{
   String clname;
   int tot_stu;

   public void get()
   {
       Console.WriteLine("Enter class name");
       clname=Console.ReadLine();
       Console.WriteLine("Enter the total no.of students");
       tot_stu=Convert.ToInt32(Console.ReadLine());
   }

   public void put()
   {
       Console.WriteLine("Maximum no.of students in {0} is {1}",clname,tot_stu);
   }

 public static bool operator  >(school stud1,school stud2)
   {
      if(s1.tot_stu<s2.tot_stu)
          return true; 
      else
         return false;
   }
}

public class student
{
   public static void Main()
   {
        school c1,c2,c3;
        c1=new school();
	c2=new school();
	c3=new school();

 	c1.get();
 	c2.get();
 	c3.get();

	if(c1>c2)
           if(c1>c3)
		c1.put();
	   else
		c3.put();
        else
           if(c2>c3)
		c2.put();
	   else
		c3.put();
     }
}

student.cs(22,21): error CS0216: The operator 'school.operator >(school,
        school)' requires a matching operator '<' to also be defined

---

### Post by cariboo on 2011-01-08
A bump for the move.

---

### Post by dwhitney67 on 2011-01-08
Well, as the error indicates, you need to add an operator<() function.  Also, it would be helpful to correct your variable names in the operator>() function you have already defined.

Consider this:
```

...
   public static bool
   operator>(school s1, school s2)
   {
      return s1.tot_stu > s2.tot_stu;
   }

   public static bool
   operator<(school s1, school s2)
   {
      return s1.tot_stu < s2.tot_stu;
   }

...

```


P.S.  It seems odd that you declared your class as "school", instead of "Class" or "Course".  Probably the latter is a bit confusing.

---

### Post by varshasharat on 2011-01-13
thanks, my program worked.....

---

