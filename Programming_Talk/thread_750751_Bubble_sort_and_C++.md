---
title: "Bubble sort and C++"
date: 2008-04-09
forum: Programming Talk
---

### Post by nickoli on 2008-04-09
I need to write a program that sorts nine scores and I'm confused as to why my sort isn't working any insight is appreciated. 

My code :
[PHP]#include <iostream>
#include <fstream>
#include <string>
#include <iomanip>
using namespace std;

void bubbleSort(double list[], int length);

int main()
{
	int length,i = 0, x = 0;			// 9 judges score each dive
	double difficulty[7],			    //float value between 1 and t3
		  scores[9] = {0};				// 1 - 10
	string FirstNames[7];

	ifstream fin;
	fin.open("data.txt");
	fin >> length;

	cout << showpoint << fixed << setprecision(1);
	
		
		for(i = 0; i < length; i++)
		{
			fin >> FirstNames[i];
			fin >> difficulty[i];
			cout << setw(10)<< left << FirstNames[i] << " " ;
			cout << difficulty[i] << " " ;
			for(x = 0; x < 9; x++)
			{
				fin >> scores[x];
				
				bubbleSort( scores ,x);
				cout << setw(4) << scores[x] << "  ";
			}
			cout << endl;
			
		}
		return 0;
}

void bubbleSort(double list[], int length)
{
	int i = 0, iteration, index;
	for(iteration = 1; iteration < length; iteration++)
		for(index = 0; index < length - iteration; index++)
			if( list[index] > list[index + 1])
				swap(list[index], list[index + 1]);

}[/PHP]

My output: Is attached.

My input data :


[PHP]7
Anne      2.0    8.5 8.5 9.0 9.0 9.0 9.5 8.5 8.0 9.5
Sarah     1.6    7.5 8.5 8.0 8.0 7.0 9.0 8.5 8.5 8.0
Deborah   2.3    9.0 9.0 9.5 10.0 10.0 9.5 9.5 9.5 9.5
Kathryn   2.4    9.0 9.0 9.0 9.5 9.5 9.5 9.0 8.0 8.5
Martha    2.7    9.0 9.0 9.5 9.5 9.0 8.5 8.5 8.5 9.5
Elizabeth 2.9    8.0 8.0 7.5 8.5 8.5 8.0 8.0 7.5 8.5
Tina      2.5    8.5 8.5 8.5 8.5 8.5 8.5 8.5 8.5 8.5[/PHP]


Thanks for your time I appreciate any help you can give me.

---

### Post by Can+~ on 2008-04-09
Sounds like a homework to me. But at least you provided code, instead of "OMG DO MY HOMEWORK PLZ".

Let's see..

*first edit*
I don't get the whole C++ syntax. But, for each loop you handle a value to the array to be sorted, then send it to the bubblesort function?

So, you're doing more loops than you should, you need one loop to copy all the data from the file to the array, then bubblesort it, otherwise, you're increasing the order to something like O((n!)^2)

*edit 2*

Repeating myself, take out the bubblesort out of the loop and the printing function. The reason of the mess, is that the cout was done after the bubblesort (which had the issue explained above), and caused it to return values as they were sorted inside.

I mean (pseudocode):

[PHP]first round:
array = 8.5
bubblesort(array)
array_sorted = [8.5]
printed value (0): 8.5

second round:
array = [9.5, 8.5]
bubblesort(array)
array_sorted = [8.5, 9.5]
printed value (1): 9.5

third round:
array = [9.5, 8.5, 7.5]
bubblesort(array)
array_sorted = [7.5, 8.5, 9.5]
printed value (2): 9.5 <--error.

etc.[/PHP]

Everything else works fine it seems..

---

### Post by nickoli on 2008-04-09
Busted. When I get stuck I like to come here you guys are really helpful. Sometimes I can get stuck for days on something simple.:guitar:

---

### Post by Can+~ on 2008-04-09
Did you fix it?

You can bring homework problems only if you've done something and you're stuck (like this case), so I guess it's fine. The problem comes when people do the job for you, ending up with lame/lazy programmers.

---

### Post by themusicwave on 2008-04-09
I am not sure if this is it, but since it's your homework you can try and see.

Rember that when you have a <loop that runs from i=1 to i < x it runs x-1 times.

Perhaps you need to start your loop at 0?

It looks like your data gets partially sorted, but isn't getting enough iterations.

I haven't written a bubble sort in about 5 years, after this you hopefully never will either.

Once again this could be completely wrong, just a thought though. After all it is your homework.

---

### Post by nickoli on 2008-04-10
I tried to set it to 0 no avail. The loop thing makes alot of sense to me. I'm not sure I'm going about sorting them the right way.  Eventually I'm going to need to sort the names and keep there scores with them so I'm thinking about using some display functions for my loops. I'm not sure if I'm going to have to nest them because, I have 7 divers , 1 difficulty rating, and 9 judges. I just started using arrays so this is where My learning curve hopefully decrease, :confused: or vice versa.

[PHP]void display(string FirstNames[], int length)
{
	int i = 0 ;
	for(i = 0; i < length; i++)
	{
		cout << setw(10)<< left << FirstNames[i] << "string " ;


	}
}

void display(double difficulty[], int length)
{
	int i = 0 ;
	for(i = 0; i < length; i++)
	{
		cout << setw(10)<< left <<  difficulty[i] << "double " ;
	}
}

void display1(double scores[], int length)
{
	int i = 0 ;
	for(i = 0; i < length; i++)
	{
		cout << scores[i] << " " ;
	}
}[/PHP]
I was thinking about trying this for a simple display function but like I said I  will nest a couple together and give that a shot. Any insight is appreciated and thanks for your time.

---

### Post by nickoli on 2008-04-10
Ok I'm making a little ground This is my code so far.




[PHP]#include <iostream>
#include <fstream>
#include <string>
#include <iomanip>
using namespace std;

void bubbleSort(string list[], int length);
void bubbleSort(double list[], int length);
void display(string FirstNames[], int i);
void display(double difficulty[], int length);   //difficulty
void display1(double[], int length);


int main()
{
	int length,i = 0, x = 0;			// 9 judges score each dive
	double difficulty[7],			    //float value between 1 and t3
		  scores[9] = {0};				// 1 - 10
	string FirstNames[7];

	ifstream fin;
	fin.open("data.txt");
	fin >> length;

	cout << showpoint << fixed << setprecision(1);
	
		for(i = 0; i < length; i++) 
        { 
            fin >> FirstNames[i]; 
            fin >> difficulty[i];    //obtain data
          
            for(x = 0; x < 9; x++) 
            { 
                fin >> scores[x]; 
            } 
           
        } 
		bubbleSort(FirstNames, length);
                                           bubbleSort(scores, 9);

		for(i = 0; i < length; i++) 
        { 
            cout << FirstNames[i] <<  " "; 
            cout << difficulty[i] <<  " ";    //print data
          
            for(x = 0; x < 9; x++) 
            { 
                cout << scores[x] <<  " "; 
            } 
           cout << endl;
        } 
		//display(FirstNames, length);
		//display(difficulty, length);
		//display(scores, length);
		//cout << endl;
        return 0; 


	
}

void bubbleSort(string list[], int length)
{
	int i = 0, iteration, index;
	for(iteration = 1; iteration < length; iteration++)
	for(index = 0; index < length - iteration; index++)
			if( list[index] > list[index + 1])
				swap(list[index], list[index + 1]);
}

void bubbleSort(double list[], int length)
{
	int i = 0, iteration, index;
	for(iteration = 1; iteration < length; iteration++)
	for(index = 0; index < length - iteration; index++)
			if( list[index] > list[index + 1])
				swap(list[index], list[index + 1]);
}

void display(string FirstNames[], int length)
{
	int i = 0 ;
	for(i = 0; i < length; i++)
	{
		cout << setw(10)<< left << FirstNames[i] << " "  << endl;
	}
}

void display(double difficulty[], int length)
{
	int i = 0 ;
	for(i = 0; i < length; i++)
	{
		cout << setw(10)<< left <<  difficulty[i] << "double " ;
	}
}

void display1(double scores[], int length)
{
	int i = 0 ;
	for(i = 0; i < length; i++)
	{
		cout << scores[i] << " " ;
	}
}[/PHP]

My names list is sorting so thats cool the only thing I need to sort now is the scores. For some reason all of my scores are printing the same value.
I'll attach my output;

---

### Post by samjh on 2008-04-10
Put some diagnostic code in strategic places.  Print the score list just before the sort and just after the sort, both inside and outside of the sorting function.  You will be able to tell:

Whether the bubblesort is actually sorting properly.

Whether the score array is being properly processed.

If the bubblesort is doing its job, and the score array is being passed to and from the function correctly, then there is a more subtle error involved here.

(Just found out that I can't copy-paste your code.  I ain't spending time typing it in verbatim. :) )

---

### Post by dwhitney67 on 2008-04-10
Please, rather than present the code, can you please present the problem (that is, the original homework problem)?

I don't get why you are sorting the names and _then_ sorting the difficulties.  Should this information not be paired together (along with the scores).

In other words, if the data looks like:
```
Joe Difficult 8.6 6.7 9.1 ...
Bubba Extreme 9.5 9.4 8.9 ...
```
When this is sorted, it would seem to me that Bubba will come before Joe, however their dive (?) difficulty should remain with the diver, not be swapped as well.

Thus is it possible that you were supposed to read in the data from the file as a whole record (storing it into a struct or class), so that this data is held intact throughout the swapping process?

Using this approach, the data from above, once sorted, would look like:
```
Bubba Extreme 8.9 9.4 9.5 ...
Joe Difficult 6.7 8.6 9.1 ...
```
Note how the divers name is sorted, as well as their respective scores.  The difficulty of the dive remains with the diver.

P.S.  Your C++ code looks awfully like C code.  Just my $0.02.

---

### Post by pedro_orange on 2008-04-10
If you're using C++. Use classes. 
This problem has classes written all over it. It seems like you're mixing your indicies up. (Like dwhitney said!)
Then it's just a case of writing 1 bubble sort algorithm to run against each instance of the class. (ie for each diver)

---

### Post by themusicwave on 2008-04-10
> **pedro_orange said:**
> If you're using C++. Use classes. 
This problem has classes written all over it. It seems like you're mixing your indicies up. (Like dwhitney said!)
Then it's just a case of writing 1 bubble sort algorithm to run against each instance of the class. (ie for each diver)

He may not have learned OOP yet.  Usually you learn bubble sort way before you learn OOP.

OOP would be good, but not needed.

---

### Post by dwhitney67 on 2008-04-10
> **themusicwave said:**
> He may not have learned OOP yet.  Usually you learn bubble sort way before you learn OOP.

OOP would be good, but not needed.
Huh?  What does the bubble-sort algorithm have to do with OOP?  The bubble-sort can be implemented in pretty much any language, OO or not.

What really baffles me is people trying to help the poor bloke code a solution, without even knowing what the problem is?  Perhaps his instructor wants the data sorted by name, and then after, sorted again by dive difficulty.  Perhaps the judges scores need to be sorted in each case.

I doubt the homework assignment is about creating a "scrambled egg", where diver's names and their dive difficulties are mixed up.

---

### Post by nickoli on 2008-04-10
I figured out the major part of my problem. Scores is a two dimensional array. So now I have to make a bubble sort that works for a two dimensional array and then display it. As far as classes I haven't made  it that far yet. I'm pretty much a newbie if it wasn't overly obvious. I deleted the instance where I was sorting the difficulty , it was really stupid to begin with being that I only have one difficulty per diver.:lolflag:. Thanks everyone for your insight I'm learning as I go along I appreciate the help.

my output should look like this.
[PHP]NAME   DIFFICULTY    	              SORTED SCORES                                                                    Points     
 Anne            2.0       		8.0  8.5  8.5  8.5  9.0  9.0  9.0  9.5  9.5  	124.0

 Sarah            1.6       		7.0  7.5  8.0  8.0  8.0  8.5  8.5  8.5  9.0  	  91.2[/PHP]

---

### Post by dwhitney67 on 2008-04-10
Have you learned to use structures (i.e. struct), perhaps in a C course?

If not, then you need to read in your data into arrays as you have done before, and each time you sort (swap) the diver's name, you need to ensure that you do the same for their difficulty level and scores (so that they are kept together in relation to the diver).

I would suggest that you avoid using the swap() function until you fully understand how it works.  Here's a hint how to swap two values:
```
temp = value_one;
value_one = value_two;
value_two = temp;
```

You are free to sort the diver's scores at anytime (of course, after they are read from the file).

Good luck.

---

### Post by nickoli on 2008-04-12
I've made a little ground I have the name sorts and difficulty  grouped together. The data is following the names. My problem comes when I'm working with the two dimensional array scores. I can't figure out how to put the sort together to take in the names, difficulty and scores, thus keeping my data intact. Here is my code thus far.


[PHP]#include <iostream>
#include <fstream>
#include <string>
#include <iomanip>
using namespace std;

void bubbleSort(string list[], int length ,double difficulty[]) ;

void display(string FirstNames[], int i, double difficulty);
void display(double difficulty[], int length);   //difficulty
void display1(double[], int length);


int main()
{
	int length,i = 0, x = 0;			// 9 judges score each dive
	double difficulty[7],			    //float value between 1 and t3
		  scores[9][7] = {0};				// 1 - 10
	string FirstNames[7];

	ifstream fin;
	fin.open("data.txt");
	fin >> length;

	cout << showpoint << fixed << setprecision(1);
	
	for(i = 0; i < length; i++) 
    { 
         fin >> FirstNames[i]; 
         fin >> difficulty[i];									 //obtain data
         for(x = 0; x <= 8; x++) 
         { 
            fin >> scores[x][i]; 
		 } 
	} 
	bubbleSort(FirstNames, length, difficulty);
    for(i = 0; i < length; i++)                                 // sort data
	{ 
		cout << setw(10) << left << FirstNames[i] <<  " "; 
	    cout << difficulty[i] <<  " "; 
		for(x = 0; x <= 8; x++) 
        { 
            cout << scores[x][i] <<  " "; 
        } 

        cout << endl;
	}
    return 0; 
}

void bubbleSort(string list[], int length ,double difficulty[])  //keeps the difficulty values together with the names after a sort.
{
	int i = 0, iteration, index, x = 0;
	for(iteration = 1; iteration < length; iteration++)
		for(index = 0; index < length - iteration; index++)
			if( list[index] > list[index + 1])
				{
					swap(list[index], list[index + 1]);
					swap(difficulty[index], difficulty[index + 1]);
				}
}


void display(string FirstNames[], int length, double difficulty)
{
	int i = 0 ;
	for(i = 0; i < length; i++)
	{
		cout << setw(10)<< left << FirstNames[i] << "\t "  <<  difficulty << endl;
	}
}

void display(double difficulty[], int length)
{
	int i = 0 ;
	for(i = 0; i < length; i++)
	{
		cout << setw(10)<< left <<  difficulty[i] << "double " ;
	}
}

void display1(double scores[], int length)
{
	int i = 0 ;
	for(i = 0; i < length; i++)
	{
		cout << scores[i] << " " ;
	}
}[/PHP]


The problem I keep having is with syntex errors. It won't compile when I trie to impliment this function below. 
[PHP]void bubbleSort(string list[], int length ,double difficulty[], double scores[][])  //keeps the difficulty values together with the names after a sort.
{
	int i = 0, iteration, index, x = 0;
	for(iteration = 1; iteration < length; iteration++)
		for(index = 0; index < length - iteration; index++)
			if( list[index] > list[index + 1])
				{
					swap(list[index], list[index + 1]);
					swap(difficulty[index], difficulty[index + 1]);
					swap(scores[index], scores[index + 1]);
				}
}[/PHP]


Any help is appreciated Thanks.

---

### Post by nvteighen on 2008-04-12
> **nickoli said:**
> (...)
The problem I keep having is with syntex errors. It won't compile when I trie to impliment this function below. 
[PHP]void bubbleSort(string list[], int length ,double difficulty[], double scores[][])  //keeps the difficulty values together with the names after a sort.
{
	int i = 0, iteration, index, x = 0;
	for(iteration = 1; iteration < length; iteration++)
		for(index = 0; index < length - iteration; index++)
			if( list[index] > list[index + 1])
				{
					swap(list[index], list[index + 1]);
					swap(difficulty[index], difficulty[index + 1]);
					swap(scores[index], scores[index + 1]);
				}
}[/PHP]

Shouldn't it be as follows?
[PHP]
(...)
for(iteration = 1; iteration < length; iteration++)
{
    for(index = 0; index < length - iteration; index++)
    {
        if( list[index] > list[index + 1])
        {
            (etc...)
[/PHP]

At least in C, if you don't include the brackets, only the next line will be executed inside the loop. I suppose C++ does it the same way...

---

### Post by dwhitney67 on 2008-04-12
The first thing I see that looks odd (but not necessarily wrong) is your usage of the scores array, starting from where it is declared and first used when it is populated with the data from the file.

The scores array should be defined as a two dimensional array, with the diver's ID (or index) as the primary subscript, where the number of dives should come as the second subscript.

Thus, you scores array should be declared as:
[PHP]double scores[ 7 ][ 9 ];[/PHP]

As stated in earlier posts, and I think you somewhat understand by now, the scores need to be carried along with the name and dive-difficulty when sorting.

Thus you declaration for bubble_sort will have to look something like:
[PHP]void bubble_sort(const unsigned int num_divers, const unsigned int num_scores, string list[], double difficulty[], double *scores );[/PHP]

The position of the function parameters is purely arbitrary, however I personally like to place the constants at the beginning of the functions, the return values at the end.

Frequently the size of an array is not known during compilation, thus it is wise to get into the habit of passing arrays as a pointer.  Thus as an example, I have done this with the two-dimensional array holding the diver's scores.

Anyhow, here's a sample bubble_sort() method that just _may_ work for your needs.  I have not tested it, and as the comments indicate in the code, there is still one task missing... that is to sort the diver's scores so that they are stored in ascending order.  Good luck!
[PHP]#include <string>
#include <iostream>
using namespace std;


void bubble_sort( const unsigned int num_divers, const unsigned int num_scores,
                 string name[], double difficulty[], double *scores )
{
  for ( int d1 = 0; d1 < num_divers; ++d1 )
  {
    for ( int d2 = 1; d2 < num_divers; ++d2 )
    {
      // compare diver's name
      if ( name[ d1 ] > name[ d2 ] )
      {
        // make temp copy of all data to be swapped
        string temp_name = name[d1];
        double temp_diff = difficulty[d1];
        double temp_scores[num_scores];

        for ( int s = 0; s < num_scores; ++s )
        {
          temp_scores[s] = scores[d1 * num_divers + s];
        }


        // swap data, first d2 into d1
        name[d1] = name[d2];
        difficulty[d1] = difficulty[d2];
        for ( int s = 0; s < num_scores; ++s )
        {
          scores[d1 * num_divers + s] = scores[d2 * num_divers + s];
        }

        // now temp to d2
        name[d2] = temp_name;
        difficulty[d2] = temp_diff;
        for ( int s = 0; s < num_scores; ++s )
        {
          scores[d2 * num_divers + s] = temp_scores[s];
        }

        // swap of diver's name (and associated data) is done.
        // However, the diver's scores has not been done yet.
        // This is left as an exercise to the reader.
      }
    }
  }
}
[/PHP]

---

### Post by nickoli on 2008-04-15
Thanks for everyones help I appreciate it. My last lecture the instructor introduced us to structures and said he would give us extra credit if we used one. So I finished this program using one. It was pretty simple after that . The final code is as such.

[PHP]#include <iostream> 
#include <fstream> 
#include <string> 
#include <iomanip> 
#include "mylib.h"
using namespace std; 

int Judges = 9;
void DisplayTitle();
void getData(fstream& inFile, diverType diver);
double ScoreTally(diverType [], diverType);
void bubbleSort(string list, int length ,double difficulty, double scores[9]) ;
int main() 
{ 
    int length, rolls = 0, scores = 0, i, x;            // 9 judges score each dive 
	double points = 0, DiverScore = 0, FinalScore = 0;											  //float value between 1 and t3 
	diverType diver;

    ifstream fin; 
    fin.open("data.txt"); 
	cout << fixed << showpoint << setprecision(1);
	DisplayTitle();
    fin >> length; 
	for(rolls = 0; rolls < length; rolls++)
	{ 
		fin >> diver.name;
		fin >> diver.difficulty;
		for (scores = 0; scores < Judges; scores++)
		{
			fin >> diver.scores[scores];
		}
		bubbleSort( diver.name,  length , diver.difficulty,diver.scores); 
		cout << setw(10)<< left << diver.name << "\t";
		cout << diver.difficulty << "\t";
		for (scores = 0; scores < Judges; scores++)
		{
			cout << diver.scores[scores] <<" ";
		}
		for(x = 1; x < 8; x ++)
		{
			DiverScore = DiverScore + diver.scores[x];
			FinalScore = DiverScore * diver.difficulty;
		}
		cout << "\t" << FinalScore << endl;
		
		cout << endl;
		cout << endl;
		DiverScore = 0;
		FinalScore = 0;
	}
	for(i = 0; i < 75; i++)
	cout << "-"; 
	cout << endl;
	return 0;
}



void bubbleSort(string list, int length ,double difficulty, double scores[9])  //keeps the difficulty values together with the names after a sort. 
{ 
    int i = 0, iteration, index, x = 0; 
	for(iteration = 0; iteration < length; iteration++) 
      for(index = 0; index < 8; index++) 
        for(i = 0; i < 8 - iteration ; i++)
		{   if(scores[index] > scores[index + 1])
			swap(scores[index], scores[index + 1]);
		}
      
} 


void DisplayTitle()
{
	int i;
	for(i = 0; i < 75; i++)
	cout << "-"; 
	cout << endl;
	cout << "NAME " << "\t    "   << " DIFFICULTY " << "\t     " 
		<< " SORTED SCORES " << "\t" << "\t" << " Points " << endl;
	for(i = 0; i < 75; i++)
	cout << "-"; 
	cout << endl;
}

double ScoreTally(diverType diver, diverType difficulty)
{	

	double DiverScore = 0, TotalScore;
	int x;
	for(x = 1; x < 8; x ++)
	{
		DiverScore = DiverScore + diver.scores[x];
		
	}
	return DiverScore;
}[/PHP]

The structure I used in mylib.h 

[PHP]#include <string>
using namespace std;

struct diverType
{
	string name;
	double difficulty;
	double scores[9];
};[/PHP]

Once again I appreciate your insight. Thanks alot.

---

### Post by dwhitney67 on 2008-04-15
If you really want to impress your teacher, slap those function definitions inside your structure!

---

