---
title: "Passing secondary command inputs to the shell though a script"
date: 2014-01-25
forum: Programming Talk
---

### Post by Keith_Benjamin on 2014-01-25
I'm in a programming class that autogrades software with a script. It does so by passing keyboard input to the program after execution. I'd like to make a script that does the same thing so I can test my software before submission but can't seem to find the right information.

I'm adding the code in case it might help someone understand what I need. Essentially, this is just a simple GPA calculator that loops until 0 0 is input and then outputs a student's name and GPA. All information is read from the keyboard each run so I'd like to have a script that runs it several times with different data to make sure it passes a many cases as I can think of (I'm not given all the test cases before submission of the assignment.)

```

#include <iostream>
#include <iomanip>
#include <string>


using namespace std;




struct GradeValue {
    string  grade;
    double value;
};


const GradeValue gradeValues[] = {
    { "A", 4.0 },
    { "A-", 3.7 },
    { "B+", 3.3 },
    { "B", 3.0 },
    { "B-", 2.7 },
    { "C+", 2.3 },
    { "C", 2.0 },
    { "C-", 1.7 },
    { "D+", 1.3 },
    { "D", 1.0 },
    { "F", 0.0 }
};


struct Student
{
    string name;
    int credits;
    double qualityPoints;
};




double findGradeValue(const GradeValue table[], int tableSize, string grade)
{
    for (int i = 0; i < tableSize; i++)
    {
        if (grade == table[i].grade)
            return table[i].value;
    }
    return 0.0;
}


void addGrade(Student& aStudent, string grade, int credits)
{
    if (credits < 0)
        credits = 0;
    aStudent.credits += credits;
    aStudent.qualityPoints += findGradeValue(gradeValues, 11, grade) * credits;
}


double computeGPA(const Student& aStudent)
{
    if (aStudent.credits == 0)
        return 0.0;
    else return aStudent.qualityPoints / aStudent.credits;
}


void gpaCalc(istream& input, ostream& output)
{
    Student student;
    getline(input, student.name);
    input >> student.credits >> student.qualityPoints;
    string grade;
    int credits;
    input >> grade >> credits;
    while (grade != "0" && credits != 0)
    {
        addGrade(student, grade, credits);
        input >> grade >> credits;
    }
    double gpa = computeGPA(student);
    output << student.name << ' '
        << fixed << setprecision(2) << gpa << endl;
}




int main(int argc, char** argv)
{
    gpaCalc(cin, cout);
    return 0;
}

```

---

### Post by trent.josephsen on 2014-01-25
I like the way your code is organized -- each function does one thing, is short, and is appropriately named. Very nice to read (once I fixed the indentation; use ```
 tags when you post to maintain formatting). There are some stylistic choices that differ from mine but I'm used to C, not C++, and you didn't ask for a code review.

I will observe, though, that you have no way to tell whether findGradeValue() succeeded or not -- i.e., a grade of "a", "AA", or "Z" (all plausible typos for "A") is marked failing. If my grades were the ones being calculated, I'd want the program to warn about that :)

Now, on to the question at hand. If you want to write a script that runs the program, examines the output, and checks it against the correct output, you can do that. But it's quite simple to run the program by itself with input from a file instead of typing it in every time, and a full-blown test script is probably unnecessary for such a small program. Just put the data in a file, and use the "<" input redirection operator when you run your program from the command line, like so:

[code]% cat file1
Jack Ryan
0 0
A 3
B- 1
B 3
A 1
A 3
A- 3
B+ 3
0 0
% ./grades <file1
Jack Ryan 3.57
```
If you're using an IDE like Code::Blocks or something, it is more complicated to do stuff like this, and that's one reason I don't like IDEs. Nevertheless it is still possible to do it the old fashioned way through a terminal if you can figure out where your IDE hides the compiled executable file.

---

### Post by Keith_Benjamin on 2014-01-25
Great! Thanks - I had tried a line insertion but I did it with the actual input vice a file. Thanks for pointing out my mistake - it was driving me nuts! And so simple too!

I agree it handles things a little screwy. The whole catch is that you have know idea what the test parameters are before you submit your code. BUT they have a precompiled answer for you to run tests against. The 'correct' code, according to the professor, didn't check for case-sensitivity or anything like that so I just made my code do the same thing.

Anyway, Thanks again!

---

