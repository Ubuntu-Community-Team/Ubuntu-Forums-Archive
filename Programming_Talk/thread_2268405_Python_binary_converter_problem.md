---
title: "Python binary converter problem"
date: 2015-03-08
forum: Programming Talk
---

### Post by Ethan_Wright on 2015-03-08
im having trouble with this code ```
 con_input  = input("1.binary-decimal 2.binary-ASCII 3.binary-hexadecimal\n-\n4.decimal-binary 5.ASCII-binary 6.hexadecimal-binary\n> ")
 

 

 if con_input != "1" and con_input != "2" and con_input != "3" and con_input != "4" and con_input != "5" and con_input != "6":
     print("enter one of the numerical options")
 

 def code_conversion():
     if con_input == "1":
         print("separate bytes by a space")
         binary_input = input("enter binary:\n> ")
         int(binary_input)
         while len(binary_input) < 8:
             print("please enter a 8bits or higher")
             binary_input = input("enter binary:\n> ")
         while "1" not in binary_input and "0" not in binary_input:
             error = ("Please enter binary")
             print("\nseparate bytes by a space")
             binary_input = input("enter binary:\n> ")
         binary_input = list(binary_input)
         if [0] in binary_input == '1':
             binary_input[0] = '128'
         print(binary_input)           
                  
 code_conversion()     

 
```


im trying to turn items in the list into their binary coversion depending if they are a 0 or a 1 however when I try it it does not seem to change to the 128 it just stays as the 1.

any help with this would be greatly appreciated :D

---

