---
title: "Cobertura code coverage issue"
date: 2011-11-18
forum: Programming Talk
---

### Post by miten.morakhia on 2011-11-18
Hi there, 
 
We are using sonar in our project. Sonar by default uses cobertura for determining code coverage. My application is divided into multiple projects and each of them having their own pom.xml files. So as I understand, the cobertura stats will also be calculated on per project basis. My pom.xml has following config 
 
<reporting> 
<plugins> 
<plugin> 
<groupId>org.codehaus.mojo</groupId> 
<artifactId>cobertura-maven-plugin</artifactId> 
<version>2.4</version> 
</plugin> 
 
The problem that I am facing is I have a JUnit test class in project A which calls and tests certain classes in project B. However, when I look at the cobertura report for project B, it shows 0% line coverage. Coverage report for project A anyways would not contain the details about project B. Is there some configuration required for getting the correct code coverage? 
 
I suspected it might be due to cobertura instrument details not getting merged correctly hence I tried adding the following in the pom.xml files of project A & B but still the results were no different. 
 
<cobertura-merge> 
<fileset dir="${basedir}"> 
<include name="**/cobertura.ser" /> 
</fileset> 
</cobertura-merge> 
 
In any case, I think Sonar should be smart enough to merge the results. Any specific configuration changes that I might need to make in order to get the correct code coverage figures? 
 
This is important for us because we do not want to lag behind the other teams who are faring much better code coverage. We know that a lot of code has been covered via unit and integration testing classes but don't have the numbers to prove it! 
 
Has anyone faced similar issue in the past? 
 
Thanks, 
Miten

---

### Post by fct on 2011-11-18
You shouldn't be using tests in A for covering B project's use cases. B should have its own tests within. Same for A.

It's not to be expected of tools like sonar to automatically merge results, since they adhere to recommended practices and expect the tests included in the project they should be testing in the first place.

---

### Post by miten.morakhia on 2011-12-11
What if you are testing the whole application using the Integration test class? You are bound to call components present in various modules, so having the test classes residing in individual modules is at times not possible. 
 
So, should this go down as one of the limitations of the code coverage tool?

---

### Post by r-senior on 2011-12-12
I agree with fct. Each project should have self-contained unit tests.

If project A depends on classes in project B and I change something in B that breaks tests in A but not in B, that suggests to me that i am missing tests in B or A is using B incorrectly. The tests in B, in combination with a high level of reported coverage, should give me confidence that B is as specified. If A fails, I don't want the uncertainty of whether the fault is in A or B. It should be a fault in A.

If it's not possible to test B without elements of A and not possible to test A without elements of B, that suggests to me that there is excessive coupling between the projects and some refactoring is required.

Integration testing is still valuable of course but the objective should be to test A's correct use of B, not to test whether B is correct. Test failures in A should indicate a problem in A, not in B.

---

