---
title: "More C++ Questions from me on functions"
date: 2007-10-23
forum: Programming Talk
---

### Post by TreeFinger on 2007-10-23
I have just completed a homework problem for my C++ class. I am pretty happy with how it turned out. I have never used more than 2 functions in one program before (main and another). This program takes 5 user inputs of scores (must be between 0 and 100), drops the lowest and finds the average. I'd like to share the code with all of you and have you comment on it. I'd like to know about the readability and what I could do to make it better. What I'd like the most comments on is the findLowest() function. I don't like having all of those if statements. There must be a way to use a loop to do the same thing. Thanks for the time.

```

#include <iostream>
#include <iomanip>
using namespace std;

int getScore();
void calcAverage(int, int, int, int, int);
int findLowest(int, int, int, int, int);

int main() {
	cout << "Enter 5 test scores. The lowest of the five will be dropped.\n";
	//Assign user inputted scores to variables using getScore()
	int sc1 = getScore(), sc2 = getScore(), sc3 = getScore(), sc4 = getScore(), sc5 = getScore();
	//Calls calcAverage() with user inputted scores as parameters
	calcAverage(sc1, sc2, sc3, sc4, sc5);

return 0;
}

int getScore() { //Obtains user inputted test scores
	int score;
	cout << "Enter Score between 0-100: ";
	cin >> score;
	while ( score < 0 || score > 100 ) { //Input validation
		cout << "Score must be between 0 and 100: ";
		cin >> score;
	}
return score;
}

void calcAverage(int sc1, int sc2, int sc3, int sc4, int sc5) { //Calculates average of 4 highest test scores
	double avg;
	cout << "I will now find the average of the 4 top scores entered.\n";
	avg = ( sc1 + sc2 + sc3 + sc4 + sc5 - findLowest(sc1, sc2, sc3, sc4, sc5) ) / 4.0; //Sums total of all scores entered then subtracts value returned by findLowest()
	cout << showpoint << fixed << setprecision(2) << avg << endl;
}

int findLowest(int sc1, int sc2, int sc3, int sc4, int sc5) { 	//Finds lowest test score
	int lowScore = sc1; //Initalizes low score to first number entered
	if ( sc2 < lowScore )
		lowScore = sc2;
	if ( sc3 < lowScore )
		lowScore = sc3;
	if ( sc4 < lowScore )
		lowScore = sc4;
	if ( sc5 < lowScore )
		lowScore = sc5;
return lowScore;
}

```

---

### Post by CptPicard on 2007-10-23
Just replace your input variables with an array. :)

---

### Post by Jessehk on 2007-10-23
I would write it like this:
```

#include <iostream>
#include <vector>
#include <algorithm>
#include <numeric>
#include <iomanip>

int getScore() {
    std::cout << "Enter score between 0-100: ";
    
    int score;
    std::cin >> score;
    
    while ( score < 0 || score > 100 ) {
        std::cout << "Score must be between 0 and 100: ";
        std::cin >> score;
    }
    
    return score;
}

template <typename IntegerType>
float average( std::vector<IntegerType> &vec ) {
    vec.erase( std::max_element( vec.begin(), vec.end() ) );
    return std::accumulate( vec.begin(), vec.end(), 0 ) / static_cast<float>( vec.size() );
}

const int NUMB_SCORES = 5;

int main() {
    std::vector<int> scores;
    
    for ( int i = 0; i < NUMB_SCORES; i++ )
        scores.push_back( getScore() );
    
    float avg = average( scores );
    std::cout << std::showpoint << std::fixed << std::setprecision( 2 ) << avg << std::endl;
}

```

That uses several libraries (including the STL) that you might not be familiar with. :)

---

### Post by TreeFinger on 2007-10-23
> **CptPicard said:**
> Just replace your input variables with an array. :)

Did not learn about arrays yet :)

**Jessehk** - Why do you write a lot of things with ```
std::
```? 
Could someone replace 'things' with what they really are? Are they objects or another word?

---

### Post by Jessehk on 2007-10-23
> **TreeFinger said:**
> 

**Jessehk** - Why do you write a lot of things with ```
std::
```? 
Could someone replace 'things' with what they really are? Are they objects or another word?

All of the C++ standard functions and objects are in the **std** namespace. A namespace helps group together related things and avoids name conflicts. 

When you wrote:
```

using namespace std;

```

at the beginning of your code, you were telling the compiler to import everything in the **std** namespace into your program.

I like referring to the things explicitly (like **std::cout** instead of **cout**) because I can immediately see what code is part of the standard and what is my own. It's pretty subjective. The one thing you should really avoid is **using namespace std** in a header file.

Hope that helped. :)

---

### Post by LaRoza on 2007-10-23
You can also use:

[php]
using std::cout
[/php]

This won't clutter your global namespace, but allows you to use cout alone.

(I personally explicitly state the namespace in code)

---

### Post by slavik on 2007-10-24
1. I wouldn't declare the five variables the way you did. I think it would be better to just have them on separate lines (for easier readability).

2. I would not have the average function print the final score, but return it to main (just how you did with getting scores).

Other than that, maybe adding extra blank lines in some places, but that's highly personal.

And what Jessehk wrote, keep a copy and after your advanced C++ class revisit it (or keep it with you in class and mark off the weird things in his code when you learn them). That code is way overkill though with templates and such ...

A C version for reference:
[php]
#include <stdio.h>

int get_score() {
  int ret; //ret is for return :) another personal preference
  printf("Please enter a score between 0 and 100 (inclusive): ");
  scanf("%d, &ret);
  while (ret < 0 || ret > 100) {
    printf("Please enter a valid score: ");
    scanf("%d, &ret);
  }
  return ret;
}

int calc_avg (int a, int b, int c, int d, int e) {
  int low=a;
//what follows are different examples of and if statement
  if (low > b) low = b;
  (low > c) ? low = c : 1 ;
  if (low > d) { low = d; }
  if (low > e) {
    low = e;
  }
  return low;
}

//the main you know.
[/php]

---

### Post by dwhitney67 on 2007-10-24
Here's an alternative solution that uses the STL set container.

[PHP]#include <set>
#include <iostream>

typedef std::set< int >     Set;
typedef Set::const_iterator SetIterator;

float averageScore( const Set& scores )
{
  float total = 0.0;

  if ( scores.size() < 2 )
  {
    return total;
  }

  // drop the lowest when initializing the iterator
  for ( SetIterator iter = ++scores.begin(); iter != scores.end(); ++iter )
  {
    total += *iter;
  }

  return total / (scores.size - 1);
}

int main()
{
  Set myScores;

  myScores.insert( 80 );
  myScores.insert( 70 );
  myScores.insert( 90 );
  myScores.insert( 95 );
  myScores.insert( 65 );

  std::cout << "Average score = " << averageScore( myScores ) << std::endl;
}[/PHP]

---

