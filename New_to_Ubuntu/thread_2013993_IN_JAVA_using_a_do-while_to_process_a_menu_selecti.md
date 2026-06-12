---
title: "IN JAVA using a do-while to process a menu selection"
date: 2012-07-01
forum: New to Ubuntu
---

### Post by ndsun on 2012-07-01
I am a beginner in java ,when i run code below,
//using a do-while to process a menu selection
class Menu
{
 public static void main(String args[])
  throws java.io.IOException
  {
   char choice;
   do
   {
    System.out.println("Help on: ");
    System.out.println("1.if ");
    System.out.println("2.switch ");
    System.out.println("3.while ");
    System.out.println("4.do-while ");
    System.out.println("5.for\n ");
    System.out.println("Choose one: ");
    choice=(char) System.in.read();
   }while(choice <'1'||choice>'5');
   System.out.println("\n");
   switch(choice)
   {
    case '1':
    System.out.println("The if:\n ");
    System.out.println("if(condition) statement;");
    System.out.println("else statement;");
    break;
    case '2':
    System.out.println("The switch:\n ");
    System.out.println("switch(expression) { ");
    System.out.println("case constant:");
    System.out.println("statement sequence");
    System.out.println("break;");
    System.out.println("//...");
    System.out.println("}");
    break;
    case '3':
    System.out.println("The while:\n");
    System.out.println("while(condition) statement;");
    break;
    case '4':
    System.out.println("The do-while:\n");
    System.out.println("do {");
    System.out.println(" statement;");
    System.out.println("while(condition);");
    break;
    case '5':
    System.out.println("The for:\n");
    System.out.println("for(init;condition;iteration)");
    System.out.println(" statement;");
    break;
  }
 }
}

when I run above code with the help of command prompt,it appears
C:\Java\jdk1.7.0\bin>javac Menu.java

C:\Java\jdk1.7.0\bin>java Menu
Help on:
1.if
2.switch
3.while
4.do-while
5.for

Choose one:
9
Help on:
1.if
2.switch
3.while
4.do-while
5.for

Choose one:
Help on:
1.if
2.switch
3.while
4.do-while
5.for

Choose one:
Help on:
1.if
2.switch
3.while
4.do-while
5.for
           Please tell me why after entering 9, 3 times such help menu is appearing ,while it should appear only one time.(it is happening with all values which're <1 and >5).

---

