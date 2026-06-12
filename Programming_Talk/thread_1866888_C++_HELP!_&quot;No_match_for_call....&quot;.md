---
title: "C++ HELP! &quot;No match for call....&quot;"
date: 2011-10-22
forum: Programming Talk
---

### Post by Synia on 2011-10-22
Hello, I'm writing a C++ program intended to manage the resources and duties in a flat.

I created a class call HomePage for users to login. I've also got another class called SelectionPage. Which are the Menus after the user got past the login. In my main functions, i wish to pass some data obtained by an instance of the HomePage class, to an instance of the SelectionPage class. 

I've been stuck here for half a day, Could someone please help?](*,)

[FONT=Comic Sans MS]_***Here's the error:***_
[/FONT]```
g++ C_Main.cpp C_HomePage.cpp C_SelectionPage.cpp -o Project
C_Main.cpp: In function &#8216;int main()&#8217;:
C_Main.cpp:17:93: error: no match for call to &#8216;(std::vector<std::basic_string<char> >) ()&#8217;
C_Main.cpp:17:122: error: no match for call to &#8216;(std::vector<std::basic_string<char> >) ()&#8217;
C_HomePage.cpp:290:41: error: no &#8216;std::vector<std::basic_string<char> > HomePage::getDutiesList()&#8217; member function declared in class &#8216;HomePage&#8217;
C_HomePage.cpp:294:44: error: no &#8216;std::vector<std::basic_string<char> > HomePage::getResourcesList()&#8217; member function declared in class &#8216;HomePage&#8217;
C_SelectionPage.cpp:9:144: error: declaration of &#8216;SelectionPage::SelectionPage(std::string, int, std::vector<std::basic_string<char> >, std::vector<std::basic_string<char> >, std::string)&#8217; outside of class is not definition
C_SelectionPage.cpp:9:146: error: expected unqualified-id before &#8216;{&#8217; token
make: *** [Project] Error 1

```[U][I][B]

Here is my main()[/B][/I][/U]
```
// Testing Home Page Functionality
#include "H_HomePage.h"
#include "H_SelectionPage.h"

using namespace std;

string initializationFile = "D_initialization.dat";
string flatMemberFile = "D_flatMember.dat";

**int main()**
   {
    HomePage frontEnd(initializationFile);             //Create Boundary Object
    system("clear");                                //Clear Terminal Screen
    frontEnd.login(flatMemberFile);
    
SelectionPage Menu(frontEnd.getManager(), frontEnd.getInitPoints(), frontEnd.getDutiesList(), frontEnd.getResourcesList(), frontEnd.getLoginName());
  Menu.showManagerMenu();
    return 0;
   }
```**Here's my constructor for SelectionPage class:**
```

.....
SelectionPage(string Manager, int Points, vector <string> dutiesList, vector <string> resourceList, string loginName);
......

```**Here's the implementation of the constructor for SelectionPage class:**
```

SelectionPage::SelectionPage(string newanager, int points, vector <string> newDutiesList, vector <string> newResourceList, string newLoginName);{
        manager = newManage;
        initPoints = points;
        dutiesList = newDutiesList;
        resourceList = newResourceList;
        loginName = newLoginName;
}
```

---

### Post by muteXe on 2011-10-22
Well firstly, you have a semi-colon at the end of your constructor parameter list in your last code section.

Also you pass in "newanager", but dont do anything with it?

do you '#include "vector" ' anywhere?

And initialise your strings like this: string initializationFile("D_initialization.dat");

---

