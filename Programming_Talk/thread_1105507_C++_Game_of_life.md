---
title: "C++ Game of life"
date: 2009-03-24
forum: Programming Talk
---

### Post by AnarchyMaster on 2009-03-24
Hey guys,
I'm trying to program a game of life style thing in C++
([information]("http://en.wikipedia.org/wiki/Conway%27s_Game_of_Life"))
only I'm stuck, for some reason it isn't working

Heres the code ( on the "Glider shape" )
```
#include <iostream>
using namespace std;

int Coords[10][10] = {0};
int Alive[10][10] = {0};
void TermRed()
{
	printf("\033[22;31m");
}
void TermGreen()
{
	printf("\033[22;32m");
}
void TermBlack()
{
	printf("\033[22;30m");
}
void PlayGame()
{
	int NumberAround = 0;
	
	for(int count1 = 0; count1 < 10; count1++)
	{
		for(int count2 = 0; count2 < 10; count2++)
		{
			if( Alive[count1][count2] == 1)
			{
				TermGreen();
				cout << Coords[count1][count2] << " ";
				TermBlack();
			}
			else
			{
				TermRed();
				cout << Coords[count1][count2] << " ";
				TermBlack();
			}
		}
		cout << endl;
	}
	cout << endl;			
	for(int countx = 0; countx < 10; countx++)
	{
		for(int county = 0; county <10; county++)
		{
			for(int countx2 = -1; countx2 <= 1; countx2++)
			{
				for(int county2 = -1; county2<=1;county2++)
				{
					if((countx - countx2 >= 0) && (county - county2 >= 0) && (countx + countx2 < 10) && (county + county2 < 10))
					{
						if( (Alive[countx+countx2][county+county2] == 1) && (countx2 != 0 && county2 != 0))
						{
							NumberAround++;
						}
					}
				}
			}

			Coords[countx][county] = NumberAround;
			if((Alive[countx][county] == 1 && (NumberAround ==2 || NumberAround == 3)) ||(Alive[countx][county] == 0 && NumberAround == 3))
			{
				Alive[countx][county] = 1;
			}
			else
			{
				Alive[countx][county] = 0;
			}
			NumberAround = 0;
		}
		printf("\n");
	}
	sleep(1);
	printf("\n\n\n");
	PlayGame();			
}

int main(int argc, char** argv)
{
	Coords[3][3] = 2;
	Coords[3][4] = 2;
	Coords[3][5] = 1;
	Coords[4][3] = 2;
	Coords[5][4] = 1;
	Alive[3][3] = 1;
	Alive[3][4] = 1;
	Alive[3][5] = 1;
	Alive[4][3] = 1;
	Alive[5][4] = 1;
	PlayGame();		
	return 0;
}

```
and the console output is:
```
0 0 0 0 0 0 0 0 0 0 
0 0 0 0 0 0 0 0 0 0 
0 0 0 0 0 0 0 0 0 0 
0 0 0 2 2 1 0 0 0 0 
0 0 0 2 0 0 0 0 0 0 
0 0 0 0 1 0 0 0 0 0 
0 0 0 0 0 0 0 0 0 0 
0 0 0 0 0 0 0 0 0 0 
0 0 0 0 0 0 0 0 0 0 
0 0 0 0 0 0 0 0 0 0 



0 0 0 0 0 0 0 0 0 0 
0 0 0 0 0 0 0 0 0 0 
0 0 1 1 2 1 1 0 0 0 
0 0 1 0 1 0 0 0 0 0 
0 0 0 1 0 1 0 0 0 0 
0 0 0 0 0 0 0 0 0 0 
0 0 0 0 0 0 0 0 0 0 
0 0 0 0 0 0 0 0 0 0 
0 0 0 0 0 0 0 0 0 0 
0 0 0 0 0 0 0 0 0 0 



0 0 0 0 0 0 0 0 0 0 
0 0 0 0 0 0 0 0 0 0 
0 0 0 0 0 0 0 0 0 0 
0 0 0 0 0 0 0 0 0 0 
0 0 0 0 0 0 0 0 0 0 
0 0 0 0 0 0 0 0 0 0 
0 0 0 0 0 0 0 0 0 0 
0 0 0 0 0 0 0 0 0 0 
0 0 0 0 0 0 0 0 0 0 
0 0 0 0 0 0 0 0 0 0 

```

any ideas?

Thanks!

---

### Post by lisati on 2009-03-24
It looks to me like it's not picking up all the neighbours to the cell currently being considered. I'd suggest looking at the test(s) that exclude counting the cell as its own neighbour - can the difference between the counters result in a negative number, and would that make a difference?

Edit: I hope this isn't part of a homework assignment!

---

### Post by AnarchyMaster on 2009-03-24
Thanks for the quick reply! that seem to sort out most the problems...

And it wasn't XD damn school teaches pascal...

---

