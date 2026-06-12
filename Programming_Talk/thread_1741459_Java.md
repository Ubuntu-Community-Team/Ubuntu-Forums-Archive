---
title: "Java"
date: 2011-04-28
forum: Programming Talk
---

### Post by Drenriza on 2011-04-28
Hi all.

I have some code as follows
```
public Student(String fullName, String studentID)
    {
        name = fullName;
        id = studentID;
        //Space holder
    if(name.length() <=4) //then
    System.out.println("fullnavn er for kort");
    else
    name = fullName;
        {
            if(id.length() <=3) //then
            System.out.println("studentID er for kort");
            else
            id = studentID;
        }
    }
```

And a second part
```
/**
     * Return the login name of this student. The login name is a combination
     * of the first four characters of the student's name and the first three
     * characters of the student's ID number.
     */
    public String getLoginName()
    {
        return name.substring(0,4) + id.substring(0,3); //even if name and studentID is less then expected
    }
```

My "problem" is how do i get the GetLoginName to create a login name even if student name is less then 4 characters and even if the studentID is less then 3 characters??

---

### Post by simeon87 on 2011-04-28
You could add some extra characters to make sure it is the desired length: John123 and JoeX456, where I added an X to give Joe still four characters. Is this a homework assignment? Does the assignment say anything about this?

---

### Post by Drenriza on 2011-04-28
This is some java tutorials i'm studying to try and become better to java, but it is not school related.

---

### Post by simeon87 on 2011-04-28
> **Drenriza said:**
> This is some java tutorials i'm studying to try and become better to java, but it is not school related.

In that case you can choose how you wish to resolve this :)

If the total length would become shorter than 7, you could add some spaces at the front or some predefined character, such as _:

```

"  Aa123"
"__Aa123"

```

As long as the rest of the program knows how to handle this then you're fine. When displaying the student number you could remove these characters from the front. Alternatively, you could also add them at the back of the student number.

---

### Post by PaulM1985 on 2011-04-28
If you are going to say that the name should be greater than 4, should you throw an exception to say that this is incorrect?  

You are printing a message to say this is wrong, but not dealing with the issue.  You are still trying to use a class which is not formed correctly given your rules on name and id lengths.

Paul

---

### Post by Drenriza on 2011-04-28
Can you give an example of this in the code? this dosent tell me much.

---

### Post by PaulM1985 on 2011-04-28
What I meant was that should you be creating objects with invalid information?  Should you be doing something like this:

```

Student s = null;
if (name.length() > 4 && id.length() > 3)
{
   s = new Student(name, id);
}
else
{
  System.out.println("Invalid arguments");
}

```

Then you know you have either created a valid student class or haven't created one at all.

Alternatively, you could have the validation in the Student constructor:
```

Student s = null;
try
{
  s = new Student(name, id);
}
catch (InvalidArgumentException e)
{
  System.out.println("Invalid arguments");
  s = null;
}

...

public Student(String name, String id) throws InvalidArgumentException
{
  if (name.length() < 4 || id.length() < 3)
  {
    throw new InvalidArgumentException();
  }
  
  myName = name;
  myId = id;
}

```

So in these cases it is not possible to create an invalid student object.

Paul

---

