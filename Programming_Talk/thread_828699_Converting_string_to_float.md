---
title: "Converting string to float"
date: 2008-06-14
forum: Programming Talk
---

### Post by elpichi on 2008-06-14
i'm having a hard time finding the right way to convert from string to a float.
I'm making a program that makes a file that logs the profits of a person
the problem comes when i try to get the number which could be anywhere in the file except it has "The ending balance for the account is: $399.09" or any other float. i managed to make a loop that searches through the entire file for those exact words, but i get a string and i need that info in a float variable.

Any advice would be super helpful, thanks.

```
	float balance=0;
	string name, line, clean, number;
	stringstream streamer;
	string match = "The ending balance for the account is: ";
	cout << setprecision(2);
	//check if file exist and create a new file if there isn't any
	ifstream inbudget;
	inbudget.open("budget.dat", ios::ate);	
	if(inbudget.is_open())
	{
	while(inbudget)
	{
	
	int pos = -1;
	getline(inbudget, line);
	pos = line.find('$');
	clean = line.substr(0, pos);
	line = line.substr(pos+1);
	
	if(clean == match)
	number = line;	
	}

	cout << number << endl;
	streamer >> number;

	inbudget.close();
	}

```
while displaying the number before converting it shows exactly what i want, but somehow it turns into a 1.8 or 1.9 after streamer does its job.

---

### Post by Can+~ on 2008-06-14
[http://www.cplusplus.com/reference/clibrary/cstdlib/atof.html](http://www.cplusplus.com/reference/clibrary/cstdlib/atof.html)

You could use some indentation in your code btw.

---

### Post by Zugzwang on 2008-06-14
> **Can+~ said:**
> [http://www.cplusplus.com/reference/clibrary/cstdlib/atof.html](http://www.cplusplus.com/reference/clibrary/cstdlib/atof.html)

You could use some indentation in your code btw.

Another alternative is to use an [istringstream]("http://www.cplusplus.com/reference/iostream/istringstream/istringstream.html") (this is more C++ style). Make sure that you use the fail() method to check if the conversion was successful afterwards.

This is an example. Give a number as parameter to the program and it will be multiplied by 2.
[PHP]
// Multiply by 2
#include <sstream>
#include <iostream>

int main(int argsv, char **args) {
  if (argsv<2) {
    std::cout << "No number given" << std::endl;
    return 1;
  }	

  std::istringstream in(args[1]);

  float number;
  in >> number;

  if (in.fail()) {
    std::cout << "No valid number given" << std::endl;
    return 1;
  }	

  std::cout << "Multiplied by two, this is: " << number*2 << std::endl;
  return 0;
}[/PHP]

---

### Post by elpichi on 2008-06-14
For some reason atof() doesn't work for me, an error compiling got me stumped saying it could not convert a const char into a char, but istringstream works great, though it doesn't convert to floats, I converted the number and the decimals separately, then added them together.
Thanks for the answers

---

### Post by Jessehk on 2008-06-15
I like writing a little wrapper for converting from strings to other types.
I'm not exactly sure what you mean about floats not working...

```

#include <iostream>
#include <string>
#include <sstream>
#include <stdexcept>

template <typename T>
T fromString( const std::string &str ) {
    std::stringstream ss( str );
    T result;

    if ( ! (ss >> result) )
        throw std::invalid_argument( "Conversion error" );

    return result;
}

int main() {
    try {
        float pi = fromString<float>( "3.14159" );
    } catch ( std::exception &e ) {
        std::cout << e.what() << std::endl;
    }
}

```

---

### Post by elpichi on 2008-06-15
Whoa sorry a little piece of code was making me go nuts.
seems like setting precision to 2 messed up the output of my conversions so i was getting weird things like 2e+02 etc.

This is how i got it.

```

      float balance=0;
	string name, line;
	string match = "The ending balance for the account is: ";
	//check if file exist and create a new file if there isn't any
	ifstream inbudget;
	inbudget.open("budget.dat");	
	if(inbudget.is_open())
	{
	//if file exists it looks in the whole file for phrases similar to match
	while(inbudget)
	{
	int pos = -1; 		 //location of pointer
	getline(inbudget, line); //gets a line from the file and puts it inside line as a string
	pos = line.find('$'); 	 //sets location of posible places where money is represented
	
	if(match == line.substr(0, pos)) 	 //if a match comes up the number converted into a float and saved 
	balance = converter(line.substr(pos+1));		
	
	}
	inbudget.close();
	}

```

And this is how my function for convertion.
```

float converter(string number)
{
  float val;
  string stringvalues;

 istringstream iss (number,istringstream::in);
 iss >> val;

  return val;
}

```
don't really need to check for successful conversions since the file is only going to be edited by the program itself.

---

