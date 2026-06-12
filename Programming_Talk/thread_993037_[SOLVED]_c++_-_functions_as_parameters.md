---
title: "[SOLVED] c++ - functions as parameters"
date: 2008-11-25
forum: Programming Talk
---

### Post by Despot Despondency on 2008-11-25
Hi, I'm writing a function which takes a function as a parameter, which in turn takes another function as a parameter, e.g.

```

void general_write_analysis(std::ostream& out, const std::string& name,
			    double analysis(const std::vector<Student_info>&, double second_function(const Student_info&)),
                    const std::vector<Student_info>& did,
                    const std::vector<Student_info>& didnt);


```

I believe I'm not meant to give names for the parameters of the analysis function (which is the third parameter of the general_write_analysis function). Is this right? If so, what do I write instead of second_function? Is it something like

```

void general_write_analysis(std::ostream& out, const std::string& name,
			    double analysis(const std::vector<Student_info>&, double (*f)(const Student_info&)),
                    const std::vector<Student_info>& did,
                    const std::vector<Student_info>& didnt);


```

Cheers for any help.

---

### Post by monkeyking on 2008-11-25
It looks a bit complicated, :)
can you give us all your function prototypes.

---

### Post by dwhitney67 on 2008-11-25
Do you really need this complexity in your code?  I would strongly suggest that you re-examine your design.

If you are stubborn and want to continue with your approach, then I recommend that you use typedefs to define your functions.  It makes life a lot easier.

[php]
#include <algorithm>
#include <string>
#include <vector>
#include <iostream>


struct StudentInfo
{
  StudentInfo(int id) : id(id) {}
  int id;
};

typedef double (*SecondFunction)(const StudentInfo&);
typedef double (*FirstFunction)(const std::vector<StudentInfo>&, SecondFunction);


double SF(const StudentInfo& info)
{
  return 10;
}

double FF(const std::vector<StudentInfo>& info, SecondFunction sf)
{
  std::for_each(info.begin(), info.end(), sf);
  return 5 * sf(info[0]);
}

double analysis(const std::ostream& out,
                const std::string& name,
                FirstFunction ff,
                std::vector<StudentInfo>& did,
                std::vector<StudentInfo>& didnt)
{
  return ff(did, SF);
}

int main()
{
  std::string              name("Confucious");
  std::vector<StudentInfo> did;
  std::vector<StudentInfo> didnt;

  did.push_back(StudentInfo(12345));

  double result = analysis(std::cout, name, FF, did, didnt);

  std::cout << "result = " << result << std::endl;

  return 0;
}
[/php]

---

### Post by Despot Despondency on 2008-11-25
Thanks for your responses. I'm not particularly stubborn, it's just an exercise from a book. Basically, there are three functions in the code that do almost the exact same thing,

```

double optimistic_median_analysis(const vector<Student_info>& students)
{
        vector<double> grades;

        transform(students.begin(), students.end(),
                  back_inserter(grades), optimistic_median);
        return median(grades);
}

double average_analysis(const vector<Student_info>& students)
{
	vector<double> grades;

	transform(students.begin(), students.end(),
	          back_inserter(grades), average_grade);
	return median(grades);
}

double median_analysis(const vector<Student_info>& students)
{
	vector<double> grades;

	transform(students.begin(), students.end(),
	          back_inserter(grades), grade_aux);
	return median(grades);
}

```

where optimistic_median, average_grade and grade_aux are just functions that work out a students grade in different ways. Now the book asks for these three to be written into a single function, which I did as follows

```

double general_analysis(const vector<Student_info>& students, double grading_scheme(const Student_info&)){
  
  vector<double> grades;

    transform(students.begin(), students.end(), back_inserter(grades), grading_scheme);

    return median(grades);
}

```

I then had to change the write analysis function which was originally

```

void write_analysis(ostream& out, const string& name,
                    double analysis(const vector<Student_info>&),
                    const vector<Student_info>& did,
                    const vector<Student_info>& didnt)
{
	out << name << ": median(did) = " << analysis(did) <<
	               ", median(didnt) = " << analysis(didnt) << endl;
}

```

to 

```

void general_write_analysis(ostream& out, const string& name,
			    double analysis(const vector<Student_info>&, double g_s(const Student_info&)),
			    double grading_scheme(const Student_info&),
                    const vector<Student_info>& did,
                    const vector<Student_info>& didnt)
{
  out << name << ": median(did) = " << general_analysis(did, grading_scheme) <<
    ", median(didnt) = " << general_analysis(didnt, grading_scheme) << endl;
}

```

I've got everything working, it turns out the problem was something else. But is this overly complex? How would you go about instead?

---

### Post by dwhitney67 on 2008-11-25
It seems that no matter which approach one takes, that the 3 different analysis functions must be called.  And you are probably doing this indirectly in your main program by passing each analysis function and the wrapper-function general_analysis() to general_write_analysis(), then printing the result that is generated by the function median().

Is it overly complex? Nope.  Is it simple?  Nope.  The solution falls into the median I suppose.

Btw, what book are you reading?

---

### Post by Despot Despondency on 2008-11-25
Accelerated c++ by Koenig and Moo. It's pretty good. I've found it has a couple of things missing that I would have liked explained, like my initial problem, but it's easy to read and nowhere near as boring as most programming books. 

Cheers for your help btw.

---

