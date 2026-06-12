---
title: "Errors compiling java on iPhone"
date: 2009-12-18
forum: Programming Talk
---

### Post by ChodeOfDoom on 2009-12-18
Hey guys,
     I recently jailbroke my iPhone and was experimenting with java on it. However, as I progressively moved to more and more complicated programs, the compiler (jikes) started giving me semantic errors.  For example, in the second pogram I made, I copie the script from an exisiting program that pretty much just asked or an integer input.  Now in the line where in have
(variable)=input.nextInt();
the compiler tells me that 
"no accessible field name 'input' was found in type '(my program name)'"
would anybody here who has experience with this please help me out?

Thanks,
Chode

---

### Post by Some Penguin on 2009-12-18
It's telling you that you didn't define a member variable named 'input'.  Obviously, with just the code you showed there, it's impossible for any of us to know whether you did.

Do you disagree with it?

---

