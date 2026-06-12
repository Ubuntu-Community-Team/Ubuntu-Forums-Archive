---
title: "Seeking help for a scheduling problem(Routine Generator)"
date: 2012-02-22
forum: New to Ubuntu
---

### Post by rpupa on 2012-02-22
I am doing my AI project , trying to implement a routine generator program in java. The program reads a file containing (subjectName: teacherName: ppw: tpp) where ppw is periods per week the subject should be taught in collage and tpp is the time per period
 ( for normal class =1 and for lab=3). The free time of teachers are stored in file with data(day:period) means in which period of which day the teacher is available for teaching. The program is supposed to generate a subject schedle for one section only satisfying the constraints of the free time and may be other. The collage runs from sunday to friday with seven periods each day. Now what i need is ideas about the most optimised way (algorithms hints) that i can search for the possibility and find the best solution.

---

### Post by blazemore on 2012-02-22
What have you tried?

The first thing to do is read in that text file and parse it, to store the data in some kind of Java data structure such as a class.

Can a mod please move this to Programming?

---

### Post by rpupa on 2012-02-26
> **blazemore said:**
> What have you tried?

The first thing to do is read in that text file and parse it, to store the data in some kind of Java data structure such as a class.

Can a mod please move this to Programming?
I have done that part , and the datas are stored in java map data structures. Now , i have the Maps of (subject,teacher),(subject,ttp),(subject,ppw), and (teacher,List<String>freetime).
Now the logical part is driving me nuts. I was busy trying to solve the problem so for some time i even forgot about i have posted in this forum. Well , the main problem i am facing is that there is not an efficient way to manage variables about the data. I mean the initial data which will not change till the end is made but while i allocate a period , i have to store that information in some variable, and that is really messed up. Is there any good way to code in the managed way for this particular problem.

---

### Post by rpupa on 2012-03-25
The project completed successfully. I implemented the depth first search with the use of heuristics to generate all the possible routines, and print them in tables in a html page. The project was not very perfect but still satisfactory...........thats all , thanks........

---

