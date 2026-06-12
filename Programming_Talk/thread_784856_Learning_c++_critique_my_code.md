---
title: "Learning c++: critique my code"
date: 2008-05-06
forum: Programming Talk
---

### Post by JohnnyBoy022 on 2008-05-06
Hey all, I'm learning c++ from a great tutorial at learncpp.com . I made a program that asks the user to enter how many courses they are taking, the name of each course, their current grade, the grade they want after taking the final exam, and the weight of the final exam. Then it calculates what grade they need on the final to get the grade they want. Take a look at my code please: what could be better, or anything that is totally wrong.

```

#include <iostream>
#include <string>
using namespace std;

struct class_t
{
    string strName;         // Name of the class
    float fCurGrade;        // Current grade in the class
    float fDesiredGrade;    // Desired grade after final
    float fWeight;          // Percent weight of the final (stored as a decimal between 0.0 and 1.0)
    float fFinalScore;      // The score on the final that is needed to maintain the desired grade
};

/* Function Declarations */
class_t* inputClasses(int &nClasses);                         // Asks the user to input their class data and returns an array of this data
void calculateFinalScores(class_t *paClasses, int nClasses);  // Accepts an array of class_t structs as an argument and calculates the necessary final score for each class_t

int main()
{
    // Holds the number of classes which is set by inputClasses()
    int nClasses;

    // Dynamically located array that holds each of the user's classes
    class_t *paClasses = inputClasses(nClasses);

    calculateFinalScores(paClasses, nClasses);

    // Print out the user's classes
    cout << "Name\t\tGrade\tDesired\tWeight\tScore Needed" << endl;
    for (int iii = 0; iii < nClasses; iii++)
    {
        cout << paClasses[iii].strName << "\t\t" << paClasses[iii].fCurGrade << "\t" <<
             paClasses[iii].fDesiredGrade << "\t" << paClasses[iii].fWeight << "\t" << paClasses[iii].fFinalScore << endl;
    }

    delete[] paClasses;
}

class_t* inputClasses(int &nClasses) {
    cout << "How many classes would you like to add? ";
    cin >> nClasses;
    cout << endl;

    // Dyamically allocate memore based on how many classes he wants.
    class_t *paNewClasses = new class_t[nClasses];

    for (int iii=0; iii < nClasses; iii++)
    {
        // Holds the name of the class so we can write it to the screen easily....
        string strClassName;

        cout << "What is the name of class " << iii + 1 << "? ";
        cin >> strClassName;
        paNewClasses[iii].strName = strClassName;

        cout << "What is your grade in " << strClassName << "? ";
        cin >> paNewClasses[iii].fCurGrade;

        cout << "What grade do you want in " << strClassName << "? ";
        cin >> paNewClasses[iii].fDesiredGrade;

        cout << "What is the weight of the final? ";
        cin >> paNewClasses[iii].fWeight;

        cout << endl;
    }

    return paNewClasses;
}

void calculateFinalScores(class_t *paClasses, int nClasses)
{
    for (int iii = 0; iii < nClasses; iii++)
    {
        // Very long formula to calculate what they need on the final to mantain the grade they want.
        paClasses[iii].fFinalScore = (paClasses[iii].fDesiredGrade - (paClasses[iii].fCurGrade*(1 - paClasses[iii].fWeight)))/paClasses[iii].fWeight;
    }
}

```

---

### Post by ultimatsz on 2008-05-06
shouldn't it be

using namespace::std;

?

i m just learning too.

sigh i have posting and editing issues...

---

### Post by Lux Perpetua on 2008-05-06
> **ultimatsz said:**
> shouldn't it be

using namespace::std;

?

i m just learning too.

sigh i have posting and editing issues...That is apparently a valid way to state the using declaration, but I think your syntax there is a bit confused. I think what happens is that **namespace::std** is parsed as {namespace{::std}}, and ::std is the same as std (since the namespace std itself belongs to the global namespace). Thus, it's better to write **namespace std**. **namespace::std** makes it look like the identifier **namespace** is literally a namespace that is being used to resolve the identifier **std**, which is nonsense. (**namespace** itself is not a namespace; it's just a C++ keyword.)

---

### Post by dwhitney67 on 2008-05-07
One little thing that is generally left out from the discussion of C++ is that struct and classes are the "same", with the exception that members in a struct are by default public, whereas in a class they are private.

Anyhow, a couple of things I would do with the code are:

1)  Declare both functions inside the struct; the inputClasses() function should be declared static.

2)  Rename the struct to use a name other than class_t.  This name is so similar to the class keyword.

3)  Abandon the "hungarian" notation; hardly nobody uses it anymore.  Damn M$ for supporting it in their "domain".

Defining a function in your struct would look something like:
[PHP]struct ClassSchedule
{
  public:
    static class_t * inputClasses();
    void calculateFinalScores();
  private:
    string strName;         // Name of the class
    float fCurGrade;        // Current grade in the class
    float fDesiredGrade;    // Desired grade after final
    float fWeight;          // Percent weight of the final (stored as a decimal between 0.0 and 1.0)
    float fFinalScore;      // The score on the final that is needed to maintain the desired grade
}[/PHP];

Then usage:
[PHP]int main()
{
  ClassSchedule * classes = ClassSchedule::inputClasses();
  classes->calculateFinalScores();
  delete []classes;
  return 0;
}[/PHP]

P.S.  If you are concerned about memory allocation failing, then you should consider placing the first two statements in the main() function within a try{} block; then add a catch{} block to capture the exception thrown by 'new'.

---

### Post by JohnnyBoy022 on 2008-05-07
Thanks for the suggestions.

That is interesting that you can have functions in a struct, I never knew that. I agree with what you said about the name "class_t". I rewrote it with the name "course" to distinguish it.

I was using the hungarian notation because that's what the tutorial used. I don't really like it either, it gets really annoying to type it out all the time.

And about the memory allocation, is it I good idea to use vectors for these types of things, so I don't have to worry about allocating the memory myself?

---

### Post by dwhitney67 on 2008-05-07
With the "simple" data that you have, there really is no need to allocate objects.  Below is an example that I was playing with.  Note that I did not complete calculateFinalGrade() to your specs... it merely outputs course information.

[PHP]
#include <vector>
#include <string>
#include <iostream>


//
//  CourseInfo
//
class CourseInfo
{
  public:
    bool getCourseInfo();
    friend std::ostream& operator<<( std::ostream &os, const CourseInfo &info );

  private:
    std::string	name;
    float	curGrade;
    float	desiredGrade;
    float	weight;
    float	finalScore;
};

bool
CourseInfo::getCourseInfo()
{
  static unsigned int courseNum = 1;

  std::cout << "Enter the name for course " << courseNum++ << " (or ctrl-d when done): ";
  std::cin >> name;

  if ( std::cin.eof() )
  {
    return false;
  }

  std::cout << "What is your grade in " << name << "? ";
  std::cin >> curGrade;

  std::cout << "What grade do you want in " << name << "? ";
  std::cin >> desiredGrade;

  std::cout << "What is the weight of the final? ";
  std::cin >> weight;
  std::cout << std::endl;

  return true;
}

std::ostream&
operator<<( std::ostream &os, const CourseInfo &info )
{
  os << "------------------------------------------------------" << std::endl;
  os << "Course Name         : " << info.name << std::endl;
  os << "Current Grade       : " << info.curGrade << std::endl;
  os << "Desired Grade       : " << info.desiredGrade << std::endl;
  os << "Weight of Final Exam: " << info.weight << std::endl;

  return os;
}


//
//  Courses
//
class Courses
{
  public:
    void addCourses();
    void calculateFinalScores() const;

  private:
    std::vector< CourseInfo > courseList;
};

void
Courses::addCourses()
{
  while ( !std::cin.eof() )
  {
    CourseInfo info;

    if ( info.getCourseInfo() )
    {
      courseList.push_back( info );
    }
  }
}

void
Courses::calculateFinalScores() const
{
  std::cout << std::endl << std::endl << "Course Listing:" << std::endl;

  for ( unsigned int i = 0; i < courseList.size(); ++i )
  {
    std::cout << courseList[i] << std::endl;
  }
}


//
//  main
//
int main()
{
  Courses courses;
  courses.addCourses();
  courses.calculateFinalScores();

  return 0;
}
[/PHP]

---

### Post by JohnnyBoy022 on 2008-05-07
Thanks for the info. The way you rewrote it does seem a lot different. If I understand it correctly, there is a struct called "Courses" that holds a bunch of "CourseInfo" structs in a vector. Anyways I rewrote the whole thing using a "Course" class. If you have any suggestions on making this code cleaner / simpler that would be great. I was wondering if I made a "Course List" class that holds a bunch of "Course" classes in a vector if that would simplify it. Of course, like you said with this simple data there really isn't a need for it but I am just trying to learn some concepts here. Thanks for the help

Also, how do you get that "PHP Code" box that highlights the colors in the forums?

[php]
#include <iostream>
#include <string>
using namespace std;

class Course
{
    private:
        string m_strName;        // Name of the course
        float m_fCurGrade;       // The current grade in the class
        float m_fDesiredGrade;   // Desired grade in the class
        float m_fFinalWeight;    // Weight of final (0.0 - 1.0)
        float m_fScoreNeeded;    // Score needed on final to maintain desired grade

        void calculateScoreNeeded()
        {
            m_fScoreNeeded = (m_fDesiredGrade - (m_fCurGrade*(1 - m_fFinalWeight))) / m_fFinalWeight;
        }
    public:
        void init(string strName, float fCurGrade, float fDesiredGrade, float fFinalWeight)
        {
            m_strName = strName;
            m_fCurGrade = fCurGrade;
            m_fDesiredGrade = fDesiredGrade;
            m_fFinalWeight = fFinalWeight;
            calculateScoreNeeded();
        }

        string getName() { return m_strName; }
        float getCurGrade() { return m_fCurGrade; }
        float getDesiredGrade() { return m_fDesiredGrade; }
        float getFinalWeight() { return m_fFinalWeight; }
        float getScoreNeeded() { return m_fScoreNeeded; }
};

/* Function Declarations */
Course* inputCourses(int nCourses);                   // Asks the user to input their class data and returns an array of this data
void printCourses(Course *paCourses, int nCourses);   // Prints an array of Courses

int main()
{
    int nCourses;                                   // Number of courses the user is taking
    cout << "How many courses are you taking? ";
    cin >> nCourses;
    cout << endl;

    Course *paCourses = inputCourses(nCourses);     // Array to hold each course
    printCourses(paCourses, nCourses);

    delete[] paCourses;
}

Course* inputCourses(int nCourses) {
    Course *paNewCourses = new Course[nCourses];

    for (int iii=0; iii < nCourses; iii++)
    {
        string strName;
        float fCurGrade, fDesiredGrade, fFinalWeight;

        cout << "What is the name of course " << iii + 1 << "? ";
        cin >> strName;

        cout << "What is your grade in " << strName << "? ";
        cin >> fCurGrade;

        cout << "What grade do you want in " << strName << "? ";
        cin >> fDesiredGrade;

        cout << "What is the weight of the final? ";
        cin >> fFinalWeight;
        cout << endl;

        paNewCourses[iii].init(strName, fCurGrade, fDesiredGrade, fFinalWeight);
    }

    return paNewCourses;
}

void printCourses(Course *paCourses, int nCourses)
{
    cout << "Name\t\tGrade\tDesired\tWeight\tScore Needed" << endl;

    for (int iii=0; iii < nCourses; iii++)
    {
        cout << paCourses[iii].getName() << "\t\t" << paCourses[iii].getCurGrade() << "\t" <<
                paCourses[iii].getDesiredGrade() << "\t" << paCourses[iii].getFinalWeight() << "\t" <<
                paCourses[iii].getScoreNeeded() << endl;
    }
}
[/php]

---

### Post by mssever on 2008-05-07
> **JohnnyBoy022 said:**
> Also, how do you get that "PHP Code" box that highlights the colors in the forums?
Use [noparse][php][/noparse] tags.

---

### Post by dwhitney67 on 2008-05-08
> **JohnnyBoy022 said:**
> Thanks for the info. The way you rewrote it does seem a lot different. If I understand it correctly, there is a struct called "Courses" that holds a bunch of "CourseInfo" structs in a vector. Anyways I rewrote the whole thing using a "Course" class. If you have any suggestions on making this code cleaner / simpler that would be great. I was wondering if I made a "Course List" class that holds a bunch of "Course" classes in a vector if that would simplify it. Of course, like you said with this simple data there really isn't a need for it but I am just trying to learn some concepts here. Thanks for the help

Also, how do you get that "PHP Code" box that highlights the colors in the forums?

I redesigned the code I presented yesterday, hopefully making it somewhat easier to understand.  I've removed the old code and pasted in its place the update.  Please see my previous post.

By the way, your thoughts of splitting the Course class from the Course List is spot on; it is what inspired me to redesign the code.

Concerning the pretty display of code, as mssever pointed out, you need to use PHP tags.  There's a handy button for inserting PHP tags around selected text (or code).  The button is located above, to the far right of the editor.

---

