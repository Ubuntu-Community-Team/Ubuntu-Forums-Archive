---
title: "C++ Making code work for a vector"
date: 2013-03-06
forum: Programming Talk
---

### Post by Amulon on 2013-03-06
```



	//Quicksort
	template <class Record>
	void Sortable_list<Record>::quick_sort()
	{
		recursive_quick_sort(0, count - 1)
	}


	template <class Record>
	void Sortable_list<Record>::recursive_quick_sort(int low, int high)
	{
		int pivot_position;
		if (low < high)
		{
			pivot_position = partition(low, high);
			recursive_quick_sort(low, pivot_position - 1);
			recursive_quick_sort(pivot_position + 1, high);
		}
	}
```

I have data files stored in a vector and i need to sort it using the quicksort. This is the code that the professor supplied. How do I go about changing this so it works with a vector? 


Thanks so much

---

### Post by dwhitney67 on 2013-03-07
What you have posted is merely a snip of the Sortable_list template class.  Perhaps you could reveal what type of container is declared (possibly as private) in the Sortable_list class.  Is it an STL list containing data of type "Record"?

An STL vector can be considered to be a "glorified" array when used as such.  Your sorting algorithm (specifically the partition function) will access the vector using the operator[] function.  You have not shown the partition function, so unless you post the code, I'll assume its development is part of your class assignment -- and because of such, you should do your own research into how this function should be implemented.

---

### Post by Amulon on 2013-03-07
Well there is more to the project then just the quicksort. There have been other sorts that I have done. But those ones have been easy to make work with the vectors I've implemented. This is just the code he provided for us to do the quicksort and I have having trouble making this work for vectors. I don't have to use a list, but i am not that familiar with it. If I used a list and stored the files in there, would it be easier than making this code work for vectors?

---

### Post by dwhitney67 on 2013-03-07
I think you misunderstood my previous comments.

The code snip you posted calls a function called 'partition'.  Where is that implemented?  Can you show me?  Within that function, the container storing the data will need to be manipulated during the sort process.

---

### Post by Amulon on 2013-03-07
That is true there is a partition function... All the code I provided is the code that the professor gave us. So partition isn't previously implemented. Hmmmm. I'll have to ask him about that. Or just do the quick sort another way

---

### Post by dwhitney67 on 2013-03-07
Or implement the partition function.  :-)   Perhaps that is part of your assignment.

---

### Post by Amulon on 2013-03-07
Maybe. Hah. Thanks for the help on pointing that out.

---

### Post by GeneralZod on 2013-03-07
"partition" could be the one from the C++ Standard Library:

[http://www.cplusplus.com/reference/algorithm/partition/](http://www.cplusplus.com/reference/algorithm/partition/)

---

### Post by ofnuts on 2013-03-07
Maybe it's time to remember the forum policy about helping over homework?

---

