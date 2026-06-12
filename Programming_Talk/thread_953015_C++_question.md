---
title: "C++ question"
date: 2008-10-19
forum: Programming Talk
---

### Post by Flynn555 on 2008-10-19
im currently working on a project where i am required to read in a line to text into a string.  i then have to split that string into separate variables

i.e.

string str1= "|COMPUTERS|LINUX|UBUNTU|100|55|";

and beak it up into...

string str2 = "COMPUTERS";
string str3 = "LINUX";
string str4 = "UBUNTU";
int num1 = 100;
int num2 = 55;


i have reserched some substring functions but i have had no luck so far...

any help would be much appreciated :)

thx Flynn

---

### Post by issih on 2008-10-19
[http://www.cplusplus.com/reference/string/string/](http://www.cplusplus.com/reference/string/string/)

That page ought to help a lot...have a close look at the find operations and the substring operations...combining the two will do wht you want quite happily

hope that helps

P.S. for converting strings to integers you probably need to use atoi from the c stndard library:

[http://www.cplusplus.com/reference/clibrary/cstdlib/atoi.html](http://www.cplusplus.com/reference/clibrary/cstdlib/atoi.html)

---

### Post by Flynn555 on 2008-10-19
thanks...finally got it to work.  its ugly. lol

---

### Post by dwhitney67 on 2008-10-19
Post your code so we can critique it.  Perhaps some things can be simplified?

Btw, is this task for a class assignment?

---

### Post by Flynn555 on 2008-10-20
yes it's for one of my classes at school
well it has 4 classes so ill post what i can

ok you probably need to know that Movie is a derived class of StoreItem

here is an expample of what string info will be:
|Movie|2000|Jurassic Park|Steven Spielberg|19.99|5|0|

i know its complicated but...it works

```


const char DELIMITER = '|'; 

StoreItem* Movie::createFromString( const string info){
/*@pre:      A line of text has been read from the input 
 *            file "inventory.txt"
 *@post:     A StoreItem pointer has been returned.
 *@purpose:  This function creates a movie object and returns a
 *             pointer to that object.
 *             The function takes one string and breaks it into
 *             substrings that are insterted as the private
 *             values of a movie object
 */
	string manip;     //temporary string for manipulation
        string type;      //type of storeitem
	string copy;      //temp storage for the number of copies
	string demand;    //temp storage for the number to order
	string price;     //temp storage for the price; later to
	                  //to be converted into float/int
	size_t pos;       //position of the DELIMITER in the string
    
	//break info string into substrings and store the data
	pos=info.find(DELIMITER);
	manip = info.substr(pos+1);
	pos=manip.find(DELIMITER);
	type = manip.substr(0, pos);  
	manip = manip.substr(pos+1);
	pos=manip.find(DELIMITER);
       //store the barcode of the movie
	m_barcode= manip.substr(0, pos);  
	manip = manip.substr(pos+1);
	pos=manip.find(DELIMITER);
       //store the title of the movie
	m_title = manip.substr(0, pos);   
        manip = manip.substr(pos+1);
	pos=manip.find(DELIMITER);
        //store the director of the movie
	m_director = manip.substr(0, pos); 
        manip = manip.substr(pos+1);
	pos=manip.find(DELIMITER);
	price = manip.substr(0, pos);
	manip = manip.substr(pos+1);
	pos=manip.find(DELIMITER);
	copy = manip.substr(0, pos);
	manip = manip.substr(pos+1);
	pos=manip.find(DELIMITER);
	demand = manip.substr(0, pos);
    
	//convert substrings; copy, demand and price values
	//into integer/float values using stringstreams
	istringstream a(demand);
	a >> m_demand;
        istringstream b(price);
	b >> m_price;
	istringstream c(copy);
	c >> m_copy;

    //return the movie
    return this; 

}//endcreateFromString


```

---

### Post by mdawg414 on 2008-10-20
```

manip = info;

string contents[8];

size_t pos;
int index = 0;
while ((pos = manip.find(DELIMETER)) != string::npos) {
	if (pos > 0) {
		contents[index++] = manip.substr(0,pos);
	}
	manip = manip.substr(pos+1);
}

```

This is a much more concise approach that essentially acts as a string tokenizer, since I don't think c++ has one. In order to implement this with your project, you would need to make a few assumptions. But basically, you could set the strings like so:

type = contents[0]

since the type is described by the first token in the input string. This segment also assumes you will have 8 tokens or at least know the number of tokens. You can use a dynamic array to change this if you want

---

### Post by anna jennifer on 2008-10-20
C++ is object oriented programming language.It follows bottom-up approach.it has some special feature than C is inheritance,polymorphism.
------------------------------------
Anna jennifer
[Influencer]("http://www.drivenwide.com")

---

### Post by Flynn555 on 2008-10-20
wow man thanks...that really cleaned up my code. i knew there was probably a way to iterate that.  one thing i have learned with c++...is that if it looks too long/repetitive  there is probably a way to loop it.

here is my revised code :D
```

StoreItem* Movie::createFromString( const string info){
/*@pre:      A line of text has been read from the input 
 *            file "inventory.txt"
 *@post:     A StoreItem pointer has been returned.
 *@purpose:  This function creates a movie object and returns a
 *             pointer to that object.
 *             The function takes one string and breaks it into
 *             substrings that are insterted as the private
 *             values of a movie object
 */
	string manip = info;     //temporary string
	size_t pos;              //position of the DELIMITER
	manip = info;            //string for manipulation
        string contents[8];      //array of string for content
                                 //storage

    //break contents of string into the array contents[8]
    int index = 0;
    while ((pos = manip.find(DELIMITER)) != string::npos){
	if (pos > 0){
           contents[index++] = manip.substr(0,pos);
	}
	manip = manip.substr(pos+1);
    }
	//store data into the object
	m_barcode = contents[1];
	m_title = contents[2];
	m_director = contents[3];
	//convert int/float values with stringstreams
        istringstream a(contents[6]);
	a >> m_demand;
        istringstream b(contents[4]);
	b >> m_price;
	istringstream c(contents[5]);
	c >> m_copy;

    //return the movie
    return this; 

}//endcreateFromString

```

---

### Post by Martin Witte on 2008-10-20
> **Flynn555 said:**
> ok you probably need to know that Movie is a derived class of StoreItem

here is an expample of what string info will be:
|Movie|2000|Jurassic Park|Steven Spielberg|19.99|5|0|

i know its complicated but...it works


It would make sense to store this data as a stl map, see e.g. [this link]("http://www.cprogramming.com/tutorial/stl/stlmap.html")

You would get then something like 

In your class definition use as storage:
```

std::map<std::string,std::string> m_storage;
```

and in your method:
```

m_storage["type"]="Movie";
m_storage["title"]="Jurassic Park";
```
etcetera

---

