---
title: "A few questions about pointers and dynamic arrays (in C++)"
date: 2007-06-18
forum: Programming Talk
---

### Post by danhm on 2007-06-18
I'm trying to write up a quick program that takes satellite data and formats it into CSV files that GIS software can use. I've run into a little roadblock, though -- I am doing something wrong. In Linux, it seg faults and in Windows it tells me that the memory cannot be written to.  I've left in my debugging lines, so you can see that the crash occurs as soon as I try to input something.

```

#include<iostream>

#include<fstream>

#include<string>



using namespace std;




#define HEIGHT 54

#define WIDTH 96

//these are kittu specific.



class merger {

	private:

		struct boxes {

			string latitude_point, longitude_point, albedo, co2, thermal;

			string toprightLon, toprightLat, topleftLon, topleftLat, bottomrightLon, bottomrightLat, bottomleftLon, bottomleftLat;			

		};

		short whentostop;

		boxes *raw, *formatted;

	

	public:

		merger();

		void inputter();

		void outputter(short);

		void makeBoxes(short);

		void format(short);

		bool onRightOrBottom(short);

};



merger::merger(){

	int i;

	cout << "How large should I make the first array (5563)?\n"; //5563 and 5184 are the exact sizes they should be (for kittu)

	scanf("%d", &i);

	raw = (boxes*) malloc (i);

	cout << "And the second array (5184)?\n?";

	scanf("%d", &i);

	formatted = (boxes*) malloc (i);

	cout << "debugging: allocated\n";

	}

	



int main () {

	merger mymerge;



	mymerge.inputter();

	

	cout << "Done!\n";

	

	return 0;

}



void merger :: inputter() {

	ifstream fileLat ("g7kittu_latitude.txt");

	ifstream fileLong ("g7kittu_longitude.txt"); //todo: prompt user for file names

	ifstream fileData ("g7kittu_albedo.txt");

	

	if(fileLat.is_open() && fileLong.is_open() && fileData.is_open())

	{

		y = 0;

		for(whentostop = 0; fileLat; whentostop++) //goes until the EOF is reached; all files are the same size

		{

			cout << "debugging: made it to the loop!\n";

			getline(fileLat,raw[whentostop].latitude_point,','); //crashes here!

			cout << "debugging: i think it crashes here\n"; //this does not get output

			getline(fileLong,raw[whentostop].longitude_point,',');

			getline(fileData,raw[whentostop].albedo,',');

			format(whentostop);

				

		}
...etc...

```

I have a feeling I'm forgetting something pretty simple; it's been awhile since I had to do anything real with pointers and memory allocation.

Does anyone have any...pointers?

---

### Post by WW on 2007-06-18
The constructor merger() simply allocates a block of memory for raw.  This won't work; the strings in the boxes struct are also C++ objects.  Your code will never call the constructors for these objects.  Use **new** instead, e.g. **raw = new boxes[i];**

EDIT: My initial post was not useful--I didn't realize that <string> provides a getline function.

---

### Post by danhm on 2007-06-18
> **WW said:**
> The constructor merger() simply allocates a block of memory for raw.  This won't work; the strings in the boxes struct are also C++ objects.  Your code will never call the constructors for these objects.  Use **new** instead, e.g. **raw = new boxes[i];**

EDIT: My initial post was not useful--I didn't realize that <string> provides a getline function.

Thanks! It gets past that with no crashes now, but crashes later on. I'm going to see if I can figure it out myself before asking for help again. 

Just one question, though -- am I going to have to use the free() function with these boxes* pointers?

---

### Post by WW on 2007-06-18
To free the memory, use **delete**, like this: **delete[] raw;**

---

### Post by aks44 on 2007-06-18
**new**'ed objects have to be **delete**'d
**new[]**'ed arrays (your case) have to be **delete[]**'d
;)

---

### Post by s1ightcrazed on 2007-06-18
> **aks44 said:**
> 
**new[]**'ed arrays 


Off topic, but I had to mention that the immature sleep-starved adolescent in me giggled when I read this..

Carry on!

---

### Post by aks44 on 2007-06-19
> **s1ightcrazed said:**
> Off topic, but I had to mention that the immature sleep-starved adolescent in me giggled when I read this..
Sorry, maybe the fact that I'm not a native english speaker explains why I didn't understand what you meant / why it is funny (as it seems)?...

---

### Post by GeneralZod on 2007-06-19
> **aks44 said:**
> Sorry, maybe the fact that I'm not a native english speaker explains why I didn't understand what you meant / why it is funny (as it seems)?...

"new[]'ed" would be pronounced "nude" as in "naked" :)

---

### Post by aks44 on 2007-06-19
oh, ok...

damn I guess that one day I'll have to do something about my awful english accent... I'd have pronounced it "new-ed" ;)

---

