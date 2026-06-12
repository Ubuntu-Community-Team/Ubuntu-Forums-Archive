---
title: "Simple Gradebook program"
date: 2014-02-14
forum: New to Ubuntu
---

### Post by eli5 on 2014-02-14
I'm really new to java, and ubuntu itself, but I am trying to learn as much as I can. I am working on a simple gradebook program for my programming class, but I'm stuck. This is what I have so far.
[PHP]import java.util.scanner;
public class Homework2 {

    public static void main(String[] args)
    {    System.out.println("1 Average grades for a new student, 2 Quit");
    Scanner user_input = new Scanner(System.in);

    int choice = user_input.nextInt();
    if (choice == 1){
        Average ();    }
    else if(choice == 2){
        quit();
    }
    public void average();
        String student;
            System.out.println("Enter student's name: ");
        student = input.nextInt();
                    }
    public static void menu(){
    System.out.println("
        int studentName = 0        
}[/PHP]

After the user inputs the student's name, these are the following instructions to the assignment

4. Print instructions telling the user the order the grades will be entered in and 
what to enter to indicate that there are no more grades to enter for that category. 
 
5. For each category print what category of grade they are entering then the user 
is repeatedly prompted to enter a grade and this keeps going until a “-1” is 
entered. 
 
6. Once the user has entered a “-1” for a category move on to the next category. 
 
7. Once grades have been entered for all three categories, the student’s name 
and current average is printed to the screen. 
 
8. Repeat steps 1 through 6 until the user enters “2” at the main menu to indicate 
that the user has no more students to grade, and the program should terminate. 

A little help? I've been fumbling around for hours.

---

