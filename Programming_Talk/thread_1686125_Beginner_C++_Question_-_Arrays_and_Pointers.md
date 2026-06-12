---
title: "Beginner C++ Question - Arrays and Pointers"
date: 2011-02-11
forum: Programming Talk
---

### Post by abraxyz on 2011-02-11
I'm trying to figure out this exercise from the C++ Primer Plus book:

[FONT=Courier New][I]Write a C++ program that requests and displays information as shown in the following
example of output:
What is your first name? Betty Sue
What is your last name? Yew
What letter grade do you deserve? B
What is your age? 22
Name: Yew, Betty Sue
Grade: C
Age: 22
Note that the program should be able to accept first names that comprise more than one
word. Also note that the program adjusts the grade downward&#8212;that is, up one letter.
Assume that the user requests an A, a B, or a C so that you don&#8217;t have to worry about the
gap between a D and an F.[/I][/FONT]

The thing is, I'm not supposed to use branching statements, so basically I'm having a hard time incrementing the grade value. I know I should use something like:

```
char grades[4] = {'A', 'B', 'C', 'D'};
char * pt = grades;
```And eventually:

```
pt = pt + 1;
cout << pt[*element number*] << endl;
```So, how do I read the grade character and later increment it using this method? I was also thinking about using enumerators:

```
enum grades {A, B, C, D};
```But, the user would have to input an int type instead of grade letter. I guess...

Well, thanks for your help

---

### Post by MadCow108 on 2011-02-11
try using two arrays.

you can also do it without arrays. have a look at the ascii table

---

### Post by worksofcraft on 2011-02-11
remember that if you add 1 to a character the result becomes an integer and if you increment the character it stays a character.
so the following two produce different output:
[php]
	char iGrade;
	cout << "desired grade:";
	cin >> iGrade;

	cout << "actual grade: " << iGrade+1 << endl;
	cout << "actual grade: " << ++iGrade << endl;
[/php]

---

### Post by abraxyz on 2011-02-11
```
cout << "actual grade: " << ++iGrade << endl;
```**@worksofcraft**
That looks perfect, but nowhere in the chapter is mentioned, so you're the first one I'm learning it from. I guess I'm going to encounter it in the latter chapters.

**@MadCow108**
Silly me, I totally forgot to take a glimpse at the ASCII table and discover that the three letters have the consecutive codes. So, i immediately came up with this:

```
cout << "What letter grade do you deserve?" << endl;
char grade;
cin >> grade;
cout << "Grade: " << char(grade +1) << endl;
```[FONT=Courier New][SIZE=2]Thanks for the help![/SIZE][/FONT]

---

