---
title: "convert java code to mips"
date: 2010-10-14
forum: Programming Talk
---

### Post by mohm200 on 2010-10-14
package javaapplication1;
public class Main{
 public static void main(String args[]){
  // declare two arrays of char
         char []a ;
         char []b;
// Two Strings to be check
         String s1 = "talk";
         String s2 = "took";
// max to define the max String to be used in compare
         int max=0;
// diff to find the differance betwwen two String
         int diff=0;
//Determaine the max string
         if(s1.length()>s2.length()){
              max =s1.length();
                                    }
              else max =s2.length();
// build a array with lenght max
         a = new char [max];
         b = new char [max];
//Represent each string as an array of characters
         for(int i=0 ; i<s1.length() ; i++){
              a[i]=s1.charAt(i);
                                           }
//**************************************************************************//
         for(int i=0 ; i<s2.length() ; i++){
              b[i]=s2.charAt(i);
                                           }
//Comparing each character in the first string with the character at the same index in the second string
      for (int i=0 ; i<max ;i++){
            if (a[i]== b[i]);
                else diff+=1;
                                }
       System.out.println("  diff is = " + diff );
//method to find the diff in lenght
              diff(s1,s2);
                                              }

      //////////////////METHODS//////////////////////////////////////
        ////method to find the diff in lenght
        public static void diff(String c , String d){
             int a = c.length();
             int b = d.length();
             int differance =a-b;
             int max;
             
             if (a>b){
                 max =a;
                     }
                else max=b;

            if(differance > 0)
                      System.out.println( "  The difference between the two strings in length = " + differance);
                 else System.out.println( "  The difference between the two strings in length = " + (differance)*-1);
                                                     }
                                                     }

---

