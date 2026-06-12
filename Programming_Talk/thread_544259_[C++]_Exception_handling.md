---
title: "[C++] Exception handling"
date: 2007-09-06
forum: Programming Talk
---

### Post by Mathiasdm on 2007-09-06
I'm trying to get used to C++ exceptions, but I seem to have some unknown problem.

I'm using the 'out_of_range' C++ exception in a header file as follows:

```


#ifndef H_SUDOGRID
#define H_SUDOGRID

#include <vector>
#include <exception>


namespace Sudoku {
class SudokuGrid {
	public:
		/**
		* Constructor throws out_of_range exception when maximumNumber <= 0.
		*/
		SudokuGrid(int maximumNumber) {
			if(maximumNumber<=0) {
				**throw std::out_of_range("maximumNumber <= 0");**
			}
			maxNumber = maximumNumber;
			givensAddable = true;
		}
		/**
		* The list contains (starting top left and going to the right,
		* then down) either '0' or a given.
		*/
		SudokuGrid(int maxNumber, std::vector<int>& list, int width);
		~SudokuGrid();
		int addGiven(int vertical, int horizontal);
		int addSquare(int vertical, int horizontal);
		/**
		* Makes it impossible to add more givens by calling addGiven().
		*/
		int closeGivensAccess();
		/// Returns true if the square is given, false otherwise.
		bool isGiven(int vertical, int horizontal);
		/**
		* Returns a value if there's only 1, zero otherwise.
		*/
		int getValue(int vertical, int horizontal);
		int setValue(int vertical, int horizontal, int value);
		std::vector<int>& getValues(int vertical, int horizontal);
		int removeValue(int vertical, int horizontal, int value);
		int addGroup(std::vector<std::vector<int> >& group);
		std::vector<std::vector<std::vector<int> > >& getGroups(int vertical, \
															  int horizontal);
	private:
		int maxNumber;
		bool givensAddable;
		std::vector<std::vector<std::vector<int> > > gridContainer;
		std::vector<std::vector<int> > givens;
		std::vector<std::vector<std::vector<int> > > groupsList;
};

}
#endif

```
The problem is, I seem to get an error:'out_of_range' was not declared in this scope.

It's probably something stupid (it usually is :-p ), but I just can't find it. :(

---

### Post by the_unforgiven on 2007-09-06
Try *#include*ing <stdexcept>
This should solve the problem.

---

### Post by Mathiasdm on 2007-09-06
Ah, it worked! Thanks for that :-)
My apologies for the stupid question, I had the idea that #include <exception> made sure that type of exception would work.

---

