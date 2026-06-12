---
title: "python while loop not working?"
date: 2015-02-20
forum: Programming Talk
---

### Post by Ethan_Wright on 2015-02-20
I'm relatively new to programming, i've been learning stuff through treehouse and i wanted to try out what i have learned so I made a simple "login" program

 email = input("what email would you like to use?:\n")

 print("Email accepted")
 

 name = input("\nWhat user name would you like to use?:\n")
 print("User name accepted.")
 

 Pass = input("\nWhat password would you like to use?:\n")
 print("Password accepted. ")
 

 login = input("\n1.log in   2.Username/password recovery:\n")

 

 if login == "2":
     recovery = input("\nplease enter your email to recover your username/password:\n")
     while recovery != email:
         print("incorrect email")
         recovery = input("\nplease enter your email to recover your username/password:\n")
     if recovery == email:
         print("\n"+name+"\n"+Pass)
         username_login = input("\nUser name:\n")
         password_logn = input("\nPassword:\n")
         
 if login == "1":
      print("\n\t<log in>")
      username_login = input("\nUser name:\n")
      password_logn = input("\nPassword:\n")
     
      print("\n\t<LOGGED IN>")

the problem is I want to make it so if you don't enter either 1 or 2 at this point login = input("\n1.log in   2.Username/password recovery:\n") the scripts will say print("incorrect value entered, please enter one of the numerical values above") then it will pull up this input string login = input("\n1.log in   2.Username/password recovery:\n").
I've tried a while loop, while login != "1" or "2": print("test") but when i did that it still seemed to not recognise 1 as 1 or 2 as 2 and still printed test. I also tried i with and instead of or and that seemed to only work for the first numberI put in so it worked for 1 but not for 2.
If the lovely people of the ubuntu forum could help me that would be great.

---

### Post by DCO on 2015-02-20
could you re post that using the [CODE] tag? It would be easier to make you you have your tabs right (having things tabbed wrong can cause serious issues in python)

---

### Post by Ethan_Wright on 2015-02-20
```
email = input("what email would you like to use?:\n")

 print("Email accepted")
 

 name = input("\nWhat user name would you like to use?:\n")
 print("User name accepted.")
 

 Pass = input("\nWhat password would you like to use?:\n")
 print("Password accepted. ")
 

 login = input("\n1.log in   2.Username/password recovery:\n")

 

 if login == "2":
     recovery = input("\nplease enter your email to recover your username/password:\n")
     while recovery != email:
         print("incorrect email")
         recovery = input("\nplease enter your email to recover your username/password:\n")
     if recovery == email:
         print("\n"+name+"\n"+Pass)
         username_login = input("\nUser name:\n")
         password_logn = input("\nPassword:\n")
         
 if login == "1":
      print("\n\t<log in>")
      username_login = input("\nUser name:\n")
      password_logn = input("\nPassword:\n")
     
      print("\n\t<LOGGED IN>")
```

---

### Post by DCO on 2015-02-20
yeah that extra space on all the lines after email caused the error (as I understood it from your original post.) I fixed it for you here:
```
email = input("what email would you like to use?:\n")

print("Email accepted")


name = input("\nWhat user name would you like to use?:\n")
print("User name accepted.")


Pass = input("\nWhat password would you like to use?:\n")
print("Password accepted. ")


login = input("\n1.log in   2.Username/password recovery:\n")



if login == "2":
    recovery = input("\nplease enter your email to recover your username/password:\n")
    while recovery != email:
        print("incorrect email")
        recovery = input("\nplease enter your email to recover your username/password:\n")
    if recovery == email:
        print("\n"+name+"\n"+Pass)
        username_login = input("\nUser name:\n")
        password_logn = input("\nPassword:\n")
```

---

### Post by DCO on 2015-02-20
I have a question I just thought of, what are you using to write your code?

---

