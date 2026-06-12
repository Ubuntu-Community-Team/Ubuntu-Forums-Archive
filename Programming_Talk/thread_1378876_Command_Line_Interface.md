---
title: "Command Line Interface"
date: 2010-01-11
forum: Programming Talk
---

### Post by RevengeOfTidus on 2010-01-11
Hey everyone,

My friend and I are trying to create a basic command line interface to a research program we are doing.  We have basic/intermediate knowledge of C++ but are having trouble with making it "idiot-proof."  The program responds accordingly when we pass any integer value to the menu.  However, whenever we pass a char/string value, it freaks out and prints the menu loop infinite amounts of times, not prompting the user again.  What type of error-checking/correcting code should we use so that when the user inputs a char/string value, it re-prompts the user again?

Thank you for your time,
-RoT

```

#include <iostream>
#include <cmath>

using namespace std;

int main( int argc, char** argv ) {
    
    int choice = 0;

    cout << "Welcome to the OpenCV Test Program\n";
    cout << "Please choose from the following to test out certain functions\n";
    
    while (true){
        choice = 0;
        cout << "Note: Please do not enter anything but numbers!\n";
        cout << "1. Display snap.jpg \n";
        cout << "2. Display snap.jpg with 'grain'\n";
        cout << "3. Display snap.jpg with applied edge detection algorithm\n";
        cout << "4. Stream video\n";
        cout << "5. Stream video with applied edge detection algorithm\n WARNING: Resource intensive\n"; 
        cout << "6. Take picture from camera\n";
        cout << "7. Take picture and compare to snap.jpg (experimental)\n";
        cout << "8. Exit\n";
        cin >> choice;
        
        
        switch (choice){
    
        case 1 :    //choice 1
                break;
        case 2 :    //choice 2
                break;
        case 3 :    //choice 3
                break;
        case 4 :    //choice 4
                break;
        case 5 :    //choice 5
                break;
        case 6 :    //choice 6
                break;
        case 7 :    //choice 7
                break;
        case 8 :     "Thank you for your time \n";
                 exit(0);
        default :     "Please enter a choice from the menu\n";
                choice = 0;
                break;
    
        }//end switch
    }//end while
    
}

```

---

### Post by wmcbrine on 2010-01-12
Take a look here for some tips:

[http://augustcouncil.com/~tgibson/tutorial/iotips.html](http://augustcouncil.com/~tgibson/tutorial/iotips.html)

---

### Post by RevengeOfTidus on 2010-01-12
This seems to be what I'm looking for.  I'll give it a try soon.  Thanks!

---

### Post by miklcct on 2010-01-12
Simple way:
```

int x;
cin >> x;
if(!x) {
  // display error message
  string x;
  getline(cin, x); // discard the invalid line
}

```

Here's the full code used in my coursework, instead I take another approach: Read the entire line first and use wcstoul (for wchar_t string) or strtoul (for char string) to convert it to integer.
```

//! read a number with validation
/*! @return The number read
 */
std::size_t read_num() {
	std::size_t n;
	while(true) {
		std::wstring str;
		std::getline(std::wcin, str);
		if(str.empty()) {
			return -1;
		} else if(str[0] >= L'0' && str[0] <= L'9') {
			wchar_t *ptr;
			n = std::wcstoul(str.c_str(), &ptr, 10);
			if(!*ptr) {
				break;
			}
		}
		std::wcout << L"Invalid data entered. Try again: ";
		std::wcout.flush();
	}
	return n;
}

```

---

