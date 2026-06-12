---
title: "Netbeans Doesn't Recognize Classes"
date: 2012-01-23
forum: Programming Talk
---

### Post by Tk007LwZFJW5ej on 2012-01-23
[RIGHT][LEFT]I  have GradeBook.java and GradeBookTest.java in a project called AD1. The main method in GradeBookTest.java creates a GradeBook object:  

 
  ```

public class GradeBookTest 
{    // main method begins program execution    
   public static void main( String args[] )    
      {        // create GradeBook object and initialize data       
         GradeBook gradeBook1 = new GradeBook

```and there is a little warning symbol on the line containing the instantiation:  "cannot find symbol symbol: class GradeBook." 

Also, netbeans can't find my main class (I'm new to netbeans so I assume this is the class holding the main method?) even though I specified it as GradeBookTest in Project->Properties->Run. Please see the attached image.

[/LEFT]
  
[/RIGHT]

---

### Post by ofnuts on 2012-01-23
> **StarKid said:**
> [RIGHT][LEFT]I  have GradeBook.java and GradeBookTest.java in a project called AD1. The main method in GradeBookTest.java creates a GradeBook object:  

 
  ```

public class GradeBookTest 
{    // main method begins program execution    
   public static void main( String args[] )    
      {        // create GradeBook object and initialize data       
         GradeBook gradeBook1 = new GradeBook

```and there is a little warning symbol on the line containing the instantiation:  "cannot find symbol symbol: class GradeBook." 

Also, netbeans can't find my main class (I'm new to netbeans so I assume this is the class holding the main method?) even though I specified it as GradeBookTest in Project->Properties->Run. Please see the attached image.

[/LEFT]
  
[/RIGHT]

```
GradeBook gradeBook1 = new GradeBook
```isn't correct.This is what your little warning is all about. So GradeBookTest doesn't compile, so there is no .class (compiled Java) with a main() in it in the project.

---

### Post by Tk007LwZFJW5ej on 2012-01-23
> **ofnuts said:**
> ```
GradeBook gradeBook1 = new GradeBook
```isn't correct.This is what your little warning is all about. So GradeBookTest doesn't compile, so there is no .class (compiled Java) with a main() in it in the project.

No, there are parentheses there. I just didn't post the entire GradeBookTest.java file because I didn't ant to make a huge post. Here it is:

```

public class GradeBookTest
{
   // main method begins program execution
   public static void main( String[] args )
   { 
      // create GradeBook object and initialize data
      GradeBook gradeBook1 = new GradeBook( "ENG CS 60 JAVA Programming", "Judy Jones" ); 
      
     // display change instructor name
      System.out.printf( "\nChanging instructor name from %s to Sonny Huang\n", gradeBook1.getInstructorName());
    // call setInstructorName function to set a new name.
      gradeBook1.setInstructorName( "Sonny Huang" ); 

    //display change course name
      System.out.printf( "Changing course name from %s to CISP401 Object Oriented Programming with JAVA\n\n", gradeBook1.getCourseName());
     // call setCourseName function to set a new name.
      gradeBook1.setCourseName( "CISP401 Object Oriented Programming with JAVA" ); 

      gradeBook1.displayMessage(); // display welcome message
   } // end main

} // end class GradeBookTest

 
```

and GradeBook.java:

```

public class GradeBook
{
   private String courseName; // course name for this GradeBook
   private String instructorName; //course instructor's name

   // constructor initializes courseName and instructorName with Strings supplied as arguments
   public GradeBook( String name, String instructor )
   {
      courseName = name; // initializes courseName
      instructorName = instructor; //initializes instructorName
   } // end constructor

   // method to set the course name
   public void setCourseName( String name )
   {
      courseName = name; // store the course name
   } // end method setCourseName

   // method to retrieve the course name
   public String getCourseName()
   {
      return courseName;
   } // end method getCourseName

   // display a welcome message to the GradeBook user
   public void displayMessage()
   {
      // this statement calls getCourseName to get the 
      // name of the course this GradeBook represents
      System.out.printf( "Welcome to the grade book for\n%s!\n", 
         getCourseName() );
   } // end method displayMessage
   
   //method to set course instructor's name
   public void setInstructorName(String name)
   {
       instructorName = name;
   }
   
   //method to retrieve course instructor's name
   public String getInstructorName()
   {
      return instructorName;
   }

} // end class GradeBook

```

---

### Post by Tk007LwZFJW5ej on 2012-01-23
Figured it out. My two java files were pre-existing, and I was adding them to the project incorrectly. I was setting the folder they were in as the project folder, which added them to the project, but not as source files (although I don't understand what sort of files netbeans thought they were).

To create the project correctly, I had to select this folder in the Existing Sources dialog of the New Project wizard.

---

